# Daoshi_daoshi_Raspberry_pi

When u have a raspberry pi ,you should do something.

## Somestory

为什么要写这篇哦，我原本是没有打算的，直到我的树莓派系统被我彻底的玩坏掉。

预知后事如何，转到-->>`STORY.md`

## Something Used

使用本教程之前，你需要准备一些东西：

1. 树莓派 3代 B+

   这里使用的是三代B+版本，其他版本，自行尝试，一切后果概不负责。本人于2017年三月底购买的树莓派3代B+，约软妹币220，而现在九月份，某宝上的报价是178软妹币。

2. SD卡

   一般8G到16G到32G不等，但是一定得注意，需要一张高速读写的SD卡。这一点很关键，因为是用来当作系统盘的，如果买读写速度很次的次品卡，就会对系统运行时显得没有耐心，从而失去热情。

3. 一个5V、2.0A的稳定输出电源

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

这两个版本的区别，我也不清楚，也没有查到相关的资料，但根据英文解释来说，第一个支持图形桌面，是基于Debian系统的拓展。第二个则偏向与低配版本的。

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
3. 写完后将SD卡插入树莓派即可运行。、
4. 装机后，树莓派系统的pi用户密码默认为raspberry，root权限密码为raspberry

## Initial Settings

注意，需要先将HDMI线连接显示器，打开显示器，再启动树莓派。键盘鼠标可上电后再插入USB接口。

### 进入系统

树莓派默认是支持1920*1080分辨率的，树莓派上电后，屏幕上就能显示出开机界面了。在左上角有几个🍓一样的东西，然后下面一行行代码逐次出现。

首次进入，需要输入用户pi及密码raspberry，之后会在显示屏上显示出图形界面。第一个映入眼里的桌面应该是一条通往远方的公路。__果断鼠标右键，Desktop Preference__，修改成经典的可爱的树莓派。

最重要的一件事，右上角，点击`wifi` 图标，连接对应wifi名称，输入密码，连接wifi。这里需要注意，系统对中文名的wifi显示不出中文，只能显示对应的数字编码（不知道什么编码规则）。

### 远程连接

刚才开wifi干嘛，远程连接啊！这里提供两种同一局域网内，用个人电脑登录raspberry pi。

#### 进入终端，命令行操作

1. 通过本地路由器查看树莓派内网IP地址，也可在树莓派终端（`ctrl+alt+t` 打开）输入

   ```bash
   sudo ifconfig -a
   ```

   在输出的信息中找到树莓派连接的IP地址，假设为192.168.31.231。

2. 终端输入

   ```bash
   sudo raspi-config
   ```

   进入树莓派配置工具界面，选择…… 开启SSH。

3. PC端下载Putty软件，双击运行后，将树莓派IP地址输入在`Host Name (or IP address)`输入框中，`Port` 默认为**22** 。点击右下角`Open` 进入终端操作窗口。

4. 输入默认用户名pi，对应密码raspberry即可。

#### GUI操作界面

1. 终端输入

   ```bash
   sudo apt-get install xrdp
   ```

   询问时输入默认Y。

2. 在PC上可以借助远程桌面连接，在程序附件中找到，或者`Win+r`，在运行中输入

   ```cmd
   mstsc.exe
   ```

   回车即可，在打开的窗口中，输入树莓派IP地址如192.168.31.231，点击连接。

3. 在弹出的窗口中，Module选sesman-Xvnc，username为pi，password为raspberry，点击ok即可。

此图形操作界面，能够完美适配FHD屏幕，但是由于是局域网内连接，收到数据传输速率的影响，整体图形界面会显得非常卡顿，但是不耽误系统的正常使用，如果有条件，建议树莓派直接连接显示器操作。

### 一些配置















## 未完待续

