# `git switch`

## Introduce

- 可以根据 HEAD 或 start-point 切换或创建指定分支, work tree 与 index 与指定分支有冲突时, 切换失败

## Usage

- switch [<options>] <branch>
- switch [<options>] --detach [<start-point>]
- switch [<options>] (-c|-C) <new-branch> [<start-point>]

## Option

- -d|--detach: 切换到指定 commit
- -c|--create: 创建一个新分支, 默认为 HEAD, 可以指定 start-point
- -C|--force-create: 如果 new-branch 已经存在, 则将它重置为当前分支的 HEAD 或指定的 start-point
- -f|--force|--discard-changes: 丢弃 work tree 及 index 中的修改后切换分支
- -t|--track: 为切换的分支添加远程分支
