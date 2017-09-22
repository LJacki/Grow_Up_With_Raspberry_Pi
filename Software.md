## Suggested  Software

[TOC]

Raspberry Pi 的系统 Raspbain 毕竟是基于 Linux 的发行版 Debain，所以一些在 Linux 上的软件，在树莓派上理应也都能使用。

在学习的过程中，也遇到过形形色色的软件，有的非常实用，不时的感叹，这功能也忒强大了，同样的也有的软件，特别搞笑，让人不禁使用一次，笑一整天，然后也还是用的爱不释手。这种软件越是无聊，你就觉得这种软件很是奇妙。

现在开始介绍吧！

### APT命令

介绍软件之前先介绍这款工具，`apt-get` 是一条命令 `Advanced Package Tool` ，是一款适用于Unix和Linux系统的应用程序管理。 `apt-get` 成名的原因之一在于其出色的解决软件依赖关系的能力，在Linux社区得到广泛使用，成为用来管理桌面、笔记本和网络的重要工具。

#### apt命令用法

Package name指代为软件包的名称。

#####  apt-get update

需要定期运行这一命令以确保软件包列表是最新的。

- apt-get install package name

  安装一个新软件包

- apt-get remove package name

  卸载一个已安装的软件包（保留配置文档）

- apt-get remove --purge package name

  卸载一个已安装的软件包（删除配置文档）

- apt-get autoremove package name

  删除包及其以来的软件包

- apt-get autoremove  --purge package name

  删除包及其依赖的软件包+配置文件，删除的更加彻底

- dpkg -- force-all --purge package name

  有些软件很难卸载，而且还阻止了别的软件的应用，就用这个，但是有点冒险。

##### apt-get autoclean

apt会把已装或者已卸载的软件都备份在硬盘上，所以假如需要空间的话，就能让这个命令来删除已经卸载的软件的备份。

##### apt-get clean

这个命令会把安装的软件的备份也删除，但是不会影响软件的正常使用。

##### apt-get upgrade

这条指令可以更新软件包，不仅可以从相同版本号的发布版中更新软件包，也可以从新版本号的发布版中更新软件包，尽管实现后一种更新的推荐命令为 `apt-get dist-upgrade`。

 在运行apt-get upgrade命令时加上-u选项很有用（即：`apt-get -u upgrade` )。这个选项让APT显示完整的可更新软件包列表。不加这个选项，你就只能盲目地更新。APT会下载每个软件包的最新更新版本，然后以合理的次序安装它们。注意在运行该命令前应先运行 `apt-get update` 更新数据库，更新任何已安装的软件包。

##### apt-get dist-upgrade

将系统升级到新版本。

##### apt-cache search string

在软件包列表中搜索字符串。

`dpkg -l package-name-pattern` 列出任何和模式相匹配的软件包。假如您不知道软件包的全名，您能够使用 `package-name-pattern` 。

##### aptitude

周详查看已安装或可用的软件包。和 `apt-get` 类似，`aptitude` 能够通过命令行方式调用，但仅限于某些命令——最常见的有安装和卸载命令。

由于 `aptitude` 比 `apt-get` 了解更多信息，能够说他更适合用来进行安装和卸载。

##### apt-cache showpkg pkgs

显示软件包信息。

`apt-cache dumpavail` 打印可用软件包列表。

##### apt-cache pkgnames

打印软件包列表中任何软件包的名称。

##### dpkg -S file

这个文档属于哪个已经安装的软件包。

##### dpkg -L package

列出软件包中的任何文档。

##### dpkg -l

理出所有已经安装的软件包。

##### apt-file search filename

查找包含特定文档的软件包（不一定是已安装的），这些文档的文档中含有指定的字符串。

`apt-file` 是个单独的软件包。需先试用 `apt-get install` 安装。

假如`apt-file search filename` 输出的内容太多，可以尝试使用 `apt-file search filename | grep -w filename` （只显示指定字符串作为完整的单词出现在其中的那些文档名）或类似方法，例如：`apt-file search filename | grep /bin/` （只显示位于诸如/bin或/usr/bin这些文件夹中的文档，假如要查找的是某个特定的执行文档的话，这样做是有帮助的）。

##### apt-get autoclean

定期运行这个命令来清除那些已卸载的软件包的.deb文档。通过这种方式，您能够释放大量的磁盘空间。假如您的需求十分迫切，能够使用 `apt-get clean` 以释放更多空间。这个命令会将已安装软件包裹的.deb文档一并删除。大多数情况下不会再用到这些.debs文档，因此假如你为磁盘空间不足而感到焦头烂额，这个办法也许值得一试。

#### 致谢

 以上对于APT命令的介绍来自[百度百科__apt-get](https://baike.baidu.com/item/apt-get/2360755?fr=aladdin) ，感谢所有为此文档做过贡献的笔者。

### Useless__Software

### Useful__Software

### Others__Software

### 写在后面

### Loading

