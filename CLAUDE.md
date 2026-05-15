# 52HUB Admin Frontend Claude Entry

当前目录是 52HUB admin 后台前端源码仓库。

开始任务前必须先读：

1. `/Users/Apple/52hub-source-hardening/52HUB-AGENT-BOOTSTRAP.md`
2. `/Users/Apple/52hub-source-hardening/52HUB-PROJECT-STATUS.md`
3. `/Users/Apple/52hub-source-hardening/52HUB-OPERATIONS-RUNBOOK.md`
4. `/Users/Apple/52hub-source-hardening/52HUB-CHANGELOG.md`

当前关键状态：

- 分支：`52hub/v1.0.2-admin-hardening`
- commit：`666c376 52hub: harden admin branding and production fixes`
- tag：`v1.0.2-52hub-admin-001`
- working tree：clean
- 后台保留 `zh-TW` 是刻意设计，用于内容管理兼容。

边界：

- 没有明确任务时不要修改 admin。
- 不 push 到 `origin`。
- 不碰 user。
- 不碰生产，除非用户明确要求上线。
- 上线只同步 `dist/` 到 `/opt/dujiao-next/web/admin/`。
- 上线前必须备份 `/opt/dujiao-next/web/admin`。
- 不输出任何配置密钥。

构建命令：

```bash
npm run build
```

