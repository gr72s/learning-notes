# `git status`

1. `-s`：输出排序
   - A：已添加
   - M：修改
   - ??：未添加

```bash
A  .idea/untitled2.iml
A  .idea/vcs.xml
AM index1.js
A  index2.js
?? index3.js
```

# `git commit`

1. `-C [commit id]`：复用已`commit`的`message`
2. `-c [commit id]`：复用并重新编辑已`commit`的`message`
3. `--author=[author]`
4. `--date=[date]`
5. `-m`：提交单行`message`
6. `--amend`：重新提交上次`commit`

# `git diff`

1. 修改后未被`git add .`的文件

# `git notes`

1. `add [commit id]`：为一个`commit`添加`notes`
2. `apend [commit id]`：为一个`commit`追加`notes`
3. `show [commit id]`
4. `remove [commit id]`

# `git restore`

撤销文件

# `git reset`

1. `[file]`：将文件移出暂存区
2. `--mixed [commit id]`：恢复至该`commit`，该`commit`之后的更改被保留，未`add`状态
3. `--soft [commit id]`：该`commit`之后的更改被移到暂存区，已`add`状态
4. `--hard [commit id]`：该`commit`之后的更改被移除
5. `--keep`：保留工作区与暂存区的修改，恢复为`HEAD`
6. `--merge`：保留工作区的修改，丢弃暂存区的修改，恢复为`HEAD`

# `git rm`

1. `--cached`：在暂存区中移除
2. `-f`：强制删除

# `git branch`

1. `-d`：删除分支
2. `-m`：重命名分支
3. `-c`：复制分支
4. `-r`：与`--list`为列出远程分支，与`-d`为删除远程分支
5. `merge [branch name]`：分支名

# `git checkout`

1. `-b [branch name]`：创建并切换分支
2. `-track [origin/name]`：`pull`本地没有的远程分支

# `git revert`

1. `[commit id]`：回滚指定的`commit`

# `git rebase`

```bash
p, pick: 使用提交
r, reword: 使用提交，但是修改message
e, edit: 使用提交，进入shell进行提交修补
s, squash: 使用提交，合并到前一个提交
f, fixup: 使用提交，但是丢弃message
x, exec: 运行shell
b, break: 执行到这里停止，使用--continue继续执行
d, drop: 删除提交
l, label: 打标记
t, reset: 充值HEAD到此标记
m, merge [-C|-c] <label> [#<online>]:创建合并提交
```

# `git cherry-pick`

1. `[commit id]`：合并指定的分支
2. `-n`：只更新工作区和暂存区，不产生新的提交
3. `-x`：在`message`中追加`cherry picked`的信息
4. `-s`：追加作者信息
5. `-m [parent number]`：如果原始提交是一个合并节点，则应该告诉`git`采用哪个分支的变动
   `git cherry-pick -m 1 <commitHash>`
   - `1`：代表接收变动的分支
   - `2`：代表变动来源的分支
6. `--about`：发生冲突时放弃合并，回到操作前的样子
7. `--continue`：将修改的文件重新放入暂存区后继续执行本命令
8. `--quit`：退出但是不回到操作前的样子

# `git format-patch`

1. `[commit id]`：生成`.patch`文件，不包含指定的`commit`

# 打补丁

1. `git format-patch commit-id`
2. `git apply --stat patchfile`
3. `git apply --check patchfile`
4. `git apply patchfile`
