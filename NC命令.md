nc -nv ipaddrecss port     

nc -lp port   

nc -nvl port -c bash --ssl  

nc  -nv ipaddrecss port --ssl  

#使用nc命令来进行传输文件  
A主机：nc -nv 182.168.1.1 8888  < windows.iso 传输方  
B主机：nc -lp 8888 > windows.iso	接收方  

#使用nmap来进行扫描指定ip的端口  
nmap 192.168.254.100 200  

