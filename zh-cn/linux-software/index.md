# Linux常用软件

<!--more-->
## shell
- fish 配合 <a href="https://github.com/oh-my-fish/oh-my-fish" target="_blank">oh-my-fish</a>
```shell
curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
```

## Terminal
- alacritty
    使用Rust编写，支持GPU加速
![image alacritty](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh5f4acbd1f53259b_h5a982290008951797aa65575cc3_WXIMAGE_140530b29fd04aee841bdeaadb3927ba.png)
```shell
yay -s alacritty
```

## 浏览器
- Firefox(默认安装)
- google-chrome

```shell
yay -s google-chrome
```

{{< admonition type=tips title="chrome设置" open=false >}}
![image chrome](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh5a3cb01f7aee465_h515bb258c520e4243086f75eef4_WXIMAGE_df1dd95825204890b2283e5c3ac82989.png)
可以如上图所示，创建~/.config/chrome-flags.conf，写入相关启动设置
{{</admonition>}}

## 办公软件
- wps
1. 安装wps以及相关字体
```shell
yay -s wps-office-cn ttf-wps-fonts
```

## 音乐
- qqmusic-bin
![image qqmusic](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh51b1245fc85b011_h5659498391de45acbe217396ce0_WXIMAGE_5e80368dcb804a05bb0b50fd2bad7a09.png)
- 网易云音乐
- spotify

## 密码管理
- Bitwarden
```
yay -s bitwarden
```

## 编辑器
- vscode
- vim
```shell
yay -s vscode vim
```

## 系统状态查看
- btop
![image btop](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh5845e640fd6d24e_h5ad7a39692a5a2f194d1196f56d_WXIMAGE_ace3f6664d60470ab35c1842e20aafd2.png)

## Rust软件
- bat (替代cat)
![image bat](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh5a095b33739e919_h52c6ef768c5b8b8e124838d59c1_WXIMAGE_ab7222e1feb9409ab97434cf3de3ca1c.png)
- exa (替代ls)
![image exa](https://yzf.qq.com/fsnb/kf-file/kf_pic/20220601/KFPIC_kfh5638f3bf7f68fc3_h59e0e8184f5533b2c7f20918abc_WXIMAGE_858eb5e366eb48c1ad7946d4259f2e96.png)

```shell
yay -s exa bat
```



