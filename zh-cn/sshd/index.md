# sshd配置


<!--more-->

## 生成key
```bash
MacBook-Pro:~ hnboy$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/hnboy/.ssh/id_rsa): /Users/hnboy/.ssh/test_rsa          #询问保存路径，如果默认，则在当前用户的 ~/.ssh 目录下生成id_rsa文件。这里我们自定义一个key，取名：test_rsa
Enter passphrase (empty for no passphrase):                                #如果你想用密码来保护你的证书，可以选择在这里输入。
Enter same passphrase again:                                      #如果输入了密码，需要再次输入该密码
Your identification has been saved in /Users/hnboy/.ssh/test_rsa.
Your public key has been saved in /Users/hnboy/.ssh/test_rsa.pub.
The key fingerprint is:
SHA256:V4RNi8fLUgeiCRMY6UJU8YR73SQ//JTgdSMBjyBJKws hnboy@MacBook-Pro.local
The key's randomart image is:
+---[RSA 2048]----+
| ...+BBo. o==.   |
|  . +o.=.++B+oo  |
| .E...o.oBooB+.. |
|  ..oo. . *=oo   |
|   ...  S o+o    |
|         . ..    |
|                 |
|                 |
|                 |
+----[SHA256]-----+
```

完成操作就生成一对key，再home/.ssh/路径下

## 将公钥安装到远程服务器上

- 使用scp或者rsync方法
```bash
rsync -av ~/.ssh/test_rsa.pub username@remote:~/.ssh/authorized_keys
scp ~/.ssh/test_rsa.pub username@remote:~/.ssh/authorized_keys
```

- 使用ssh-copy-id
```bash
ssh-copy-id -i ~/.ssh/test_rsa.pub username@remote
```

