查找当前指令的文件生成的密码包位置。 可使用以下命令来进行操作。  
dpkg -L dnsenum  
其中dnsenum 为软件名称  
find / -name dnsenum   
找到所有以dnssenum为头的文件  

#强力爆破DNS  

fierce -dnsserver 8.8.8.8 -dns sina.com.cn -wordlist -字典地址  
使用此命令可以拿到sina的二级域名服务器的DNS以及IP地址！  

#强力爆破DNS  
dnsdict6 -d4 -t 16 -x sina.com  
-d 显示IPV6的信息  
-d4显示ipv4的信息  
-t 线程数  
-x 使用字典强度。  
好像歇比了阿  

#强力爆破DNS   
dnsenum -f dnsbig.txt -dnsserver 8.8.8.8 sina.com -o sina.xml  
dnsbig 这个文件所字典的位置  
xml文件是你用来保存你生成的字典密码。  

#强力爆破dns  
dnsmap sina.com -w dns.txt  

#强力爆破dns  推荐五星！  
dnsrecon -d sina.com --lifetime 10 -t brt -D /usr/share/dnsrecon/namelist.txt  
其中-D后面为字典的路径，字典路径查询方法请看文章头  

