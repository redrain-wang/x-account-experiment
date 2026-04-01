# 北京花粉浓度每日提醒 - Cron 配置

## 📅 定时任务

**执行时间**：每天早上 7:00
**截止日期**：2026 年 5 月 31 日
**推送渠道**：Telegram (chat_id: 1682060517)

---

## 🤖 Cron 配置

### macOS LaunchAgent 方式

创建文件：`~/Library/LaunchAgents/com.pollen.daily.plist`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.pollen.daily</string>
    
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/node</string>
        <string>/Users/redrain/.openclaw/workspace/scripts/pollen-daily.js</string>
    </array>
    
    <key>StartCalendarInterval</key>
    <dict>
        <key>Hour</key>
        <integer>7</integer>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
    
    <key>EnvironmentVariables</key>
    <dict>
        <key>TELEGRAM_BOT_TOKEN</key>
        <string>8540460373:AAHIVFrMqnUzjn-odYvsX6phcIc5FoELRao</string>
        <key>TELEGRAM_CHAT_ID</key>
        <string>1682060517</string>
    </dict>
    
    <key>StandardOutPath</key>
    <string>/tmp/pollen-daily.log</string>
    
    <key>StandardErrorPath</key>
    <string>/tmp/pollen-daily.err</string>
</dict>
</plist>
```

### 加载任务

```bash
# 加载任务
launchctl load ~/Library/LaunchAgents/com.pollen.daily.plist

# 查看状态
launchctl list | grep pollen

# 卸载任务
launchctl unload ~/Library/LaunchAgents/com.pollen.daily.plist
```

---

## 📝 推送内容模板

```
🌸 北京花粉浓度日报 | {日期}

📊 今日浓度：{等级}
🌡️ 主要花粉：{种类}
📍 高发区域：{区域}

💡 防护建议：
• {建议 1}
• {建议 2}

---
数据来源：花粉监测预报 / 花粉健康宝
```

---

## 🔗 数据获取方式

### 方式 1：花粉健康宝小程序
- 微信小程序搜索"花粉健康宝"
- 提供当日及未来 2 天预报
- 支持分区域查询

### 方式 2：花粉监测预报公众号
- 微信公众号关注"花粉监测预报"
- 每日发布官方预报

### 方式 3：北京市气象局官网
- https://www.bjmb.gov.cn/
- 花粉浓度监测数据

---

## ⏰ 任务周期

| 项目 | 时间 |
|------|------|
| 开始日期 | 2026-04-02 |
| 结束日期 | 2026-05-31 |
| 执行频率 | 每日 7:00 |
| 预计执行次数 | ~60 次 |

---

## 📌 注意事项

1. **数据源限制**：目前没有公开 API，需要手动查询或爬虫
2. **替代方案**：可以订阅"花粉监测预报"公众号推送
3. **停用时间**：5 月 31 日后自动停止（春季花粉季结束）

---

*配置日期：2026-04-01*
*下次执行：2026-04-02 07:00*
