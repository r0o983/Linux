# overthewire

## first 0 :

帐号和密码：
主机信息：bandit.labs.overthewire.org -p 2220

connect  the ssh 

cat readme // 获取密码 result :boJ9jbbUNNfktd78OOpsqOltutMc3MY1

## 第一关

读取虚线文件内的密码

cat ./-

如果直接使用cat -  命令，则会被当作命令进行执行 

result: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

## 第二关

获取带有空格的文件名文件的内容

result:UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

## 第三关

找到隐藏文件中的密码

result:pIwrPrtPN36QITSp3EQaw936yaFoFgAB

code:cat inhere/.hidden

## 第四关

找到非乱码文件中的密码
注意：使用虚线开头需要重设路径来查看文件内容

result :koReBOKuIDDepwhWk7jZC0RTdopnAYKh

## 第五关

当前文件夹下找到字节数为1033的文件

find . -size 1033c 

result : DXjZPULLxYr17uwoI01bNLQbtFemEgo7

## 第六关

找到字节数为33字节的文件，并且属主为bandit7,属组为bandit6.

find / -size 33c -user bandit7 -group bandit6

find / -size 33c -user bandit7 -group bandit6 2>/dev/null 删除报错信息

result : HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

## 第七关

从文本中找到关键字和匹配的密码

cat date.txt | grep "millonth"

result: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

## 第八关

从文档中的重复文本中找到唯一的值

code : sort data.txt | uniq -c | sort -c

result : UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

## 第九关

从乱码文件中找到密码，提示为：最后几个字符为=

思路：打开文本都是乱码，所以第一时间先找到原文提示的位置，看看有没有什么发现，结果发现啥都没。
于是使用xdd（16进制）来打开文件，并定位到提示位置，发现可以用xdd打开，并且显示正常，于是使用strings （二进制）来进行打开文件，最终发现了密码

code : strings date.txt | grep "="

result : truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

## 第十关

使用base64解密即可

code : cat data.txt | base64 -d

result : IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

## 第十一关

踩坑：只纠结于题面，要求大小写进行反转，忽略了后续的提示。实际上只需要使用rot13解密即可（浪费一天时间，我艹。

code : cat date.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

result : 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

## 第十二关

不解释。。。

result : 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

## 第十三关

