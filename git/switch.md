# `git switch`

## Introduce

- 可以根据HEAD或start-point切换或创建指定分支, work tree与index与指定分支有冲突时, 切换失败

## Usage

- switch [<options>] <branch>
- switch [<options>] --detach [<start-point>]
- switch [<options>] (-c|-C) <new-branch> [<start-point>]

## Option

- -d|--detach: 切换到指定commit
- -c|--create: 创建一个新分支, 默认为HEAD, 可以指定start-point
- -C|--force-create: 如果new-branch已经存在, 则将它重置为当前分支的HEAD或指定的start-point
- -f|--force|--discard-changes: 丢弃work tree及index中的修改后切换分支
- -t|--track: 为切换的分支添加远程分支