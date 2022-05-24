# `git stash`

## Introduce

- 在需要临时切换分支时, 保存当前分支的修改记录

## Usage

- git stash list: 查看 stash 栈
- git stash push [-u] [-m <msg>]: 将修改记录压入栈
- git stash pop: 栈顶记录删除并出栈
- git stash apply stash@{${N}}: 应用栈中的记录至当前分支

## Argument

- push: 将保存的修改记录放入 stash 栈中保存, 默认只保存已 add 的文件
- save: 与 push 类似, 但不支持 pathspec, 已弃用
- list: 列出 stash 栈中的信息
- show: 显示保存的差异
- pop: 从栈中自动移除一个记录并合并, 合并冲突时不移除记录
- apply: 与 pop 类型, 但是不移除记录
- branch <branchname> <stash>: 创建并 checkout 一个新分支, 新分支保留原分支的 stash 栈, 新分支会 apply 并删除至指定的 stash, 新分支操作不影响原分支
- clear: 删除 stash 栈. 慎用
- drop: 删除指定的 stash, 默认删除栈顶
- create: 创建一个 stash 并返回记录, 该 stash 并未在 refs/stash 中存储(list 中未列出)
- store: 存储指定的 stash 记录(通过 create 创建)

## Option

- -m|--message: 添加描述信息
- -k|--keep-index: 已 add 的文件仍然保留在修改记录中(git status)
- -q|--quiet: 安静模式, 不输出日志信息
- -u|--include-untracked: 添加未 add 的文件
- -a|--all: 添加全部文件, 包含已 add、未 add、隐藏和清除被忽略的文件
