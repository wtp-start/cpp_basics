[参考网址]<https://www.liaoxuefeng.com/wiki>
#### 1、git和svn
1. svn为集中式的版本控制。依赖于中央服务器，所以是联网的。流程为先拉下来最新数据，干活，上传数据。
2. git为分布式的版本控制。不必联网，且跟踪的是修改而非文件。
	
#### 2、git的一些基本操作
1. 创建版本库-------------git init 
2. 查看状态---------------git status
3. 添加或删除到缓存区-----git add/rm <file> 
4. 提交-------------------git commmit -m "描述"
5. 查看不同---------------git diff <file>
6. 查看提交历史-----------git log --pretty=oneline
7. 回退版本---------------git reset -- hard 版本号
8. 查看命令历史-----------git reflog
9. 撤销修改---------------输入git status，根据撤销提示操作
10. 缓存区撤销------------输入git status，根据撤销提示操作

#### 3、远程仓库
1. 创建SSH Key -----------若用户目录下没有.ssh目录（有，看有没有id_rsa（私钥）和id_rsa_pub（公钥）,有就跳到下一步），没有的话，打开shell(windows下打开git bash)，创建SSH key:ssh-keygen -t rsa -C "youremail@example.com"  (换成自己的邮箱地址)。
2. 登录github，打开设置（Settings）,点进SSH key，在Add SSH Key，在key中复制id_rsa_pub中的内容，点击添加Add key。
3. 创建仓库（create repository）,输入仓库名，选择是否要readme.md，然后创建。
4. 根据出来的提示（如 git remote add origin git@github.com:michaelliao/learngit.git）将本地仓库和远程仓库关联。
5. git push -u origin master（第一次推送加-u，后面的不加）。
6. git pull 抓取最新提交
7. 克隆远程仓库：git clone git@github.com:michaelliao/gitskills.git（大致命令），也有https的（git://是使用ssh，https的速度较慢）。

#### 4、分支管理
1. head指向的是当前的分支。
2. 创建分支并指向它--------git switch -c 分支名
3. 合并分支----------------git merge 分支名
4. 删除分支----------------git branch -d 分支名
5. 切换分支----------------git switch 分支名
6. 普通合并模式------------git merge --no-ff -m "merge with no-ff" 分支名（合并后的历史有分支，可以看出合并过，不加--no-ff看不出）
7. master分支应该非常稳定，仅用来发布新版本。干活在分支上，分支是不稳定的。发布时将分支合并到master上。
8. bug分支-----------------
   1. git stash（将当前的工作现场“储藏起来”，等以后恢复现场后继续工作--即当前工作的分支还没提交，需要在另外分支干活改bug）
   2. git stash pop（恢复现场，同时将stash内容也删了）
   3.  git cherry-pick 提交号 （用于复制其他分支的提交到当前分支（即修改其他分支已修改但当前分支还存在的bug））
9. feature分支-------------如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除
10. 多人协作---------------
    1.  查看远程库信息，使用git remote -v；
    2.  本地新建的分支如果不推送到远程，对其他人就是不可见的；
    3.  从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交	；
    4.  在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
    5.  建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
    6.  从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

#### 5、标签管理
1. 打标签------------------git tag v1.0(标签名)
2. 查看所有标签------------git tag
3. 在以前的commit打标签----git tag 标签名 commit号
4. 查看标签信息------------git show 标签名
5. 删除标签----------------git tag -d 标签名
6. 推送标签到远程----------git push origin 标签名
7. 推送所有标签------------git push origin --tags
8. 删除远程标签------------
   1. 先：git tag -d 标签名
   2. 再：git push origin :refs/tags/标签名