# git 使用教程
### 命令
#### 1. 获得本地版本库
##### 1.1 在当前文件夹创建本地仓库
git init xxx
##### 1.2 在当前文件夹下新建{name}文件夹，并使用{name}文件夹作为本地仓库
git init –bare {name}
##### 1.3 会创建xxx目录，并且将共享版本库的复制到xxx目录下,并且后续提交时，从哪儿clone的就会提交到哪里.
git clone {xxx.git} （最重要的第一步）
eg: git clone https://github.com/zycloud68/learningJava.git
##### 1.4 查看工作区相对于暂缓区的状态
git status
##### 1.5 将文件的变化以及新增文件由工作区提交到暂存区
git add xxx
##### 提交单个文件 git add first.txt
##### 提交多个txt类型的文件 git add* .txt
##### 提交到某个目录下 git add /src/main/java/*
##### 注意: 未加add是红色,加上add是绿色
##### 1.6 将暂存区的内容change提交到本地仓库
git commit -m "提交信息"
##### 1.7 查看提交日志
git log
##### 1.8 将本地仓库的内容提交到远程共享版本库
git push
##### 1.9 拉取远程共享版本库的内容到本地仓库
git pull
##### 1.10 冲突处理
后提交代码的人需要处理冲突,冲突处理：先pull 如果发生冲突，需要重新执行提交流程（add commit push,如果未发生冲突会自动合并.
##### 1.11 版本回退（谨慎操作）
git reset –hard 版本号
##### 1.12 2.10撤销工作区的修改（千万谨慎操作）
git checkout 文件名
##### 1.13 撤销暂存区的修改（谨慎操作）
git rm --cache first.txt

### 分支
树状结构：在任意分支上都可以拉出新的分支，在这个节点，父分支和子分支的内容是一致的
##### 1.1 查看分支
git brach -a
##### 1.2 切换分支 
git checkout 分支名
##### 1.3 合并分支
分支a的内容要合并到分支b中,先切换到分支b,在b分支上执行git merge 分支a,在将b分支上更新的内容push到远程b分支上

