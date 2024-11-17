# Juvei (Jubei) Quest

## Various:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0001 | Menu         |
| 0006 | Front character sprite x-coord
| 0007 | Front character sprite x-coord rollover | Increments/decrements when 0x0006 rolls 0xFF/0x00
| 0008 | Front character collision detection y-coord | Not sure why there isn't one for x-coord...  I may be wrong on what this is doing?
| 000A | Front character Sprite y-coord
| 0011 | Input Value  |
| 0013 | Input Check? | Briefly flashes to the same value as 0011 on input press, then flips back to 0x00
| 0018 | Movement indicator | Sets to 01 when character is moving.  Flips back to 00 when movement cycle completed
| 0020 | Timer for screen transition cycles (enter/exit towns and battles, etc) | If value frozen, screen will fade to black and stay there until value unfrozen
| 0092 | Something to do with exit locations and endpoints | Changing this may remove exits to/from towns and buildings. It may also change where they take you to.
| 00C5 | Something to do with enemy encounters | If value frozen, encounter is triggered
| 00D4 | Stops music. Not sure if drum channel still playing?
| 00D7 | Music channel/pattern
| 00F0 | Sprite animation | Freezing will lock your character in place, but NPCs will continue to slide around
| 0500 | Main Quest Slot 1 Character Status Pointer | This value seems to point to the spot in memory to get the character attributes + sprite for the STATUS screen
| 0501 | Main Quest Slot 2 Character Status Pointer | This value seems to point to the spot in memory to get the character attributes + sprite for the STATUS screen
| 0504 | Side-Quest Slot 1 Character Status Pointer | This value seems to point to the spot in memory to get the character attributes + sprite for the STATUS screen
| 0505 | Side-Quest Slot 2 Character Status Pointer | This value seems to point to the spot in memory to get the character attributes + sprite for the STATUS screen
| 0506 | Side-Quest Slot 3 Character Status Pointer | This value seems to point to the spot in memory to get the character attributes + sprite for the STATUS screen
| 0510 | Character Menu (A on Overworld) Slot 1
| 0512 | Character Menu (A on overworld) Slot 2 | Changing this value also gives you access to their inventory. The inventory will update on up/down, but the name won't update until you go in/out of the name menu or an inventory.
| 0514 | Sidequest Character Menu Slot 1 
| 0515 | Sidequest Character Menu Slot 2
| 0516 | Sidequest Character Menu Slot 3
| 05FC | Sound/Music Trigger | If a song is playing (ie: 0x90) you can change to a sound (ie: 0x01) and it will play both.

## 0x0001 Menu Values

***Careful!*** Some of these values will scuff your game up pretty bad.  Use  with caution!

***Note: Mostly only tested in main quest world***

| Byte | Notes | | Byte | Notes |
| ---  |  ---  |-| ---  | ---   |
| 00 | Forces intro cutscene over whatever screen you're on                                           || 10 | Flips between Main Quest world and Side Quest world
| 01 | Jubei name registration (will re-trigger start of game after setting and reset your character) || 11 | Helpers submenu
| 02 | Starting story cutscene                                                                        || 12 | Skills  submenu
| 03 | Not even sure                                                                                  || 13 | Arts    submenu
| 04 | Quick black screen then flips back to 05 and screen restores to where you were                 || 14 | Executes "Diary" to save game
| 05 | Regular gameplay screen (sort of a default value)                                              || 15 | Executes "Look" action
| 06 | Action menu                                                                                    || 16 | "Call me when you need to walk through the desert again" Executes desert auto-walk procedure
| 07 | Seems to be used to clear menus, but can't be set on its own                                   || 17 | Sabanosuke (water searching helper) action menu (Talk/Search/Return). Searching replaces your character with helper.  Returning is glitchy, but tries to take you back to where he was last spanwed.
| 08 | Executes "Talk" action                                                                         || 18 | "Jubei is Dead!"
| 09 | Fade out/in.  Used to teleport in/out of scenes.  Setting to 09 again takes you back to where you originally flipped to 09 || 19 | Sabanosuke dialogue: "Ugh... I'm so exhausted"
| 0A | Breaks tiles around character. Not sure where this is used                                     || 1A | Sabanosuke dialogue: "Can't swim any... more..." then triggers procedure that runs when helper gets exhausted.
| 0B | Triggers enemy encounter                                                                       || 1B | Plays "falling" sound then warps you the cave at Miminari Island.  This only works "properly" in the side-quest.  Will take you to scuffed area in main quest.
| 0C | Screen fade out/in, plays one of the town songs                                                || 1C | Calls "Time Priest" procedure
| 0D | "Select" screen overlay                                                                        || 1D | Dialogue: "I cannot leave everybody here!" Character then attempts to move 1 coordinate opposite to the direction they're facing
| 0E | Status submenu                                                                                 || 1E | Character moves several Y co-ordinates.  Sprite changes, dialogue shows "Here we are." Ryumi returned everyone to solid ground.
| 0F | Items submenu                                                                                  || 1F | Firefighter helper dialogue/action: "A-Ha! Burning wild,eh? I will take care of you! Here we go! Ain't no match for me!" Runs procedure to put out fire


| Byte | Notes | | Byte | Notes |
| ---  |  ---  |-| ---  | ---   |
| 20 | Firefighter helper dialogue: "Call me when you have more flames to battle!"                    || 30 | Locks characters, no other effect. Setting 05 fixes |
| 21 | Crashes game (Invalid OP Code) 	                                                              || 31 | Shows broken "Curse Curse" text on screen |
| 22 | Breaks graphics. Setting back to 05 fixes it                                                   || 32 | Locks characters, no other effect. Setting 05 allows control, but characters go flying, "Jubei is Dead" message shows, then map breaks.  |
| 23 | Breaks greaphics. Setting to 05 does not fix                                                   || 33 | Broken title screen |
| 24 | Locks characters, no other effect. Setting 05 fixes                                            || 34 | Locks characters, no other effect. Setting 05 fixes  |
| 25 | Locks characters, no other effect. Setting 05 fixes                                            || 35 | Plays water sound.  Locks characters.  On 05 displays broken actions menu. Action menu remains broken |
| 26 | Breaks graphics on overworlds (graphics appear fine in towns), locks characters. Setting to 05 unlocks but graphics are still broken || 36 | Like 35, but doesn't display/break the action menu |
| 27 | Crashes game (Invalid OP Code)                                                                 || 37 | Locks characters, freezes animation, no other effect. Setting 05 fixes  |
| 28 | Locks characters, no other effect. Setting 05 fixes                                            || 38 | Locks characters. Setting 05 fixes.  Map somewhat broken on edges after flipping back to 05 |
| 29 | Crashes game (Invalid OP Code)                                                                 || 39 | Locks characters, changes Jubei's sprite to 4 circles. Setting 05 unlocks movement, sprite still broken |
| 2A | Crashes game (Invalid OP Code)                                                                 || 3A | Crashes game (Invalid OP Code) |
| 2B | Locks characters, no other effect. Setting 05 fixes                                            || 3B | Moves Ryumi into Jubei, locks movement. Flip back to 05 to unlock, Ryumi will be missing |
| 2C | Crashes game (Invalid OP Code). Recoverable by setting back to 05                              || 3C | Breaks graphics. Flipping to 05 does not fix |
| 2D | Locks characters, no other effect. Setting 05 fixes                                            || 3D | Breaks graphics. Flipping to 05 does not fix |
| 2E | Locks characters, no other effect. Setting 05 fixes                                            || 3E | Locks characters, no other effect. Setting 05 fixes |
| 2F | Splash animation (used by Sabanosuke when diving)                                              || 3F | Crashes game (Invalid OP Code) |

| Byte | Notes | | Byte | Notes |
| ---  |  ---  |-| ---  | ---   |
| 40 | Plays tune. Flip back to 05 to fix                                                             || 50 | Characters disappear. Flipping 05 restores movement but not sprites
| 41 | Characters disappear. Flipping 05 restores movement but not sprites                            || 51 |  Crashes game (Invalid OP Code)
| 42 | Crashes game (Invalid OP Code)                                                                 || 52 |  Crashes game (Invalid OP Code)
| 43 | Crashes game                                                                                   || 53 | Glitches character sprites, doesn't seem to affect gameplay
| 44 | Causes background tiles Black to flash Magenta                                                 || 54 | Locks characters, no other effect. Setting 05 fixes
| 45 | Plays splashing SFX, then crashes game (Invalid OP Code)                                       || 55 | Locks characters, no other effect. Setting 05 fixes
| 46 | Crashes game (Invalid OP Code)                                                                 || 56 | Crashes game (Invalid OP Code) 
| 47 | Crashes game (Invalid OP Code)                                                                 || 57 | Crashes game (Invalid OP Code) 
| 48 | Crashes game (Invalid OP Code)                                                                 || 58 | Crashes game (Invalid OP Code). Flip back to 05 to restore
| 49 | Displays broken letter entry. Flip back to 05 to fix                                           || 59 | Crashes game (Invalid OP Code) 
| 4A | Causes background tiles Black to flash Magenta                                                 || 5A | Locks characters, Jubei disappears. Flip to 05 to restore movement. Ryume disappeared after entering town.
| 4B | Screen goes black.  Game still responsive.  Set to 4A then 05 to fix                           || 5B | Locks movement, places black square behind Jubei.  Causes Jubei to twirl. Movement restored with 05, some graphics broken.
| 4C | Ryumi moves into Jubei. Movement locked.  Set to 05 to restore movement, but may be stuck in invisible walls  || 5C | Locks characterrs, Screen flashes black. Restores with 05, graphics still broken. Can repair by entering/leaving town
| 4D | Jubei flickers. Setting to 05 moves Jubei 1 coordinate opposite to the direction he's facing   || 5D | Locks charcters. No further effects.  Set back to 05 to restore
| 4E | Corrupts graphics.  Chracters auto-travel along predetermined route.  Seems to be manipulatable, not sure how it works.  Setting back to 05 does not fix graphics || 5E | Characters locked, explosion SFX and screen shake. Set to 05 to end SFX and shake and restore movement.
| 4F | Crashes game (Invalid OP Code) Partially recoverable by flipping back to 05                    || 5F | Breaks graphics, throws Invalid OP Code.  Recoverable by setting to 05 and entering/leaving town.

| Byte | Notes | | Byte | Notes |
| ---  |  ---  |-| ---  | ---   |
| 60 | Locks characters, triggers explosion SFX. Throws invalid OP cde. Set to 05 to recover          || 70 | Crashes game (Invalid OP Code). Unrecoverable 
| 61 | Same as 60 without the Invalid OP Code                                                         || 71 | Locks characters, breaks some sprites. Set to 05 to restore
| 62 | Same as 61                                                                                     || 72 | Crashes game (Invalid OP Code). Unrecoverable
| 63 | Crashes game, Invalid OP code.  Unrecoverable                                                  || 73 | Locks characters, breaks character sprites. Set to 05 to unlock. Enter/exit town to reset sprites
| 64 | Locks characters, throws invalid OP Code.  Set back to 05 to recover                           || 74 | Crashes game (Invalid OP Code). Unrecoverable 
| 65 | Locks characters. No other effect. Set back to 05 to recover                                   || 75 | Locks characters. No other effect. Set back to 05 to recover
| 66 | Locks characters, throws invalid OP Code.  Set back to 05 to recover                           || 76 | Crashes game (Invalid OP Code). Unrecoverable 
| 67 | Locks characters, throws invalid OP Code.  Set back to 05 to recover                           || 77 | Like 1B but with a fade out/in instead of the falling SFX 
| 68 | Locks characters, throws invalid OP Code.  Set back to 05 to recover                           || 78 | Crashes game. No error. Unrecoverable
| 69 | Crashes game (Invalid OP Code). Unrecoverable                                                  || 79 | Locks characters, throws invalid OP Code.  Set back to 05 to recover    
| 6A | Crashes game (Invalid OP Code). Unrecoverable                                                  || 7A | Locks characters. No other effect. Set back to 05 to recover
| 6B | Locks characters. No other effect. Set back to 05 to recover                                   || 7B | Crashes game. No error. Unrecoverable
| 6C | Crashes game (Invalid OP Code). Unrecoverable                                                  || 7C | Crashes game (Invalid OP Code). Unrecoverable  
| 6D | Locks characters. No other effect. Set back to 05 to recover                                   || 7D | Locks characters, breaks sprites, throws Invalid OP Code. Flip back to 05 to fix.  Enter/exit town to correct sprites
| 6E | Locks characters, breaks some sprites. Set to 05 to restore, enter/exit town to fix broken sprites || 7E | Crashes game. No error. Unrecoverable
| 6F | Crashes game (Invalid OP Code). Unrecoverable                                                  || 7F | Crashes game (Invalid OP Code). Unrecoverable    

0x80 overflows loops back to 0x00 effect and so on


## 0x0011 Input Values:

*Note pressing multiple inputs adds the byte values together.
ie: Up-Left = 08 + 02 = 0A

| Byte | Input  |
| ---  |  ----  |
|  01  | Right  |
|  02  | Left   |
|  04  | Down   |
|  08  | Up	    |
|  10  | Start  |
|  20  | Select |
|  40  | B      |
|  80  | A      |




## 0x0500 - 0x0506 Values (assuming default names)
| Byte | Value |
| ---  |  ---  |
| 00 | Jubei   |
| 01 | Corrupt Value |
| 02 | Ryumi   |
| 03 | Sabu    |
| 04 | Onitan  |
| 05 | Shiro   |
| 06 | Feeny   |
| 07 | Corrupt Value |
| 08 | >=0x08 will set Jubei |
| | Setting a character in the wrong "world" will show a corrupt sprite

## 0x0510 & 0x0512 Values (assuming default names)
| Byte | Value | | Byte | Value   | Notes |
| ---  |  ---  |-| ---  |  ---    | ----- |
| 00 | Jubei   | | 08 | Penta     | Shares same INV address as Onitan
| 02 | Wolf    | | 09 | Lucky     | Shares same INV address as Shiro
| 03 | Ivan    | | 0A | ...T      | Shares same INV address as Feeny
| 04 | Onitan  | | 0B | Rock      | Shares same INV address as Shiro
| 05 | Shiro   | | 0C | Tamas     | Shares same INV address as Onitan
| 06 | Feeny   | | 0D | PqikkuQ L | Corrupt/Invalid nane.  Share same INV slot as Shiro
| 07 | Saru    | | 0E | ...T      | Shares same INV address as Feeny
|    |         | | 0F | ...T      | Shares same INV as Feeny

### Money
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0508 | Ryo Amount | Main Quest Currency
| 0509 | Ryo Overflow | Increments 0x01 every time 0x0508 rolls FF
| 050A | Ryo Overflow Overflow | Increments 0x01 every time 0x0508 rolls FF
| 050C | Peach Amount | Side Quest Currency
| 050D | Peach Overflow | Increments 0x01 every time 0x050C rolls FF
| 050E | Peach Overflow Overflow | Increments 0x01 every time 0x050D rolls FF

### Map Party Location info
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 05E8 - 05EB | This has something to do with the formation of your party. | `0x6C` `0x6C` `0x6C` when party is 3x horizontal
| 05EC - 05EF    | Something to do with Y-coordinate distance between party and NPCs
| 05F8 | Used when `FLIRT`ing and `SCOUT`ing.  Tracks Y-distance from main hero.  If you freeze this value, the main hero moves vertically instead of being locked into place.  You can still `TALK` to the empty spot where the hero should be to return to normal. | Will self-correct as soon as you un-freeze the value and move your character up/down 1 unit.
| 05FA | Same as 05F8, but for the other non-controlled character during that should be locked into place.

### Battle Stuff:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 00EB | Damage (given and received)
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
| 0550 | Experience Overflow Overflow | Increments 0x01 every time 0x0548 > 0XFF
| 0558 | Condition   |
| 0598 | Kenpo Dan   | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05B8 | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C0 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C8 | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D0 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D8 | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E0 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0578 | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0580 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 0588 | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
|  | 
| | |
| 1B00 - 1B06 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable
| 0B06 - 0B0B | Dodonkey Slots 1 through 5

#### Ryumi:
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
| 054A | Experience Overflow | Increments by 0x01 every time 0x0542 > 0xFF
| 0552 | Experience Overflow Overflow | Increments by 0x01 each time 0x54A > 0xFF
| 055A | Condition       |
| 05BA | Attack          | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C2 | Defense         | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CA | Speed           | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D2 | Luck            | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DA | Spirit          | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0569 | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0582 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058A | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| 059A | Race |
| | |
| 131A - 1320 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable
| 1321 - 1325 | Dodonkey Slots 1 through 5


#### Onitan:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053C | Level       |
| 0564 | Current HP  |
| 05A4 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0574 | Current AP  |
| 05B4 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0544 | Experience  |
| 054C | Experience Overflow | Increments by 0x01 when 0x0544 > FF
| 0554 | Experience Overflow Overflow | Increments by 0x01 when 0x054C > FF
| 055C | Condition   |
| 05BC | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C4 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CC | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D4 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DC | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E4 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 057C | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0584 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058C | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 0334 - 033A | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

### Shiro:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053D | Level       |
| 0565 | Current HP  |
| 05A5 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0575 | Current AP  |
| 05B5 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0545 | Experience  |
| 054D | Experience Overflow | Increments by 0x01 when 0x0545 > FF
| 0555 | Experience Overflow Overflow | Increments by 0x01 when 0x54D > FF
| 055D | Condition   |
| 05BD | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C5 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CD | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D5 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DD | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E5 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 057D | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0585 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058D | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 0341 - 0347 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

### Feeny:
| Address | Modifies | Notes
| --- | --- | --- |
| 053E | Level       |
| 0566 | Current HP  |
| 05A6 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0576 | Current AP  |
| 05B6 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0546 | Experience  |
| 054E | Experience Overflow | Increments by 0x01 when 0x0546 > FF
| 0556 | Experience Overflow Overflow | Increments by 0x01 when 0x054E > FF
| 055E | Condition   |
| 05BE | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C6 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CE | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D6 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DE | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E6 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 057E | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0586 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058E | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 034E - 0354 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

### Saru:
| Address | Modifies | Notes
| --- | --- | --- |
| 053F | Level       |
| 0567 | Current HP  |
| 05A7 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0577 | Current AP  |
| 05B7 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0547 | Experience  |
| 054F | Experience Overflow | Increments by 0x01 when 0x0547 > FF
| 0557 | Experience Overflow Overflow | Increments by 0x01 when 0x054F > FF
| 055F | Condition   |
| 05BF | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C7 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CF | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D7 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DF | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E7 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 057F | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0587 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058F | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 035B - 0361 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

## Character Races
| Value   | Race | Notes |
|   ---   |  --------------  |  ---  |
| 00 | ???
| 01 | ???
| 02 | Dragon | Anything >01 sets "Dragon"

## Conditions
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


## Inventory Items
|  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    |
|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |
| 00 | Empty Slot      | | 10 | Cosmotron       | | 20 | Atlas           | | 30 | Old  Fang 3     |
| 01 | Scroll Box      | | 11 | Viper Orb       | | 21 | Atlas           | | 31 | Old Armor 2     |
| 02 | 10              | | 12 | Fire Feather    | | 22 | Undecided 34    | | 32 | Old Armor 3     |
| 03 | Daifuku         | | 13 | Dodonkey        | | 23 | Norn's Tear     | | 33 | Adult Magazine  |
| 04 | 50 pb           | | 14 | Fried Tofu      | | 24 | Fire Sake       | | 34 | Blue Book       |
| 05 | 100 pb          | | 15 | "Zippo" Oil     | | 25 | Baldonite       | | 35 | Crystal Ball    |
| 06 | Old Fang 2      | | 16 | Burnt Grass     | | 26 | Yawny Mukkuri   | | 36 | Teardrop        |
| 07 | Old Armor 1     | | 17 | Undecided 23    | | 27 | Baldon Burst    | | 37 | Undecided 55    |
| 08 | Snow Gun        | | 18 | E-Interpreter   | | 28 | Ancient Flame   | | 38 | Golden Shell    |
| 09 | 500 pb          | | 19 | Dark Hammer     | | 29 | Iron Pipe       | | 39 | Teleport Stone  |
| 0A | 1000 pb         | | 1A | Trampoline      | | 2A | Occulton        | | 3A | Missile Pod     |
| 0B | Gold Coin       | | 1B | Bean Sprout     | | 2B | Ancient Gun     | | 3B | Palm Rocket     |
| 0C | Undecided 12    | | 1C | Bingbing        | | 2C | Ancient ?       | | 3C | Old Fang 1      |
| 0D | Bagra Seed      | | 1D | Sandblalst Lamp | | 2D | Undefined 45    | | 3D | Old Collar      |
| 0E | Ath Staff       | | 1E | Foliage Set     | | 2E | Doll Key        | | 3E | Old Fang 4      |
| 0F | Gain Burst      | | 1F | Megaton Coin    | | 2F | Sealing Sphere  | | 3F | Dragon Orb      |

|  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    |
|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |
| 40 | Return Orb      | | 50 | Pharoa Key      | | 60 | Undecided 96    | | 70 | Lightning Rod   |
| 41 | Undecided 65    | | 51 | Cold Key        | | 61 | Undecided 97    | | 71 | Makibishi       |
| 42 | Herb            | | 52 | Manju           | | 62 | Oni Tear        | | 72 | Undecided       |
| 43 | Antidote        | | 53 | Chocolate       | | 63 | Wedding Gift    | | 73 | Golden Diamond  |
| 44 | Elixir          | | 54 | Undecided 84    | | 64 | Throttle Ball   | | 74 | Crazy Gas       |
| 45 | Burn Cure       | | 55 | Dynamite Sake   | | 65 | Golden Orb      | | 75 | Ancient Metal   |
| 46 | Pip             | | 56 | Sake            | | 66 | Machine Gun     | | 76 | Fullmetal Bomb  |
| 47 | Reviver         | | 57 | Plum Sake       | | 67 | Snow Machine    | | 77 | Smoke Bomb      |
| 48 | All-Reviver     | | 58 | Para Beer       | | 68 | Molotov         | | 78 | Undecided       |
| 49 | Dungeon Key     | | 59 | Sake Barrel     | | 69 | Fireball        | | 79 | Shocker         |
| 4A | Jail Key        | | 5A | Cursed Key      | | 6A | Flamethrower    | | 7A | Bird Lime       |
| 4B | Eel Key         | | 5B | Reed Flute      | | 6B | Cannon          | | 7B | Laughing Gas    |
| 4C | Shell Key       | | 5C | Bat Flute       | | 6C | Bazooka         | | 7C | Smoky Gas       |
| 4D | Bat Key         | | 5D | Gohei Cake      | | 6D | Earth Hammer    | | 7D | Oni Drum        |
| 4E | Undefined 78    | | 5E | Ice Mint        | | 6E | Aqua Gun        | | 7E | Ice Bowl        |
| 4F | Cigarette       | | 5F | Gatling Gun     | | 6F | Stun Gun        | | 7F | Ice Harp        |

|  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    |
|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |
| 80 | Undecided       | | 90 | Shinkage        | | A0 | Hibagon Suit    | | B0 | Cloudy Sword    |
| 81 | Undecided       | | 91 | Mursame         | | A1 | Thunder Plate   | | B1 | Mountain Spear  |
| 82 | Undecided       | | 92 | Yama Arashi     | | A2 | Carver Sword    | | B2 | Serene Sword    |
| 83 | Baramos         | | 93 | Unryu           | | A3 | Yamabushi Cane  | | B3 | Scimitar        |
| 84 | Gamellun        | | 94 | Mesamune        | | A4 | Ivory Knife     | | B4 | Commoner        |
| 85 | Fencer          | | 95 | Laser Sword     | | A5 | Sengoku Sword   | | B5 | Ninja           |
| 86 | Aurora Guard    | | 96 | Shinobi Katana  | | A6 | Eagre Sword     | | B6 | Thorny Pads     |
| 87 | Chain Collar    | | 97 | Battle Surcoat  | | A7 | Naginata        | | B7 | Holy Plate      |
| 88 | Ogre Fang       | | 98 | Shinobi Cloth   | | A8 | Fang Spear      | | B8 | Mameluke        |
| 89 | Ice Blade       | | 99 | Chain Mail      | | A9 | Ivory Katana    | | B9 | Musashi         |
| 8A | Pyramid Sword   | | 9A | Shinobi Armor   | | AA | Crying Sword    | | BA | Idaten          |
| 8B | Campo Cane      | | 9B | Ripple Plate    | | AB | Cement Grout    | | BB | Genghis Khan    |
| 8C | Hightech Sword  | | 9C | Whirling Plate  | | AC | Yamata Sword    | | BC | Marfia          |
| 8D | Iron Spear      | | 9D | Rose Armor      | | AD | Smashing Fang   | | BD | Health          |
| 8E | Ultimate Fnag   | | 9E | Purple Hood     | | AE | Falcon Plate    | | BE | Oni Claw        |
| 8F | Short Sword     | | 9F | Aster Armor     | | AF | Breaking Fang   | | BF | Oni Fang        |

|  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    | |  Value  |    Item    |
|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |-|   ---   |  --------  |
| C0 | Ancient Icicle  | | D0 | Thunder Sword   | | E0 | Red Hood        | | F0 | Warden          |
| C1 | Heavy Log       | | D1 | Ryozan Sword    | | E1 | Battle Armor    | | F1 | Hermit          |
| C2 | Blunt Club      | | D2 | Metal Spear     | | E2 | Mink Suit       | | F2 | Immortal        |
| C3 | Club            | | D3 | Golden Sword    | | E3 | Alpha Oil       | | F3 | Maitreya        |
| C4 | Oni Collar      | | D4 | Glacier Sword   | | E4 | Metal Armor     | | F4 | Guardian        |
| C5 | Leather Collar  | | D5 | Dragon Spear    | | E5 | Branded Suit    | | F5 | Cosmos          |
| C6 | Tiger Pants     | | D6 | Shiranui        | | E6 | Golden Cross    | | F6 | Dreamer         |
| C7 | Blade Wing      | | D7 | Aura Blade      | | E7 | Princess Dress  | | F7 | Ice Pick        |
| C8 | Valor Pants     | | D8 | Steel Fang      | | E8 | Last Armor      | | F8 | Charm Cane      |
| C9 | Headgear        | | D9 | Edomae Sword    | | E9 | Plasma Oil      | | F9 | Ice Cutter      |
| CA | Flame Wing      | | DA | Ceramic Club    | | EA | Dragon Suit     | | FA | Glacier Cane    |
| CB | Nyoi Staff      | | DB | Ath Spear       | | EB | Hyper Suit      | | FB | Tuxedo          |
| CC | Red Fundoshi    | | DC | Titan Pillar    | | EC | Iron Collar     | | FC | Aurora Suit     |
| CD | Gold Fundoshi   | | DD | Chinese Dress   | | ED | Zeus            | | FD | Charm Clothes   |
| CE | Huge Club       | | DE | Carbon Suit     | | EE | Iron            | | FE | Ice Clothes     |
| CF | Stone Head      | | DF | Dragon Clothes  | | EF | Tyson           | | FF | Empty Slot      |



## Inventory Notes

| Value   | Item | Notes |
|   ---   |  --------------  |  ---  |
| 02 | 10 | Not really sure what this item is about
| 04, 05, 09, 0A | "pb" items  | Corrupt/invalid item of some sort
| 0C | Undecided 12 | Not sure if this is something the translation team was confused about and just left as-is?  The number seems to correlate to the decimal value of their hex value
| 2D | Undefined 45 | There are 2 "Undefined" items amidst the Undecided items.  Not sure why.
| 20 | Atlas | This expands to the individual Atlas pages 
| 21 | Atlas | This item throws "The atlas can't be used here" in both main-quest and side-quest

## Notes:

- Attack/Defense etc are only checked when entering a battle and if any stat buff/debuff spells are used.  They are not read each turn, so if you nerf your character stats, have fun with that until you can freeze in a value and cast a buff on yourself (or get the enemy to try to debuff you) to force a re-read of the address.

- If you target a spot where you already killed the enemy (via `0x064E`), it will cause the sprite to appear back on screen.  You can then attack that monster again and kill it, which will add to the counter of defeated monsters.  Thus, you could "respawn" a weak enemy and keep attacking it, which will end the battle as if you killed it and the stronger ones.

- Changing the value at `064E` will change the monster that receives the effects of the attack, despite the monster that your character is in front of.  The battle animation will continue to play out for that monster, too.

- Chaacter "Class" lengths are 1 character shorter than weapon/armor names.

- Side-quest characters (Onitan, Shiro, Feeny) can have dodonkeys hacked into their INV, but the Dodonkeys don't have valid addresses to store items.  Giving to a character with full INV with dodonkey hacked in throws standard "no room left to hold anything" message.

## Things I'd like to find still:

- Location bytes for quick-warp

- How to manipulate encounters

- Forgot to look out the Depository addresses
