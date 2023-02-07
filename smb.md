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

## anonymous login list shares  

List shares with anonymous login.  

`smbclient -L \\test.local -I 10.10.0.3 -N`
