# 远端开发机（vultr-us）代码存储与安全规范

1. **统一工作目录**：所有新项目统一创建在 `/root/workspace/<项目名>` 下。
2. **严格脱敏（最高优先级）**：绝不将 `.env`、API Key、私钥、数据库密码等敏感信息提交到 Git（系统已配置全局 `/root/.gitignore_global` 兜底，但提交前仍需 `git status` 检查）。
3. **自动存盘到 GitHub 私有库**：
   - 每当完成一个阶段性开发任务或功能修改后，如果当前项目已绑定 GitHub 远程库（`origin`），**自动执行 `git add -A && git commit -m "..." && git push`** 同步到 GitHub 私有库。
   - 如果是全新项目尚未绑定 GitHub 远程库，先执行 `git init` 并完成首次本地 commit，然后提醒用户（或协助）绑定对应的 GitHub 私有库地址。
4. **开发与生产隔离**：本机仅通过 GitHub 私有库同步代码，不直接连接或修改生产服务器。
