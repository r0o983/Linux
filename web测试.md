http协议：  
	无内建的机密性安全机制  
	嗅探或代理截断可查看全部明文信息  
	https只能提高传输层安全  

无状态：  
	每一次客户端和服务器的的通信都是独立的过程  
	web应用需要跟踪客户端会话（多步通信）  
	不使用cookie的应用，客户端每次请求都要重新身份验证  
	session用于在用户身份验证后跟踪用户行为轨迹  
		提高用户体验，但增加了攻击向量  

cycle：  
	请求/响应  
	
重要的header：  
	set-cookie：服务器发给客户端的sessioNid(有被窃取的风险）  
	content-length：响应body部分的字节长度  
	location：重定向用户到另一个页面，可识别身份认证后允许访问的页面  
	cookie：客户端发回给服务器证明用户状态的信息（头：值成对出现）  
	Referrer：发起新请求之前用户位于哪个页面，服务器基于此头的安全限制很容易被修改绕过  

http协议基础-状态码：  
	基本分为5大类  
		100s：服务器响应的信息，通常表示服务器还有后续处理，很少出现  
		200s：请求被服务器成功接受并处理后返回的相应结果  
		300s：重定向，通常在身份认证成功后重定向到一个安全页面（301/302）  
		400s：表示客户端请求错误  
			401：需要身份验证  
			403：拒绝访问  
			404：目标为发现  
		500s：服务器内部错误（503：服务不可用）  
		
侦察：  
	httrack--减少与目标系统的交互  
	

扫描工具：  
	nikto  
	vega  
	skipfish  
	w3af  
	arachni  
	owasp-zap  
	

nikto：  
	perl语言开发的开源web安全扫描器  
	软件版本  
	搜索存在安全隐患的文件  
	服务器配置漏洞  
	web application层面的安全隐患  
	避免404误判  
		很多服务器不存手RFC标准，对于不存在的对象返回200响应码  
		依据响应文件内容判断，不同扩展名的文件404响应内容不同  
		去除时间信息后的内容取md5  
		-no404    

	nmap -p80 192.168.1.0/24 -oG |nikto -host		使用nmap扫描到存活主机，然后使用nikto来进行刺探


​	

burpsuite:  
	web安全工具中的瑞士军刀  
	统一的集成概念股据发现全部现代web安全漏洞  
	portswigger公司开发  
		burp free  
		burp professional  
		http://www.portswigger.net  
	所有的工具共享一个能处理http消息的可扩展框架，模块之间无缝交换信息。  
	谷歌搜索破解的burpsutie，下载之后保存在任意路径，比如说：/usr/bin/burpsuite/ 	鉴于担心相互冲突，所以我在opt目录下创建了一个目录  
	使用到的命令如下：  
		首先改变默认的java环境。update-alternatives  --config  java  
		之后执行破解文件，使用注册机进行破解。burp-loader-keygen.jar 	  	
		之后删除掉原本自带的社区版burpsuite 	rm -rf burpsuite  
		新建一个文本文件，起名为burpsuite ，接着写入  
			#!/bin/sh  
			java -Xbootclasspath/p:/usr/bin/burp-loader-keygen.jar -jar /usr/bin/burpsuite_pro_v1.7.37.jar 		注意路径的替换，比如我用的opt目录  
		java -Xbootclasspath/p:/opt/burpsuite/burp-loader-keygen.jar -jar   /opt/burpsuite/burpsuite_pro_v1.7.37.jar 	  
		保存退出，添加执行权限chmod 755 burpsuite  
		进入/usr/share/applications，并编辑burpsuite的快捷方式   
		   cd /usr/share/applications  
		vi kali-burpsuite.desktop  
		Exec=sh -c "java -jar /usr/bin/burpsuite"改为Exec=sh -c "/usr/bin/burpsuite"  
		以下为备选方案：可以结合在一起使用  

```
mkdir /opt/burpsuite/
mv BurpLoader.jar /opt/burpsuite/
mv burpsuite_pro_v1.7.37.jar /opt/burpsuite/

cd /usr/bin/
mv burpsuite burpsuite.bak
rm /usr/bin/burpsuite

ln -s /opt/burpsuite/BurpLoader.jar /usr/bin/burpsuite
chmod +x /opt/burpsuite/BurpLoader.jar

```

首先在options里面修改显示字体（避免抓取到的内容乱码）