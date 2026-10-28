# go-overseas · Global Integration Challenge（英文版入口）

线上地址：<https://yan-shipeng.github.io/go-overseas/>

## 这个仓库做什么

它**只做一件事**：提供一个英文版入口页，把英文版模拟游戏用一层 iframe 嵌进来。

```
https://yan-shipeng.github.io/go-overseas/          ← 本仓库（薄壳）
  └─ iframe → https://78701606623f48b18f877315adf995ed.sg2.agentos-app.run/en   ← 英文版（当前）
```

## 指向说明

英文版托管在 WorkBuddy Sites 上（含服务端排行榜），因此这里直接指向它，
而不是自己放一份静态副本。

> ⚠️ WorkBuddy Sites 每次重新发布会生成**新的域名**，届时需要同步更新 `index.html` 里的 `iframe src`。

> 如需改指向 `integration`（自包含静态副本），只需改 `index.html` 里的 `iframe src`。

## 与其它站点的关系

| 站点 | 语言 | 指向 | 依赖 |
|---|---|---|---|
| `go-overseas` | 英文 | WorkBuddy Sites 应用 `/en` | 依赖 WorkBuddy 运行时 |
| `integration` | 中文 | 自包含游戏 + 排行榜 | 仅 GitHub Pages |
| `go-global` | 中文 | Manus 托管应用 | 依赖 Manus 运行时 |

## 部署

纯静态，无需构建：把内容推到 `gh-pages` 分支，GitHub Pages 自动发布。

## 说明

- 页面本身不做任何逻辑，只有加载动画 + 一层 iframe，外加 12 秒兜底
  （避免 iframe 已加载但 `onload` 未触发时加载层一直盖住画面）。
- 本仓库只负责入口，游戏内容与修复都在上游（WorkBuddy Sites 项目）维护。
