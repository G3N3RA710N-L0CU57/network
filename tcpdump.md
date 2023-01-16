# tcpdump  

pcap analysis.  

`sudo tcpdump -r file.pcap`  

Printing count of destination ports.  

`sudo tcpdump -n -r file.pcap | awk -F " " '{print $5}' | sort | uniq -c | head`  

Filter source host.  

`sudo tcpdump -n src host 192.168.1.10 -r file.pcap`  

Filter destination host.  

`sudo tcpdump -n dest host 192.168.1.11 -r file.pcap`  

Filter port.  

`sudo tcpdump -n port 81 -r file.pcap`  

Dump capture in hex and ascii.  

`sudo tcpdump -nX -r file.pcap`  

Display packets with ACK and PSH bits.  

`sudo tcpdump -A -n 'tcp[13]=24' -r file.pcap`  

