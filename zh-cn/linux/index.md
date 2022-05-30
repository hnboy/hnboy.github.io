# Linux使用


<!--more-->
## 使用何种文件系统
目前我安装使用的btrfs文件系统，特点如下：
### 优点
1. 快照，对于滚动发行版，如果更新过程中有意外发生，可以使用btrfs文件的快照恢复。当然也会带来一个新问题，这个快照特性无法区隔工作磁盘区和快照存储区，快照档案会占用工作空间。
2. 透明压缩，减少磁盘的使用空间
3. 动态扩容，不同块设备可以随时加入空间不足的分区中，不用费劲调整分区
### 缺点
1. 性能上从phoronix评测结果来看不如ext4. <a href="https://openbenchmarking.org/result/2108260-PTS-SSDS978300&sor" target="_blank">phoronix测评 </a>

## 软件源修改
- 可以使用ustc，tsinghua等国内的开源镜像，加速软件安装以及系统更新。
### 修改方式
1. 可以通过软件中心选择
2. 参考<a href="https://mirrors.ustc.edu.cn/help/manjaro.html" target="_blank">ustc源使用帮助</a>来进行修改。

## 安装yay
### 安装

```
sudo pacman -S yay
```

{{< admonition type=error title="注意" open=true >}}
不要修改yay为清华源，保持默认即可，清华已经移除的yay反代。
{{</admonition>}}

## 字体
### 基本字体
- Noto 
### 等宽字体
- Source Code Pro
### 其他
- WQY字体
```shell
yay -S wqy noto sourcecodepro
```
## 缩放
- 150% , 我使用的32寸2560x1440分辨率的屏幕，150%缩放看起来比较舒服


## SSDM 介绍
### 主题更换

## 中文输入法安装
- fcitx-clover
```shell
yay -s fcitx5-diagnoes fcitx-clover
```

## 杂项

### grub启动项目修改
```c++
//nowatchog可以修复部分电脑关机慢的问题
//i8042.dumbkdb 修复部分笔记本电脑键盘无法识别的问题
GRUB_CMDLINE_LINUX="nowatchdog i8042.dumbkdb"
```

### Enable Wayland
参考KDE enable wayland 


