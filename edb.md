#禁止其他任何地址进行访问。  
iptables -A INPUT -P tcp --destinaltion-port 13327 \! -d 127.0.0.1 -j DROP	设定  
iptables -A INPUT -p tcp --destinaltion-port 4444 \! -d 127.0.0.1 -j DROP		设定  
#查看服务是否开启。  
iptables -L  