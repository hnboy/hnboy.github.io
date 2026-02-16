# cmake

<!--more-->
## cmake 配合gdb使用
方法一：
```makefile
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_BUILD_TYPE RelWithDebInfo)
```
方法二：
```makefile
cmake -DCMAKE_BUILD_TYPE=Debug <path and other arguments>
```

## make install 删除
```shell
#make install 之后会在当前目录生城install_manifest.txt文件，里面记录了安装信息
xargs rm < install_manifest.txt
```


