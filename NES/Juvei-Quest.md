# Juvei (Jubei) Quest

## Various:

| Address | Modifies | Notes
| --- | --- | --- |
| 0503 | Gold Amount | Main Quest Currency
| 050C | Peach Amount | Side Quest Currency

## Character Attributes:

### Jubei:
| Address | Modifies | Notes
| --- | --- | --- |
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
| --- | --- | --- |
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
| --- | --- | --- |
| 053C | Level |
| 0564 | Current HP |
| 05A4 | Max HP |
| 0565 | Shiro's Current HP | Reverts to level defeault as soon as you open the Stats screen
| 0574 | Current AP |
|  | Max AP |
|  | Experience |
|  | Condition |
|  | Attack |
|  | Defense |
|  | Speed |
|  | Luck |
|  | Spirit

### Shiro:
| Address | Modifies | Notes
| --- | --- | --- |
|  | Level |
|  | Current HP |
|  | Max HP |
|  | Shiro's Current HP |
|  | Current AP |
|  | Max AP |
|  | Experience |
|  | Condition |
|  | Attack |
|  | Defense |
|  | Speed |
|  | Luck |
|  | Spirit


| Address | Modifies | Notes
| --- | --- | --- |
| 053C | Onitan's Level |
| 053D | Shiro's Level |
| 053E | Feeny's Level |
|  |
|  | Onitan's Current HP |
|  | Onitan's Max HP |
| 05A5 | Shiro



| Address | Modifies | Notes
| --- | --- | --- |
|  | Level |
|  | Current HP |
|  | Max HP |
|  | Shiro's Current HP |
|  | Current AP |
|  | Max AP |
|  | Experience |
|  | Condition |
|  | Attack |
|  | Defense |
|  | Speed |
|  | Luck |
|  | Spirit

## Things I'd like to find still:

**Individual character EXP**  
`0x0540` and `0x0541` may be handling Jubei's EXP.  
`0x953E` and `0x053F` may be handling Ryume's EXP.

Both of these values behave kind of strangely.  They definitey do some math off another address.  You can set the value to FF, then defeat a monster and set to FF again and the EXP value will continue to increment (if I recall correctly).  In any case, it's not as straight-forward as just hunting down the exact EXP values to find the addresses.
