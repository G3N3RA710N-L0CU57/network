# nmap  

Basic top 1000 common port scan.  

`nmap <ip>`  

All ports.  

`nmap -p 1-65535`  

Stealth scan (no complete of the handshake).  

`sudo nmap -sS 10.11.1.220`  

Connect scan using socket api (handshake complete).  

`nmap -sT 10.11.1.220`  

UDP scan.  

`sudo nmap -sU 10.11.1.115`  

Stealth and UDP scan.  

`sudo nmap -sS -sU 10.11.1.115`  

