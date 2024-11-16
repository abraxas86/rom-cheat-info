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
| 0578 | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0580 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 0588 | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 1B00 - 1B06 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

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
| 0569 | Equipped Weapon | Equipping any weapon/armour will adjust ATK. Equipping anything else will drop to base value.
| 0582 | Equipped Armour | Equipping any weapon/armour will adjust DEF. Equipping anything else will drop to base value.
| 058A | Equipped Class  | Equipping any class will adjust stats. Equipping anything else will drop to base value.
| | |
| 131A - 1320 | Inventory Slots 1 through 7 | If set to 0x00 or 0xFF, all following slots will be blank and unselectable

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
| 054D | Experience Overflow | Increments by 0x01 when 0x0545 > 255
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
| 054E | Experience Overflow | Increments by 0x01 when 0x0546 > 255
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

## Things I'd like to find still:

**Individual character EXP**  
`0x0540` and `0x0541` may be handling Jubei's EXP.  
`0x953E` and `0x053F` may be handling Ryume's EXP.

Both of these values behave kind of strangely.  They definitey do some math off another address.  You can set the value to FF, then defeat a monster and set to FF again and the EXP value will continue to increment (if I recall correctly).  In any case, it's not as straight-forward as just hunting down the exact EXP values to find the addresses.
