# Liqora Design

Liqora 的 UI 需求、交互原型、设计参考、配色与素材。当前原型与 UI 需求均为 v0.21，业务基线为 PRD v1.17。

- [UI 需求](docs/current-lp-ui-requirements.md)
- [交互原型](mockup/index.html) · [原型说明](mockup/README.md)
- [总览截图](mockup/overview.jpg) · [详情截图](mockup/detail.jpg) · [活动与交易标签](mockup/activity.jpg)
- [关联 Swap](mockup/linked-swap.jpg) · [居中费用关联弹框](mockup/allocation.jpg)
- [设计稿与参考素材](mockup/designs/README.md) · [Revert 参考观察](docs/revert-reference-review.md)
- [图表配色 SVG](chart-palette.svg) · [PNG](chart-palette.png) · [交易标签配色 SVG](tag-palette.svg)
- [字体、图标与 Logo 来源](mockup/assets/README.md)

业务 PRD、领域术语、计算样例与 ADR 继续维护在 [liqora-docs](https://github.com/JIAMING-LI/liqora-docs)。本地可将两个仓库并列检出，最新工作区 PRD 位于 `../liqora-docs/prd/current-lp-performance-prd.md`。

## 预览

从本仓库根目录运行：

```sh
python3 -m http.server 8767 --bind 127.0.0.1 --directory mockup
```

打开 [本地原型](http://127.0.0.1:8767/)。使用原生 HTML、CSS、JavaScript，所需字体、Logo、图标及图表脚本均在仓库内，无需安装前端项目依赖。主设计宽度 1440px，最小桌面宽度 1100px。

## 验证

```sh
node mockup/check.mjs --logic-only
node mockup/check.mjs
```

完整交互检查需要 Node.js、Python 3 和已安装的 `agent-browser`，会自行启动并关闭临时 HTTP 服务。添加 `--screenshots` 可更新截图。

原型仅使用构造数据和模拟验证，费用关联保存在页面会话中；不连接钱包、RPC 或生产数据库。历史对照图保留在 `mockup/qa/`，不代表当前页面状态。
