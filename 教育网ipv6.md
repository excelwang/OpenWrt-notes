#教育网ipv6
##环境
教育网ipv6当前的设置是slaac,支持ndp和ra的relay.参考:http://bbs.pku.edu.cn/bbs/bbstcon.php?board=Networking&threadid=15501646
##搭建
更新odhcp到trunk版.（2015年7月版有bug导致路由器下游不能正常路由）
###配置纯ipv6环境下的域名解析
不知何故取不到wan6的peer dns。故需要增加公共ipv6 dns
uci add_list network.wan6.dns=2001:4860:4860::8888
uci add_list network.wan6.dns=2001:4860:4860::4444
uci commit
/etc/init.d/network restart
注意：网上的一些参考配置要注释掉network.globals。但并无必要这样做。
###配置dhcp
####注释掉dhcp.wan
####增加wan6到lan的relay
uci set dhcp.wan6=dhcp
uci set dhcp.wan6.dhcpv6=disabled
uci set dhcp.wan6.ra=relay
uci set dhcp.wan6.ndp=relay
uci set dhcp.wan6.master=1
uci set dhcp.lan.dhcpv6=disabled
uci set dhcp.lan.ra=relay
uci set dhcp.lan.ndp=relay
uci commit
/etc/init.d/odhcp restart