# Juvei (Jubei) Quest

## Various:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 05FC | Sound/Music Trigger | If a song is playing (ie: 0x90) you can change to a sound (ie: 0x01) and it will play both.


### Money
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0503 | Gold Amount | Main Quest Currency
| 050C | Peach Amount | Side Quest Currency

### Map Party Location info
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 05E8 - 05EA | This has something to do with the formation of your party. | `0x6C` `0x6C` `0x6C` when party is 3x horizontal
| 05EC - 05EF    | Something to do with Y-coordinate distance between party and NPCs
| 05F8 | Used when `FLIRT`ing and `SCOUT`ing.  Tracks Y-distance from main hero.  If you freeze this value, the main hero moves vertically instead of being locked into place.  You can still `TALK` to the empty spot where the hero should be to return to normal. | Will self-correct as soon as you un-freeze the value and move your character up/down 1 unit.
| 05FA | Same as 05F8, but for the other non-controlled character during that should be locked into place.

### Battle Stuff:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 064C | Something with battle attack animation/timing  | Might be a boolean indicator that a player character is actively attacking an enemy?  Flips to 01 when ATK ART used against enemy. Flips to 01 when DEBUFF ART used against enemy. Stays 00 when BUFF ART used on own team 
| 064E | Enemy number being attacked (00 = first enemy) | Confirmed not used for the player character being attacked by enemy
| 064D | Enemy visibility? | Seems to stick to 0x80 and self-correct to that value if changed.  If frozen to another value, enemy sprite will disappear when hit.
| 064F | Something with battle attack animation/timing  | Flips 00/01 several times per attack phase.
| 065C | Something with enemy sprite animations during battle | Flips between 00 and 02, looks like it may have something to do with ending turn cycles?

### Character Attributes:

#### Jubei:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0538 | Level       | Character level defines attribute values, arts/skills, and EXP cap
| 0560 | Current HP  |
| 0568 | HP Overflow | Increments by 0x01 each time 0x0506 > 0xFF
| 05A0 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05A8 | Max HP Overflow | Increments by 0x01 when 0x05A0 is > 0xFF
| 0570 | Current AP  |
| 05B0 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0540 | Experience  |
| 0548 | Experience Overflow | Increments by 0x01 every time 0x0540 > 0xFF
| 0558 | Condition   |
| 0598 | Kenpo Dan   | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05B8 | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C0 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C8 | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D0 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D8 | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E0 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level

#### Ryume:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053A | Level | Character level defines attribute values, arts/skills, and EXP cap
| 0562 | Current HP  | 
| 056A | HP Overflow | Increments by 0x01 each time 0x0562 > 0xFF
| 05A2 | Max HP      | 
| 05AA | Max HP Overflow | Increments by 0x01 when 0x05A2 is > 0xFF
| 0572 | Current AP  |
| 05B2 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level 
| 0542 | Experience      | 
| 054A | Experience Overflow | Increments by 0x01 every time 0x0542 > 0x FF
| 055A | Condition       |
| 05BA | Attack          | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C2 | Defense         | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CA | Speed           | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D2 | Luck            | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DA | Spirit          | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level

#### Onitan:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053C | Level       |
| 0564 | Current HP  |
| 05A4 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0574 | Current AP  |
| 05B4 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0544 | Experience  |
| 054C | Experience Overflow | Increments by 0x01 when 0x0544 > 255
| 055C | Condition   |
| 05BC | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C4 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CC | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D4 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DC | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E4 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| | |
| 0334 - 033A | Inventory Slots 1 through 7 | If invalid/0x00 set on INV slot, all following slots will be blank and unselectable


### Shiro:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053D | Level       |
| 0565 | Current HP  |
| 05A5 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0575 | Current AP  |
| 05B5 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0545 | Experience  |
| 054D | Experience Overflow | Increments by 0x01 when 0x0545 > 255
| 055D | Condition   |
| 05BD | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C5 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CD | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D5 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DD | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E5 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level

### Feeny:
| Address | Modifies | Notes
| --- | --- | --- |
| 053E | Level       |
| 0566 | Current HP  |
| 05A6 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0576 | Current AP  |
| 05B6 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0546 | Experience  |
| 054E | Experience Overflow | Increments by 0x01 when 0x0546 > 255
| 055E | Condition   |
| 05BE | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C6 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CE | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D6 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DE | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E6 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level



| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
|  | Level       |
|  | Current HP  |
|  | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Current AP  |
|  | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Experience  |
|  | Condition   |
|  | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level

### Conditions
| Value   | Status Condition | Notes |
|   ---   |  --------------  |  ---  |
| 0x00 | Normal | |
| 0x01 | Sleep | |
| 0x02 | Freeze | | 
| 0x03 | Not used, corrupted | ![Corrupted status](images/Juvei-Quest/juvei-condition-0x03.png) |
| 0x04 | Curse | |
| 0x05 | Seal | |
| 0x06 | Sick | |
| 0x07 | Poison | |
| | | Unlike the other statuses which need the panel to be refreshed to update, setting to 0x08 or 0x09 will immediately display the status icon beside whatever status you currently are |
| 0x08 | Puts red dude sprite next to status | ![Red dude sprite](images/Juvei-Quest/juvei-condition-0x08.png) |
| 0x09 | Puts ghost sprite next to status | ![Ghost sprite](images/Juvei-Quest/juvei-condition-0x09.png) |
| | | The rest are invalid status bytes |
| 0x0A | 0x0A and on appear to all be corrupted statuses | ![Corrupted status](images/Juvei-Quest/juvei-condition-0x0A.png) ![Corrupted status](images/Juvei-Quest/juvei-condition-0x0B.png)

## Notes:

- Attack/Defense etc are only checked when entering a battle and if any stat buff/debuff spells are used.  They are not read each turn, so if you nerf your character stats, have fun with that until you can freeze in a value and cast a buff on yourself (or get the enemy to try to debuff you) to force a re-read of the address.

- If you target a spot where you already killed the enemy (via `0x064E`), it will cause the sprite to appear back on screen.  You can then attack that monster again and kill it, which will add to the counter of defeated monsters.  Thus, you could "respawn" a weak enemy and keep attacking it, which will end the battle as if you killed it and the stronger ones.

- Changing the value at `064E` will change the monster that receives the effects of the attack, despite the monster that your character is in front of.  The battle animation will continue to play out for that monster, too.

## Things I'd like to find still:

**Individual character EXP**  
`0x0540` and `0x0541` may be handling Jubei's EXP.  
`0x953E` and `0x053F` may be handling Ryume's EXP.

Both of these values behave kind of strangely.  They definitey do some math off another address.  You can set the value to FF, then defeat a monster and set to FF again and the EXP value will continue to increment (if I recall correctly).  In any case, it's not as straight-forward as just hunting down the exact EXP values to find the addresses.
