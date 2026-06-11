# 52HUB Admin Frontend — Claude Code Entry

当前目录是 52HUB admin 后台前端源码仓库。

---

## ⚠️ 开始任务前——强制执行，不可跳过

### 第一步：读完四份共享文档

```
/Users/Apple/52hub-source-hardening/52HUB-AGENT-BOOTSTRAP.md
/Users/Apple/52hub-source-hardening/52HUB-PROJECT-STATUS.md
/Users/Apple/52hub-source-hardening/52HUB-OPERATIONS-RUNBOOK.md
/Users/Apple/52hub-source-hardening/52HUB-CHANGELOG.md
```

### 第二步：只读预检

```bash
cd /Users/Apple/52hub-source-hardening/dujiao-next-admin
git branch --show-current
git log --oneline -3
git status --short
```

**对比下方「当前仓库快照」，若 commit hash 不一致，以 git log 为准。**

---

## 当前仓库快照（每次 commit 后必须更新此块）

- 分支：`52hub/v1.0.2-admin-hardening`
- **最新业务代码 commit：`a95c824 52hub: upgrade admin backend console to v1.2.1`**（最新交接文档 commit 以 `git log -1` 为准）
- 上游基线：`v1.2.1`
- tag：`v1.0.2-52hub-admin-001`
- private remote：`https://github.com/yaajie/52hub-admin-private`（已同步）
- working tree：以 `git status --short` 为准；文档交接更新后应保持 clean 并 push 到 private

最近一次生产上线：

- 时间：2026-06-04
- 范围：admin 静态文件 + API 容器
- admin commit：`a95c824 52hub: upgrade admin backend console to v1.2.1`
- API commit：`e058f7a 52hub: upgrade api to v1.2.1 preserving sort order`
- 生产备份：`/opt/dujiao-next/backups/pre-backend-upgrade-20260604-061527`
- admin 部署路径：`/opt/dujiao-next/web/admin/`
- API 镜像：compose tag `dujiaonext/api:v1.0.2-52hub-sortorder` 已指向 v1.2.1 构建镜像 id `sha256:a457c1b96766440240ad78ab4999739ea808e31d1afc06605b7da042bd5c75e3`

## 2026-06-12 生产迁移状态

- 当前生产后台入口：`https://ht.aikaitong.com`
- 当前主站 API：`https://aikaitong.com/api`
- 旧主域：`https://52hub.org` / `https://www.52hub.org` 301 到 `https://aikaitong.com/`
- 中转业务：`ai.52hub.org` / `relay.52hub.org` 保留不迁移。
- 生产后台 favicon/logo/标题/侧边栏已热修为 AI开通；备份见 `/opt/dujiao-next/backups/admin-brand-assets-20260611-235000/`、`/opt/dujiao-next/backups/admin-brand-text-20260611-235236/`、`/opt/dujiao-next/backups/brand-static-cleanup-20260612-005927/`。
- 注意：本仓库源码若仍有旧品牌静态文案，后续重建 admin 前必须先把生产热修回灌源码，再构建部署，避免覆盖生产品牌。

---

## ⚠️ 任务完成后——强制清单，全部勾完才算完成

- [ ] `git add` 相关文件，`git commit`，`git push private 52hub/v1.0.2-admin-hardening`
- [ ] `/Users/Apple/52hub-source-hardening/52HUB-CHANGELOG.md`：新增改动条目（改了什么 / 是否上线 / commit hash / 备份路径）
- [ ] `/Users/Apple/52hub-source-hardening/52HUB-AGENT-BOOTSTRAP.md`：更新相关快照
- [ ] `/Users/Apple/52hub-source-hardening/52HUB-PROJECT-STATUS.md`：更新相关状态描述
- [ ] 本文件（`CLAUDE.md`）：更新「当前仓库快照」中的 commit hash
- [ ] `AGENTS.md`（同目录）：更新「当前仓库快照」中的 commit hash

**以上清单未完成 = 任务未完成。下一个 agent 将读到错误状态。**

---

## 操作边界

- **没有明确任务时不要修改 admin**
- 不碰 user
- 不 push 到 `origin`（只推 `private`）
- 部署前必须备份：`cp -a /opt/dujiao-next/web/admin /opt/dujiao-next/web/admin.pre-<描述>-$(date +%Y%m%d-%H%M%S)`
- 上线只同步 `dist/` 到 `/opt/dujiao-next/web/admin/`
- 不输出任何配置密钥
- `zh-TW` 内容保留，是刻意设计，用于内容管理兼容，不要删

## 构建命令

```bash
cd /Users/Apple/52hub-source-hardening/dujiao-next-admin
npm run build
```
