# NFS (network file sharing)  

Access files over the network as if locally mounted.  

Scan for rpc with nmap.  

`nmap -v -p 111 10.11.1.1-254`  

Find services that may have registered with rpc.  

`nmap -sV -p 111 --script=rpcinfo 10.11.1.1-254`  

Once NFS is found, we can use nmap NSE.  

`ls -1 /usr/share/nmap/scripts/nfs*`  

Run all NFS scripts.  

`nmap -p 111 --script nfs* 10.11.1.72`  

If a directory is found, it can be mounted on our local machine. In this case home is being shared.  

```
mkdir home
sudo mount -o nolock 10.11.1.72:/home ~/home/
```  

If we need to change UUID to view a file.  

```
sudo adduser pwn
sudo sed -i -e 's/1001/1014/g' /etc/passwd
su pwn
```  

