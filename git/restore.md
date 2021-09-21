# `git restore`

## Introduce

- 将 HEAD 恢复为指定状态

## Usage

- git restore <filename>: 恢复指定、未 add 的文件
- git restore -S <filename>: 恢复已 add 的文件
- git restore -s=<tree> <filename>: 恢复提交
- git restore -m <filename>: 恢复 merge 后的文件

## Option

- -s|--source=<tree>: 指定一个 commit、branch 或 tag. 语法"commit_a...commit_c"可以回滚从 commit_a 到 commit_c 的提交
- -W|--worktree: 恢复 work tree. 未指定 option 时的默认行为
- -S|--staged: 恢复 index. 将指定文件移出 index
- -m|--merge: 如果 HEAD 为 merge 后的结果, 使用此 option 将指定文件恢复为 merge 前的结果. 恢复后可使用`--ours|--theirs`处理冲突
- --ours: 被合并分支(本地分支)
- --theirs: 合并分支(远程分支或其他分支)
