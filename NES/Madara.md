# Madara (Mouryou Senki Madara)

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


### Inventory

> Item slots appear to store item bytes from the item table below.

| Address | Modifies           | Notes |
|---------|--------------------|-------|
| 0680    | Belt Slot 1        |       |
| 0681    | Team slot 1 Helmet |       |


## Items

### Weapons

#### Swords
| Byte | Swords           |   | Byte | Swords         |   | Byte | Swords           |
|------|------------------|---|------|----------------|---|------|------------------|
| 00   | Kusanagi Blade   |   | 05   | Kasumi Blade   |   | 0A   | Ashura Blade     |
| 01   | Light Kusanagi   |   | 06   | Pope Blade     |   | 0B   | Susano Blade     |
| 02   | Seiken Kusanagi  |   | 07   | Scion Blade    |   | 0C   | SalamanderBlade  |
| 03   | Knife            |   | 08   | Yasha Blade    |   | 0D   | Karma Blade      |
| 04   | Sword            |   | 09   | Myouo Blade    |   |      |                  |

#### Axes / Spears / Bows
| Byte | Axes             |   | Byte | Spears           |   | Byte | Bows            |
|------|------------------|---|------|------------------|---|------|-----------------|
| 0E   | Stone Axe        |   | 13   | Spear            |   | 18   | Bow             |
| 0F   | Tomahawk         |   | 14   | Long Spear       |   | 19   | Big Bow         |
| 10   | Kamaitachi Axe   |   | 15   | Kimon Spear      |   | 1A   | Furona Bow      |
| 11   | Fuujin Axe       |   | 16   | Shidenkai Spear  |   | 1B   | Moai Bow        |
| 12   | Raijin Axe       |   | 17   | MizumitamaSpear  |   | 1C   | Aszusa Bow      |
|      |                  |   |      |                  |   | 1D   | Shiba Bow       |

### Armor & Suits
| Byte | Armor            |   | Byte | Suits            |
|------|------------------|---|------|------------------|
| 1E   | Armor            |   | 25   | Rikio Suit       |
| 1F   | Big Armor        |   | 26   | Kaio Suit        |
| 20   | Kubira Armor     |   | 27   | Raio Suit        |
| 21   | Shatra Armor     |   | 28   | Kouo Suit        |
| 22   | Indra Armor      |   | 29   | Meio Suit        |
| 23   | Bishamon Armor   |   | 2A   | Tenou Suit       |
| 24   | Fudaraku Armor   |   | 2B   | True King Suit   |

### Cloth / Helmets / Shields

| Byte | Cloth            |   | Byte | Helmets         |   | Byte | Shields         |
|------|------------------|---|------|-----------------|---|------|-----------------|
| 2C   | Traveler Cloth   |   | 33   | Helmet          |   | 39   | Shield          |
| 2D   | Maiko Cloth      |   | 34   | Rubikon Helmet  |   | 3A   | Karida Shield   |
| 2E   | Noble Cloth      |   | 35   | Mujakau Helmet  |   | 3B   | JudgementShield |
| 2F   | Monarch Cloth    |   | 36   | Sahasu Helmet   |   | 3C   | Sukyura Shield  |
| 30   | Cotton Mesh      |   | 37   | Amogu Helmet    |   | 3D   | Dragon Scale    |
| 31   | Agartha Robe     |   | 38   | Ezekiel Helmet  |   | 3E   | Eternal Shield  |
| 32   | Dark Cape        |   |      |                 |   | 3F   | Empty (glitch)  |

### Invalid / Glitch Items
| Byte | Description                                                                 |
|------|-----------------------------------------------------------------------------|
| 3F   | Appears as an empty line. It can be selected but not used/equipped; selling causes overflow, breaks the game until reset. Don't save after. |
| 66   | Same as above                                                              |
| 6A   | Same as above                                                              |
| 6B   | Shows as long glitched string; unusable, selling crashes the game.        |
| 6C   | Same as 6B                                                                |

### Consumables

| Byte | Item              | Description                  |   | Byte | Item             | Description                      |
|------|-------------------|------------------------------|---|------|------------------|----------------------------------|
| 40   | Red Soma          | Restores some HP             |   | 4D   | Zio Coin         | Escape from a dungeon            |
| 41   | Blue Soma         | Restores some MP             |   | 4E   | Echo Bar         | Casts "Illusion"                 |
| 42   | Yellow Soma       | Cures Poison                 |   | 4F   | Wine             | Casts "Hypnotize"                |
| 43   | Green Soma        | Cures Numb                   |   | 50   | Calm Flute       | Casts "Silence"                  |
| 44   | Purple Soma       | Cures Lure                   |   | 51   | Brahman Eye      | Stops falling into pits          |
| 45   | Pale Soma         | Restores HP & MP             |   | 52   | Crystal Ball     | Increases HP recovery rate       |
| 46   | Brown Soma        | Cures Blindness              |   | 53   | Mahni Flame      | Curses curses                   |
| 47   | White Soma        | Resurrects & fills HP & MP  |   | 54   | Cobr Fang        | Casts "Poison Fang"              |
| 48   | BaramonBracelet   | Refills HP and MP            |   | 55   | Tornado Seed     | Casts "Tornado"                  |
| 49   | Battle Gadgets    |                              |   | 56   | Trick Vision     | Casts "Black Mist"               |
| 4A   | Sazanami          |                              |   | 57   | Invisible Chain  | Casts "Tied"                    |
| 4B   | Kabbalah Scroll   | Casts "Silence"              |   | 58   | Wind Seal        | Escape from Battle               |
| 4C   | Gold Beetle       | Halves enemy speed           |   |      |                  |                                |

### Junk Item?
| Byte | Item    | Description                                  |
|-------|---------|----------------------------------------------|
| 59    | "No Use"| Consumable item that does nothing; can't be equipped or sold. |

### Key Items

> Note: These appear in the "Items" section, not in your belt.

| Byte | Item             |
|-------|-----------------|
| 5A    | Bat Key         |
| 5B    | Ear Key         |
| 5C    | Blue Key        |
| 5D    | Red Key         |
| 5E    | Desert Key      |
| 5F    | Wolf Key        |
| 60    | Kekkaju         |
| 61    | Orochi Orb      |
| 62    | Abyss Map       |
| 63    | Mark of Cain    |
| 64    | Signed Permit   |
| 65    | Champ Medal     |
| 66    | Empty (glitch)  |
| 67    | Peg Leg         |
| 69    | Barrier Jinx    |
| 6A    | Empty (glitch)  |
| 6B    | Long glitched name |
| 6C    | Same as 6B      |
| 6D    | Blessed Salt    |
| 6E    | Crystal Powder  |
| 6F    | Tao Braid       |
| 70    | Rations         |
| 71    | Signal Flute    |
| 72    | Psalm of Nine   |
| 73    | Agartha Ring    |
| 74    | Eternal Flame   |
| 75    | Shadow Pot      |
| 76    | Precious Bell   |
| 77    | Pond Key        |
| 78    | Empty (glitch)  |
| 79    | Black Key       |
| 7A    | Crimson Key     |
| 7B    | Light Green Key |
| 7C    | Moki Key        |
| 7D    | Purple Key      |
| 7E    | Empty (glitch)  |
| 7F    | Empty (glitch)  |

> Note: Items wrap from 80 to FE.

| Byte | Description              |
|-------|--------------------------|
| FF    | Empty Slot (consuming an item shifts inventory left by 1 byte and sets last address to FF) |
