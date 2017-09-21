# Grow_Up_With_Raspberry_Pi

When u have a raspberry pi ,you should do something.

[TOC]

## Another Story

为什么要写这篇哦，我原本是没有打算的，直到我的树莓派系统被我彻底的玩坏掉。

预知后事如何，转到-->>`STORY.md`

## Something Used

使用本教程之前，你需要准备一些东西：

1. 树莓派 3代 B+

   这里使用的是三代B+版本，其他版本，自行尝试，一切后果概不负责。本人于2017年三月底购买的树莓派3代B+，约软妹币220，而现在九月份，某宝上的报价是178软妹币。

2. SD卡

   一般8G到16G到32G不等，但是一定得注意，需要一张高速读写的SD卡。这一点很关键，因为是用来当作系统盘的，如果买读写速度很次的次品卡，就会对系统运行时显得没有耐心，从而失去热情。

3. 一个`5V、2.0A`的稳定输出电源

   电源对于一切电子产品都是至关重要的，电源的稳定与否，直接影响电子产品的体验，性能甚至寿命。

4. HDMI线

   看一下家里的显示器是否支持HDMI如果不支持，就需要HDMI转VGA线，最好选用有源的。

5. 一套键鼠

   树莓派支持鼠标键盘的热插拔，亲测不能用鼠标蓝牙直接连树莓派蓝牙。

6. 其他硬件

   个人电脑，路由器，显示器（电视机如果有接口也能使用），后面的看情况需求，读卡器，网线，树莓派彩虹壳，芯片纯铜散热片。

7. 软件

   - SDFormatter.exe
   - Win32DiskImager.exe
   - putty.exe
   - Windows 远程桌面连接

## Install Operating_System

在[树莓派官网](https://www.raspberrypi.org/)页面，选择`DOWNLOADS` 进入[系统下载](https://www.raspberrypi.org/downloads/raspbian/) 界面，这里可以看到一些介绍：

Raspbian is the Foundation's official supported Operating System.You can install it with [NOOBS](https://www.raspberrypi.org/downloads/noobs/) or download the image below and follow our [installation guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).

Raspbian comes pre-installed with plenty of software for education, programming and general use. It has Python, Scratch, Sonic Pi, Java, Mathematica and more.

一般我们选择`RASPBIAN`，之后会有两个版本：

- RASPBIAN STRETCH WITH DESKTOP

  Image with desktop based on Debian Stretch

- RASPBIAN STRETCH LITE

  Minimal image based on Debian Stretch

这两个版本的区别，我也不清楚，也没有查到相关的资料，但根据英文解释来说，第一个支持图形桌面，是基于Debian系统的拓展。第二个是偏向与低配版本的。

这里我选择下载第一个，可以通过浏览器直接下载，也可以下载种子，通过迅雷或其他种子下载文件进行下载。

下载后的文件为：

```C
--|_> 2017-09-07-raspbian-stretch.zip
  --|_>2017-09-07-raspbian-stretch.img
```

将`.img` 解压到当前文件夹，以供后面使用。

接下来，开始写入系统：

1. 将SD卡用读卡器连接电脑，电脑识别SD卡后，打开工具`SDFormatter.exe`，按照提示将SD卡格式化。这一步我在windows系统中将SD卡格式化也能使用。格式化时要注意修改文件系统为FAT或FAT32。
2. 打开软件`Win32DiskImager.exe` ，按照步骤，先选刚才解压过的`2017-09-07-raspbian-stretch.img`，然后选对应的SD盘符，点击`write`，等进度完成，如果提示需要格式化SD卡，直接跳过即可。
3. 写完后将SD卡插入树莓派即可运行。
4. 装机后，树莓派系统的pi用户密码默认为`raspberry`，root权限密码为`raspberry`。

## Initial Settings

注意，需要先将HDMI线连接显示器，打开显示器，再启动树莓派。键盘鼠标可上电后再插入USB接口。

### 进入系统

树莓派默认是支持1920*1080分辨率的，树莓派上电后，屏幕上就能显示出开机界面了。在左上角有几个🍓一样的东西，然后下面一行行代码逐次出现。

首次进入，需要输入用户pi及密码raspberry，之后会在显示屏上显示出图形界面。第一个映入眼里的桌面应该是一条通往远方的公路。

_果断鼠标右键_ -->_Desktop Preferences_ ，调出 _Appearance Settings_ ， 在 _Picture_ 中选出`raspberr-pi-logo.png` ，修改成经典的可爱的树莓派。

你若喜欢，Follow Your Information！

最重要的一件事，右上角，点击`wifi` 图标，连接对应wifi名称，输入密码，连接wifi。这里需要注意，系统对中文名的wifi显示不出中文（可以将系统本地语言更改为中文，后面设置中涉及到），只能显示对应的数字编码（不知道什么编码规则）。

### 远程连接

刚才开wifi干嘛，远程连接啊！这里提供两种同一局域网内，用个人电脑登录`raspberry pi`。

#### 进入终端，命令行操作

1. 通过本地路由器查看树莓派内网IP地址，也可在树莓派终端（`ctrl+alt+t` 打开）输入

   ```bash
   sudo ifconfig -a
   ```

   在输出的信息中找到树莓派连接的IP地址，假设为`192.168.31.231`。

2. 终端输入

   ```bash
   sudo raspi-config
   ```

   进入树莓派配置工具界面，选择_Interfacing Options_ --> _SSH_  后开启SSH。

3. PC端下载Putty软件，双击运行后，将树莓派IP地址输入在`Host Name (or IP address)`输入框中，`Port` 默认为**22** 。点击右下角`Open` 进入终端操作窗口。

4. 输入默认用户名`pi`，对应密码`raspberry`即可。

#### GUI操作界面

1. 终端输入

   ```bash
   sudo apt-get install xrdp
   ```

   询问时输入默认Y。

2. 在PC上可以借助远程桌面连接，可在程序附件中找到，或者`Win+r`，在运行中输入

   ```cmd
   mstsc.exe
   ```

   回车即可，在打开的窗口中，输入树莓派IP地址如192.168.31.231，点击连接。

3. 在弹出的窗口中，`Module`选sesman-Xvnc，`username`为pi，`password`为raspberry，点击ok即可。

此图形操作界面，能够完美适配FHD屏幕，但是由于是局域网内连接，受到数据传输速率的影响，整体图形界面会显得非常卡顿，但是不耽误系统的正常使用，如果有条件，建议树莓派直接连接显示器操作。

某宝上也有使用微雪的3.5 inch 到7.0 inch 尺寸不等的 LCD 带触控显示屏出售。但分辨率普遍不高，而且触屏操作十分笨拙，除任性外不建议购买。

### 一些配置

#### 配置界面

树莓派有自己的配置工具，基于终端显示的配置界面。终端输入：

```bash
sudo raspi-config 
```

就回弹出如下所示画面：

```bash
┌─────────┤ Raspberry Pi Software Configuration Tool (raspi-config) ├──────────┐
│                                                                              │
│    1 Change User Password           Change password for the current u        │
│    2 Hostname                       Set the visible name for this Pi         │
│    3 Boot Options                   Configure options for start-up           │
│    4 Localisation Options           Set up language and regional sett        │
│    5 Interfacing Options            Configure connections to peripher        │
│    6 Overclock                      Configure overclocking for your P        │
│    7 Advanced Options               Configure advanced settings              │
│    8 Update                         Update this tool to the latest ve        │
│    9 About raspi-config             Information about this configurat        │
│                                                                              │
│                                                                              │
│                                                                              │
│                     <Select>                     <Finish>                    │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

这里的设置内容够我说一辈子的，这里只介绍几个用得到的。

1. Change User Password

   修改当前用户的密码

2. Hostname

   为你的 Pi 设置一个可用的名字

3. Boot Options

   这里选择一些启动的方式：包括命令行的加载，图形界面的加载，自动以 `pi` 用户登录，等候知道有可用网络启动，以及启动界面加载。

4. Localisation Options

   - Change Locale 

     用来设置语言及本地初始化设置，选中回车，在 `Configuring locales` 窗口中，找到 zh_CN.UTF-8 UTF-8，通过空格选中，确认后再次选择 zh_CN.UTF-8，然后重启树莓派，即可完成 `raspberry pi` 中文环境配置。

     但还是建议使用英文环境。重启可以在终端中使用命令行：

     ```bash
     sudo shutdown now
     ```

   - Change Timezone

     这里配置时区，官方系统开机默认是伦敦所在的东一区，国内为东八区，回车确认后，在先在 `Geographic area` 选择亚洲 `Asia` 之后在 `Timezone` 中选择 `Shanghai` ，真有意思，我也不知道为啥会是上海，可是上面大陆地区只有上海，国内还有台北可以选。

   - Change Wi-Fi Country 

     Set the legal channels used in your country. 这个配置我没看懂啥意思，不过我还是选了 `CN China` 。

     后来仔细想一想，可能是在这里配置了 WiFi 的名字可以以中文显示。。。

5. Interfacing Options

   这里可以配置一些外设的开启或关闭，如 Camera，SSH（之前我们开启命令行远程连接用到过），VNC（远程桌面操作连接），SPI，I2C，Serial，1-Wire，Remote GPIO等。

   这些接口无疑就是树莓派强大功能的基础，有些接口想必大家都不陌生，但是有一些还没有接触到，后续笔者会使用I2C和SPI分别驱动128*64的OLED小屏幕，敬请期待。

6. Overclock

   好吧，这里真是坑，本来想用这里来配置树莓派超频，来疯狂一把，但是回车后一直提示 `This pi cannot be overclocked ` ，至于为什么，还没有找到合理的解释。

   在知道树莓派能超频之后，我通过其他方法查询了本机，才发现本机已经超频到了1200Mhz，难怪 _小核桃_ 的树莓派网页看视频很卡，而我的关掉弹幕， `cpu` 使用情况也就六七十，想要了解关于 overclock的事情，请点击这里。、

7. Advanced Options

   Configure advanced settings，这里预留了一些高级配置。

   - Expand Filesystem

     树莓派默认不适用SD卡的全部空间，有一部分保留，所以可以选中将根分区扩展到整张SD卡。

   - Overscan

     可以扩充或缩小屏幕，之前老版本的树莓派可能不能自适应，但是现在都能自适应。

   - Memory Split

     可以选择给GPU分配多少内存，默认是 64M 。

   - Audio

     这里配置树莓派的音频输出，通过3.5mm Jack 还是通过HDMI，当然有三种选项，Auto，Force 3.5mm和Force HDMI。

     这里提一下，如果使用HDMI转接VGA的转接线，而且是有源带音频接口的，如果选择Auto项，就需要使用转接头上的3.5mm Jack。

   - Resolution

     Set a specific screen resolution 用于配置连接显示的规格， 比如：DMT Mode 82 1920*1080 60Hz 16：9 等。

   - GL Driver 

     这个没看懂是啥，不说了不说了，如果想知道是啥的话，可以试一试，要大胆的尝试。

8. Update 

   这里把 raspi-config 这个工具自动升级到最新版本。

9. About raspi-config

   This tool provides a straight-forward way of doing initial configuration of the Raspberry Pi. Although it can be run at any time, some of the options may have difficulties if you have heavily customised your installation.

诶呀，说好了只介绍几个用的到的，结果没忍住，还是基本都行都覆盖了。当然，第一次配置这个，当然要什么都试一遍啊，要不然怎么能出现系统崩溃的状况呢。

## Raspberry Pi正常使用

以上内容介绍的基本配置，当我们首次拿到树莓派，我们需要进行这些配置，或者说我们需要了解这些配置，因为在以后的操作中会很经常的与这些基本配置打交道，几乎每次Raspberry Pi的使用都会与这些戚戚相关。

那么问题来了，当我们第二次打开树莓派的时候，能做些什么呢？看到可爱的树莓浮现在桌面上的时候，在思考些什么呢?

接下来与树莓派一起的成长过程中，会遇到形形色色的趣事，本篇README也接近尾声，我会在这里留下以后每次捣鼓树莓派的主题，从这里开始，记录每一次跟树莓派的血战肉搏。





