# Libvirt

 Libvirt可以通过qemu和OVMF来支持UEFI虚拟机，先安装edk2-ovmf,然后添加如下内容
 /etc/libvirt/qemu.conf
 ```c
 // /etc/libvirt/qemu.conf
 nvram = [
     "/usr/share/ovmf/x64/OVMF_CODE.fd:/usr/share/ovmf/x64/OVMF_VARS.fd"
     ]
 ```
<!--more-->

