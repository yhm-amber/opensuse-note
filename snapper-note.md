
### Snapper

#### 基本

##### 配置

配置类似于 Kubernetes 的 _命名空间_ 一样的东西。

默认使用 `snapper list` 查看都有哪些快照时，等同于 `snapper -c root list` ，即选用 `root` 配置。

一个配置对应一个卷（在这里就是 Btrfs 卷）。

看都有哪些配置： `snapper list-configs`

创建一个配置： `snapper -c home create-config -- /home`

基于一个配置做些什么：

- `snapper -c home create -t single --description 'home snap born' --userdata important=yes`
- `snapper -c root create -t single --description 'root snap born' --userdata important=yes`

其中 `-c root` 默认可省略。

#### 对一堆命令打快照

会更改系统文件的行为，建议都基于这个命令来执行，以便后续追踪。

##### 需要的命令

~~~~ bash
snapper create -d 'desc' --command 'commands'
~~~~

如果是一堆命令，可以先把那堆命令做成函数，然后利用 `declare -f` 让它在里面调用。（类似的手段 `export -f` 在这里不适用：可能是因为上面的命令并不是作为当前进程的子进程来运行的。）

##### 示例

定义：

~~~~ bash
ask_user ()
{
    predesc="${1:-Hey 👻}"
    ask="${2:-what should i ask ???}" &&
    anss="${3:-[y/n] (:p)}" &&
    
    cases="${4:-
        case \"\$ans\" in 
            
            y|\'\') echo 😦 yup\?\? ; break ;; 
            n) echo 🤔 no\? ; break ;; 
            *) echo 🤨 ahh\? what is \'\$"{"ans:-:p"}"\' \? ;; esac }" &&
    
    
    echo "$predesc" &&
    while read -p "$ask $anss " -- ans ;
    do eval "$cases" ; done ;
} ;

uuid_xfstab__ ()
{
    local rt ;
    
    case "$#" in 1|2) ;; *) 1>&2 echo need one or two args ; return 4 ;; esac ;
    
    : ::::::::::::::::: : ;
    
    dev_uuid ()
    {
        local device="$1" &&
        local field="$2" &&
        (eval "$(blkid -o export -- "$device")"' ; echo $'"${field:-UUID}") ;
    } &&
    
    uuid_fstab ()
    {
        local device="$1" &&
        local dir="${2:-/var/lib/docker}" &&
        
        echo UUID="$(
            dev_uuid "$device" UUID )"  "${dir:-/var/lib/containers}"  "$(
            dev_uuid "$device" TYPE )"  defaults,pquota  0 0 ;
    } &&
    
    : ::::::::::::::::: : &&
    
    local device="$1" &&
    local dir="${2:-/var/lib/libvirt/images/pool0}" &&
    
    mkdir -p -- "$dir" &&
    
    : 下边都是如果回答 n 就退出'(quit)' uuid_xfstab__ 否则就会执行到下边 &&
    
    {
        ask_user "
$(lsblk)

============

: got 
: 
:   dev: $device 
:   dir: $dir 
" ": make the $device in to xfs ? will clear datas in it ~~ 😬" "[y/n]" '
            
            case "$ans" in 
                y) echo ; return 0 ;; 
                n) echo : quit tool 😋 ; return 2 ;;
                *) ;; esac ' || return ;
        
        mkfs -t xfs -n ftype=1 -f -- "$device" ;
        
    } &&
    
    
    {
        ask_user "
: will add this line to fstab:
$(uuid_fstab "$device" "$dir")
" ': 🤔 go on ?' '[y/n]' '
            
            case "$ans" in
                y) echo ; return 0 ;;
                n) echo : quit tool 😘 ; return 2 ;;
                *) ;; esac ' || return ;
        
        (echo ; uuid_fstab "$device" "$dir" ; echo) | tee -a -- /etc/fstab ;
        
    } &&
    
    
    mount -a ||
    { rt=$? ; echo 😨 may need to check /etc/fstab and recmd mount -a ; return $rt ; } ;
    
    lsblk &&
    
    :;
} ;
~~~~

上面有两个函数。 [`ask_user`](https://github.com/hmrg-grmh/meta-shells/tree/main/dialec-cmdline) 可以当成是一个被使用的库，我在 `uuid_xfstab__` 的定义中使用了它，后者则能在一个有问话阻塞的字符界面，在经过用户检查并同意后，做出相应操作。


使用：

~~~~ bash
snapper create -d 'add a fstab data-volme for /var/lib/libvirt/images/pool2 use xfs' --command "$(declare -f -- ask_user uuid_xfstab__) ; "'uuid_xfstab__ /dev/sdi /var/lib/libvirt/images/pool2'
~~~~

这并不会影响交互的功能，一切都运行良好。我通过这个，可以为特定目录挂载特定的盘——格式化和对 `/etc/fstab` 的更改都是在询问要不要做并得到肯定答复后自动完成的。

库 `ask_user` 中使用了 `eval` 来达到元编程的效果，在此处（ `snapper crate --command cmds` ）也是完好运行的。
