# systemctl

> systemctl是 Systemd 的主命令，用于管理系统。

```bash
# 重启系统
$ sudo systemctl reboot

# 关闭系统，切断电源
$ sudo systemctl poweroff

# CPU停止工作
$ sudo systemctl halt

# 暂停系统
$ sudo systemctl suspend

# 让系统进入冬眠状态
$ sudo systemctl hibernate

# 让系统进入交互式休眠状态
$ sudo systemctl hybrid-sleep

# 启动进入救援状态（单用户状态）
$ sudo systemctl rescue
```

# hostnamectl

> hostnamectl查看当前主机信息

```bash
# 显示当前主机的信息
$ hostnamectl
```

# timedatectl

> timedatectl查看当前时区
>
> ```bash
> # 查看当前时区设置
> $ timedatectl
> ```

# 显示所有可用的时区

$ timedatectl list-timezones                                                                                   

# 设置当前时区

$ sudo timedatectl set-timezone America/New_York
$ sudo timedatectl set-time YYYY-MM-DD
$ sudo timedatectl set-time HH:MM:SS

    # loginctl
    >loginctl命令用于查看当前登录的用户。
    ```bash

    # 列出当前session
    $ loginctl list-sessions

    # 列出当前登录用户
    $ loginctl list-users

    # 列出显示指定用户的信息
    $ loginctl show-user ruanyf

# Unit

> Systemd 可以管理所有系统资源。不同的资源统称为 Unit（单位）。
> Unit 一共分成12种。

| unit           | 注释                  |
| -------------- | ------------------- |
| Service unit   | 系统服务                |
| Target unit    | 多个 Unit 构成的一个组      |
| Device Unit    | 硬件设备                |
| Mount Unit     | 文件系统的挂载点            |
| Automount Unit | 自动挂载点               |
| Path Unit      | 文件或路径               |
| Scope Unit     | 不是由 Systemd 启动的外部进程 |
| Slice Unit     | 进程组                 |
| Snapshot Unit  | Systemd 快照，可以切回某个快照 |
| Socket Unit    | 进程间通信的 socket       |
| Swap Unit      | swap 文件             |
| Timer Unit     | 定时器                 |

## unit管理

```bash
# 列出正在运行的 Unit
$ systemctl list-units

# 列出所有Unit，包括没有找到配置文件的或者启动失败的
$ systemctl list-units --all

# 列出所有没有运行的 Unit
$ systemctl list-units --all --state=inactive

# 列出所有加载失败的 Unit
$ systemctl list-units --failed

# 列出所有正在运行的、类型为 service 的 Unit
$ systemctl list-units --type=service

# 显示系统状态
$ systemctl status

# 显示单个 Unit 的状态
$ sysystemctl status bluetooth.service

# 显示远程主机的某个 Unit 的状态
$ systemctl -H root@rhel7.example.com status httpd.service

# 显示某个 Unit 是否正在运行
$ systemctl is-active application.service

# 显示某个 Unit 是否处于启动失败状态
$ systemctl is-failed application.service

# 显示某个 Unit 服务是否建立了启动链接
$ systemctl is-enabled application.service
```

## 常用命令

```bash
# 立即启动一个服务
$ sudo systemctl start apache.service

# 立即停止一个服务
$ sudo systemctl stop apache.service

# 重启一个服务
$ sudo systemctl restart apache.service

# 杀死一个服务的所有子进程
$ sudo systemctl kill apache.service

# 重新加载一个服务的配置文件
$ sudo systemctl reload apache.service

# 重载所有修改过的配置文件
$ sudo systemctl daemon-reload

# 显示某个 Unit 的所有底层参数
$ systemctl show httpd.service

# 显示某个 Unit 的指定属性的值
$ systemctl show -p CPUShares httpd.service

# 设置某个 Unit 的指定属性
$ sudo systemctl set-property httpd.service CPUShares=500

# 开机自动激活单元：
$ systemctl enable apache.service
```

# Unit 配置

单元文件可以从两个地方加载，优先级从低到高分别是

-   /usr/lib/systemd/system/ ：软件包安装的单元
-   /etc/systemd/system/ ：系统管理员安装的单元
-   当 systemd 运行在用户模式下时，使用的加载路径是完全不同的。

## 配置Nginx服务

```bash
# 进入系统单元目录
$ cd /usr/lib/systemd/system/
# 创建 nginx.service
$ touch nginx.service
# 编辑 nginx.service文件
$ vi nginx.service

****
    [Unit]
    Description=nginx - high performance web server
    After=network.target
    [Service]
    Type=forking

    ExecStartPre=/usr/local/nginx/sbin/nginx -t -c /usr/local/nginx/conf/nginx.conf
    ExecStart=/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
    ExecReload=/usr/local/nginx/sbin/nginx -s reload
    ExecStop=/usr/local/nginx/sbin/nginx -s stop
    ExecQuit=/usr/local/nginx/sbin/nginx -s quit
    PrivateTmp=true
    [Install]
    WantedBy=multi-user.target
****
# 将上面的内容安装实际配置目录修改，保存。
# 重载所有修改过的配置文件
$ sudo systemctl daemon-reload
# 启动Nginx服务
$ sudo systemctl start nginx.service
```

* * *

# 附：

[Systemd (简体中文)](https://wiki.archlinux.org/index.php/systemd_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
