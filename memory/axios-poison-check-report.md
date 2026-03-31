# Axios 投毒事件排查报告

**排查日期**：2026-03-31 20:26 (Asia/Shanghai)
**排查范围**：OpenClaw 环境 + 相关目录

---

## 📋 排查项目

| 检查项 | 状态 | 说明 |
|--------|------|------|
| 1. 恶意 axios 版本 (1.14.1/0.30.4) | ✅ 安全 | 未发现 |
| 2. package-lock.json 污染 | ✅ 安全 | 无恶意版本记录 |
| 3. plain-crypto-js 恶意模块 | ✅ 安全 | 未发现 |
| 4. macOS RAT 痕迹 | ✅ 安全 | `/Library/Caches/com.apple.act.mond` 不存在 |
| 5. Linux RAT 痕迹 | ✅ 安全 | `/tmp/ld.py` 不存在 |
| 6. workspace 目录依赖 | ✅ 安全 | 无恶意 axios |
| 7. ~/.openclaw 全局目录 | ✅ 安全 | 无 plain-crypto-js |

---

## 🔍 检查命令

```bash
# 1. 检查 axios 恶意版本
npm list axios 2>/dev/null | grep -E "1\.14\.1|0\.30\.4"

# 2. 检查 package-lock.json
grep -A1 '"axios"' package-lock.json | grep -E "1\.14\.1|0\.30\.4"

# 3. 检查 plain-crypto-js
ls node_modules/plain-crypto-js 2>/dev/null

# 4. macOS RAT 检查
ls -la /Library/Caches/com.apple.act.mond 2>/dev/null

# 5. Linux RAT 检查
ls -la /tmp/ld.py 2>/dev/null
```

---

## ✅ 结论

**OpenClaw 环境和相关目录均未受到 axios 投毒事件影响。**

---

*排查完成时间：2026-03-31 20:26*
*OpenClaw 版本：2026.3.28*
