---
title: Tailscale CLI Reference
tags: [tailscale, vpn, cli, reference]
created: 2026-07-05
updated: 2026-07-05
---

# Tailscale CLI Reference

> Tailscale 命令行工具速查
> 最后更新：2026 年 7 月

## 连接

| 命令 | 说明 |
|------|------|
| `tailscale up` | 连接到 Tailscale，如需时进行登录 |
| `tailscale down` | 从 Tailscale 断开连接 |
| `tailscale set` | 更改指定的首选项 |

## 账号

| 命令 | 说明 |
|------|------|
| `tailscale login` | 登录到 Tailscale 账户 |
| `tailscale logout` | 断开连接并使当前节点密钥失效 |
| `tailscale switch` | 切换到不同的 Tailscale 账户 |

## 网络诊断

| 命令 | 说明 |
|------|------|
| `tailscale netcheck` | 显示本地网络条件分析 |
| `tailscale ping` | 在 Tailscale 层 ping 主机，查看路由情况 |
| `tailscale status` | 显示 tailscaled 及其连接的状态 |
| `tailscale ip` | 显示 Tailscale IP 地址 |

## 连接工具

| 命令 | 说明 |
|------|------|
| `tailscale nc` | 连接到主机上的端口，接入 stdin/stdout |
| `tailscale ssh` | SSH 到 Tailscale 机器 |
| `tailscale file` | 发送或接收文件 |

## 对外服务

| 命令 | 说明 |
|------|------|
| `tailscale funnel` | 在公网上暴露内容和本地服务器 |
| `tailscale serve` | 在 tailnet 内部提供内容和本地服务器 |
| `tailscale cert` | 获取 TLS 证书 |

## 系统管理

| 命令 | 说明 |
|------|------|
| `tailscale configure` | 配置主机以启用更多 Tailscale 功能 |
| `tailscale lock` | 管理 tailnet 锁定 |
| `tailscale update` | 将 Tailscale 更新到最新或指定版本 |
| `tailscale web` | 运行用于控制 Tailscale 的 Web 服务器 |

## 其他

| 命令 | 说明 |
|------|------|
| `tailscale version` | 显示 Tailscale 版本 |
| `tailscale bugreport` | 显示可共享的标识符以帮助诊断问题 |
| `tailscale licenses` | 获取开源许可信息 |
