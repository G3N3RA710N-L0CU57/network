# smb and netBIOS  

nmap scan.  

`nmap -v -p 139,445 -oG smb.txt 10.11.1.1-254`  

Search netBIOS names with nbtscan on originating UDP port 137.  

`sudo nbtscan -r 10.11.1.0/24`  

## nmap NSE smb scripts  

To locate scripts.  

`ls -1 /usr/share/nmap/scripts/smb*`  

OS detection.  

`nmap -v -p 139, 445 --script=smb-os-discovery 10.11.1.227`  

Scan for vuln, be careful with unsafe scripts set to true.  

`nmap -v -p 139,445 --script=smb-vuln-ms08-067 --script-args=unsafe=1 10.11.1.5`  

