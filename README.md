# LearnGitHub 演示仓库（入门示例）

此仓库用来演示 Git 与 GitHub 的基础操作：版本控制、分支、合并和 GitHub Actions 的基本工作流。下面记录了在本地执行的步骤与命令，便于回顾学习。

## 教学目标（入门）：
- 理解版本控制的基本概念与常用命令
- 学会使用分支进行并行开发，理解 main（主线）与 feature 分支的作用
- 学会把本地仓库推送到 GitHub 并查看分支/提交历史

## 本次练习流程说明：
本练习将一步一步演示如何创建分支、在分支上开发而不影响主线、如何切换查看不同分支的功能，以及如何合并分支回 main。每一步都会给出命令与说明，请按顺序操作并确认理解后再继续下一步。

## 本次创建的文件
- index.html：最小静态页面演示应用
- .gitignore：忽略常见文件
- .github/workflows/ci.yml：简单的 CI workflow（由脚本生成）

## 本次执行的关键命令（已在本地运行）

1. 初始化仓库并提交初始文件：

   git init
   git config user.name "Demo User"
   git config user.email "demo@example.com"
   git add .
   git commit -m "Initial commit: add demo web app and docs"
   git branch -M main

2. 创建 feature 分支并在其上提交变更（演示如何在分支上开发而不影响主线）：

   # 在本地创建并切换到新分支
   git checkout -b feature/demo

   # 在分支上进行修改（例如修改 index.html，添加一段内容）
   # 这些修改只存在于 feature/demo 分支，main 分支保持不变
   git add index.html
   git commit -m "feat: add demo change on feature branch"

   # 查看当前分支与提交历史，确认更改只在 feature 分支上
   git status
   git log --oneline --graph --decorate --all

3. 在本地查看 main 与 feature 的区别（不影响主线）：

   # 切回主线查看 main 的内容（此时不会有 feature 分支的改动）
   git checkout main
   # 打开或查看 index.html（比如在编辑器或通过命令行查看）

   # 若想把 feature 的更改合并回主线
   git merge feature/demo -m "Merge feature/demo into main"

   # 如果不想保留 feature 分支，可删除：
   git branch -d feature/demo

   # 若远程存在 origin，可推送 main 并查看 GitHub 上的分支与差异：
   git push origin main
   git push origin --delete feature/demo  # 若要删除远程分支

   # 可使用 gh 或 GitHub 网站创建 Pull Request 来合并分支（演示协作流程）

## 关于 GitHub 远程仓库（可选）
如需把本地仓库推送到 GitHub，可使用 gh CLI：

   gh auth login
   gh repo create REPO_NAME --public --source=. --remote=origin --push

之后会在 GitHub 上看到 Push 与 Actions 运行记录（如果 workflow 在 main/feature 分支触发）。

---

本 README 同时作为本次操作的记录。若需要把仓库发布到 GitHub 或创建保护分支与 Secrets，请告知。

## 步进演示：分支操作 — 第一步（创建并查看 feature 分支）

已执行的操作（演示分支 feature/step1）：

1. 在本地创建并切换到 feature 分支：

   git checkout -b feature/step1

2. 在该分支上对 index.html 进行了修改（示例添加一段内容），提交并推送到了远程：

   git add index.html
   git commit -m "feat(step1): add feature step1 content"
   git push --set-upstream origin feature/step1

3. 如何查看并比较分支（在本地）：

   # 切换到 feature 分支查看其内容
   git checkout feature/step1
   # 查看修改状态与提交历史
   git status
   git log --oneline --graph --decorate --all

   # 比较 main 与 feature/step1 的差异（在任一分支上运行）
   git fetch origin
   git diff main..feature/step1

   # 切回 main 查看主线内容（此时不会包含 feature 的改动）
   git checkout main
   # 在本地打开或查看 index.html 来对比差异

4. 当前状态：

   - 已在远程创建并推送分支：feature/step1
   - main 分支保持不变，feature/step1 包含示例变更

请按照上述步骤在你的本地或编辑器中查看分支内容并确认理解，确认后告知准备继续下一步演示（例如在 feature 分支上运行或创建 Pull Request）。

CI triggered at 2026-02-27 09:41:29 by Copilot
