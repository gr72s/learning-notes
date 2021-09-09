# `git stash`

## Introduce

- 在需要临时切换分支时, 保存当前分支的修改记录

## Usage

- push: 将保存的修改记录放入stash栈中保存, 默认只保存已add的文件
- save: 与push类似, 但不支持pathspec, 已弃用
- list: 列出stash栈中的信息
- show: 显示保存的差异
- pop: 从栈中自动移除一个记录并合并, 合并冲突时不移除记录
- apply: 与pop类型, 但是不移除记录
- branch <branchname> <stash>: 创建并checkout一个新分支, 新分支保留原分支的stash栈, 新分会应用并删除至指定的stash, 新分支操作不影响原分支
- clear: 删除stash栈. 慎用
- drop: 删除指定的stash, 默认删除栈顶
- create: 创建一个stash并返回记录, 该stash并未在refs/stash中存储(list中未列出)
- store: 存储指定的stash记录(通过create创建)

## Option

- -m|--message: 添加描述信息
- -k|--keep-index: 已add的文件仍然保留在修改记录中(git status)
- -q|--quiet: 安静模式, 不输出日志信息
- -u|--include-untracked: 添加未add的文件
- -a|--all: 添加全部文件, 包含已add、未add、隐藏和清除被忽略的文件