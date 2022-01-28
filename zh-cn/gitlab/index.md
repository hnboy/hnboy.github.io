# Gitlab


<!--more-->

## 安装前
- 关闭防火墙和SELINUX

```bash
##关闭防火墙
systemctl stop firewalled
##关闭SELINUX
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
```

{{< admonition type=tip title="tip" open=false >}}
也可以尝试让防火墙enable http/https
```bash
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
```
{{</admonition>}}


## 安装
```bash
sudo EXTERNAL_URL="ip" yum install -y gitlab-ee
```

## 修改配置文件
- 修改配置文件
```bash
##修改/ect/gitlab/gitlab.rb
external_url "https://gitlab.example.com"
```

## 启动
```bash
sudo gitlab-ctl reconfigure
sudo gitlab-ctl restart
```


