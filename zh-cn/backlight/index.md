# light调节背光


<!--more-->
- 安装light调整背光
```shell
yay -S light
```
- light移出sudo权限
```shell
sudo chgrp video /sys/class/backlight/*/brightness
sudo chgrp video /sys/class/backlight/*/brightness
sudo usermod -a -G video $USER
```

