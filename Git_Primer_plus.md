<a name="DdLZe"></a>
## 基本知识
**工作区->暂存区->版本库**

- **工作区在本地，独立于分支且仅有一个**
- **暂存区相当于中转站，保存本地的更改**
- **版本库是我们每次commit持久化的集合，可以看成是树状结构**
<a name="Sk1cK"></a>
## 常用命令
<a name="UEOyh"></a>
### 1.tmux常用命令

- **tmux**一般使用命令和快捷键进行操作，`cral + a`为快捷键前缀，需要在使用命令快捷键前先按一下。
- **从tmux中往外复制粘贴的方法**

先按住`shift`不放，用鼠标选中想复制的东西<br />松开`shift`，再按`ctrl+insert`复制<br />然后在电脑上按`cral + v`粘贴

- **在tmux内复制粘贴的方法**

先按下`cral + a`，松开后再按`[`，用鼠标选中需要复制的内容<br />内容会自动保存到`tmux`的`buffer`里<br />再按`cral + a`，松开后按`]`，会将`buffer`中的内容粘贴到光标处

---

<a name="FNyaU"></a>
### 2.Git常用命令

- **配置git仓库**

`git config --global user.name xxx`：设置全局用户名，信息记录在~/.gitconfig文件中<br />`git config --global user.email xxx@xxx.com`：设置全局邮箱地址，信息记录在~/.gitconfig文件中<br />`git init`：将当前目录文件**配置成git仓库**，信息记录在隐藏的.git文件夹中

---

`git add XX`：将XX文件**添加到暂存区**<br />`git status`：查看仓库状态<br />`git add.`：将所有待加入暂存区的文件**加入暂存区**<br />`git commit -m "给自己看的备注信息"`：将暂存区的内容**提交到当前分支，将暂存区持久化**

---

- **如何清除暂存区、对比本地工作区与暂存区不同**

`git restore --stage XX`：将XX文件从暂存区中清除，git仍然管理XX文件<br />`git rm --cached XX`：将文件从仓库索引目录中删掉，git不再管理XX文件，可以通过git add重新添加<br />`git diff XX`：查看**本地工作区**XX文件**相对于暂存区**修改了哪些内容

---

- **如何查看历史版本和回滚版本**

`git log`：查看从根节点到HEAD节点的所有版本，**树形结构从下向上看，按q退出**<br />`git reflog`：查看HEAD指针的移动历史（包括被回滚的版本），同样是树形结构。**可以找到所有HEAD走过的结点**<br />`git reset --hard HEAD^ 或 git reset --hard HEAD~`：将**工作区代码回滚**到上一个版本<br />`git reset --hard HEAD^^`：往上回滚两次，以此类推<br />`git reset --hard HEAD~100`：往上回滚100个版本<br />`git reset --hard 版本号`：回滚到某一特定版本<br />


---

- **删除工作区未add的内容**

`git checkout — XX 或 git restore XX`：将本地XX文件尚未加入暂存区的修改内容全部删除

---

- **关联本地与远程仓库以及上传到GitHub**

`git remote add origin git@git.acwing.com:xxx/XXX.git`：将本地仓库关联到远程GtiHub仓库XXX<br />`git push -u` (第一次需要-u，以后不需要了)：将当前分支推送到远程仓库<br />`git push origin branch_name`：将本地的**某个分支**推送到远程仓库<br />`git clone git@git.acwing.com:xxx/XXX.git`：将**远程GitHub仓库XXX下载**到当前目录下，所有节点都有，但删去了引用记录

---

- **创建查看管理分支**

`git checkout -b XXX`：创建并切换到**XXX**这个分支<br />`git branch XXX`：创建新分支**XXX**<br />`git branch`：查看所有分支和当前所处分支<br />`git checkout XXX`：**切换到XXX**这个分支<br />`git merge XXX`：将**分支XXX**合并到当前分支上<br />`git branch -d XXX`：删除**本地仓库的XXX**分支

---

- **多分支上传相关命令**

`git push --set-upstream origin branch_name`：设置本地的branch_name分支对应远程仓库的branch_name分支<br />`git push -d origin branch_name`：删除远程仓库的branch_name分支<br />`git pull`：将远程仓库的当前分支与本地仓库的当前分支合并<br />`git pull origin branch_name`：将远程仓库的branch_name分支与本地仓库的当前分支合并<br />`git branch --set-upstream-to=origin/branch_name1 branch_name2`：将远程的branch_name1分支与本地的branch_name2分支对应<br />`git checkout -t origin/branch_name` 将远程的branch_name分支拉取到本地<br />`git stash`：将工作区和暂存区中尚未提交的修改存入栈中<br />`git stash apply`：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素<br />`git stash drop`：删除栈顶存储的修改<br />`git stash pop`：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素<br />`git stash list`：查看栈中所有元素<br />

