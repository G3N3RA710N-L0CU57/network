# LDAP protocol  

Anonymous bind with ldapsearch.  

`ldapsearch -x -H ldap://IP -b "dc=example,dc=com"`  

Bind with credentials.  

`ldapsearch -x -H ldap://IP -D "domain\username" -w "password" -b "dc=example,dc=com"`
