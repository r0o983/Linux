#语法  

dig @114.114.114.114 www.sina.com mx  

dig 163.com mx   
dig 163.com any  

ptr 反向查询  

dig +noall +answer -x 8.8.8.8 sina.com    #dns服务器进行反向查询。  


dig +noall +answer txt chaos VERSION.BIND @DNS服务器地址  

dns追踪  
查看以及DNS欺骗。  

dig +trace example.com  


dns递归查询  

--从本地dns直接取得结果。  
dig sina.com  


DNS区域传输命令 如果DNS服务器配置有问题，那么可以使用以下命令来进行爆破NDS服务。  

dig @ns1.example.com example.com axfr  

host -T -l sina.com 114.114.114.114   