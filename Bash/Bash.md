例子：

```bash
#!/bin/bash
# hello world bash script
echo "hello world"
```

第一行标记为使用什么语言

第二行为一行注释

使用echo输出一段字符

将代码保存为文件后，添加执行权限即可，chmod +x ***.sh .文件后缀为sh的文件为bash文件

## 变量

first_name=good

last_name=hacker —定义一个变量

echo $first_name $last_name —使用echo进行输出内容，输出多个内容以空格隔开

输出：good hacker

new_name=aaa bbb 注意：此时需要将值使用单引号或双引号标记起来，正确写法为：new_name='aaa bbb '

user=$(whoami) —将命令赋值给一个变量

输出：kali

user2=`whoami` —将命令赋值给一个变量的另一种写法，使用反引号将命令包裹起来

### 备注：不推荐使用反引号的书写方式。

```bash
#!/bin/bash

echo "The first two arguments are $1 and $2"

# **.sh hello there .
```

传参并输出在控制台

## 接收用户输入

```bash
!/bin/bash

echo "Hello there ,would you like to learn how to hack:y/n?"

read answer

echo "Yor answer was $answer"
```

使用read参数来进行读取用户输入的内容，并展示在控制台

```bash
#!/bin/bash
# Prompt the user for credentials

read -p 'useranme:' username
read -sp "password:" password
echo "hanks ,your creds are as follows: "$username "and" $password
```

参数说明：

-p 使用指定提示符

-s 使用户输入方式为静默状态（没有回显）

## if，else，elif

### if

```bash
#!/bin/bash
# if statement example

read -p "what is your age: " age

if [ $age -lt 16 ] #写法1
then
	echo "You might need parental permission to take this course!"
fi

#以下为多行注释
:<<!
if test $age -lt 16 #写法2
then
	echo "You might need parental permission to take this course!"
fi
!
```

运行结果：输入小于16的数字时，会输出echo中的内容，否则什么都不输出

注意：空格一定要写，要不然会报错。推荐使用第一种写法，更清晰直观

参数说明：

-lt 表示小于某个数字

-gt 表示大于某个数字

更多参数请参阅：https://tldp.org/LDP/abs/html/comparison-ops.html

### else

```bash
#!/bin/bash
# else statement example

read -p "what is your age: " age

if [ $age -lt 16 ] 
then
	echo "You might need parental permission to take this course!"
else
	echo "Welcome to the course!"
fi
```

条件运行为真时，执行then中的语句，否则执行else中的语句

### elif

```bash
#!/bin/bash
# elif example

read -p "what is your age: " age

if [ $age -lt 16 ] 
then
	echo "You might need parental permission to take this course!"
elif [ $age -gt 60 ]
then
	echo "Hats off to you ,respect!"
else
	echo "Welcome to the course!"
fi
```

## boolean

```bash
user2=kali
grep $user2 /etc/passwd && echo "user2 found!"
```

使用管道符将值传送到某个文件中进行查找，如果找到则进行后续的输出，否则什么都不做

```bash
user2=bob
grep $user2 /etc/passwd && echo "user2 found!" || echo "$user2 not found!"
```

参数说明：

&& and操作符，如果条件为真则执行，否则不执行

｜｜ or操作符，如果前面的条件为假，则执行，否则不执行

```bash
#!/bin/bash
# and example

if [ $USER == 'kali' ] && [ $HOSTNAME == 'kali' ]
then
	echo "Multiple statements are true!"
else
	echo "Not much to see here..."
fi
```

查看当前用户以及主机名是否为kali，如果是则执行第一段，否则执行else

```bash
#!/bin/bash
# and example

if [ $USER == 'kali' ] || [ $HOSTNAME == 'pwn' ]
then
	echo "One condition is true, this line is printed"
else
	echo "You are out of luck"
fi
```

条件有一个为真，则为真，否则为假

## 循环

```bash
写法1：for ip in$(seq 1 10); do echo 10.11.1.$ip;done
写法2：for ip in{1..10}; do echo 10.11.1.$ip;done
```

while:

```bash
#!/bin/bash
# while loop example

counter=1

while [ $counter -lt 10 ]
do
	echo "192.168.2.$counter"
	((counter++))
done
```

while2:

```bash
#!/bin/bash
# while loop example

counter=1

while [ $counter -le 10 ]
do
	echo "192.168.2.$counter"
	((counter++))
done
```

参数：小于：lt     小于等于：le

## Functions

```bash
#!/bin/bash
# function example

print_me(){
	echo "You have been printed"
}
print_me
```

例子：

```bash
#!/bin/bash
# passing arguments to functions

pass_arg(){
	echo "Today's random number is:$1'"
}

pass_arg $RANDOM # 产生一个随机数
pass_arg $(($RANDOM % 10)) #产生一个10以内的数
pass_arg $(($RANDOM % 10 +1 )) #产生一个1-10的数
```

参数：random 是一个bash函数（不是常量），它返回一个随机的带符号16位整数（从0到32767）

接收变量

例子2:

```bash
#!/bin/bash
# function return value example

return_me(){
	echo "Oh hello there ,I'm returning a random value!"
	return $RANDOM	
}

return_me

echo "The previous function returned a value of $?" #这里会接收到返回值
echo $? #程序运行结束，返回值为0
```

例子3:（作用域

```bash
#!/bin/bash
# var scope example

name1="john"
name2="Jason"

name_change(){
	local name1="Edward"
	echo "Inside of this function,name1 is $name1 and name2 is $name2"
	name2="lucas"
}

name_change

echo "After the function call,name1 is $name1 and name2 is $name2"
```

使用local可以将变量的作用域确定在当前语句内，如果没有使用lcoal则会影响到全局变量的值。

想要在当前的语句内使用变量而不影响全局变量值时，可以使用local

## 实例：

```bash
wget www.megacorpone.com 
#下载首页
grep "href=" index.html 
#查找所有带有href的字符串的行
grep "href=" index.html |grep "\\.megacorpone" | grep -v "www\\.megacorpone\\.com" | head
#使用-v去除所有已知域名的行
grep "href=" index.html |grep "\\.megacorpone" | grep -v "www\\.megacorpone\\.com" | awk -F "http://" '{print $2}' 
#使用awk的-F选项将多个字符进行分割，然后取得已知的链接第二节的字段
grep "href=" index.html |grep "\\.megacorpone" | grep -v "www\\.megacorpone\\.com" | awk -F "http://" '{print $2}' | cut -d "/" -f 1
#使用cut-d参数将第一个/之前的内容留下，其他的全部删除
```

简单的写法：

```bash
grep -o '[^/]*\\.megacorpone\\.com' index.html ｜sort -u >list.txt
#使用正则表达式将以megacorpone的内容全部取出，并去重   使用-u参数
```

示例：

```bash
#1
for url in $(cat list.txt); do host $url ;done
# 将文件内的域名使用for循环来获取主机IP地址
#2
for url in $(cat list.txt); do host $url; done | grep "has address" | cut -d " " -f 4 | sort -u
#将获取到的主机IP地址进行去重
```

## 实例2:

```bash
searchsploit afd windows -w -t 
#搜索带有afd的exploit文件的url
```

参数：

-w 返回url而不是本地路径

-t 搜索exploit标题

```bash
searchsploit afd windows -w -t | grep http |cut -f 2 -d '|'
# 将获取到的结果使用grep过滤出带有http的连接，并使用-f参数切割出包含url这一列
searchsploit afd windows -w -t | cut -f 2 -d "|"
#类似上一条语句，切割出带有url这一列
```

例子：

```bash
for e in $(searchsploit afd windows -w -t | grep http | cut -f 2 -d "|"); do exp_name=$(echo $e | cut -d "/" -f 5) && url=$(echo $e | sed 's/exploits/raw/') && wget -q --no-check-certificate $url -O $exp_name; done
#将下载到的文件进行切割，最终得到下载的文件
```

## 实例3：

```bash
mkdir temp
cd temp/
sudo nmap -A -p80 --open 10.11.1.0/24 -oG nmap-scan_10.11.1.1-254
```

检测当前c段是否存在开放80端口的机器，并将结果保存为greppable格式

参数：

-A 主动扫描

-p 指定端口

—open 只返回打开指定端口的机器信息

-oG 保存结果为特定格式

```bash
cat nmap-scan_10.11.1.1-254 | grep 80
#过滤出包含80字段的行
cat nmap-scan_10.11.1.1-254 | grep 80 | grep -v "Nmap"
#去除带有Nmap的行
cat nmap-scan_10.11.1.1-254 | grep 80 | grep -v "Nmap" | awk '{print $2}'
#提取IP地址，使用awk提取第二个字段，使用空格作为分割符
```

