# kali_linux 目录结构

/usr -basic programs() ls cd cat etc 基础命令存放位置

/sbin -system program 系统级命令存放位置

/etc -configuration files 配置文件

/tmp -temporary file()  临时文件存储位置

/usr/bin -applications() apt ncat nmap etc. 用户执行文件位置

/use/share -application support and data files 应用程序支持文件位置

# kali_linux 基础命令

man — 常用于查看帮助信息 例如：man ls

ls —列出文件 例如：ls /ect/apache2/sites-available/*.conf

pwd —显示当前工作目录

mkdir —创建一个文件夹或多个同级文件夹，创建多个文件夹以空格分割

mkdir -p —创建多级文件夹，以递归形式创建 例：mkdir -p test/{recon,exloit,report}

echo $PATH -输出当前path路径

which sbd — 查找文件名为sbd的文件

locate wce32.exe —查找当前文件所在的目录

# kali_linux 服务

## ssh service

systemctl start ssh —开启ssh服务

ss -pantl | grep sshd —查找服务名为sshd的服务

systemctl enable ssh —设置ssh服务开机启动

## http Service

systemctl start apache2

ss -pantl | grep apache

systemctl enable apache2

## 其他服务

systemctl list-unit-files —查找其他类似服务

## 安装或卸载某些软件

apt-cache search pure-ftpd —查找该软件是否存在当前缓存包数据库中

apt install pure-ftpd —安装该软件

apt remove —purge pure-ftpd 卸载软件并卸载相关依赖包，—purge可以将该软件的一些配置文件完全删除

dpkg -i ****.deb —使用dpkg搭配参数-i或者-install来安装一些已经下载好的软件包，但是需要注意的是，该安装方式并不会从互联网下载相关依赖。

## 基础操作命令

echo $USER 输出当前用户名

echo $PWD 输出当前路径

echo $HOME 家目录

export b=127.0.0.1 设置一个变量，并赋值

ping -c 2 $b 使用ping命令发送2次数据包到该变量值

echo "$$" 使用两个符号来查看当前shell实例进程的id

var="zhangsan" 使用var命令创建一个对象

echo $var 输出当前变量

history 查看当前命令历史

!1	命令历史当中的第一条命令会被执行

!! 执行上一条命令

ls 列出当前目录下文件

echo "abc" > redirection_test.txt 将abc内容输出到一个文件中,注意，使用>会进行覆盖写入，追加写入可以使用>>

## 文件搜索及操作

ls -la /usr/bin | grep —搜索目录下包含zip字符的文件

echo "lalala a b c d header" | sed 's/header/head/' 使用sed替换文本内的某一段内容

cut -d ":" -f 1 /etc/passwd 取出当前文本内以冒号分隔的第一串字符

echo "hello::there::friend" | awk -F "::" '{print $1,$3}' 以冒号分隔并取出第一个字符串以及第三个字符串

wc -m < redirection_text.txt 记录当前文本中的字符数

wc -l  access.log —显示当前文件内有多少列

cat access.log |cut -d " " -f 1 |sort -u —截取文本中以冒号分割的第一串字符并去重

cat access.log | cut -d " " -f 1 | uniq -c | sort -run —统计查询出的内容出现在文本中的次数

comm a.txt b.txt —比较两个文件中出现相同的行，第一列表示只出现在a文本中的行，第二列表示只出现在b文本中的行，第三列表示在a和b文件中相同的行，-12 表示删除第一行和第二行

ping -c 400 [localhost](http://localhost)  > ping_results.txt & —将任务发送到后台继续执行，想要查询当前正在后台执行的任务时，输入job查看当前正在执行的任务

ps -ef —查询当前系统的进程信息，e参数为：选择所有进程，f参数为：显示完整格式列表（uid，pid，ppid等）

ps -fC leafpad  —使用C来替代某一个需要找到的进程名称

tail -f /var/log/apache2/access.log —动态显示该文件内容

watch -n 5 w —每5秒更新一次当前系统的登入用户

## 文件下载

wget -O report_wget.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf  —下载该文件并重命名为report_wget.pdf

curl -o report.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf  —下载该文件并重命名为report.pdf

axel -a -n 20 -o report_axel.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf —下载该文件并重命名为report_axel.pdf  —n参数为多线程下载 —a为提示信息

## 别名设置

alias lsa="ls -la" —将ls -la的命令设置为lsa命令

注意：别名的设置可以设置为任何单词或名称，包裹命令的引号可以是单引号或者双引号

unalias lsa —取消设置的别名。ps：或退出当前终端都可以将别名的设置清除

如果想要别名永久生效，可以将设置写入bashrc文件中