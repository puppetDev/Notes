1.  新建文件

```bash
vi /etc/yum.repos.d/mongodb-org-3.4.repo
```

将下面内容拷入

    [mongodb-org-3.4]
    name=MongoDB Repository
    baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
    gpgcheck=1
    enabled=1
    gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc

2.  安装

```bash
sudo yum install -y mongodb-org
```

3.  编写配置  
    配置文件 /etc/mongod.conf

```bash
# 修改访问权限让外网访问。修改配置文件/etc/mongod.conf,注释其中的bindip:127.0.0.1。
vi /etc/mongod.conf
```

4.  添加管理员账号

```bash
➜  ~ mongo
MongoDB shell version v3.4.9
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.4.9
>
> use admin
> show collections
> db.createUser({
    user: "admin",
    pwd: "*****",
    roles: [{
        role: "userAdminAnyDatabase",
        db: "admin"
    }]
})

Successfully added user: {
    "user" : "admin",
    "roles" : [
        {
            "role" : "userAdminAnyDatabase",
            "db" : "admin"
        }
    ]
}
> show users
```
