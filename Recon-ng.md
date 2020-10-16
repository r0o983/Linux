三大模块   

#模块化  
#数据库  
#报告  

recon-ng	进入程序  
recon-ng -r a.txt	重复大量的命令，保存起来。  
workspaces list	查看当前所有的工作区  
keys add google-api daskdsajd	添加新的API  
key delect google-api		删除api  
set user		更改扫描表头  
show schema	查看数据库表结构  
show options	查看设置  
snapshots list	类似虚拟机快照  
use			使用某一个模块  

#模块使用  
use recon/domains-hosts/google_site_web  
show options	进入之后更改source就可以开启  
show info 	查看当前需要查询的网站信息  
run		开启跑程序。  
show hosts	查看数据库已经查询到的数据  
query select * from hosts where host like '%w%'		标准的sql语句，没什么可写的。  

#爆破域名  
search brut 找到路径  
use recon/domains-hosts/brute_hosts	进入目录  
show options  
show info   
run  
query select * from hosts where module like '%brut%'  

#域名解析成IP地址  
search res   
use recon/hosts-hosts/resolve	  
set source query select host from hosts where host like '%sina.com.cn%' 将表中符合条件的记录来进行解析成  ip地址  
set source query select host from hosts 	解析全部的域名。  

#导出  
search reporting/html   
use reporting/html	使用目录  
set Creator 	创建人  
set customer 	为谁创建  
filename	/root/Desktop/aa.html	导出路径  
run		使用命令进行导出。  