# Wyatt-Panel 接手卡

## 当前状态

- 项目目录：`/Users/yjn/Documents/ChatGPT/wyatt-panel`
- 来源：`https://github.com/liandu2024/AnGe-Panel`
- 上游 Git remote：`upstream`
- 当前分支：`codex/wyatt-panel`
- 本地定位：基于 AnGe-Panel 的 Wyatt-Panel 衍生项目，尚未配置个人 GitHub remote，尚未上传。

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
3. 确定个人 GitHub 用户名与公开仓库设置后，再新增 remote、创建仓库并上传；上传前保留人工确认。
