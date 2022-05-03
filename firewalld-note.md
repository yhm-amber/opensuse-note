
以通过 tigervnc 的端口示例


~~~~ bash
: : : 看看 firewall 支持的服务里是否有 tigervnc  
firewall-cmd --get-services|fgrep vnc
: ls -l /usr/lib/firewalld/services/
: cat /usr/lib/firewalld/services/tigervnc.xml
: cat /usr/lib/firewalld/services/vnc-server.xml


: snapper create -d 'firewall pub http once' --command 'firewall-cmd --zone=public --add-service=http ## 运行时规则'
: snapper create -d 'firewall pub http' --command 'firewall-cmd --zone=public --add-service=http --permanent ## 永久规则'

snapper create -d 'firewall pub tigervnc' --command 'firewall-cmd --zone=public --add-service=tigervnc --permanent'
snapper create -d 'firewall pub vnc-server' --command 'firewall-cmd --zone=public --add-service=vnc-server --permanent'
firewall-cmd --list-services --permanent

: 开放特定的端口（TCP/UDP），例如开放 TCP/UDP 端口：55527：

: snapper create -d 'firewall pub 55527/tcp' --command 'firewall-cmd --zone=public --add-port=55527/tcp --permanent'
: snapper create -d 'firewall pub 55527/udp' --command 'firewall-cmd --zone=public --add-port=55527/udp --permanent'

sudo firewall-cmd --zone=public --list-ports
sudo firewall-cmd --zone=public --list-ports --permanent

: 拒绝/禁用 23/tcp 端口
: snapper create -d 'firewall rm 23/tcp' --command 'firewall-cmd --zone=public --remove-port=23/tcp --permanent'

: 刷新配置
sudo systemctl reload firewalld
~~~~



ref: https://zh.opensuse.org/SDB:Firewall-cmd



![image](https://user-images.githubusercontent.com/103625580/163377880-8978006d-52a1-462a-bf3d-7c9a29923dca.png)


从 `cat ...xxx/xxx/xxx.xml` 命令可以看到，一个 `firewall` 里的 “服务” 具体代表了哪些端口。


另外

这里用到的 `snapper` 是系统（ opensuse ）带的快照命令

`snapper create --command xxx` 会在执行 `xxx` 前建立一个快照、又在执行好后再建立个快照。

用 `snapper list` 可以看已有的快照，用 `snapper status 11..12` 可以比较两个快照的变化

更多：https://zh.opensuse.org/SDB:Snapper_Tutorial



 

