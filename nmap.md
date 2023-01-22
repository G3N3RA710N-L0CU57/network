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

Network sweeping.  

`nmap -sn 10.11.1.1-254`  

Network sweeping in greppable format.  

```
nmap -v -sn 10.11.1.1-254 -oG ping-sweep.txt
grep Up ping-sweep.txt | cut -d " " -f 2
```  

Network sweep for specific ports.  

```
nmap -p 80 10.11.1.1-254 -oG web-sweep.txt
grep open web-sweep.txt | cut -d" " -f2
```  

Network sweep short scan of top 20 ports with traceroute '-A'.  

`nmap -sT -A --top-ports=20 10.11.1.1-254 -oG top-port-sweep.txt`  

Services file.  

`cat /usr/share/nmap/nmap-services`  

OS finger printing.  

`sudo nmap -O 10.11.1.220`  

Banner grabbing and service enumeration.  

`nmap -sV -sT -A 10.11.1.220`  

NSE scripts.  

`nmap 10.11.1.220 --script=smb-os-discovery`  

DNS zone transfer.  

`nmap --script=dns-zone-transfer -p 53 ns2.megacorpone.com`  

To view more information about a script.  

`nmap --script-help dns-zone-transfer`  

