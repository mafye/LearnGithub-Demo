# LearnGitHub 演示仓库（入门示例）

此仓库用来演示 Git 与 GitHub 的基础操作：版本控制、分支、合并和 GitHub Actions 的基本工作流。下面记录了在本地执行的步骤与命令，便于回顾学习。

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

2. 创建 feature 分支并在其上提交变更：

   git checkout -b feature/demo
   (在 index.html 中追加一行示例内容)
   git add index.html
   git commit -m "feat: add demo change on feature branch"

3. 合并回 main：

   git checkout main
   git merge feature/demo -m "Merge feature/demo into main"

## 关于 GitHub 远程仓库（可选）
如需把本地仓库推送到 GitHub，可使用 gh CLI：

   gh auth login
   gh repo create REPO_NAME --public --source=. --remote=origin --push

之后会在 GitHub 上看到 Push 与 Actions 运行记录（如果 workflow 在 main/feature 分支触发）。

---

本 README 同时作为本次操作的记录。若需要把仓库发布到 GitHub 或创建保护分支与 Secrets，请告知。