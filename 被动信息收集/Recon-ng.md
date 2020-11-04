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

```bash
marketplace search github
#搜索包含github的模块
```

对于包含K的标记，需要指定的api才可使用

```bash
markeplace info recon/domains-hosts/google_site_web
#查看google的website模块
```

得到结果为使用site标记不需要使用到谷歌的API，所以这里使用markplace来安装该模块

```bash
marketplace install recon/domins-hosts/google_site_web
#安装该模块
```

```bash
modules load recon/domains-hosts/google_site_web
#使用load来进行加载该模块
#进入该模块后可以使用info来进行查看
```

添加一个源地址，之后则开始查询该源地址的信息

```bash
options set SOURCE megacorpone.com
#进入该模块后使用set souce来设置源地址
run
#开始搜集信息
```

使用back 从当前模块退出，使用show hosts来查询当前已经查询到的数据

```bash
marketplace info recon/hosts-hosts/resolve
#查看其他可用模块，并根据需要进行安装
```

```bash
marketplace install recon/hosts-hosts/resolve
#安装该模块
```

```bash
modules load recon/hosts-hosts/resolve
#进入该模块后使用info命令
run
#此时会将之前的到的运行结果的网址信息解析为IP地址
```

```bash
back
#返回上一级目录
show hosts
#查看当前已得到的信息
```

## note

load的模块基本在第二次使用的时候都会触发谷歌的验证码，极度蛋疼（谷歌无果