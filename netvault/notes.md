````bash
sudo iptables -A INPUT -p tcp --dport 30222 -s 100.64.0.0/10 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 30222 -j DROP
````
This allows access to port 30222 only from Tailscale IPs (100.64.0.0/10).

--- 

