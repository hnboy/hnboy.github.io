# 炉石传说


<!--more-->
# 炉石传说修改整理帧率方法：

- Windows系统：
    直接在C:\Users\用户名\AppData\Local\Blizzard\Hearthstone 文件夹中的options.txt文档中分别添加就这两行命令就可以了：(AppData文件夹默认隐藏，如果没显示，请先百度“显示隐藏文件”，操作也比较简单)
    `targetframerate=144 vsync=0`
    保存、重启炉石，第一次用可以用N卡自带的GeForce Experience、Fraps等软件自己看看帧数。
- MacOS系统：
    桌面最上面找到“前往”-“前往文件夹”，输入“~/资源库”(或者输入英文“~/library”)，点击前往(这个文件夹默认是隐藏的，所以一般方法进不去的)
    然后进入Preferences/Blizzard/Hearthstone，应该就可以看见options.txt了，编辑添加代码：
    `targetframerate=144 vsync=0`
