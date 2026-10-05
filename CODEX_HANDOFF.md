# Wyatt-Panel 接手卡

## 当前状态

- 项目目录：`/Users/yjn/Documents/ChatGPT/wyatt-panel`
- 来源：`https://github.com/liandu2024/AnGe-Panel`
- 上游 Git remote：`upstream`
- 当前分支：`codex/wyatt-panel`
- 本地定位：基于 AnGe-Panel 的 Wyatt-Panel 衍生项目，已配置个人 GitHub remote `origin` 并上传到 `main`。

## 已完成

- 建立独立项目目录并保留 MIT LICENSE 与上游来源。
- 完成第一轮品牌元数据迁移：package 名称、页面标题、PWA 名称、登录/关于页显示名称、双语 locale、Docker Compose 服务名改为 Wyatt-Panel。
- 保留上游仓库链接和作者署名，未伪造尚不存在的 Wyatt-Panel GitHub 地址。
- 安装前端依赖，`vue-tsc --noEmit` 通过。

## 约束

- 不覆盖 `dist/`、`seed/`、运行数据或上游构建产物；仓库明确禁止直接运行旧前端构建覆盖当前 dist。
- Docker Compose 当前仍引用上游 GHCR 镜像，待个人 GitHub 仓库和镜像名确定后再切换。
- 当前没有 Go 工具链，因此尚未执行后端编译和 Go 测试。
- eslint 基线存在上游既有错误；本轮未做大范围格式化修复。

## 下一步

1. 明确 Wyatt-Panel 第一项功能改动和品牌视觉范围。
2. 逐项修复/验证对应前端或后端，并保持提交粒度清晰。
3. 后续功能改动继续在 `codex/wyatt-panel` 分支提交，完成后推送到 GitHub `main`。

## 最新变更｜移除开发者广告与自有图标

- Wyatt-Panel About 页面已移除上游社群、市场及 AI 推广内容，改为简短的自托管产品说明；保留版本检查和 Sun-Panel MIT 来源声明。
- 新图标位于 `src/assets/logo.svg`，并已同步到 `dist/assets/logo-3d38229d.svg`、`dist/favicon.svg` 与 `dist/favicon-black.svg`。
- 为保证当前 3005 后端服务可直接看到改动，已定点修补 `dist/assets/index-69cf921e.js`、`index-4d989675.js`、`index-8a73d23b.js` 和 `dist/index.html`；未运行被禁止的旧前端构建。

## GitHub 上传（2026-10-05）

- 公开仓库：[wyattrnmm-del/wyatt-panel](https://github.com/wyattrnmm-del/wyatt-panel)。
- 默认分支：`main`；当前远程提交：`8c10bbd`。
- 仓库描述和 README 已明确标注“基于 AnGe-Panel 二次开发”，并保留 Sun-Panel MIT 来源声明。
- `upstream` 继续指向原始 AnGe-Panel；`origin` 指向个人 Wyatt-Panel 仓库。

## 直接拖动排序与版本链接（2026-10-05）

- About 页版本号和检查新版本链接已指向个人 Wyatt-Panel 仓库。
- 首页登录后可直接拖动网站/书签图标，松手自动保存排序；搜索过滤时禁用拖动。
- 已加入 NAS 运行数据忽略规则，个人 NAS 数据不会随 Git 提交上传。
- 已推送提交：`ee6250b`（功能）、`c06e78c`（数据忽略规则）。
