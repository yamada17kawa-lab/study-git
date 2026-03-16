# 🛠️ Git 全能实战速查手册

## 一、 基础配置 (Config)
> 第一次安装 Git 后，必须配置身份标识，否则无法提交。

* **配置用户信息**：
    * `git config --global user.name "你的用户名"`
    * `git config --global user.email "你的邮箱"`
* **记住密码**（仅需输入一次）：
    * `git config --global credential.helper store`
* **查看所有配置**：
    * `git config --list`

---

## 二、 创建与获取仓库 (Create)
* **本地初始化**：
    * `git init` (在当前文件夹创建仓库)
    * `git init <文件夹名>` (新建文件夹并初始化为仓库)
* **克隆远程仓库**：
    * `git clone <仓库HTTPS地址>`
    * `git clone <仓库SSH地址>` (需先配置 SSH Key)
* **生成 SSH 密钥**：
    * `ssh-keygen -t ed25519 -C "你的备注"`

---

## 三、 工作区域逻辑 (Workflow)
Git 的核心操作围绕三个区域展开：
1. **工作区 (Working Directory)**：你直接修改代码的地方。
2. **暂存区 (Staging Area)**：准备提交的临时区域。
3. **本地仓库 (Local Repository)**：存放已提交的历史版本。

**基本流动方向**：
`工作区` -- (git add) --> `暂存区` -- (git commit) --> `本地仓库`

---

## 四、 常用文件操作 (Add & Commit)
* **查看状态**：`git status` (查看哪些文件被修改或未追踪)
* **添加文件到暂存区**：
    * `git add .` (添加当前目录下所有修改)
    * `git add <文件名>` (添加指定文件)
* **提交到本地仓库**：
    * `git commit -m "提交说明"` (必须带备注)
    * `git commit -am "提交说明"` (直接跳过 add 提交已追踪过的修改)
* **查看暂存区文件**：`git ls-files`
* **临时储藏修改**：`git stash` (当你在写功能 A，突然要去修 Bug B 时使用)

---

## 五、 版本回退 (Reset)
> 撤销错了的代码？根据需求选择模式：

| 模式 | 工作区 (代码内容) | 暂存区 (add 记录) | 说明 |
| :--- | :--- | :--- | :--- |
| `--soft` | ✅ 保留 | ✅ 保留 | 只撤销 commit，代码还在暂存区 |
| `--mixed` | ✅ 保留 | ❌ 丢失 | **默认模式**，撤销 commit 和 add |
| `--hard` | ❌ **丢失** | ❌ **丢失** | **慎用！** 彻底回到过去，当前修改全没 |

---

## 六、 远程协作 (Remote)
* **关联远程仓库**：`git remote add <别名> <地址>`
* **查看远程连接**：`git remote -v`
* **首次推送并建立追踪**：`git push -u <别名> <本地分支>:<远程分支>`
* **拉取并合并**：`git pull <别名> <远程分支>:<本地分支>`

---

## 七、 分支管理 (Branch)
* **查看分支**：`git branch`
* **创建分支**：`git branch <分支名>`
* **切换分支**：
    * `git checkout <分支名>` 或 `git switch <分支名>`
    * `git checkout -b <分支名>` (创建并立即切换)
* **合并分支**：`git merge <被合并的分支名>`
* **删除分支**：
    * `git branch -d <分支名>` (安全删除)
    * `git branch -D <分支名>` (强制删除)
* **重命名分支**：`git branch -m <旧名> <新名>`

---

## 八、 工作区差异对比 (Diff)
* `git diff`：比较 **工作区** 与 **暂存区**
* `git diff --cached`：比较 **暂存区** 与 **本地仓库**
* `git diff HEAD`：比较 **工作区+暂存区** 与 **本地仓库**
* `git diff <分支A> <分支B>`：比较两个分支的差异

---

## 九、 删除文件 (Remove)
* **手动删除**：`rm <文件名>` (仅删除工作区，需手动 add)
* **彻底删除**：`git rm <文件名>` (同时从工作区和暂存区删除)
* **删除暂存区文件**：`git rm --cached <文件名>` 

---

## 十、 忽略文件 (.gitignore)
> 在仓库根目录创建 `.gitignore` 文件，规则如下：

* `*.log`：忽略所有后缀为 .log 的文件。
* `/temp`：忽略根目录下的 temp 文件夹。
* `!important.log`：虽然忽略 log，但这个文件除外。
* `**/build`：忽略任何层级下的 build 文件夹。