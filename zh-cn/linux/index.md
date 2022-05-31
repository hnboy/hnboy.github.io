# Linux使用


<!--more-->

## 文件系统

目前我安装使用的btrfs文件系统，特点如下：

### 优点
1. 快照，对于滚动发行版，如果更新过程中有意外发生，可以使用btrfs文件的快照恢复。当然也会带来一个新问题，这个快照特性无法区隔工作磁盘区和快照存储区，快照档案会占用工作空间。
1. 透明压缩，减少磁盘的使用空间
1. 动态扩容，不同块设备可以随时加入空间不足的分区中，不用费劲调整分区

### 缺点
1. 性能上从phoronix评测结果来看不如ext4. <a href="https://openbenchmarking.org/result/2108260-PTS-SSDS978300&sor" target="_blank">phoronix测评 </a>

## 软件源修改
  可以使用ustc，tsinghua等国内的开源镜像，加速软件安装以及系统更新。

- 修改方式

1. 可以通过软件中心选择

2. 参考<a href="https://mirrors.ustc.edu.cn/help/manjaro.html" target="_blank">ustc源使用帮助</a>来进行修改。


## 安装yay

```
sudo pacman -S yay
```
{{< admonition type=error title="注意" open=true >}}
不要修改yay为清华源，保持默认即可，清华已经移除的yay反代。
{{</admonition>}}

## 字体
1. Noto(默认已经安装好) 
2. Source Code Pro（默认已经安装）


### 缩放
- 150% , 我使用的32寸2560x1440分辨率的屏幕，150%缩放看起来比较舒服

## 中文输入法安装

- fcitx5
```shell
yay -s fcitx5 fcitx5-configtool fcitx5-rime rime-cloverpinyin fcitx5-qt fcitx5-gtk fcitx5-material-color
```

### fcitx5 设置

- 安装好fcitx5后需要配置好相关的环境变量,可以在~/.config/environment.d/目录下创建按fcitx.conf配置文件，如果没有该目录请自行创建, 内容如下：

```shell
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

### 安装设置rime-clover
在 ~/.local/share/fcitx5/rime/ 路径下添加 default.custom.yaml 文件
内容如下
```shell
patch:
  menu/page_size: 8
  schema_list:
    - schema: clover
```
- 至此系统基本配置已经完成，如果不想一行一行敲，可以在terminal执行如下命令，一键完成如上设定
```shell
wget -O -  https://raw.githubusercontent.com/hnboy/script/master/linux/install/linux.sh | bash
```
## 杂项
- grub启动项目修改

```c++
//nowatchog可以修复部分电脑关机慢的问题
//i8042.dumbkdb 修复部分笔记本电脑键盘无法识别的问题
GRUB_CMDLINE_LINUX="nowatchdog i8042.dumbkdb"
```

### Enable Wayland
参考KDE enable wayland 


