# iptables  

Monitoring traffic.  

Source.  

`sudo iptables -I INPUT 1 -s 10.11.1.220 -j ACCEPT`  

Destination.  

`sudo iptables -I OUTPUT 1 -d 10.11.1.220 -j ACCEPT`  

Zero the packet and byte counter in all chains.  

`sudo iptables -Z`  

