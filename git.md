配置git
	1、git config --global user.name 用户名
	2、git config --global user.email 用户邮箱
	3、git config --global credential.helper store
	4、git config --global --list


创建仓库
	1、git init\git init 文件夹名
	2、git clone <仓库url>
	
克隆文件
	1、git clone <仓库https>
	2、git clone <仓库ssh>   --ssh-keygen -t ed25519
	
关联本地仓库和远程仓库
	1、git remote add 仓库别名 仓库地址
	2、git push -u 仓库别名 仓库分支
	3、git remote -v
	4、git pull 仓库别名 本地分支:仓库分支
	
	
工作区域
	1、工作区 ----- 暂存区 ----- 本地仓库
	2、--git add--->
	3、				--git commit-->
	4、						   -git reset- 

添加和提交文件
	1、git status     查看工作区和暂存区文件状态
	2、git add .\git add 文件名   添加文件
	3、git commit -m "备注"    将添加到暂存区的文件提交到本地仓库
	4、git commit -am "备注"   同时将被追踪且已修改的文件存到暂存区和本地仓库
	4、git stash   将被追踪的文件临时存到一个堆栈
	5、git ls-files  默认查看暂存区的文件
	
回退本地仓库版本			工作区    暂存区
	1、git reset --soft   	  √			√
	2、git reset --hard		  X         X
	3、git reset --mixed	  √			X
	
	
分支
	1、git branch
	2、git branch 分支名
	3、git checkout 分支名\git switch 分支名
	4、git merge 被合并的分支名
	5、git branch -d 分支名\git branch -D 分支名
	6、git branch -m 旧分支名 新分支名
	
合并冲突
	不同分支修改了同一份文件，git不知道要哪份

	
工作区域的差异
	1、git diff   比较工作区和暂存区
	2、git diff HEAD   比较工作区 + 暂存区和本地仓库
	3、git diff --cached   比较暂存区和本地仓库
	4、git diff 分支名\分支h哈希id   分支名\分支h哈希id     互相比较分支



git删除文件
	1、rm 文件名   普通删除文件         只会删除工作区的文件
	2、git rm 文件名   git删除文件      删除工作区和暂存区的文件
	3、git rm --cached 文件名           只删除暂存区的文件
	
忽略文件
	编译有关的文件、日志文件、敏感文件
	1、*任意字符
	2、?单个字符
	3、[一堆字符]其中任一字符
	4、!不忽略该文件
	5、**中间文件
	
	