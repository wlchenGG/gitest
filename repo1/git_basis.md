## git repo 文件夹结构

在 git repo 文件夹下，命令行执行 `git init` 初始化后，会生成一个 .git 文件夹，里面包含以下内容：

- .git/HEAD：指向当前分支
- .git/config：配置文件
- .git/description：描述文件
- .git/index：索引文件
- .git/hooks/：钩子脚本
- .git/info/：包含全局忽略文件
- .git/objects/：存储对象（commit、tree、blob）
- .git/refs/：存储引用（branch、tag）
- .git/logs/：存储提交日志

一般来说，`.git` 文件夹自动隐藏了，Power Shell 可以通过 `ls -Hidden` 命令查看。


## git 基本命令

- `git init`：初始化 git 仓库

- `git add <file>...`：添加文件到暂存区
- `git add .` 或 `git add -A`：添加所有文件到暂存区
- `git status`：查看当前 git 状态

- `git diff`：查看暂存区与工作区的差异
- `git diff --cached`：查看暂存区与本地仓库的差异
- `git diff HEAD`：查看工作区与本地仓库的差异
- `git diff <commit>`：查看工作区与指定 commit 的差异
- `git diff <commit> <commit>`：查看两个 commit 之间的差异
- `git diff <branch>`：查看工作区与指定 branch 的差异
- `git diff <branch> <branch>`：查看两个 branch 之间的差异
- `git diff <commit> <branch>`：查看 commit 与 branch 之间的差异
- `git diff <commit> <commit> <branch>`：查看两个 commit 与 branch 之间的差异
- `git diff <commit> <commit> <commit>`：查看三个 commit 之间的差异

- `git rm <file>`：删除文件
- `git mv <file> <file>`：移动文件
- `git rm --cached <file>`：删除暂存区的文件
- `git mv --cached <file> <file>`：移动暂存区的文件

- `git reset`：重置暂存区
- `git reset --hard`：重置暂存区和工作区
- `git reset --soft`：重置暂存区，保留工作区
- `git reset --mixed`：重置暂存区和工作区，保留 commit
- `git reset --hard <commit>`：重置暂存区和工作区到指定 commit
- `git reset --soft <commit>`：重置暂存区到指定 commit，保留工作区
- `git reset --mixed <commit>`：重置暂存区和工作区到指定 commit，保留 commit
- `git reset --hard HEAD~1`：重置暂存区和工作区到上一个 commit
- `git reset --hard HEAD^^`：重置暂存区和工作区到上两个 commit
- `git reset --hard HEAD~n`：重置暂存区和工作区到上 n 个 commit

- `git commit -m "commit message"`：提交暂存区的文件到本地仓库
- `git commit`：提交暂存区的文件到本地仓库
- `git commit --amend`：修改最近一次提交的 commit message

- `git log`：查看提交日志，展示每次提交的 commit id、commit message、commit author、commit date
- `git log --oneline`：查看提交日志（简洁），展示每次提交的 commit id 和 commit message
- `git log --graph`：查看提交日志（图形化），展示提交树
- `git log --stat`：查看提交日志（统计），展示每次提交的修改文件和修改数
- `git log --pretty=format:"%h - %an, %ar : %s"`：查看提交日志（自定义格式），展示每次提交的 commit id、commit author、commit date 和 commit message
- `git log --pretty=format:"%h - %an, %ar : %s" --graph`：查看提交日志（自定义格式+图形化），展示每次提交的 commit id、commit author、commit date 和 commit message
- `git log <branch>`：查看指定分支的提交日志

- `git merge <branch>`：合并指定 branch 到当前 branch
- `git merge --no-ff <branch>`：合并指定 branch 到当前 branch，不使用 fast-forward
- `git merge --squash <branch>`：合并指定 branch 到当前 branch，将所有 commit 合并为一个 commit
- `git merge --no-commit <branch>`：合并指定 branch 到当前 branch，不自动提交
- `git merge --abort`：取消合并，回到合并前的状态
- `git merge --continue`：继续合并，解决冲突后继续合并，解决冲突后需要手动提交
- `git merge --ff-only <branch>`：合并指定 branch 到当前 branch，只使用 fast-forward
- `git merge --no-ff --no-commit <branch>`：合并指定 branch 到当前 branch，不使用 fast-forward，不自动提交
- `git merge --no-ff --squash <branch>`：合并指定 branch 到当前 branch，不使用 fast-forward，将所有 commit 合并为一个 commit
- `git merge --no-ff --no-commit --squash <branch>`：合并指定 branch 到当前 branch，不使用 fast-forward，不自动提交，将所有 commit 合并为一个 commit

- `git rebase <branch>`：将当前 branch 的提交应用到指定 branch 上，保留指定 branch 的提交
- `git rebase --onto <branch> <branch>`：将当前 branch 的提交应用到指定 branch 上，忽略指定 branch 的提交
- `git rebase --interactive <branch>`：交互式 rebase，可以修改、删除、合并提交

- `git branch`：查看当前分支
- `git branch <branch>`：创建分支
- `git branch -d <branch>`：删除分支
- `git branch -D <branch>`：强制删除分支
- `git branch -m <branch>`：重命名分支
- `git branch -M <branch>`：强制重命名分支
- `git branch -r`：查看远程分支
- `git branch -a`：查看所有分支
- `git branch -vv`：查看本地分支与远程分支的关联
- `git branch -u <remote>/<branch>`：设置本地分支与远程分支的关联
- `git branch -d -r <remote>/<branch>`：删除远程分支
- `git branch -D -r <remote>/<branch>`：强制删除远程分支

- `git checkout <branch>`：切换分支
- `git checkout -b <branch>`：创建并切换分支
- `git checkout -B <branch>`：强制创建并切换分支
- `git checkout <commit>`：切换到指定 commit，即将 HEAD 指向这个commit。会提示 `detached HEAD` 警告，因为此时 HEAD 不再指向任何分支，而是指向一个具体的 commit。此时**可以进行任意修改，但不会影响其他分支**。如果需要创建一个新的分支来保存这些修改，可以使用 `git switch -c <new-branch-name>` 命令。
- `git checkout <file>`：恢复工作区文件到指定 commit
- `git checkout -- <file>`：恢复指定工作区文件到暂存区。用来放弃掉所有还没有加入到缓存区（就是 git add 命令）的修改，但是此命令不会删除掉刚新建的文件。因为刚新建的文件还没已有加入到 git 的管理系统中。所以对于git是未知的。手动删除即可。
- `git checkout -- .`：恢复工作区所有文件到暂存区。
- `git checkout -p <branch>`：比较当前分支与指定分支的差异
- `git checkout -p <commit>`：比较当前分支与指定 commit 的差异
- `git checkout -p <file>`：比较当前分支与指定文件的差异
