# Madara (Mouryou Senki Madara)

## Character Stats:

> Note: These stats are **not** laid out in memory in the same order as the in-game stats screen.

### Strength:
| Address | Modifies              | Notes  |
|---------|------------------------|--------|
| 0618    | Team slot 1 Strength   | Madara |
| 0619    | Team slot 2 Strength   | Kirin  |
| 061A    | Team slot 3 Strength   |        |
| 061B    | Team slot 4 Strength   |        |

### Wisdom:
| Address | Modifies              | Notes  |
|---------|------------------------|--------|
| 061C    | Team slot 1 Wisdom     |        |
| 061D    | Team slot 2 Wisdom     |        |
| 061E    | Team slot 3 Wisdom     |        |
| 061F    | Team slot 4 Wisdom     |        |

### Agility:
| Address | Modifies              | Notes  |
|---------|------------------------|--------|
| 0620    | Team slot 1 Agility    |        |
| 0621    | Team slot 2 Agility    |        |
| 0622    | Team slot 3 Agility    |        |
| 0623    | Team slot 4 Agility    |        |

### Charm:
| Address | Modifies              | Notes  |
|---------|------------------------|--------|
| 0624    | Team slot 1 Charm      |        |
| 0625    | Team slot 2 Charm      |        |
| 0626    | Team slot 3 Charm      |        |
| 0627    | Team slot 4 Charm      |        |

### HP:

> HP values are stored as 2-byte little-endian integers:  
> `(High Byte * 256) + Low Byte`  
> For example, if `0638` = `0C` and `0639` = `04`, HP = `04 * 256 + 0C = 1036`.  
> Bytes beyond `0F27` (9999) will overflow and not display properly.

| Address     | Modifies               | Notes |
|-------------|------------------------|-------|
| 0638–0639   | Team slot 1 Current HP |       |
| 063A–063B   | Team slot 2 Current HP |       |
| 063C–063D   | Team slot 3 Current HP |       |
| 063E–063F   | Team slot 4 Current HP |       |
| 0640–0641   | Team slot 1 Max HP     |       |
| 0642–0643   | Team slot 2 Max HP     |       |
| 0644–0645   | Team slot 3 Max HP     |       |
| 0646–0647   | Team slot 4 Max HP     |       |

### MP:

> MP follows the same encoding rules as HP (2-byte little-endian).

| Address     | Modifies               | Notes |
|-------------|------------------------|-------|
| 0648–0649   | Team slot 1 Current MP |       |
| 064A–064B   | Team slot 2 Current MP |       |
| 064C–064D   | Team slot 3 Current MP |       |
| 064E–064F   | Team slot 4 Current MP |       |
| 0650–0651   | Team slot 1 Max MP     |       |
| 0652–0653   | Team slot 2 Max MP     |       |
| 0654–0655   | Team slot 3 Max MP     |       |
| 0656–0657   | Team slot 4 Max MP     |       |

### Inventory:

> Item slots appear to store item bytes from the item table below.

| Address | Modifies              | Notes         |
|---------|------------------------|---------------|
| 0680    | Belt Slot 1            |               |
| 0681    | Team slot 1 Helmet     |               |

---

## Items:

### Weapons

#### Swords

| Byte | Swords           | Byte | Swords         | Byte | Swords           |
|------|------------------|------|----------------|------|------------------|
| 00   | Kusanagi Blade   | 05   | Kasumi Blade   | 0A   | Ashura Blade     |
| 01   | Light Kusanagi   | 06   | Pope Blade     | 0B   | Susano Blade     |
| 02   | Seiken Kusanagi  | 07   | Scion Blade    | 0C   | Salamander Blade |
| 03   | Knife            | 08   | Yasha Blade    | 0D   | Karma Blade      |
| 04   | Sword            | 09   | Myouo Blade    |      |                  |

#### Axes / Spears / Bows

| Byte | Axes             | Byte | Spears           | Byte | Bows            |
|------|------------------|------|------------------|------|-----------------|
| 0E   | Stone Axe        | 13   | Spear            | 18   | Bow             |
| 0F   | Tomahawk         | 14   | Long Spear       | 19   | Big Bow         |
| 10   | Kamaitachi Axe   | 15   | Kimon Spear      | 1A   | Furona Bow      |
| 11   | Fuujin Axe       | 16   | Shidenkai Spear  | 1B   | Moai Bow        |
| 12   | Raijin Axe       | 17   | Mizumitama Spear | 1C   | Aszusa Bow      |
|      |                  |      |                  | 1D   | Shiba Bow       |

---

## Notes:
