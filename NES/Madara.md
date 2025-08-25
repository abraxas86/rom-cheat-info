# Madara (Mouryou Senki Madara)

Note: My copy of the game was patched using the English translation by Aeon Genesis.


### Gold (coins/money, it goes by a few names)
| Address   | Modifies                               |
|-----------|----------------------------------------|
| 06A0-06A2 | Modifies money in hand (Little-endian) |

## Character Stats

> **Note:** These stats are **not** laid out in memory in the same order as the in-game stats screen.

### Strength
| Address | Modifies             | Notes  |
|---------|----------------------|--------|
| 0618    | Team slot 1 Strength | Madara |
| 0619    | Team slot 2 Strength | Kirin  |
| 061A    | Team slot 3 Strength |        |
| 061B    | Team slot 4 Strength |        |

### Wisdom
| Address | Modifies           | Notes |
|---------|--------------------|-------|
| 061C    | Team slot 1 Wisdom |       |
| 061D    | Team slot 2 Wisdom |       |
| 061E    | Team slot 3 Wisdom |       |
| 061F    | Team slot 4 Wisdom |       |

### Agility
| Address | Modifies            | Notes |
|---------|---------------------|-------|
| 0620    | Team slot 1 Agility |       |
| 0621    | Team slot 2 Agility |       |
| 0622    | Team slot 3 Agility |       |
| 0623    | Team slot 4 Agility |       |

### Charm
| Address | Modifies          | Notes |
|---------|-------------------|-------|
| 0624    | Team slot 1 Charm |       |
| 0625    | Team slot 2 Charm |       |
| 0626    | Team slot 3 Charm |       |
| 0627    | Team slot 4 Charm |       |

### HP

> HP values are stored as 2-byte little-endian integers:  
> `(High Byte * 256) + Low Byte`  
> Example: `0638` = `0C`, `0639` = `04` → HP = `04 * 256 + 0C = 1036`  
> Values beyond `0F27` (9999) will overflow and not display properly.

| Address   | Modifies               | Notes |
|-----------|------------------------|-------|
| 0638–0639 | Team slot 1 Current HP |       |
| 063A–063B | Team slot 2 Current HP |       |
| 063C–063D | Team slot 3 Current HP |       |
| 063E–063F | Team slot 4 Current HP |       |
| 0640–0641 | Team slot 1 Max HP     |       |
| 0642–0643 | Team slot 2 Max HP     |       |
| 0644–0645 | Team slot 3 Max HP     |       |
| 0646–0647 | Team slot 4 Max HP     |       |

### MP

> MP follows the same encoding rules as HP (2-byte little-endian).

| Address   | Modifies               | Notes |
|-----------|------------------------|-------|
| 0648–0649 | Team slot 1 Current MP |       |
| 064A–064B | Team slot 2 Current MP |       |
| 064C–064D | Team slot 3 Current MP |       |
| 064E–064F | Team slot 4 Current MP |       |
| 0650–0651 | Team slot 1 Max MP     |       |
| 0652–0653 | Team slot 2 Max MP     |       |
| 0654–0655 | Team slot 3 Max MP     |       |
| 0656–0657 | Team slot 4 Max MP     |       |


### Inventory (Belt)
> Item slots appear to store item bytes from the item tables below

| Address | Modifies      |   | Address | Modifies      |   | Address | Modifies      |   | Address | Modifies      |
| ------- | ------------- | - | ------- | ------------- | - | ------- | ------------- | - | ------- | ------------- |
| 0680    | Team 1 Slot 1 |   | 0688    | Team 2 Slot 1 |   | 0690    | Team 3 Slot 1 |   | 0698    | Team 4 Slot 1 |
| 0681    | Team 1 Slot 2 |   | 0689    | Team 2 Slot 2 |   | 0691    | Team 3 Slot 2 |   | 0699    | Team 4 Slot 2 |
| 0682    | Team 1 Slot 3 |   | 068A    | Team 2 Slot 3 |   | 0692    | Team 3 Slot 3 |   | 069A    | Team 4 Slot 3 |
| 0683    | Team 1 Slot 4 |   | 068B    | Team 2 Slot 4 |   | 0693    | Team 3 Slot 4 |   | 069B    | Team 4 Slot 4 |
| 0684    | Team 1 Slot 5 |   | 068C    | Team 2 Slot 5 |   | 0694    | Team 3 Slot 5 |   | 069C    | Team 4 Slot 5 |
| 0685    | Team 1 Slot 6 |   | 068D    | Team 2 Slot 6 |   | 0695    | Team 3 Slot 6 |   | 069D    | Team 4 Slot 6 |
| 0686    | Team 1 Slot 7 |   | 068E    | Team 2 Slot 7 |   | 0696    | Team 3 Slot 7 |   | 069E    | Team 4 Slot 7 |
| 0687    | Team 1 Slot 8 |   | 068F    | Team 2 Slot 8 |   | 0697    | Team 3 Slot 8 |   | 069F    | Team 4 Slot 8 |


## Items

### Equippables
> Equipped items use the number in brackets in the tables below. Note that injecting these values into the belt slots will not apply the item stats. You will need to unequip/equip the item to get the stat buffs. This means you can't equip invalid items to classes that can't handle them - you also won't be able to unequip them unless you drop the item or manually edit the memory address

# Swords/Blades

| Byte    | Swords          |   | Byte    | Swords       |   | Byte    | Swords           |
| ------- | --------------- | - | ------- | ------------ | - | ------- | ---------------- |
| 00 (80) | Kusanagi Blade  |   | 05 (85) | Kasumi Blade |   | 0A (8A) | Ashura Blade     |
| 01 (81) | Light Kusanagi  |   | 06 (86) | Pope Blade   |   | 0B (8B) | Susano Blade     |
| 02 (82) | Seiken Kusanagi |   | 07 (87) | Scion Blade  |   | 0C (8C) | Salamander Blade |
| 03 (83) | Knife           |   | 08 (88) | Yasha Blade  |   | 0D (8D) | Karma Blade      |
| 04 (84) | Sword           |   | 09 (89) | Myouo Blade  |   |         |                  |


#### Axes / Spears / Bows
| Byte    | Axes           |   | Byte    | Spears           |   | Byte    | Bows       |
| ------- | -------------- | - | ------- | ---------------- | - | ------- | ---------- |
| 0E (8E) | Stone Axe      |   | 13 (93) | Spear            |   | 18 (98) | Bow        |
| 0F (8F) | Tomahawk       |   | 14 (94) | Long Spear       |   | 19 (99) | Big Bow    |
| 10 (90) | Kamaitachi Axe |   | 15 (95) | Kimon Spear      |   | 1A (9A) | Furona Bow |
| 11 (91) | Fuujin Axe     |   | 16 (96) | Shidenkai Spear  |   | 1B (9B) | Moai Bow   |
| 12 (92) | Raijin Axe     |   | 17 (97) | Mizumitama Spear |   | 1C (9C) | Aszusa Bow |
|         |                |   |         |                  |   | 1D (9D) | Shiba Bow  |


### Armor & Suits

| Byte     | Armor            |   | Byte     | Suits            |
|----------|------------------|---|----------|------------------|
| 1E (9E)  | Armor            |   | 25 (A5)  | Rikio Suit       |
| 1F (9F)  | Big Armor        |   | 26 (A6)  | Kaio Suit        |
| 20 (A0)  | Kubira Armor     |   | 27 (A7)  | Raio Suit        |
| 21 (A1)  | Shatra Armor     |   | 28 (A8)  | Kouo Suit        |
| 22 (A2)  | Indra Armor      |   | 29 (A9)  | Meio Suit        |
| 23 (A3)  | Bishamon Armor   |   | 2A (AA)  | Tenou Suit       |
| 24 (A4)  | Fudaraku Armor   |   | 2B (AB)  | True King Suit   |


### Cloth / Helmets / Shields

| Byte    | Cloth          |   | Byte    | Helmets        |   | Byte    | Shields         |
| ------- | -------------- | - | ------- | -------------- | - | ------- | --------------- |
| 2C (AC) | Traveler Cloth |   | 33 (B3) | Helmet         |   | 39 (B9) | Shield          |
| 2D (AD) | Maiko Cloth    |   | 34 (B4) | Rubikon Helmet |   | 3A (BA) | Karida Shield   |
| 2E (AE) | Noble Cloth    |   | 35 (B5) | Mujakau Helmet |   | 3B (BB) | JudgementShield |
| 2F (AF) | Monarch Cloth  |   | 36 (B6) | Sahasu Helmet  |   | 3C (BC) | Sukyura Shield  |
| 30 (B0) | Cotton Mesh    |   | 37 (B7) | Amogu Helmet   |   | 3D (BD) | Dragon Scale    |
| 31 (B1) | Agartha Robe   |   | 38 (B8) | Ezekiel Helmet |   | 3E (BE) | Eternal Shield  |
| 32 (B2) | Dark Cape      |   |         |                |   | 3F (BF) | Empty (glitch)  |


### Invalid / Glitch Items
| Byte | Description                                                                 |
|------|-----------------------------------------------------------------------------|
| 3F   | Appears as an empty line. It can be selected but not used/equipped; selling causes overflow, breaks the game until reset. Don't save after. |
| 66   | Same as above                                                               |
| 6A   | Same as above                                                               |
| 6B   | Shows as long glitched string; unusable, selling crashes the game.          |
| 6C   | Same as 6B                                                                  |

### Consumables

| Byte | Item              | Description                  |   | Byte | Item             | Description                      |
|------|-------------------|------------------------------|---|------|------------------|----------------------------------|
| 40   | Red Soma          | Restores some HP             |   | 4D   | Zio Coin         | Escape from a dungeon            |
| 41   | Blue Soma         | Restores some MP             |   | 4E   | Echo Bar         | Casts "Illusion"                 |
| 42   | Yellow Soma       | Cures Poison                 |   | 4F   | Wine             | Casts "Hypnotize"                |
| 43   | Green Soma        | Cures Numb                   |   | 50   | Calm Flute       | Casts "Silence"                  |
| 44   | Purple Soma       | Cures Lure                   |   | 51   | Brahman Eye      | Stops falling into pits          |
| 45   | Pale Soma         | Restores HP & MP             |   | 52   | Crystal Ball     | Increases HP recovery rate       |
| 46   | Brown Soma        | Cures Blindness              |   | 53   | Mahni Flame      | Curses curses                    |
| 47   | White Soma        | Resurrects & fills HP & MP   |   | 54   | Cobra Fang       | Casts "Poison Fang"              |
| 48   | BaramonBracelet   | Refills HP and MP            |   | 55   | Tornado Seed     | Casts "Tornado"                  |
| 49   | Battle Gadgets    |                              |   | 56   | Trick Vision     | Casts "Black Mist"               |
| 4A   | Sazanami          |                              |   | 57   | Invisible Chain  | Casts "Tied"                     |
| 4B   | Kabbalah Scroll   | Casts "Silence"              |   | 58   | Wind Seal        | Escape from Battle               |
| 4C   | Gold Beetle       | Halves enemy speed           |   |      |                  |                                  |

### Junk Item?
| Byte | Item    | Description                                  |
|-------|---------|----------------------------------------------|
| 59    | "No Use"| Consumable item that does nothing; can't be equipped or sold. |

### Key Items

> Note: These appear in the "Items" section, not in your belt.

### Key Items

| Byte | Item           | | Byte | Item           | | Byte | Item            |
|------|----------------|-|------|----------------|-|------|-----------------|
| 5A   | Bat Key        | | 67   | Peg Leg        | | 74   | Eternal Flame   |
| 5B   | Ear Key        | | 68   | Barrier Jinx   | | 75   | Shadow Pot      |
| 5C   | Blue Key       | | 69   | Empty (Glitch) | | 76   | Precious Bell   |
| 5D   | Red Key        | | 6A   | Silver Staff   | | 77   | Pond Key        |
| 5E   | Desert Key     | | 6B   | Long glitched  | | 78   | Empty (Glitch)  |
| 5F   | Wolf Key       | | 6C   | Same as 6B     | | 79   | Black Key       |
| 60   | Kekkaju        | | 6D   | Blessed Salt   | | 7A   | Crimson Key     |
| 61   | Orochi Orb     | | 6E   | Crystal Powder | | 7B   | Light Green Key |
| 62   | Abyss Map      | | 6F   | Tao Braid      | | 7C   | Moki Key        |
| 63   | Mark of Cain   | | 70   | Rations        | | 7D   | Purple Key      |
| 64   | Signed Permit  | | 71   | Signal Flute   | | 7E   | Empty (Glitch)  |
| 65   | Champ Medal    | | 72   | Psalm of Nine  | | 7F   | Empty (Glitch)  |
| 66   | Empty (Glitch) | | 73   | Agartha Ring   | | FF   | Empty Slot      |

> Note: Items wrap from 80 to FE.

| Byte | Description               |
|-------|--------------------------|
| FF    | Empty Slot (consuming an item shifts inventory left by 1 byte and sets last address to FF) |
