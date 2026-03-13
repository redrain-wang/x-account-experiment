# GitHub 热门内容规范

## 📦 已安装技能

| 技能 | 功能 | API Key |
|------|------|---------|
| **github-trending** | 获取 GitHub 热门项目 | ❌ 不需要 |
| **github-search** | 深度搜索 GitHub 仓库 | ❌ 不需要 |

---

## 📋 使用方法

### github-trending
```bash
cd /Users/redrain/.openclaw/workspace/skills/github-trending
bash github-trending.sh              # 今日热门
bash github-trending.sh weekly       # 本周热门
bash github-trending.sh monthly      # 本月热门
```

### github-search
```bash
cd /Users/redrain/.openclaw/workspace/skills/github-search
node scripts/github-search.mjs "AI 工具"
node scripts/github-search.mjs "rag" --language python
node scripts/github-search.mjs "llm" --min-stars 1000
```

---

## 📝 内容形式

### 推文 1：每日热门
```
🔥 GitHub 今日热门项目：

1️⃣ 项目名 - 简介
2️⃣ 项目名 - 简介
3️⃣ 项目名 - 简介

都是好东西，建议收藏。
#GitHub #开源 #AI
```

### 推文 2：AI 专题
```
🤖 GitHub 上最火的 AI 项目：

1️⃣ fish-speech - TTS 语音合成（SOTA）
2️⃣ openrag - RAG 一站式解决方案
3️⃣ hindsight - Agent 记忆系统

开源的力量，真香。
#GitHub #AI #开源
```

### 推文 3：本周总结（推文串）
```
推文 1/5：
📊 本周 GitHub AI 项目总结：

Top 5 热门项目，个个都是好东西。

第 1 名太狠了，解决了一个大痛点👇

推文 2-5/5：
【每个项目详细介绍】
```

---

## 🎯 发布频率

| 类型 | 频率 | 时间 |
|------|------|------|
| **每日热门** | 每天 1 次 | 12:00 或 20:00 |
| **AI 专题** | 每周 2-3 次 | 20:00 |
| **本周总结** | 每周 1 次 | 周日 20:00 |

---

## 💡 注意事项

1. **不要只发项目名** - 要有简介和亮点
2. **结合使用场景** - 说明能解决什么问题
3. **有个人观点** - "这个项目真香"vs"这是一个项目"
4. **避免 AI 味** - 像朋友推荐，不是机器列表

---

*2026-03-13 创建*
*已同步到 Git 仓库*
