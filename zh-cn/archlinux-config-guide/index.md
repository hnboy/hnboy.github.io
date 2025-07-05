# Arch Linux 高效配置：优化 pacman 与 Docker 环境


Arch Linux 以其灵活性、简洁性和强大的社区支持而闻名。
要充分利用 Arch，精通其包管理器 `pacman` 和配置现代开发工具（如 Docker）至关重要。
本文将指导您完成对 `pacman.conf` 的关键优化和 Docker 的基础设置，让您的系统更高效、更顺手。

### 一、优化 `pacman.conf`

`pacman` 的主配置文件位于 `/etc/pacman.conf`。通过一些简单的调整，您可以显著提升其性能和功能。

#### 1. 启用彩色输出

同时可以修改cache，以此减少/var/lib占用
彩色的 `pacman` 输出更具可读性。编辑 `/etc/pacman.conf`，找到 `[options]` 部分，并取消注释 `Color` 这一行。

```ini
# /etc/pacman.conf

[options]
#...
Color
#...
```

#### 2. 开启并行下载

如果您有较快的网络，并行下载可以大幅缩短更新和安装软件包的时间。在 `[options]` 部分，取消注释并设置 `ParallelDownloads` 的值。通常，5 到 10 是一个不错的选择。

```ini
# /etc/pacman.conf

[options]
#...
Color
ParallelDownloads = 5
#...
```

#### 3. 启用 `multilib` 仓库

`multilib` 仓库包含了 32 位的软件包，这对于运行 Steam、Wine 等应用至关重要。在配置文件中，找到并取消注释 `[multilib]` 部分。

```ini
# /etc/pacman.conf

#...
[multilib]
Include = /etc/pacman.d/mirrorlist
```

取消注释后，请务必运行 `sudo pacman -Syu` 来同步仓库并更新系统。

#### 4. 添加 Arch Linux 中文社区仓库 (archlinuxcn)

Arch Linux 中文社区仓库提供了许多官方仓库中没有的常用软件，例如 `yay`、`google-chrome` 等。

首先，在 `/etc/pacman.conf` 文件末尾添加以下内容：

```ini
# /etc/pacman.conf

#...
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```

然后，您需要导入 GPG 密钥以信任该仓库的软件包：

```bash
sudo pacman -S archlinuxcn-keyring
```

最后，刷新软件包数据库：`sudo pacman -Syu`。

### 二、配置 Docker 环境

Docker 是现代开发和部署的基石。在 Arch Linux 上安装后，一些额外配置能让使用体验更佳。

#### 1. 无需 `sudo` 运行 Docker

默认情况下，操作 Docker 需要 `sudo` 权限。为了方便日常使用，您可以将自己的用户添加到 `docker` 用户组���

首先，创建 `docker` 用户组（如果它不存在）：

```bash
sudo groupadd docker
```

然后，将您的用户添加进去（将 `your-user` 替换为您的用户名）：

```bash
sudo usermod -aG docker $USER
```

**重要提示**：为了使此更改生效，您需要**注销并重新登录**系统。

#### 2. 配置国内镜像加速

从 Docker Hub 拉取镜像时，国内用户可能会遇到速度慢的问题。配置镜像加速器可以解决这个问题。

创建或编辑 Docker 的配置文件 `/etc/docker/daemon.json`：

```bash
sudo mkdir -p /etc/docker
sudo nano /etc/docker/daemon.json
```

修改data-root默认路径
在文件中添加以下内容，这里以阿里云、网易和中科大的镜像为例。您可以选择一个或多个。

```json
{
  "data-root": "/var/location",
  "registry-mirrors": [
    "https://registry.docker-cn.com",
    "https://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn"
  ]
}
```

保存文件后，重启 Docker 服务以使配置生效：

```bash
sudo systemctl restart docker
```

现在，您可以通过 `docker info` 命令查看 `Registry Mirrors` 部分是否已成功配置。

### 总结

通过以上步骤，您不仅优化了 Arch Linux 的核心包管理系统 `pacman`，还配置了一个更适合国内网络环境和日常开发的 Docker 环境。
这些小调整将为您的 Arch 之旅带来极大的便利。

