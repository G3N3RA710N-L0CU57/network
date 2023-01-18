# DNS active information gathering  

Find the ip address of a domain, by default this uses an 'A' record.  

`host www.fake-company.com`  

To query other types of records, use the '-t' option.  

`host -t mx fake-company.com`  

`host -t txt fake-company.com`  

To find name servers.  

`host -t ns fake-company.com | cut -d " " -f 4`  



## Forward looking bruteforce  

```
cat possible-hosts.txt
www
ftp
mail
owa
proxy
router
```  

Brute force loop.  

```
#!/bin/bash

for hostname in $(cat possible-hosts.txt);do host $hostname.fake-company.com; done
```  

## Reverse look up brute force  

Getting host name validation from possible ip addresses.  

```
#!/bin/bash

for ip in $(seq 50 100);do host 58.100.25.$ip; done | grep -v "not found"
```  

## DNS zone transfers  

Zone transfer command.  

`host -l <domain name> <dns server address>`  

Attempt zone transfer on numerous name servers.  

```
#!/bin/bash

for server in $(host -t ns $1 | cut -d " " -f4); do
  # For each of these servers, attempt a zone transfer, domain is first arg to script.
  host -l $1 $server |grep "has address"
done
```  

## DNSRecon  

Perform a zone transfer.  

`dnsrecon -d fake-company.com -t axfr`  

Bruteforce with a wordlist of subdomains.  

`dnsrecon -d fake-company.com -D ~/list.txt -t brt`  


## DNSEnum  

Perform a zone transfer.  

`dnsenum <domain name>`
