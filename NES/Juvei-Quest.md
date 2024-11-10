# Juvei (Jubei) Quest

## Various:

| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0503 | Gold Amount | Main Quest Currency
| 050C | Peach Amount | Side Quest Currency

## Battle Stuff:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 064C | Something with battle attack animation/timing
| 064E | Enemy number being attacked (00 = first enemy) | Confirmed not used for the player character being attacked by enemy
| 064F | Something with battle attack animation/timing
| 065C | Something with enemy sprite animations during battle

## Character Attributes:

### Jubei:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 0538 | Level | Character level defines attribute values, arts/skills, and EXP cap
| | Current HP |
| | Max HP |
| | Current AP |
| | Max AP |
| | Experience |
| | Condition |
| | Attack |
| | Defense |
| | Speed |
| | Luck |
| | Spirit

### Ryume:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053A | Level | Character level defines attribute values, arts/skills, and EXP cap
| | Current HP |
| | Max HP |
| | Current AP |
| | Max AP |
| | Experience |
| | Condition |
| | Attack |
| | Defense |
| | Speed |
| | Luck |
| | Spirit

### Onitan:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053C | Level       |
| 0564 | Current HP  |
| 05A4 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0574 | Current AP  |
| 05B4 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Experience  |
|  | Condition   |
| 05BC | Attack      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05C4 | Defense     | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05CC | Speed       | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05D4 | Luck        | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05DC | Spirit      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 05E4 | Wisdom      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level

### Shiro:
| Address | Modifies | Notes
|   ---   |    ---   |   ---  |
| 053D | Level       |
| 0565 | Current HP  |
| 05A5 | Max HP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
| 0575 | Current AP  |
| 05B5 | Max AP      | Resets on its own often (ie: opening Status menu). Likely hard-coded to current level
|  | Experience  |
|  | Condition   |
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
|  | Experience  |
|  | Condition   |
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
| Value   | Status Condition
|   ---   |    ---   |
|   | Normal
|   | Poison
|   | Paralysis

## Things I'd like to find still:

**Individual character EXP**  
`0x0540` and `0x0541` may be handling Jubei's EXP.  
`0x953E` and `0x053F` may be handling Ryume's EXP.

Both of these values behave kind of strangely.  They definitey do some math off another address.  You can set the value to FF, then defeat a monster and set to FF again and the EXP value will continue to increment (if I recall correctly).  In any case, it's not as straight-forward as just hunting down the exact EXP values to find the addresses.
