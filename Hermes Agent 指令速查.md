---
title: Hermes Agent 指令速查
tags: [hermes, agent, cli, reference]
created: 2026-07-05
updated: 2026-07-05
---

# Hermes Agent 指令速查

> 常用 CLI 命令 + 对话内斜杠命令
> 最后更新：2026 年 7 月

## 🚀 启动与对话 (CLI)

| 命令 | 说明 |
|------|------|
| `hermes` | 启动交互式对话（默认恢复最近会话） |
| `hermes -c "帮我写一个 Python 脚本"` | 一次性任务模式，执行后自动退出 |
| `hermes -z "prompt"` | One-shot 纯净模式，仅输出最终响应（适合脚本/管道） |
| `hermes --tui` | 启动现代 TUI 界面（推荐） |
| `hermes --cli` | 强制使用经典 REPL |
| `hermes --model deepseek-reasoner` | 本次使用指定模型（覆盖默认） |
| `hermes --provider openrouter --model anthropic/claude-sonnet-4` | 指定 provider + model 启动 |
| `hermes --workspace ~/project` | 以指定目录为工作上下文启动 |
| `hermes --yolo` | 跳过全部危险操作确认（慎用！） |
| `hermes --fresh` | 全新会话，不加载历史上下文 |
| `hermes --private` | 隐私模式（不保存本次对话到数据库） |
| `hermes --skills github,devops` | 预加载指定技能启动 |

## 💬 会话管理

| 命令 | 说明 |
|------|------|
| `hermes sessions list` | 列出最近会话（支持搜索过滤） |
| `hermes sessions browse` | 交互式会话浏览器（推荐日常使用） |
| `hermes sessions rename <id> "新标题"` | 为会话设置/修改标题 |
| `hermes sessions export <id> --format md` | 导出会话为 Markdown / JSONL |
| `hermes sessions delete <id>` | 删除指定会话 |
| `hermes sessions prune --older-than 30d` | 清理 30 天前的旧会话 |
| `hermes sessions stats` | 查看会话存储统计信息 |
| `hermes chat --query "快速问题"` | chat 子命令单次查询（旧式） |

## 🧠 模型管理

| 命令 | 说明 |
|------|------|
| `hermes model` | 交互式选择默认模型和 provider（推荐） |
| `hermes model list` | 列出所有已配置模型 |
| `hermes model current` | 查看当前默认模型 |
| `hermes model use <model>` | 切换默认模型 |
| `hermes model test <model>` | 测试模型连通性 |
| `hermes model benchmark` | 对所有已配置模型跑基准测试（对比速度/质量/价格） |
| `hermes model pricing` | 查看模型价格信息 |
| `hermes fallback list` | 查看 fallback provider 链 |
| `hermes fallback add` | 添加 fallback provider |

## 🛠️ 工具与技能

| 命令 | 说明 |
|------|------|
| `hermes skills list` | 列出已安装技能 |
| `hermes skills search <关键词>` | 搜索可安装的技能 |
| `hermes skills browse` | 浏览技能市场（分页） |
| `hermes skills install <name>` | 从 Hub 安装技能（如 nousresearch/xxx） |
| `hermes skills update` | 更新所有已安装的 Hub 技能 |
| `hermes skills config` | 交互式启用/禁用技能 |
| `hermes tools list` | 列出所有工具及启用状态（按平台） |
| `hermes tools enable web` | 启用某个工具集 |
| `hermes tools disable video_gen --permanent` | 禁用工具（加 --permanent 写入配置） |
| `hermes bundles list` | 列出技能 bundle（可作为 /bundle 名使用） |
| `hermes plugins list` | 列出已安装插件 |
| `hermes curator status` | 查看后台技能维护状态 |

## ⚙️ 配置与设置

| 命令 | 说明 |
|------|------|
| `hermes setup` | 重新运行完整配置向导（改 Key / 模型时推荐） |
| `hermes setup --models-only` | 仅重新配置模型 |
| `hermes setup --keys-only` | 仅重新配置 API Keys |
| `hermes setup --reset` | 重置配置（谨慎！） |
| `hermes config show` | 查看当前配置 |
| `hermes config edit` | 用 $EDITOR 编辑 config.yaml |
| `hermes config set model.provider xiaomi` | 快速设置单个配置项 |
| `hermes config check` | 检查配置缺失或过时项 |
| `hermes postinstall` | 安装非 Python 依赖（node、浏览器、ripgrep、ffmpeg） |

## 🔍 诊断与状态

| 命令 | 说明 |
|------|------|
| `hermes doctor` | 完整系统诊断（配置、依赖、模型连通性） |
| `hermes doctor --fix` | 尝试自动修复可修复的问题 |
| `hermes doctor --models` | 仅检查模型连接 |
| `hermes status` | 查看各组件状态 |
| `hermes status --deep` | 深度检查（较耗时） |
| `hermes logs -f` | 实时跟踪 agent.log（类似 tail -f） |
| `hermes logs errors --since 1h` | 查看最近 1 小时错误日志 |
| `hermes debug share` | 打包日志+系统信息上传并生成分享链接 |
| `hermes dump` | 导出完整 setup 摘要用于调试 |
| `hermes prompt-size` | 显示系统提示词 + 工具 schema 的字节占用 |

## 📡 网关、Cron 与集成

| 命令 | 说明 |
|------|------|
| `hermes gateway status` | 查看消息网关状态 |
| `hermes gateway setup` | 配置 Telegram / Discord / WhatsApp 等平台 |
| `hermes gateway start` | 启动网关后台服务 |
| `hermes gateway run` | 前台运行网关（Docker/WSL 推荐） |
| `hermes cron list` | 列出所有定时任务 |
| `hermes cron create` | 创建定时任务（自然语言描述） |
| `hermes cron run <name>` | 立即手动触发某个 cron 任务 |
| `hermes cron logs` | 查看定时任务日志 |
| `hermes portal info` | 查看 Nous Portal 连接与 Tool Gateway 状态 |
| `hermes dashboard` | 启动 Web UI 仪表盘（默认 9119 端口） |
| `hermes kanban list` | 查看多 profile 协作看板 |

## 🗄️ 备份、迁移与维护

| 命令 | 说明 |
|------|------|
| `hermes backup` | 完整备份 ~/.hermes（配置、技能、会话、状态） |
| `hermes backup --quick` | 快速快照（仅关键状态文件） |
| `hermes import ~/backup.zip` | 从备份恢复 |
| `hermes update` | 更新 Hermes Agent 到最新版 |
| `hermes update --check` | 仅检查是否有更新 |
| `hermes claw migrate` | 从 OpenClaw 迁移数据/配置 |
| `hermes migrate` | 迁移旧版配置或已退役模型设置 |
| `hermes uninstall` | 卸载 Hermes（谨慎） |

## 🧩 记忆、MCP 与高级

| 命令 | 说明 |
|------|------|
| `hermes memory setup` | 配置外部记忆提供者（honcho 等） |
| `hermes memory status` | 查看当前记忆提供者状态 |
| `hermes mcp list` | 列出 MCP 服务器 |
| `hermes mcp add <server>` | 添加 MCP 服务器 |
| `hermes profile list` | 列出多 profile（隔离实例） |
| `hermes profile create work` | 创建新 profile |
| `hermes --worktree` | 在隔离 git worktree 中运行（并行 agent） |
| `hermes completion zsh` | 生成 shell 补全脚本（bash/zsh/fish） |
| `hermes insights 7` | 查看最近 7 天使用洞察与 token 统计 |

## 💬 对话内斜杠命令 (/xxx)

| 命令 | 说明 |
|------|------|
| `/help` | 显示所有可用斜杠命令（支持 /help <cmd> 详情） |
| `/model [model]` | 切换当前会话模型（支持 --global 改默认） |
| `/memory add 关键事实` | 添加全局记忆（永久保存） |
| `/memory` | 查看/编辑/搜索记忆 |
| `/skills` | 管理当前会话加载的技能 |
| `/clear` | 清除当前对话上下文（全新开始） |
| `/compact [here N]` | 压缩上下文（释放 token，可保留最近 N 轮） |
| `/export` | 导出当前对话（Markdown / JSON / 文本） |
| `/new [name]` | 开启全新会话（别名 /reset） |
| `/retry` | 重试上一条用户消息 |
| `/undo [N]` | 撤销最近 N 轮用户输入并重提示 |
| `/rollback [num]` | 列出或恢复文件系统检查点 |
| `/private` | 本次对话进入隐私模式（不保存） |
| `/yolo` | 切换 YOLO 模式（跳过危险审批） |
| `/status` | 显示当前会话信息 |
| `/goal 长期目标描述` | 设置跨轮持久目标（直到完成） |
| `/subgoal 额外条件` | 为当前目标添加子条件 |
| `/system 指令` | 注入系统消息（纠正 Agent 行为） |
| `/temp claude-sonnet-4` | 仅下一条消息临时切换模型 |
| `/version` | 显示 Hermes 版本 |
| `/update` | 触发更新 |
| `/debug` | 上传调试报告 |
| `/quit [--delete]` | 退出 CLI（--delete 同时删历史） |
