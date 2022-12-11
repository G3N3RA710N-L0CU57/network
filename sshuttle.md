# sshuttle  

Simulates a VPN by using a SSH connection to create a tunnelled proxy that acts as a new interface. This only works on linux targets.  

`sudo apt install sshuttle`  

Basic command to connect to a server with sshuttle.  

`sshuttle -r username@address subnet`  

To try to find the subnet automatically using the servers routing table.  

`sshuttle -r username@address -N`  

Using key based authentication if no password.  

`sshuttle -r username@address --sh-cmd "ssh -i KEYFILE" SUBNET`  

To stop sshuttle interupting itself.  

`sshuttle -r user@172.16.0.5 172.16.0.0/24 -x 172.16.0.5`  

