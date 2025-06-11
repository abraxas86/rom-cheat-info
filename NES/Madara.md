# Madara (Mouryou Senki Madara)

## Character Stats:

These are strangely not listed in memory in the same order they are in the stats screen

### Strength:
| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
|  0618   | Team slot 1 Strength | Madara |
|  0619   | Team slot 2 Strength | Kirin |
|  0619   | Team slot 3 Strength ||
|  061A   | Team slot 4 Strength ||

### Wisdom:
| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
|  061C   | Team Slot 1 Wisdom |
|  061D   | Team slot 2 Wisdom |
|  061E   | Team slot 3 Wisdom |
|  061F   | Team slot 4 Wisdon |

### Agility:
| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
|  0620   | Team slot 1 Agility
|  0621   | Team slot 2 Agility
|  0622   | Team slot 3 Agility
|  0623   | Team slot 4 Agility

### Charm:
| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
|  0624   | Team slot 1 Charm |
|  0625   | Team slot 2 Charm | 
|  0626   | Team slot 3 Charm |
|  0627   | Team slot 4 Charm |

#### HP:

*Note: These all follow the same formula: HP = (Byte2 Value * 256) + Byte1 Value   
```
Exmple:
If 0638 is 0C [12 decimal] and 0639 is 04, current health is:  
(4*256) + 12  
= 1024 + 12  
= 1036 HP
```
  *Note: Any values beyond `0F 27` (9999) cause an overflow and don't display properly.

| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
| 0638-0639 | Team slot 1 Current HP |
| 063A-063B | Team slot 2 Current HP |
| 063C-063D | Team slot 3 Current HP |
| 063E-063F | Team slot 4 Current HP |
| 0640-0641 | Team slot 1 Max HP     |
| 0642-0643 | Team slot 2 Max HP     |
| 0644-0645 | Team slot 3 Max HP     |
| 0646-0647 | Team slot 4 Max HP     |

### MP:
*Note: Follows the same rule as HP

| Address | Modifies | Notes  |
|   ---   |    ---   |   ---  |
| 0648-0649 | Team slot 1 Current MP |
| 064A-064B | Team slot 2 Current MP |
| 064C-064D | Team slot 3 Current MP |
| 064E-064F | Team slot 4 Current MP |
| 0650-0651 | Team slot 1 Max MP     |
| 0652-0653 | Team slot 2 Max MP     |
| 0654-0655 | Team slot 3 Max MP     |
| 0656-0657 | Team slot 4 Max MP     |


## Notes:
