# go-overseas · Global Integration Challenge（英文版入口）

线上地址：<https://yan-shipeng.github.io/go-overseas/>

## 这个仓库做什么

它**只做一件事**：提供一个英文版入口页，把英文版模拟游戏用一层 iframe 嵌进来。

```
https://yan-shipeng.github.io/go-overseas/     ← 本仓库（薄壳）
  └─ iframe → https://yan-shipeng.github.io/integration/   ← 英文版游戏本体
       └─ iframe → integration-fixed.html（自包含单文件游戏 + 在线排行榜）
```

## 为什么指向 integration，而不是自己放一份

英文版游戏本体（`integration-fixed.html`，约 380KB 单文件）与在线排行榜
（`data/leaderboard.json` + GitHub Actions 采集器）都住在 `integration` 仓库里。

如果本仓库再放一份副本，就会出现**两套各自独立的排行榜数据**，同一堂课的学生
分成两个榜单，失去比较意义。所以这里采用「薄壳 + iframe 指向唯一数据源」的做法：
**排行榜全站唯一，且随时同步 upstream 的修复**。

## 与其它站点的关系

| 站点 | 语言 | 指向 | 依赖 |
|---|---|---|---|
| `go-overseas` | 英文 | `integration`（自包含副本） | 仅 GitHub Pages |
| `integration` | 英文 | 自包含游戏 + 排行榜 | 仅 GitHub Pages |
| `go-global` | 中文 | Manus 托管应用 | 依赖 Manus 运行时 |

## 部署

纯静态，无需构建：把内容推到 `gh-pages` 分支，GitHub Pages 自动发布。

## 说明

- 页面本身不做任何逻辑，只有加载动画 + 一层 iframe，外加 12 秒兜底
  （避免 iframe 已加载但 `onload` 未触发时加载层一直盖住画面）。
- 游戏本体的所有修复（结算页按钮、结算弹窗按钮）都在 `integration` 仓库里维护，
  本仓库无需跟着改。
