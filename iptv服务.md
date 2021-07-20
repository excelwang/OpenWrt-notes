0.安装luci-app-udpxy

1.在web界面配置udpxy：

*enable*

*设置Bind IP/Interface为lan口ip*

2.配置/etc/config/firewall，新增：

`
config rule

        option target 'ACCEPT'
        
        option src 'wan'
        
        option name 'IPTV'
        
        option family 'ipv4'
        
        option proto 'udp'
        
        option dest_ip '224.0.0.0/4'
`
