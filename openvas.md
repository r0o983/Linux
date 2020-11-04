#启动软件  
openvas-start  

#检查安装结果  
openvas-check-setup  

#检查当前帐号  
openvasmd -list-users  

#修改帐号密码  
openvasmd --user=admin --new-password=PasswOrd  

#升级  
openvas-feed-update  

#开启软件（1）  
openvas-setup  

#查询  
openvasmd -h  

#查询用户名  
openvasmd --get-users  

#修改密码  
openvsmd --user=admin --new-password=PasswOrd  

#更新  
openvas-feed-update  

#开机启动服务  
vi /usr/bin/openvas-start  
	starting Openvas Services  
	starting Openvas Manager:openvasmd  
	starting Openvas Scanner:openvassd  
	starting Greenbone   

