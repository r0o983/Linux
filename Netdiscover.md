#专用于二层发现  
#可用于无线和交换网络环境  
#主动和被动探测  

#主动  
netdiscover -i eth0 -r 1.1.1.0/24	扫描  
netdiscover -l ~/Desktop/abc		使用地址列表来进行扫描  

#被动  
netdiscover -p 	将自己的网卡制成混杂模式，当网络中有arp包经过本网卡，那么就会被抓取下来。  

