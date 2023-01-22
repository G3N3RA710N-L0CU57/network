# masscan  

Originally developed to scan the internet, which it can in 6 minutes.  

To install.  

`sudo apt install masscan`  

Scanning a large class A or B network for port 80 http.  

`sudo masscan -p80 10.0.0.0/8`  

Scan a class C network.  

`sudo masscan -p80 10.11.1.0/24 --rate=1000 -e tun0 --router-ip 10.11.0.1`  

