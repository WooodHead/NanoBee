# NanoBee

本项目是**公开开源仓库**。**公开仓库里只应包含公开的代码和公开的文档**，其他一切开发过程中产生的文件都不属于这里。

## 🔒 private/ 私密目录（重要）

- `private/` 是一个**独立的私有 git 仓库**（远程：`WooodHead/NanoBee_Private`），嵌套在本仓库内，被主仓库 `.gitignore` 忽略。
- **AI 可以并且应该读取** `private/` 下的内容（聊天历史、项目规划等）作为上下文。
- **开发过程中创建出来的所有非公开文件必须写入 `private/` 下**，禁止写到主仓库的公开目录，包括但不限于：
  - 与 AI 的聊天记录 / 聊天历史截屏 → `private/chat-history/`
  - 需求文档（PRD）→ `private/docs/`（如 `private/docs/requirements.md`）
  - 日志 → `private/logs/`
  - 项目规划、想法、未公开的路线图 → `private/planning/`
  - 设计稿、截图、prompt、调试/解释性产物 → `private/design/`、`private/screenshots/`、`private/prompts/`、`private/explain/`
- **判断标准**：一个文件如果不是「面向外部用户的代码或文档」，就放 `private/`；拿不准时默认放 `private/`。
- **版本管理规则**：
  - 修改了 `private/` 下的文件 → 在 `private/` 目录内单独 `git add / commit / push`（推到私有远程）。
  - 修改了主仓库文件 → 在仓库根目录正常提交，`private/` 会被自动忽略。
  - 🚫 任何情况下禁止把 `private/` 下的文件提交到主仓库（`.gitignore` + pre-commit hook 双重拦截，不要绕过）。
- 克隆本仓库后需重新安装保护 hook：`cp scripts/git-hooks/pre-commit .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit`
