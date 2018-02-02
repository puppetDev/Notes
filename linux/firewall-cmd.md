```bash
# 1.查询端口开放情况,若显示no则表示该端口关闭
firewall-cmd --zone=public --query-port=80/tcp

# 开启端口，–permanent参数表明该规则永久生效，否则，重启后则失效
firewall-cmd --zone=public --add-port=80/tcp --permanent

# 删除端口授权
firewall-cmd --zone= public --remove-port=80/tcp --permanent

# 重新加载Firewalld使修改生效（重要！）
firewall-cmd --reload

# 查看开放的端口
firewall-cmd --zone=public --list-ports
```
