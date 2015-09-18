1.安装squid（须为3.5版本以上）：opkg install squid
2. 更改/etc/squid/squid.conf文件中的http_port为 0.0.0.0:6112，根据机器配置调整cache_dir参数。
3. 更改squid的http访问控制为允许所有：http_access allow all。
4. /etc/init.d/squid start
5. /etc/init.d/squid enable
6. 使用Flora_Pac生成自动代理脚本。或者修改本目录中flora.pac文件，把“host.com:6112”替换成代理主机。
7. 将flora.pac文件放置到/www/下。

使用方式：
第一种：配置代理服务器为代理主机名，端口为6112。（例如：host.com:6112）
第二种：配置自动代理脚本为代理主机web根目录/flora.pac。（例如：http://host.com/flora.pac）
