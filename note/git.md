# Git 常用命令记录

## 配置
```bash
git config --global user.name "名字"
git config --global user.email "邮箱"
git config --list                    # 查看配置
```

## 仓库操作
```bash
git init                             # 初始化仓库
git clone <url>                      # 克隆远程仓库
```

## 基本工作流
```bash
git status                           # 查看状态
git add <file>                       # 暂存文件
git add .                            # 暂存所有
git commit -m "message"              # 提交
git commit -am "message"             # 跳过add直接提交（仅已跟踪文件）
```

## 分支操作
```bash
git branch                           # 查看分支
git branch <name>                    # 创建分支
git checkout <branch>                # 切换分支
git checkout -b <branch>             # 创建并切换
git switch <branch>                  # 切换（新版）
git switch -c <branch>               # 创建并切换（新版）
git merge <branch>                   # 合并分支
git merge --no-ff <branch>           # 合并保留分支记录
git branch -d <branch>               # 删除分支
git branch -D <branch>               # 强制删除
```

## 查看历史
```bash
git log                              # 完整日志
git log --oneline                    # 简洁日志
git log --oneline --graph            # 图形化
git log --oneline --graph --all      # 所有分支
git diff                             # 查看未暂存的改动
git diff --staged                    # 查看已暂存的改动
```

## 撤销操作
```bash
git restore <file>                   # 撤销工作区修改
git restore --staged <file>          # 取消暂存
git reset HEAD~1                     # 撤销上一次commit（保留修改）
git reset --hard HEAD~1              # 撤销并删除修改（危险）
git revert <commit>                  # 创建新commit来撤销
```

## 远程操作
```bash
git remote -v                        # 查看远程仓库
git remote add origin <url>          # 添加远程仓库
git push origin <branch>             # 推送
git push -u origin <branch>          # 推送并设置上游
git pull                             # 拉取并合并
git fetch                            # 仅拉取不合并
```

## 进阶操作
```bash
git stash                            # 暂存当前修改
git stash pop                        # 恢复暂存
git stash list                       # 查看暂存列表
git cherry-pick <commit>             # 挑选某个commit
git rebase <branch>                  # 变基
git rebase -i HEAD~3                 # 交互式变基（修改最近3个commit）
git reflog                           # 查看所有操作记录（救命用）
```

## 标签
```bash
git tag                              # 查看标签
git tag v1.0.0                       # 创建标签
git tag -a v1.0.0 -m "message"       # 带注释的标签
git push origin v1.0.0               # 推送标签
```

## 其他实用
```bash
git blame <file>                     # 查看每行的修改者
git show <commit>                    # 查看某次提交详情
git clean -fd                        # 删除未跟踪文件（危险）
```

## .gitignore 常用
```
node_modules/
*.log
.env
dist/
.DS_Store
```