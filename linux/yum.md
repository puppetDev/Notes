## 语法

yum(选项)(参数)

## 选项

```bash
-h：显示帮助信息；
-y：对所有的提问都回答“yes”；
-c：指定配置文件；
-q：安静模式；
-v：详细模式；
-d：设置调试等级（0-10）；
-e：设置错误等级（0-10）；
-R：设置yum处理一个命令的最大等待时间；
-C：完全从缓存中运行，而不去下载或者更新任何头文件。
```

## 参数

```bash
install：安装rpm软件包；
update：更新rpm软件包；
check-update：检查是否有可用的更新rpm软件包；
remove：删除指定的rpm软件包；
list：显示软件包的信息；
search：检查软件包的信息；
info：显示指定的rpm软件包的描述信息和概要信息；
clean：清理yum过期的缓存；
shell：进入yum的shell提示符；
resolvedep：显示rpm软件包的依赖关系；
localinstall：安装本地的rpm软件包；
localupdate：显示本地rpm软件包进行更新；
deplist：显示rpm软件包的所有依赖关系。
```

## 安装

```bash
yum install              #全部安装
yum install package     #安装指定的安装包package
yum groupinsall group   #安装程序组group
```

## 更新和升级

```bash
yum update               #全部更新
yum update package      #更新指定程序包package
yum check-update         #检查可更新的程序
yum upgrade package     #升级指定程序包package
yum groupupdate group   #升级程序组group
```

## 查找和显示

```bash
yum info package      #显示安装包信息package
yum list               #显示所有已经安装和可以安装的程序包
yum list package      #显示指定程序包安装情况package
yum groupinfo group   #显示程序组group信息yum search string 根据关键字string查找安装包
```

## 删除程序

```bash
yum remove | erase package   #删除程序包package
yum groupremove group             #删除程序组group
yum deplist package               #查看程序package依赖情况
```

## 清除缓存

```bash
yum clean packages       #清除缓存目录下的软件包
yum clean headers        #清除缓存目录下的 headers
yum clean oldheaders     #清除缓存目录下旧的 headers
```
