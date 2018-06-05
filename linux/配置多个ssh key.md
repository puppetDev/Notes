# 生成ssh key

```bash
~ ssh-keygen -t rsa -C "puppet_dev@hotmail.com"

Generating public/private rsa key pair.
# 输入要生成的文件名。
Enter file in which to save the key (/Users/puppet/.ssh/id_rsa):/Users/puppet/.ssh/github_rsa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/puppet/.ssh/github_rsa.
Your public key has been saved in /Users/puppet/.ssh/github_rsa.pub.
The key fingerprint is:
SHA256:BG+DyMCoO93freGz/EjD9IoSZFwA6R665JM1zYs43NU puppet_dev@hotmail.com
The key's randomart image is:
+---[RSA 2048]----+
| ooo...          |
|. oo ..+         |
|.. .o.. =        |
|. o +  o .       |
| = =o . S        |
|+.ooo+ E .       |
|+o= +o..=..      |
|.B o...=o=.      |
|  o  .. B=.      |
+----[SHA256]-----+
```

# 创建多个网站配置文件

```bash
vim ~/.ssh/config
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github_rsa

Host git.oschina.net
    HostName git.oschina.net
    User git
    IdentityFile ~/.ssh/oschina_rsa
```
