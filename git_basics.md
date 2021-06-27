1、git和svn
	（1）svn为集中式的版本控制。依赖于中央服务器，所以是联网的。流程为先拉下来最新数据，干活，上传数据。
	（2）git为分布式的版本控制。不必联网，且跟踪的是修改而非文件。
	
2、git的一些基本操作
	（1）创建版本库-------------git init 
	（2）查看状态---------------git status
	（3）添加或删除到缓存区-----git add/rm <file> 
	（4）提交-------------------git commmit -m "描述"
	（5）查看不同---------------git diff <file>
	（6）查看提交历史-----------git log --pretty=oneline
	（7）回退版本---------------git reset -- hard 版本号
	（8）查看命令历史-----------git reflog
	（9）撤销修改---------------输入git status，根据撤销提示操作
	（10）缓存区撤销------------输入git status，根据撤销提示操作

3、远程仓库
	（1）创建SSH Key -----------若用户目录下没有.ssh目录（有，看有没有id_rsa（私钥）和id_rsa_pub（公钥）,有就跳到下一步），没有的话，打开shell(windows下打开git bash)，创建SSH key:
			ssh-keygen -t rsa -C "youremail@example.com"        (换成自己的邮箱地址)。
	（2）登录github，打开设置（Settings）,点进SSH key，在Add SSH Key，在key中复制id_rsa_pub中的内容，点击添加Add key。
	（3）创建仓库（create repository）,输入仓库名，选择是否要readme.md，然后创建。
	（4）根据出来的提示（如 git remote add origin git@github.com:michaelliao/learngit.git）将本地仓库和远程仓库关联。
	（5）git push -u origin master（第一次推送加-u，后面的不加）。
	（6）克隆远程仓库：git clone git@github.com:michaelliao/gitskills.git（大致命令），也有https的（git://是使用ssh，https的速度较慢）。

4、分支管理
	（1）head指向的是当前的分支。
	（2）创建分支并指向它--------git switch -c 分支名
	（3）合并分支----------------git merge 分支名
	（4）删除分支----------------git branch -d 分支名
	（5）切换分支----------------git switch 分支名