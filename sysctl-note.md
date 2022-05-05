

这个用来配置内核参数。

示例：

新增配置 `net.ipv4.ip_forward = 1` ：

~~~ sh
: 新增持久配置
echo net.ipv4.ip_forward = 1 > /etc/sysctl.d/ipfwd.conf
: 立即生效所有持久配置
sysctl -p
~~~

