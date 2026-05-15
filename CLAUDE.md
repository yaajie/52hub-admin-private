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
- **最新 commit：`efa3dbc 52hub: require shared handoff docs updates`**
- tag：`v1.0.2-52hub-admin-001`
- private remote：`https://github.com/yaajie/52hub-admin-private`（已同步）
- working tree：clean

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
