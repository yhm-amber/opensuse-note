## 压缩

众所周知，在 KISS 原则下的 Linux 里面，打包和压缩是被不同的软件和文件格式负责的工作。 `TAR` 档案只是把多个文件或者多层目录变成一个单文件的方案，没有压缩率。

下面介绍两种压缩途径： `XZ` 和 `ZSTD` 。

前者具有现在开源方案里普遍而言最高的压缩率（闭源的 `RAR5` 算法有的场景会比它好），后者是兼顾了解压速度和压缩率的最佳方案——它比前者压缩率只是稍，但解压速度是大幅提升的。

*P.S. ： 在 GNU/Linux 的 Arch 系发行版上，社区对 `pacman` 包管理器的软件安装包的 `TAR` 档案最初采用的是 `XZ` 的压缩方案，后来改为了 `ZSTD` 的压缩方案。这对于同样使用 `pacman` 做包管理器的 Windows 上的 Msys2 界面亦同。*

### `XZ`

c

~~~ sh
tar -cf- -- * | xz -T0 --best > baged.tar.xz # 压缩本目录下的一切
tar -cf- -- abc | xz -T0 --best > baged.tar.xz # 压缩本目录下的 abc (不论它是文件还是文件夹)
~~~

x

~~~ sh
xz -d baged.tar.xz --stdout | tar -xf- # 解压到本目录
tar xJf baged.txz # 效果同上
~~~

使用案例：

docker/podman 的 `save` 子命令的输出结果是一个 `TAR` 格式的档案。

这个命令用于以文件的形式取得离线的镜像。

由于是 `TAR` 格式，所以没有压缩率，只是打包。所以如果想要有压缩率，就可以这样跟个管道：

~~~~ sh
docker save -- docker.io/library/hello-world:latest | xz --best -T0 -- - > hello.tar.xz
~~~~

这个示例是对全名为 `docker.io/library/hello-world:latest` 的镜像的导出档案使用 `xz` （和 7-zip 一样的算法）的最高压缩率，在动态取得的某个并发度（就是说并发度和所在机器 CPU 数相等）下完成压缩。压缩结果默认写给标准输出，需要重定向到文件。

在用 docker/podman 的 `load` 子命令时，直接使用 `-i` 选项指定这个 `xxx.tar.xz` 文件即可，无需分步骤解压。

当然，一定要分步骤也不是不行。

下面两个都能载入离线的镜像文件：

~~~~ sh
cat hello.tar.xz | xz -d --stdout -- - | docker load
docker load -i hello.tar.xz
~~~~

扩展名其实无所谓是什么， Linux 没有多少扩展名敏感的软件，有也只是在显示效果上的影响。

### `ZSTD`

(todo...)



## 网络

### `NetworkManager`

当下比较流行的网络管理组件就是 `NetworkManager` 。还有一些别的(todo...)

使用 `nmcli` 操作一个已启动的 `NetworkManager` 服务。

#### 列出

具体的 `nmcli` 的子命令可以在 `--help` 选项中看到。

它还有个特性就是缩写的机制。比如，这些个命令是一样的：

- `nmcli c show`
- `nmcli con show`
- `nmcli conn show`
- `nmcli connection show`

其中的 `show` 如果忽略的话，效果也是一样的。只要 `conn` 后面什么也没有，默认就是执行它的 `show` 子命令。另外， `show` 也可缩写为 `s` ： `nmcli c s` 。

这个命令用来列出所有的连接。

连接是名词。

如果想只显示名称的字段：

~~~ sh
nmcli -f NAME -- c s
~~~

简单显示的模式：

~~~ sh
nmcli -t -- c s
nmcli -f NAME -t -- c s
~~~

#### 配置

静态：

~~~ sh
nmcli c m <CONN-NAME> ipv4.method manual ipv4.address 10.1.0.123/24 ipv4.gateway 10.1.0.254 ipv4.dns 1.1.1.1,1.0.0.1 connection.autoconnect yes
nmcli c d <OTH-NAME>
~~~

同时你可能不希望别的某个连接自动开启：

~~~ sh
nmcli c m <SOME-CONN-NAME> connection.autoconnect no
nmcli c d <SOME-CONN-NAME>
~~~

其中：

- `m` 就是 `modify` ，也可写作 `mod` ，意思是更改，效果也是更改。
- `d` 就是 `down` ，在连接后面意思是断开（效果也是）；相反的意思是 `up` （效果也是）， `up` 简写为 `u` 。



