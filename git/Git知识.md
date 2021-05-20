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

  - 本质：改变HEAD的指向

    ![](F:\python\tools\git\git 退回.png)

  - 基于索引值操作前进后退版本[推荐使用这种方式]

    - git reset --hard 

      ![](F:\python\tools\git\git 退回历史.png)

- 删除文件并找回
  - 前提：删除前，文件存在时的状态提交到了本地库
  - 操作：git reset --hard [指针位置]
    - 删除操作已经提交到本地库：指针位置指向历史记录
    - 删除操作尚未提交到本地库：指针位置使用HEAD

- 比较文件差异
  - git diff [文件名]
    - 将工作区的文件和缓存区进行比较
  - git diff [本地库中历史版本][文件名]
    - 将工作区的文件和本地库历史记录比较
  - 不带文件名可以比较多个文件

### 分支管理

- 什么是分支：在版本控制过程中，使用多条线同时推进多个任务
- 分支的好处：同时并行推进多个功能开发，提高开发效率；各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响，失败的分支删除重新开始即可。

- 分支操作
  - 创建分支：git branch [分支名]
  - 查看分支：git branch -v
  - 切换分支：git checkout [分支名]
  - 合并分支：
    - 第一步：切换到接受修改的分支（被合并，增加新内容）上，git checkout [被合并分支名]
    - 第二步：执行merge命令。git merge[有新内容的分支名]
  - 解决冲突。
    - 第一步：编辑文件，删除特殊符号
    - 第二步：把文件修改到满意的程度，保存退出
    - 第三步：git add[文件名]
    - 第四步：git commit -m "日志信息"
      - 注意：此时commit一定不能带具体文件名



### ssh登录

- 进入当前用户的家目录 cd ~
- 删除.ssh目录 rm -rvf .ssh
- 运行命令生成.ssh密钥目录  ssh-keygen -t rsa -C xzlmark@126.com
- 进入ssh目录查看文件列表
  - cd .ssh
  - ls -lF
  - 查看id_rsa.pub 文件内容：cat id_rsa.pub
  - 复制id_rsa.pub文件内容，登录GitHub，点击用户头像-settings-ssh and gpg keys
  - new ssh key
  - 输入复制的密钥信息
  - 回到GitHub创建远程地址别名

![](F:\python\tools\git\ssh 设置用法.png)

git remote -v :查看远端地址

git remote add origin_ssh XXX.git 增加远端库的别名

git push origin_ssh master:推送到远端库



