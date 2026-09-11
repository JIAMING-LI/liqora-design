# 仓库协作规则

## 定位与阅读顺序

本仓库维护 Liqora 的 UI 需求、桌面交互原型、配色与设计素材。业务规则以独立的 `liqora-docs` 仓库为依据。

开始工作前阅读 [README.md](README.md)、[UI 需求](docs/current-lp-ui-requirements.md) 和 [原型说明](mockup/README.md)。涉及金额、权限或仓位生命周期时，同时阅读并列检出的 `../liqora-docs/prd/current-lp-performance-prd.md`、`CONTEXT.md` 及相关样例、ADR；未检出时使用 README 中的仓库链接。

协作说明和需求文档使用中文；页面可见文案、提示、错误与验证流程使用英文。版本号以当前文档为准，历史说明或参考截图不覆盖当前需求。

## 目录与实现方式

- `docs/current-lp-ui-requirements.md`：当前 UI 行为与视觉要求。
- `mockup/index.html`：原生 HTML、CSS、JavaScript 原型，包含演示数据与交互。
- `mockup/check.mjs`：现有逻辑与浏览器交互检查，优先扩展该入口。
- `mockup/assets/`：本地字体、Logo、图标及许可；来源见目录内 README。
- 根目录配色 SVG／PNG：图表与标签配色；同名预览应与源图同步。
- `mockup/designs/`、`mockup/references/`：视觉参考；`mockup/qa/`：历史对照，不代表当前界面。
- `mockup/*.jpg`：原型截图；是否为当前版本须核对原型说明。

优先复用现有函数、样式、素材和原生浏览器能力。没有实际需要时，不引入前端框架、构建工具、新依赖、运行时 CDN 或额外抽象。

## 修改边界

- 修改前追踪相关状态、计算函数及全部调用方；共享计算口径在共同入口修正，不在各页面分别补丁。
- 原型只使用明确标识的构造数据和模拟验证；钱包、RPC、服务端及持久化接入须属于明确任务范围。
- 保持 Open 总览与列表筛选分离；详情 APR 窗口不改变首页 24h APR 或累计 PnL 趋势。
- 盈亏、复投、Gas 去重、历史周期、准备费用权限遵循业务文档。设计参考只指导视觉，不决定公式或新增功能。
- 缺失数据保留不可用状态，不填零或伪造行情；演示交易对不代表真实接入承诺。
- 复用现有品牌素材，保留外部资产来源与许可证。更换素材时同步 `mockup/assets/README.md`。
- 保留键盘操作、焦点、控件名称和弹框可访问性；图表提供等价文字数据，不仅靠颜色区分状态。
- 默认验证 1440px 和最小桌面宽度 1100px。新增其他屏幕适配须与任务范围一致。
- UI 行为或版本变化时同步相关需求、原型说明和 README；只更新受影响的截图，保留有意义的历史对照。

## 预览与验证

以下命令均从仓库根目录运行：

```sh
python3 -m http.server 8767 --bind 127.0.0.1 --directory mockup
node mockup/check.mjs --logic-only
node mockup/check.mjs
# 需要更新截图时运行：
node mockup/check.mjs --screenshots
git diff --check
```

- 预览地址为 `http://127.0.0.1:8767/`；使用 HTTP 以正常加载本地资源。
- 逻辑检查需要 Node.js；完整交互检查另外需要 Python 3 和已安装的 `agent-browser`，脚本自行启动并关闭临时服务。
- 修改计算或状态逻辑须运行逻辑检查，并在现有脚本中补充能暴露问题的最小断言。
- 修改交互或布局须运行完整检查并查看受影响页面、状态和桌面宽度；截图生成成功不等于视觉验证通过。
- 纯文档修改检查格式、链接和内容即可。环境缺少验证工具时如实报告未运行项，不把逻辑检查称为完整检查。
- 交付前检查最终差异与工作区状态，说明改动及验证结果；保留用户已有修改，不混入无关文件。
- Commit 格式与拆分遵循 [COMMIT_CONVENTION.md](COMMIT_CONVENTION.md)。
