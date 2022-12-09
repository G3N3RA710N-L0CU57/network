# Proxychains

Proxy netcat.

`proxychains nc 17.16.0.10 23`  

To specify a proxy, ammend the following config file.  

`/etc/proxychains.conf`  

Proxychains checks config in following order, making engagement specific proxy setup easy.  

1. Current directory. `./proxychains.conf`  
2. `~/.proxychains/proxychains.conf`
3. `/etc/proxychains.conf`

