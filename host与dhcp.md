## /etc/hosts中的绑定ip只能绑定到对应的记录和字面的域名。如：
1.2.3.4 abc.com #只绑定abc.com一个域名的ipv4解析。dnsmasq尊重这个解析，但还是会继续向上级dns server查询其ipv6解析。
## /etc/config/dhcp中的绑定地址可以为以指定域名为前缀的所有域名绑定解析。如：
list address '/ieeexplore.ieee.org/140.98.193.112' #绑定140.98.193.112到ieeexplore.ieee.org及其子孙域名，若没有显式指定server，则不再向上级dns server查询其ipv6解析。
### ps: 实验室的dhcp需要开启Use broadcast flag，才能实时获取ip。
