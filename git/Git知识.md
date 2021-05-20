## Git 和代码托管中心

局域网环境下：gitlab服务器

外网环境下：GitHub、码云



## Git命令

### 本地初始化操作

命令：git init

效果：![](F:\python\tools\git\Git初始化.png)

注意：.git目录中存放的是本地库相关的子目录和文件，不要删除，也不要胡乱修改。

### 设置签名

- 形式：用户名+email地址

- 作用：区分不同开发人员的身份

- 辨析：这里设置的签名和登录远程库（代码托管中心）的账户、密码没有任何关系

- 命令：

  - 项目级别/仓库级别：仅在当前本地库范围内有效

    - git config user.name xzlmark

    - git config user.email xzlmark@126.com

      ![](F:\python\tools\git\git项目级别用户设置及查看.png)

      系统级别签名设置查看：签名信息保存在.git目录下面的config文件中

  - 系统用户级别：登录当前操作系统的用户范围

    - git config **--global** user.name xzlmark

    - git config **--global** user.email xzlmark@126.com

      ![](F:\python\tools\git\git系统级别用户设置及查看.png)

      系统级别签名设置查看：签名信息保存在家目录下面的.gitconfig文件中

  - 级别优先级：

    - 就近原则：项目级别优先于系统用户级别，二则都有时采用项目级别的签名
    - 如果只有系统级别的签名，就以系统级别为准
    - 二则都没有，是不允许的

### 常用命令

- 查看状态：git status  查看工作区、缓存区状态
- 添加：git add -A/[file name]将工作区的“新建/修改”文件增加到缓存区
- 提交：git commit -m "message" [file name] 将缓存区内容提交到本地库中
- git push  将本地库推送到远程库，进行合并操作

- 查看历史记录
  - git log 查看历史信息，最完整形式。
  - git log --pretty=oneline 简洁形式显示。
  - git log --oneline 更简洁的形式。
  - git reflog 移动到当前版本需要的**步数**

- 前进后退

  - 本质

    