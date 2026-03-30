# Bug Report: Telegram 图片上传被安全系统拦截

## 📋 问题概述

**OpenClaw 3.28 版本**升级后，Telegram 机器人无法上传图片，一直提示：
```
Failed to download media. Please try again.
```

## 🔍 问题原因

**OpenClaw 3.28 新增的 URL 安全系统**误判 Telegram 文件服务器地址为内网/私有 IP，导致图片上传被拦截。

### 日志证据

```
{"subsystem":"security"}
"blocked URL fetch (url-fetch) target=https://api.telegram.org/file/bot8540460373:AAHIVFrMqnUzjn-odYvsX6phcIc5FoELRao/photos/file_19.jpg 
reason=Blocked: resolves to private/internal/special-use IP address"
```

### 受影响的功能

- ✅ 文字消息：正常
- ❌ 图片上传：被拦截
- ❌ 文件下载：被拦截

## 📦 受影响版本

| 版本 | 状态 |
|------|------|
| 2026.3.28 | ❌ 有 bug |
| 2026.3.13 | ✅ 正常 |
| 2026.3.x (x<28) | ✅ 正常（推测） |

## 🔄 复现步骤

1. 升级到 OpenClaw 2026.3.28
2. 通过 Telegram bot 发送带图片的消息
3. 系统提示 "Failed to download media"
4. 查看日志发现安全系统拦截

## ✅ 临时解决方案

### 方案 1：回退到 3.13 版本（推荐）

```bash
# 1. 卸载当前版本
npm uninstall -g openclaw

# 2. 安装 3.13 版本
npm install -g openclaw@2026.3.13

# 3. 重启 Gateway
openclaw gateway restart
```

### 方案 2：等待官方修复

这是一个安全策略过于严格导致的 bug，需要官方：
1. 将 `api.telegram.org` 加入白名单
2. 或者修复 IP 判断逻辑

## 📝 建议报告给官方

**报告渠道：**
- GitHub Issues: https://github.com/openclaw/openclaw/issues
- Discord: https://discord.com/invite/clawd

**报告内容：**
```
Title: [Bug] 3.28 security system blocks Telegram file uploads

Description:
After upgrading to 2026.3.28, Telegram bot cannot upload images.
Security system blocks api.telegram.org/file/* URLs with reason:
"Blocked: resolves to private/internal/special-use IP address"

This is a false positive - Telegram's servers are not internal IPs.

Workaround: Downgrade to 2026.3.13

Logs:
{"subsystem":"security"}
"blocked URL fetch (url-fetch) target=https://api.telegram.org/file/bot.../photos/file_19.jpg 
reason=Blocked: resolves to private/internal/special-use IP address"
```

## 📊 影响评估

| 影响范围 | 严重程度 |
|----------|----------|
| 所有使用 Telegram 通道的用户 | 高（核心功能不可用） |
| 其他通道（Discord/WhatsApp等） | 未知（可能同样受影响） |

## 🕐 时间线

- **2026-03-30 17:07** - 用户报告问题
- **2026-03-30 17:08** - 定位问题原因（安全系统拦截）
- **2026-03-30 17:12** - 回退到 3.13 版本，问题解决

---

*报告生成时间：2026-03-30 17:12 (Asia/Shanghai)*
*OpenClaw 版本：2026.3.13 (回退后)*
