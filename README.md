# HermesAgent CLI 速查工具箱

一组单文件 HTML 命令速查表，覆盖 Hermes Agent、Tailscale、Proxmox VE 三个工具的常用命令。

纯原生 HTML/CSS/JS，零外部依赖，离线可用。

## 速查表一览

| 速查表 | 命令数 | 文件 | 说明 |
|--------|--------|------|------|
| Hermes Agent | ~160 条 | `hermes-command.html` | CLI 命令 + 对话内斜杠命令，含标签说明与动态路由 |
| Proxmox VE | ~220 条 | `pve-command.html` | qm / pct / pvesm / pveum / pvesr / pveceph 等全分类 |
| Tailscale | 33 条 | `tailscale-command.html` | 连接、诊断、Funnel/Serve、Drive 等全量命令 |

## 功能特性

- **实时搜索** — 输入即过滤，匹配命令名 + 描述
- **点击复制** — 点击命令文本一键复制到剪贴板
- **键盘快捷键** — 按 `/` 快速聚焦搜索框，`Esc` 退出
- **深色模式** — 自动跟随系统 `prefers-color-scheme`
- **响应式布局** — 自适应网格，桌面/移动端均可阅读
- **零依赖** — 每个文件独立可用，无需安装任何东西

## 使用方式

### 本地打开

直接用浏览器打开 `index.html`，通过首页卡片进入各速查表。

或直接打开单个文件：

```
open hermes-command.html
open pve-command.html
open tailscale-command.html
```

### GitHub Pages 部署

仓库已启用 GitHub Pages（或手动在 Settings → Pages 中开启），推送到 `main` 分支后即可在线访问：

```
https://linuxhobby.github.io/HermesAgent/
```

## 文件结构

```
HermesAgent/
├── index.html                  # 首页导航（三张卡片入口）
├── hermes-command.html         # Hermes Agent 指令速查
├── pve-command.html            # Proxmox VE 命令速查
├── tailscale-command.html      # Tailscale CLI 命令速查
├── Hermes Agent 指令速查.md     # Hermes Agent Markdown 源文档
├── Tailscale CLI Reference.md  # Tailscale Markdown 源文档
└── README.md
```

## 技术栈

纯原生 HTML + CSS + JavaScript，无构建步骤、无包管理器、无 CDN。

- 命令数据硬编码在各文件的 `data` 数组中
- GitHub 风格配色，参考 ProxmoxVE tailscale-command.html 样式
- 深色/浅色模式通过 `@media (prefers-color-scheme: dark)` 自动切换

## 更新命令

各速查表的命令数据存储在对应 HTML 文件的 `const data = [...]` 数组中，直接编辑即可更新。每条命令的结构：

```js
{ cmd: "命令名", desc: "中文说明", tags: ["CLI", "CHAT"] }
```

新增分类只需在 `data` 数组中添加 `{ cat: "分类名", items: [...] }` 对象。

## 参考来源

- **Hermes Agent** — [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) 命令注册表
- **Proxmox VE** — [Proxmox VE Wiki - Command line tools](https://pve.proxmox.com/wiki/Command_line_tools)
- **Tailscale** — [Tailscale CLI 文档](https://tailscale.com/docs/reference/tailscale-cli)

## License

MIT
