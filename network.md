``` shell
# 显示所有设备ip 地址等信息
ip addr show
# 上面这条命令的简化版：
ip a

# 显示设备wlp0s20f3 的 ip 地址等信息
ip addr show wlp0s20f3

ip link set eth1 up
ip link set eth1 down

# 只看ipv4
ip -4 a

# 给设备wlp0s20f3 添加一个ip  重启后会消失
sudo ip addr add 192.168.21.228 dev wlp0s20f3

# 此时再看设备ip：
ip addr show wlp0s20f3

# 结果为：
# 3: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
#     link/ether 80:38:fb:17:7e:24 brd ff:ff:ff:ff:ff:ff
#     inet 10.42.0.1/24 brd 10.42.0.255 scope global noprefixroute wlp0s20f3
#        valid_lft forever preferred_lft forever
#     inet 192.168.21.228/32 scope global wlp0s20f3
#        valid_lft forever preferred_lft forever
#     inet6 fe80::242c:a58b:e300:925d/64 scope link noprefixroute
#        valid_lft forever preferred_lft forever
# 可以看到在原有的10.42.0.1/24 基础上加了个192.168.21.228/32  的ip

# 移除ip
sudo ip addr del 192.168.21.228/32 dev eth1

# 查看路由
ip route show

# 添加静态路由 之所以要添加路由是希望流量不从默认路由走
ip route add 10.10.20.0/24 via 192.168.50.100 dev eth0

# 删除静态路由
ip route del 10.10.20.0/24

# 添加持久化静态路由
# 去这个网址看把
# 这些个ip命令引用于 https://www.tecmint.com/ip-command-examples/

```
