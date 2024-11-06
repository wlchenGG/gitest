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
- `git add .`：添加所有文件到暂存区
- `git status`：查看当前 git 状态
- `git diff`：查看暂存区与工作区的差异
- `git diff --cached`：查看暂存区与本地仓库的差异
- `git diff HEAD`：查看工作区与本地仓库的差异
- `git diff <commit>`：查看工作区与指定 commit 的差异
- `git diff <commit> <commit>`：查看两个 commit 之间的差异
- `git diff <branch>`：查看工作区与指定 branch 的差异
- `git diff <branch> <branch>`：查看两个 branch 之间的差异
- `git diff <commit> <branch>`：查看 commit 与 branch 之间的差异
- `git rm <file>`：删除文件
- `git mv <file> <file>`：移动文件
- `git rm --cached <file>`：删除暂存区的文件
- `git mv --cached <file> <file>`：移动暂存区的文件
- `git reset`：重置暂存区
- `git commit -m "commit message"`：提交暂存区的文件到本地仓库
- `git commit`：提交暂存区的文件到本地仓库
