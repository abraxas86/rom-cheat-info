# Juvei (Jubei) Quest

Memory Addresses: 

Various:

| Address | Value |
| --- | --- |
| 0503 | Gold |

Character Attributes:


| Address | Value | Notes
| --- | --- | --- |
| 0538 | Jubei's Level | Character level defines attribute values, arts/skills, and EXP cap
| 053A | Ryume's Level | Character level defines attribute values, arts/skills, and EXP cap



## Things I'd like to find still:

**Individual character EXP**  
`0x0540` and `0x0541` may be handling Jubei's EXP.  
`0x953E` and `0x053F` may be handling Ryume's EXP.

Both of these values behave kind of strangely.  They definitey do some math off another address.  You can set the value to FF, then defeat a monster and set to FF again and the EXP value will continue to increment (if I recall correctly).  In any case, it's not as straight-forward as just hunting down the exact EXP values to find the addresses.
