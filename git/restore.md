# `git restore`

## Introduce

- 将HEAD恢复为指定状态

## Usage

## Option

- -s|--source=<tree>: 指定一个commit、branch或tag. 语法"commit_a...commit_c"可以回滚从commit_a到commit_c的提交
- -W|--worktree: 恢复work tree. 未指定option时的默认行为
- -S|--staged: 恢复index. 将指定文件移出index
- -m|--merge: 如果HEAD为merge后的结果, 使用此option将指定文件恢复为merge前的结果. 恢复后可使用`--ours|--theirs`处理冲突
- --ours: 被合并分支(本地分支)
- --theirs: 合并分支(远程分支或其他分支)