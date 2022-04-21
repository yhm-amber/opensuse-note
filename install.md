
## necessary

~~~ sh
zypper in -y -- rsync cargo xrdp tigervnc screen libvirt qemu-kvm firecracker neovim htop screenfetch neofetch suse-module-tools guestfs-tools
zypper in -t pattern -y -- kvm_tools xen_tools
zypper in -y -- snapper-zypp-plugin yast2-snapper
~~~

## optional

### full

~~~ sh
zypper in -- containerd podman buildah katacontainers docker docker-compose virtualbox vagrant nano git emacs git-daemon git-web luajit erlang
~~~

### lang

~~~ sh
zypper in -- luajit erlang rust cargo elixir java clang llvm
zypper in -- gcc go
~~~

### container

~~~ sh
zypper in -- containerd podman buildah katacontainers cilium
zypper in -- docker docker-compose
~~~

### virt

~~~ sh
zypper in -- virtualbox vagrant
~~~

### code

~~~ sh
zypper in -- nano git
zypper in -- emacs git-daemon git-web
~~~

### ...

## ...













