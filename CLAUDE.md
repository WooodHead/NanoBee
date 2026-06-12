# NanoBee

本项目是**公开开源仓库**。

## 🔒 private/ 私密目录（重要）

- `private/` 是一个**独立的私有 git 仓库**（远程：`WooodHead/NanoBee_Private`），嵌套在本仓库内，被主仓库 `.gitignore` 忽略。
- **AI 可以并且应该读取** `private/` 下的内容（聊天历史、项目规划等）作为上下文。
- 私密内容（与 AI 的聊天记录、项目规划、想法、未公开的路线图等）**必须写入 `private/` 下**，禁止写到主仓库的公开目录。
- **版本管理规则**：
  - 修改了 `private/` 下的文件 → 在 `private/` 目录内单独 `git add / commit / push`（推到私有远程）。
  - 修改了主仓库文件 → 在仓库根目录正常提交，`private/` 会被自动忽略。
  - 🚫 任何情况下禁止把 `private/` 下的文件提交到主仓库（`.gitignore` + pre-commit hook 双重拦截，不要绕过）。
- 克隆本仓库后需重新安装保护 hook：`cp scripts/git-hooks/pre-commit .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit`
