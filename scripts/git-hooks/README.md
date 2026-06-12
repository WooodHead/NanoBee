# git hooks

## pre-commit

- **文件职责**：阻止 `private/`（私密嵌套仓库）下的任何文件被提交到公开主仓库，作为 `.gitignore` 之外的第二道保险（防 `git add -f`）。
- **依赖关系**：无外部依赖，纯 POSIX sh。需手动安装到 `.git/hooks/pre-commit` 才生效（`.git/hooks` 不被 git 跟踪，克隆后需重新安装）。
- **安装**：`cp scripts/git-hooks/pre-commit .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit`

## 变更历史

### 2026-06-12 — 创建
- **出发点**：NanoBee 计划开源，但聊天历史 / 项目规划等私密内容需要放在主目录内供 AI 读取，同时绝不能进入公开 git 历史
- **目标**：在 `.gitignore` 忽略 `/private/` 的基础上，加一道 pre-commit 强制拦截，防止误用 `git add -f` 泄露
- **关键决策**：hook 源文件存放在 `scripts/git-hooks/` 随仓库版本化，安装时复制到 `.git/hooks/`（不使用 `core.hooksPath`，避免改 git config）
