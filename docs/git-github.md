# Git 与 GitHub 使用专题

本专题聚焦「能直接上手」的 Git 与 GitHub 常用能力，覆盖从日常提交到问题排查的完整链路。

## 1. 基础工作流（add / commit / push / pull）

```bash
git status
git add .
git commit -m "feat: add xxx"
git push origin main
```

推荐节奏：

1. 先用 `git status` 看变化
2. 用 `git add <file>` 精准暂存（避免无关文件进入提交）
3. `git commit` 时写清楚“做了什么 + 为什么”
4. 推送前先 `git pull --rebase`，减少无意义 merge commit

## 2. 远程仓库管理（remote）

```bash
git remote -v
git remote add origin git@github.com:<owner>/<repo>.git
git remote set-url origin git@github.com:<owner>/<new-repo>.git
```

适用场景：仓库迁移、切换 SSH/HTTPS、配置 upstream（fork 工作流）。

## 3. 进阶协作（rebase）

```bash
git fetch origin
git rebase origin/main
# 解决冲突后
git add <conflicted-file>
git rebase --continue
```

建议在个人功能分支上整理提交历史，合并前保持线性、可读。

## 4. 临时保存现场（stash）

```bash
git stash push -m "wip: payment refactor"
git stash list
git stash pop
```

当你需要临时切分支修 bug，但当前修改还没准备好提交时非常实用。

## 5. 问题定位（bisect）

```bash
git bisect start
git bisect bad
git bisect good <good-commit>
# 按测试结果执行
git bisect good
git bisect bad
git bisect reset
```

用二分法快速定位“哪个提交引入了问题”，比手工排查更高效。

## 6. 提交签名（sign）

GitHub 支持对提交进行 GPG 或 SSH 签名，提升来源可信度：

```bash
git config --global commit.gpgsign true
# 或配置 SSH signing key（推荐按团队规范）
```

签名后在 GitHub 提交记录里可看到 Verified 标识。

## 7. GitHub 协作核心：Issue 与 Pull Request

### Issue

- 用于记录需求、缺陷、任务拆解
- 建议写清楚：背景、复现步骤、预期结果、验收标准

### Pull Request

- 描述变更范围与动机
- 关联 Issue（如 `Closes #123`）
- 请求评审并根据反馈迭代
- 合并前确保 CI 通过

## 8. 实操演练（建议）

1. 新建分支：`git checkout -b feat/git-topic-demo`
2. 修改文档并提交：`git add` + `git commit`
3. 推送分支：`git push -u origin feat/git-topic-demo`
4. 在 GitHub 发起 Pull Request，关联一个 Issue
5. 根据评审意见追加提交并再次推送
6. CI 通过后合并，回到 main 并同步：

```bash
git checkout main
git pull --rebase
```

---

通过以上流程，你可以完成从本地开发、远程协作到故障定位的一整套 Git/GitHub 实战闭环。
