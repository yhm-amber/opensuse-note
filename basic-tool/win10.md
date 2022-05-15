# Windows 软件安装建议

## 前言

首先，除非你完全知晓软件的行为并绝对信任，否则**不要允许任何不论有没有证书的软件获取你的管理员权限**。

万不得已，可以先尝试在沙箱里运行它。沙箱推荐 [Sandboxie](https://github.com/sandboxie-plus/Sandboxie) 。个人推荐 Classic 版本。

开源要辩证看待。很明显的一个事实是，开源软件确实比闭源软件真诚太多了。但有的开源软件的源码是故意写得难懂的，实质上约等于闭源，却有着开源名号，这种就会有迷惑性；而由于经济原因，一些也很优秀的软件其实并非开源。特别是在没索取太多权限的时候，这种软件还是可信从而可用的。**对于安全需要，开源软件的唯一优势就是它主动接受监督。这也是另一个软件真诚提供功能的最重要的一点，不过目前的窘境在于，这并非是来自群众的监督，因此即便监督者用意真诚，也没法避免缺少力量的窘境。。。**

**能用 `.msi` 格式的安装包就别用 `.exe` 的！！！！前者才是 Windows 的标准的安装包，后者只是一个可执行程序而已。简单说，如果大家都用前者安装，那应该也就不存在卸载还要清理残留的情况了。**

## 不建议的

360 系列。原因：

- 我曾经有电脑装过它们浏览器，后来卸载了，并用各种工具清理了注册表啊失效配置文件啊等等。然而，在 N 卡的显卡针对软件的设置选项里，可选软件下拉框里，还有这玩意。
- 它帮你监视一切，包括你，谁监视它？另外，总觉得 360 这软件大有被做成小游戏集合的趋势……它到底干啥的？
- 它有优秀而且干净甚至开源的替代：
  
  - 大部分功能：[火绒](https://huorong.cn/)。杀毒和防火墙，还有很多专业工具，火绒都能搞定。火绒可以定制各种各样的防火墙规则，你也可以用别人的分享。更重要的是，火绒那家公司有良心， 360 以前做啥的？有兴趣欢迎查查。
  - 沙箱： [Sandboxie](https://github.com/sandboxie-plus/Sandboxie) 。现在这个软件是开源的，可以下下来用用看，或者下下源码来看看。
  - 卸载： [GeekUninstaller](https://geekuninstaller.com) 或者 [Total-Uninstaller](https://github.com/tsasioglu/Total-Uninstaller) 。前者没找到源码应该是没开源，后者开源而且是用 C# 写的。二者都能清理残留。
  - 很多 360 没有但很有用的功能： [Dism++](https://github.com/Chuyu-Team/Dism-Multi-language) 。它可以轻松开关开关就配置 Windows 的很多你在意的设置，还能备份系统或者管理补丁啥的。备份系统是 WIM ，比 Ghost 高到不知道哪去了（后者伤硬盘）。


腾讯的软件。原因：

- 首先你那个电脑管家千万别装，我确定它有能力挟持你的系统的默认应用（就是所谓默认打开方式）选择界面。
- QQ 和 TIM 都被查出过这种行为：刻意扫描用户硬盘上所有文件。然而，腾讯擅长闷声和卖萌，而且大家都在用，可能还有别的原因，总之最后也就给糊弄过去了，就没人再管这事儿，从而多数人并不知道有这回事（或者知道也认为没辙）。
- 我曾经见过 QQ 浏览器的安装目录里的一个程序提示一些奇怪的错误信息，搜了一下，有结果的网站都说那是毒。
- QQ 可能不好替代，即便有优秀的开源产品，因为这个软件的功能大部分不在于软件本身，而在用软件的人。社交软件，若你想与之交流的人不用，那它再好用，也没用。
- 微信一般是不可或缺的（主要原因仍然是其在圈地运动中的胜利（而这个胜利首要的并非软件的好用）），所以我们最好把它管起来：即，使用 Windows 商店里的那个（不是看着很移动的那个而是桌面版套壳的那个），地址点[这里](https://www.microsoft.com/zh-cn/p/%E5%BE%AE%E4%BF%A1-for-windows/9nblggh4slx7)。


下载工具：

不要用迅雷。

什么 [qbittorrent](https://github.com/qbittorrent/qBittorrent) 啊 [FDM](https://www.freedownloadmanager.org) 啊，有的是免费还好用的选择。实在不行，搜一个绿化版的迅雷。前者是专门下种子的，但需要手动配置 Tracker 服务器，不过后者不用，但后者我没找到完整源码。

## 建议的

### 浏览器

Edge: 如果是最新的 Win10 其实已经装好了，三指敲击触控板然后打字搜索就好。如果不是 Win10 那是用不了的，没法装，如果是 Win10 旧版，可能装了可能没装，但微软会努力给你变成新版（如果微软的努力失败了那我也没办法了）。如果被你卸载了，哈哈哈哈哈那可太有趣了，你还可以再装，从 Bing 自己搜这个名字就好。谷歌内核，可以装谷歌的插件。

建议的浏览器：

- [Brave](https://brave.com): 它从设计上是注重隐私的。即便不装插件，隐私保护也非常不错。谷歌内核，可以装谷歌的插件。  
- [firefox](https://www.mozilla.org/zh-CN/firefox/new/): 火狐唯一要注意的就是网址。官网是 mozilla.org 而不是 firefox.cn 。火狐内核，可以装火狐插件。  
- [waterfox](https://www.waterfox.net): 它用的老版的渲染，并且构建自火狐的开源代码。一些老插件新火狐不能用了它这也能用。火狐内核，可以装火狐插件。  

建议的配置：

- 先找关键词【搜索】，把必应换成默认，把百度，删了。  
- 然后，找【追踪】或者【隐私】，选自定义，按需要选择。  
- 然后装下面的必要的插件。（在 Brave 上可以忽略这一部分。）  


### 浏览器插件

建议必装：

- [Ghostery](https://github.com/ghostery/ghostery-extension): 小蓝幽灵。默认配置就好，反追踪用的，一部分 JS 会被它拦截。火狐也有同名插件。【 [edge](https://microsoftedge.microsoft.com/addons/detail/fclbdkbhjlgkbpfldjodgjncejkkjcme) 、 [firefox](https://addons.mozilla.org/addon/ghostery) 】  
- [隐私獾](https://github.com/EFForg/privacybadger): 这个东西有学习能力，也是反追踪的。在设置里，可以把拦截 WebRTC 的勾打上。 【 [edge](https://microsoftedge.microsoft.com/addons/detail/privacy-badger/mkejgcgkdlddbggjhhflekkondicpnop) 、 [firefox](https://addons.mozilla.org/addon/privacy-badger17) 】  
- [uBlock](https://github.com/gorhill/uBlock): 一个可以用鼠标指针定制拦截项的插件。设置里同样能拦 WebRTC 。 【 [edge](https://microsoftedge.microsoft.com/addons/detail/odfafepnkmbhccpbejgmiehpchacaeak) 、 [firefox](https://addons.mozilla.org/addon/ublock-origin) 】  
- [momentum](https://www.momentumdash.com): 这是个美化新标签页的扩展——话虽如此，鉴于 Edge 那个屑得不行的全是广告的新标签页，它竟然也具备了拦截垃圾信息的功能（火狐新标签页很干净所以不用装）。。。。这个装上后要注意，你需要手动开启它。（没找到源码，可能是闭源的。） 【 [edge](https://microsoftedge.microsoft.com/addons/detail/jdoanlopeanabgejgmdncljhkdplcfed) 、 [firefox](https://addons.mozilla.org/addon/momentumdash) 】  
- [FeHelper](https://github.com/zxlie/FeHelper): 这本来是给前端开发提供方便的工具，但就算你不是，我也建议你装它。为什么？看看它里头有什么你就明白了！你很可能会大吃一惊，苦苦找了很久的动能竟然已经有了，还是开源实现！（它没上架火狐商店，可能是不符合火狐官方的要求（它其实是插件集了），但可以从它软件自己的网站用按钮装。不过这个我觉得 edge 装一个就够了，它只是工具集而不是反追踪什么的，一个系统有一个就够了。） 【 [edge](https://microsoftedge.microsoft.com/addons/detail/feolnkbgcbjmamimpfcnklggdcbgakhe) 、 [other](https://www.baidufe.com/fehelper/index/index.html) 】  
- [HTTPS Everywhere](https://github.com/EFForg/https-everywhere): 说是能让你处处都是 HTTPS 协议，不过好像得配置。（这个在前面提到过的 Brave 里已经集成安装） 【 [edge](https://microsoftedge.microsoft.com/addons/detail/https-everywhere/fchjpkplmbeeeaaogdbhjbgbknjobohb) 、 [firefox](https://addons.mozilla.org/addon/https-everywhere) 】  
- [decentraleyes](https://git.synz.io/Synzvato/decentraleyes): 也是一个反追踪的，但原理好像不太一样，具体可以看介绍，英文的。（它的新存储库不在 github ） 【 [edge](https://microsoftedge.microsoft.com/addons/detail/decentraleyes/lmijmgnfconjockjeepmlmkkibfgjmla) 、 [firefox](https://addons.mozilla.org/addon/decentraleyes) 】  
- [privacypossum](https://github.com/cowlicks/privacypossum): 隐私保护的。一般没见它起作用，但有时候发现它的拦截数一直在增加，而当时的网站页面功能没受影响，所以判断是那个网站大概是有一些《多余的功能》了吧。 【 [edge](https://microsoftedge.microsoft.com/addons/detail/privacy-badger/mkejgcgkdlddbggjhhflekkondicpnop) 、 [firefox](https://addons.mozilla.org/addon/privacy-possum) 】  
- ~~[tampermonkey](https://github.com/Tampermonkey/tampermonkey): 著名的油猴脚本。它是个插件，但它可以**被**安装很多脚本（都是能直接看代码的 JS 脚本）。我文末会提供一段内容，复制出来粘贴到 TXT 里，你就能用它导入一对还不错的油猴脚本，附带一部分配置。~~**不建议没有源码阅读能力的人使用任何油猴脚本。**  


可选：

Scrollbar 、 Adguard 、 AdblockerPlus 等等，还有你也许会看到一些你需要的工具。

### 解压软件

下面仨建议都装，因为各有各的用处不重叠。

- [bandizip](https://cn.bandisoft.com/bandizip): 这个解压快，还能很方便预览压缩包。免费有广告版本也无伤大雅，因为那都是他们家别的优秀产品的广告……（我从没见过这种放弃赚钱机会的）  
- [7-zip](https://7-zip.org): 压缩工具，还能给你校验好几种哈希。**安装包务必下那个结尾是 `.msi` 的！！！！**  
- [WinRAR](http://www.winrar.com.cn): 这个应该不用介绍了，而它的特点就是很多打包压缩有关的部分在它这都是多步并作一步的。有时候比 7-zip 最好的压缩效果还好，大部分时候都不行。支持一定的修复功能（需要压缩时开启恢复记录）。**好像分国内国外俩版本**，国内是免费的而且下的是完整包，免费版有广告，这广告可以让火绒的广告拦截解决，而且不打开也不会有广告弹出，也算比较良心。  

### 看图软件

建议必装：

- [honeyview](https://cn.bandisoft.com/honeyview): 看图很快，比系统自己那个快，浏览模式也多。

### 硬件信息

硬盘：

- [CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo): 这个页面里的几个软件功能一样，只是外观不同。根据英文提示按需选择。能看固态寿命。代码仓库： [hiyohiyo/CrystalDiskInfo](https://github.com/hiyohiyo/CrystalDiskInfo) 。  

CPU：

- [cpu-z](https://www.cpuid.com/softwares/cpu-z.html): 比较有名的看 CPU 硬件信息的软件。它甚至还能看内存信息和显卡信息。  


### 资源管理

存储容量：

- [filelight](https://www.microsoft.com/zh-cn/p/filelight/9pfxcd722m2c): 这个就从 Win10 商店下载就好。能直观展示你的硬盘内空间占用情况，盘满了谁的锅一目了然。它是 KDE 项目中的一员，我是用了 Linux 桌面才知道还有这么个东西。代码仓库： [KDE/filelight](https://github.com/KDE/filelight) 。  





### 多媒体制作

作图的：

- [krita](https://krita.org): 笔刷很多，比较专业的画画软件，同样是 KDE 开源项目中的一员。可以从官网下安装包自己装，这样是免费的（亲自从源码编译出来当然更免费），也可以从 Win10 商店下，但需要购买。（是的，谁也没说开源不允许收费，只是要求务必提供源码而已。。。）（他们这个收费意思是当捐赠渠道了。。。。）  
- GIMP


### 办公套件

Office：

- [libreoffice](https://libreoffice.org): 开源的里头它是最好用的了。比微软的 MSOffice 快速很多（主要是微软那个特效太多）。没找到代码仓库，软件网站下载页面能直接下源码。  
- MSOffice: 微软那个 Office 。有的电脑买来会赠送，有的不会。  
- WPS: 这个我是搜政府版来用，比较快，对文档的兼容能力**超过了微软的 Office 。**（只要是 `.docx` 而不是 `.doc` 的话）  


PDF：

微软商店有，自己找找，浏览器也能看。 Adobe 官方那个编辑器的话，自己想办法搞吧。。。


### 文本文件编辑

主要是写代码，或者确保文本内容的编码、行末符，等等。

- Sublime
- VSCode
- Kate
- ...


## 防毒措施

现在病毒（广义的任何形式的恶意软件）入侵就这几个途径：

- U 盘乱插：这是最严重的，乱插了建议重做系统吧，当然了不保证这样能根除（笑）。**避免手段：可以装一套 VMWare ，然后插之前开开虚拟机。但建议不要通过 U 盘分享东西，而是用局域网文件共享软件，或者哪怕是互联网文件共享应用，比如这个： `https://send.vis.ee` 。**  
- 浏览不干净的网站。我不是说那种不干净，说真的，论追踪器疯狂程度，腾讯**系**的所谓「正规」网站可比某些色情网站都猖狂得不得了的。**这个的避免手段就是前面提到的插件。**  
- 主动使用毒瘤软件。现在病毒目的都不在破坏，而是偷你信息、或者用你电脑刷广告（在你屏幕视野不可见区域），可能还有比较奇葩的会试图用你电脑挖矿。反正，都已经不是给你直接明显的经济损失了，而是在给你制造各种麻烦和更长远隐患的同时，给他们自己带来切实的经济利益，破坏性可以说其实更大了，因为它无疑会直接波及你的生活，而不是只会直接波及你的电脑。  















