# pip安装包报错


<!--more-->

## Arch Linux Pip安装包的时候报错
报错信息如下
```c++
× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
    
    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.
    
    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
    
    See /usr/share/doc/python3.11/README.venv for more information.
```

解决方法:
1. 删除文件 /usr/lib/python3.x/EXTERNALLY-MANAGED 
2. 修改pip conf文件为如下 ~/.config/pip/pip.conf 
```shell
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
break-system-packages = true
[install]
trusted-host = https://pypi.tuna.tsinghua.edu.cn
```

