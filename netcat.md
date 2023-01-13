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

