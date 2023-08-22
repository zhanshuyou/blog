_整理一些工作中使用频率很高的 git 命令_


**从 develop 分支创建 feature/test 分支并立即切换到该分支**
```
git checkout -b feature/test develop
```

**拉取远程 develop 的更新到本地 develop 分支**
```
git fetch origin develop:develop
```

**修改提交信息，同时也可以向上一次的提交中追加更改**
```
git commit --amend

git commit --amend --no-edit
```

**查看提交记录, 包括被 squash 合并掉的记录**
```
git reflog
```
**合并提交记录**
```
// 合并前 3 个提交
git rebase -i HEAD~3
```
**使用 fixup 快速提交及合并**
```
git commit --fixup ${commitId}

git rebase -i --autosquash ${commitId}
```
**本地分支与远程分支同步**
```
git fetch origin feat/test:feat/test -f
```
**本地分支 reset 到远程的某个分支**
```
git reset --hard origin/master
```
