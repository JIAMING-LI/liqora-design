# Commit 规范

两个 Liqora 仓库统一使用以下格式；本文件是设计仓库的提交约定。

```text
type(scope): 中文摘要

可选正文：说明变更原因、用户可见行为和影响。
验证：实际执行的检查及结果；未执行时写明原因。

可选页脚：关联 issue，或 BREAKING CHANGE: 不兼容变化与迁移方式。
```

## 标题

- `type` 使用小写英文；`scope` 可省略，填写时使用下表中的小写范围。
- 摘要默认中文，保留必要英文术语，明确“修改了什么”；不写“更新一下”“fix bug”等泛化描述，末尾不加句号。
- 标题建议不超过 72 个字符，详细背景放正文。简单勘误可以只有标题。

| Type | 用途 |
|---|---|
| `feat` | 新增或调整用户可见功能、交互、布局或视觉设计 |
| `fix` | 修复计算、交互、布局或视觉缺陷 |
| `docs` | UI 需求、原型说明、素材来源、参考说明与协作规范 |
| `refactor` | 调整代码结构且不改变行为或视觉结果 |
| `style` | 仅代码格式、空白等变化；界面视觉变化使用 `feat` 或 `fix` |
| `test` | 增加或修改检查脚本 |
| `chore` | 仓库维护、忽略规则等杂项 |
| `revert` | 撤销已有提交，正文注明被撤销的 commit 与原因 |

推荐 scope：`overview`、`detail`、`activity`、`allocation`、`charts`、`assets`、`mockup`、`ui`、`repo`。跨页面的共同逻辑可用 `mockup`，跨多个范围的同一变更也可省略 scope。

```text
feat(charts): 将详情趋势切换为累计 PnL
fix(allocation): 修复重复保存导致的准备费用叠加
feat(ui): 调整桌面原型的表格布局
refactor(mockup): 复用当前与历史仓位的摘要渲染
test(mockup): 增加负值 PnL 的检查
docs(repo): 增加代理协作与提交规范
```

## 拆分与验证

- 一次提交解决一个完整问题；对应原型、必要断言、UI 需求、说明和受影响截图一起提交。
- 以主要目的选择 type：修复交互并更新截图仍是 `fix`，新增功能并补检查仍是 `feat`。
- 截图与素材须有明确用途；不批量混入无关历史图片、临时输出、敏感数据或用户已有修改。
- 两个仓库分别提交。跨仓库变更使用可对应的主题，正文列出关联仓库和文件；已有 commit 或 issue 时使用真实引用，不编造编号。
- 非平凡变更在正文记录实际验证：逻辑检查、完整交互检查、检查过的页面与宽度。只生成截图不能写成已完成视觉验证，原型通过也不代表产品验收。
- 真正存在不兼容变更时使用 `type(scope)!: 摘要`，并在 `BREAKING CHANGE:` 中说明影响和迁移；普通视觉调整不自动等于 breaking change。
- 提交前按 [AGENTS.md](AGENTS.md) 完成对应验证，再检查 `git status --short`、`git diff --cached` 和 `git diff --cached --check`，确认暂存内容仅包含本次工作。

此规范通过提交时遵循，无需安装 commitlint、Husky 或 Git hooks。
