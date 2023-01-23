# SNMP (Simple Network Management Protocol)  

Scanning with nmap.  

`sudo nmap -sU --open -p 161 10.11.1.1-254 -oG open-snmp.txt`  

Brute force with ip addresses.  

`onesixtyone -c community -i ips`  

Provided we know the community string, which usually is public.  

Enumerating whole MIB tree.  

`snmpwalk -c public -v1 -t 10 10.11.1.14`  

Enumerating windows users.  

`snmpwalk -c public -v1 10.11.1.14 1.3.6.1.4.1.77.1.2.25`  

Enumerating windows processes.  

`snmpwalk -c public -v1 10.11.1.73 1.3.6.1.2.1.25.4.2.1.2`  

Enumerating open TCP ports.  

`snmpwalk -c public -v1 10.11.1.14 1.3.6.1.2.1.6.13.1.3`  

Enumerating installed software.  

`snmpwalk -c public -v1 10.11.1.50 1.3.6.1.2.1.25.6.3.1.2`  

