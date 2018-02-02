1.  安装 pip

pip是 python 的包管理工具。使用 python 版本的 shadowsocks，我们需要通过 pip 命令来安装。

```bash
$ curl"https://bootstrap.pypa.io/get-pip.py"-o"get-pip.py"$ python get-pip.py
```

2.  安装 shadowsocks

```bash
$ pip install --upgrade pip
$ pip install shadowsocks
```

3.  创建配置文件/etc/shadowsocks.json

```json
{
    "server":"0.0.0.0",
    "server_port":8888,
    "password":"12345678",
    "method":"aes-256-cfb"
}
```

| 参数 1          | 说明                           |
| ------------- | ---------------------------- |
| server        | 服务器IP地址                      |
| server_port   | SS服务指定端口                     |
| local_address | 本地服务地址，默认127.0.0.1           |
| local_port    | 本地服务端口，常用1080                |
| password      | SS服务密码，禁止使用默认密码mypassword    |
| timeout       | 服务超时，单位秒s                    |
| method        | 加密方式，默认aes-256-cfb           |
| fast_open     | TCP Fast Open ,true or false |

4.  配置systemctl服务

```bash
# 新建/usr/lib/systemd/system/shadowsocks.service 服务文件
vi usr/lib/systemd/system/shadowsocks.service

********************
    [Unit]

    Description=Shadowsocks

    [Service]

    TimeoutStartSec=0

    ExecStart=/usr/bin/ssserver -c /etc/shadowsocks.json

    [Install]

    WantedBy=multi-user.target
********************
# 加入自启动并启动该服务

systemctl enable shadowsocks
systemctl start shadowsocks
```

5.开放端口

```bash
firewall-cmd --zone=public --add-port=8888/tcp --permanent
firewall-cmd --reload
```
