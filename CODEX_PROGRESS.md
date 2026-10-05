# Wyatt-Panel 进度

## 2026-10-05

- 从 `liandu2024/AnGe-Panel` 克隆源码到 `/Users/yjn/Documents/ChatGPT/wyatt-panel`。
- 将 Git remote `origin` 重命名为 `upstream`，创建本地分支 `codex/wyatt-panel`。
- 完成 Wyatt-Panel 品牌元数据第一轮改动：package、页面标题、PWA manifest、locale、登录页、关于页、Compose 服务名、README 标题与容器名。
- 保留 MIT 许可证、作者署名和上游链接；未创建或上传 GitHub 远程仓库。
- 使用 pnpm 8.15.9 安装依赖；`./node_modules/.bin/vue-tsc --noEmit` 通过。
- ESLint 仍有上游基线错误，未大范围自动修复；Go 工具链不可用，后端编译待补。

## 2026-10-05｜移除上游推广并建立自有图标

- About 页面已移除上游 GitHub、Telegram、安格超市和两个 AI 推广入口；保留版本检查链接与 MIT 开源致谢。
- 设计并接入 Wyatt-Panel 自有彩色 SVG 标志（蓝紫粉渐变背景、W 形控制台线条、节点高光）。
- 同步更新源代码、后端实际使用的 `dist/` bundle、favicon 和默认面板名称；未覆盖运行数据、seed 或 Docker 镜像。
- 验证：Node 可解析改动后的 JS；`vue-tsc --noEmit` 待本轮复核。
