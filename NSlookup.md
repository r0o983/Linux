主机记录 A  

cname记录 别名  

fqnd 完全限定域名  

ns 域。  

mx 邮件交换记录。    

以上都是解析记录。    


prt记录。  通过IP地址，反向解析ip地址到域名解析。  

------以下为逐层请求。  
DNS客户端---DNS服务器(缓存)---首先到跟域服务器。  然后返回到DNS给服务器，再由服务器返回给客户端。  

DNS客户端--DNS服务器---com服务器。  

DNS客户端--example.com服务器。  

DNS客户端查询方式为递归查询，服务器端为迭代查询。  

DNS客户端拿到最终地址后，才通过web服务器进行访问。  

nslookup 访问某一个 www.google.com  
格式 set type=a  设置你需要查询的类型。  
google.com  

set q=any  
set type=a  
set q=ns  
set q=a   

text=sqf  include:sqf     反垃圾邮件服务器。  

```
> set type=ns         
> baidu.com
Server:		192.168.254.254
Address:	192.168.254.254#53
```



Non-authoritative answer:  
baidu.com	nameserver = ns2.baidu.com.  
baidu.com	nameserver = ns3.baidu.com.  
baidu.com	nameserver = dns.baidu.com.  
baidu.com	nameserver = ns7.baidu.com.  
baidu.com	nameserver = ns4.baidu.com.  

反向解析  
set q=ptr  

使用其他DNS服务器来解析某一个服务器解析。 server 8.8.8.8  


nslookup -q=any 163.com 8.8.8.8  
Server:		8.8.8.8  
Address:	8.8.8.8#53  

```
Non-authoritative answer:
163.com
	origin = ns4.nease.net
	mail addr = admin.nease.net
	serial = 20167815
	refresh = 7200
	retry = 1800
	expire = 1209600
	minimum = 60
```
163.com	nameserver = ns4.nease.net.  
163.com	nameserver = ns8.166.com.  
163.com	nameserver = ns1.nease.net.  
163.com	nameserver = ns6.nease.net.  
163.com	nameserver = ns5.nease.net.  
163.com	nameserver = ns3.nease.net.  
163.com	nameserver = ns2.166.com.  
Name:	163.com  
Address: 123.58.180.8  
Name:	163.com  
Address: 123.58.180.7  
163.com	mail exchanger = 10 163mx02.mxmail.netease.com.  
163.com	mail exchanger = 10 163mx01.mxmail.netease.com.  
163.com	mail exchanger = 10 163mx03.mxmail.netease.com.  
163.com	mail exchanger = 50 163mx00.mxmail.netease.com.  
163.com	text = "google-site-verification=hRXfNWRtd9HKlh-ZBOuUgGrxBJh526R8Uygp0jEZ9wY"  
163.com	text = "v=spf1 include:spf.163.com -all"  

Authoritative answers can be found from:  



nslookup -q=any 163.com 114.114.114.114  
Server:		114.114.114.114  
Address:	114.114.114.114#53  

Non-authoritative answer:  
163.com	text = "v=spf1 include:spf.163.com -all"  
163.com	text = "google-site-verification=hRXfNWRtd9HKlh-ZBOuUgGrxBJh526R8Uygp0jEZ9wY"  
163.com	mail exchanger = 10 163mx02.mxmail.netease.com.  
163.com	mail exchanger = 50 163mx00.mxmail.netease.com.  
163.com	mail exchanger = 10 163mx03.mxmail.netease.com.  
163.com	mail exchanger = 10 163mx01.mxmail.netease.com.  
Name:	163.com  
Address: 123.58.180.8  
Name:	163.com  
Address: 123.58.180.7  
163.com	nameserver = ns2.166.com.  
163.com	nameserver = ns3.nease.net.  
163.com	nameserver = ns5.nease.net.  
163.com	nameserver = ns8.166.com.  
163.com	nameserver = ns6.nease.net.  
163.com	nameserver = ns1.nease.net.  
163.com	nameserver = ns4.nease.net.  

Authoritative answers can be found from:  