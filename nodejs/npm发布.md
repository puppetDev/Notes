# 发布前

```bash
# 新建包文件夹
mkdir easy-toolkit
# 进入包文件
cd easy-toolkit
# 初始化配置
npm init
# 根据提示输入相关配置信息
```

# 注册npm

直接去[npm官网](https://www.npmjs.com/)注册，需激活邮箱

```bash
# login
npm login
# 查看当前用户
npm whoami
```

# 发布

```bash
# 发布
npm publish
```

# 更新发布

```bash
# 更新
npm version <update_type>
# 再次执行
npm publish
```

# 其他命令

```bash
# 撤销发布自己发布过的某个版本代码
npm unpublish ``package@version``
```

> npm社区版本号规则采用的是semver(语义化版本)，主要规则如下：
>
> 版本格式：主版号.次版号.修订号，版号递增规则如下：
>
> -   主版号：当你做了不相容的 API 修改，
> -   次版号：当你做了向下相容的功能性新增，
> -   修订号：当你做了向下相容的问题修正。
>     先行版号及版本编译资讯可以加到「主版号.次版号.修订号」的后面，作为延伸。
