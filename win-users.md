### Windows User Account  

To add a user.  

`net user USERNAME PASSWORD /add`  

To add newly created account to administrators group.  

`net localgroup Administrators USERNAME /add`  

To add newly created user to remote management group for rdp.  

`net localgroup "Remote Management Users" USERNAME /add`
