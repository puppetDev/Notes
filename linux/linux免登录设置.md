## 本机

```bash
# 首先要生成公钥
ssh-keygen -t rsa
# 拷贝公钥到服务器
scp .ssh/id_rsa.pub root@45.76.210.249:/root/
# 依次登录服务器
#粘贴key至keys文件
cat id_rsa.pub >> .ssh/authorized_keys
```
