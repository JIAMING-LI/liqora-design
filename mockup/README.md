# Liqora 桌面 Mockup

> 当前 HTML 为 v0.21，对应 PRD v1.17／UI v0.21，已同步关联 Swap 活动。按用户提供的 [Dashboard-2 截图](designs/dashboard-2-reference.png)更新首屏、Geist 字体、Reicon 图标和品牌素材。

当前文档见 [UI 需求](../docs/current-lp-ui-requirements.md) 和 [PRD](https://github.com/JIAMING-LI/liqora-docs/blob/main/prd/current-lp-performance-prd.md)。保留原生 HTML／CSS／JavaScript，无需安装项目依赖；从本目录运行 `python3 -m http.server 8767 --bind 127.0.0.1`，访问 `http://127.0.0.1:8767/`。使用 HTTP 预览可正常加载本地图标文件；建议宽度 1440px，最小桌面宽度 1100px。

两个页面：当前 LP 总览和单页 LP 详情。总览依次展示 Position value、Uncollected fees、Total fees、PnL 及较 24h 前变化、仓位价值柱图、各 LP 当前未领取手续费环图、逐行 LP 列表；总览图表固定使用 Open 数据，列表由状态 Tab 筛选，图下入口及列表整行都可进入对应详情。详情按新参考采用价值／Total fees／APR／PnL 四项指标及前日变化、仓位余额／APR 趋势图、费用与资产区间双栏、底部活动。加入手续费汇总、投入盈亏比、窗口日均；首页 APR 固定 24h；详情可选 1h／24h／7d／30d，返回不改变首页的 24h。活动按截图五列展示，双币数量直接可见；区间用低饱和蓝细带、端点线、圆点当前价指针和对齐的上下限。全部可见文案、提示、错误、验证及费用关联界面均为英文。

演示步骤：打开 NFT #204801 → `Link preparation costs` → `Simulate verification` → `Use sample hash` → `Parse transaction` → 输入 6 SPY → `Save allocation`。所得 10 SPY、兑换费 30 USD、Gas 2 USD，分配后费用 19.20 USD，盈亏由 295 变为 275.80 USD，投入盈亏比由 2.95% 变为 2.76%。手续费汇总仍为 100 USD，24h APR 仍为 36.50%。修改、重复保存、全部剩余、跨四个 LP 的额度限制及撤销可演示；总览和详情保持同一成本口径，断开验证恢复公开 LP 盈亏。

页脚 `Demo states` 可切换历史投入缺价、刷新失败、空持仓和费用保存失败。查询入口支持地址格式校验；本原型仅能展示演示钱包，不把其他输入地址冒充已查询。30d 窗口不足，第二个 LP 的 24h／7d／30d 也不足，1h 窗口可单独查看。

全部为构造数据。前日钱包快照为价值 $20,830、PnL $506、费用 $188、未领取 $65，当时第二个 LP 尚未创建；四项变化是快照金额变化，包含当前 LP 集合变化。当前示例 SPY = 500 USD、USDG = 0.99 USD；活动金额使用各自构造的历史估值。详情前日快照使用首个 LP 价值 $10,300、未领取 $30、PnL $385；APR 的前日同窗口值为 1h 73%、24h 32.85%、7d 18.25%，第二个 LP 尚未存在。期间费用的双币估值按构造的各半分布，首个 LP 平均本金按两币各 $5,000；这些是演示拆分。活动 Gas 原生数量使用各笔构造历史 ETH 价格 $2,500 换算，不是实时行情。哈希、合约和 poolId 也是示例，不对应真实区块浏览器记录。模拟验证、哈希解析、60 秒刷新与保存仅演示交互，不调用钱包、RPC 或服务端。保存仅存在当前页面会话，重载清空；真实产品的数据库恢复、签名鉴权、跨设备权限及费用去重仍需实现和验收。原型仅支持示例 hash，不是通用交易解析器。

- [图表配色板](palette.html) · [配色板截图](palette.jpg)
- [总览截图](overview.jpg)
- [详情截图](detail.jpg)
- [详情趋势图](trends.jpg)
- [活动表格截图](activity.jpg)
- [价格区间（v0.9 历史配色）](range.jpg)
- [费用关联截图](allocation.jpg)

趋势横轴为过去 24h（第二个 LP 从建仓起 8h），APR 在每个采样点按当前所选窗口滚动计算。View data 展示固定历史样例，末值复用当前摘要；首个 LP 的 24h 余额差为 −$100，APR 从 32.85% 到 36.50%，增加 3.65 pp。缺窗口不画曲线，第二个 LP 的创建时 1h APR 不可用。余额走势包含加减仓，不作为投资回报。

运行 `node mockup/check.mjs --logic-only` 可检查图表合计、占比、零值／空态、页面顺序、费用口径与 APR 一致性，不打开浏览器。

已安装 `agent-browser` 和 Python 3 时，从设计仓库根目录运行 `node mockup/check.mjs`；脚本自动启动并关闭临时本地 HTTP 服务。检查英文文案、盈亏与手续费汇总、比值、APR／日均、窗口保留、权限、哈希、额度、重复保存／修改／撤销、错误状态及桌面宽度。加 `--screenshots` 更新上述截图。该检查仅验证原型，不代表 PRD 的链上接入或产品验收通过。

品牌使用用户提供的 `assets/liqora-logo-v2.svg`，金额统一显示 `$`。区间上下限乘 USDG 的美元价格后再展示，列表价值／未领取／PnL 仅显示主数值且隐藏 NFT 编号；双币 Logo、数量及估值在详情账单展示。图标来自 Reicon 1.2.4 Outline，使用原始路径组成的本地 SVG sprite，保留 MIT 许可。Geist 字体与 SPY／USDG／Robinhood Chain／Uniswap Logo 均本地托管；[素材与来源](assets/README.md)列出官方链接。卡片试用 12px 轻圆角，图标用黑色 #1E2327，单系列曲线用烟灰蓝 #8FA0A8 与雾蓝 #D8DFE6 渐变面积，多 LP 图表用烟灰蓝 #8FA0A8 与苔绿 #C9D1C8；LP gas 与活动增加 ETH 原生数量／图标。没有新增项目依赖，图表使用 Canvas 并在旁边提供等价文字数值。[原型检查](../README.md#验证)记录同屏参考对照与交互验证。

### v0.14 简化演示

现有四个 SPY/USDG 仓位 #204801–#204804，分别展示 10 天／8 小时／5 天／20 天周期、两个区间内及一个低于区间／一个高于区间。总价值 $26,120、未领取 $92、累计费用 $275、PnL +$339。第 3／4 个仓位各有独立历史、双币余额、活动及前日快照；新增 APR 中间点为前日到当前值的线性演示样例。准备成本的 10 SPY 额度在四个仓位间共享。

主内容与页脚最大宽度 1340px。移除图表副标题、底部说明及 `over chart range` 文案，保留标题涨跌徽标、轴、数值、图例和 View data。第 3 系列用 #61727B，第 4 系列用 #D8DFE6，延续现有莫兰迪色系。旧 PRD 会计样例仍保留其原始两仓位数据，不等同于本版四仓位演示。

### v0.14 双币明细分列

费用和资产明细采用 Item / Total / SPY / USDG 四列；Logo 只在每张表的 Token 表头出现。币种列中数量在上、美元估值在下；没有数量样例的数据保留美元估值，不补造数量。缺少历史价格时显示 —。Gas 与准备成本仍在费用表下方，价格区间仍在资产表上方。活动表保持原有排版。主内容最大宽度 1340px。

[分列效果](token-columns-preview.jpg)

### v0.15 统一已领取手续费

复投按 Collect → Deposit 记账，移除独立 Reinvested directly 指标与数据字段。Collected 包含复投，Total deposits 同时计入同额投入；Total fees = Collected + Uncollected。第二个 LP 已领取 $60、累计投入 $6,040（SPY $40／USDG $6,000），手续费合计仍为 $70、PnL 仍为 −$104，投入盈亏比约 −1.72%。复投活动拆为同一 hash 下的领取和投入，Gas 只计一次。钱包手续费 $275 与盈亏 +$339 保持不变。

[统一已领取后的详情截图](collected-fees.jpg)。已通过逻辑检查与完整浏览器交互检查，覆盖全额／部分复投、后续取回、Gas 去重及投入盈亏比，并检查了详情布局。

### v0.16 当前与历史仓位

按[状态 Tab 截图](designs/position-tabs-reference.png)新增 Open position (4)、In Range (2)、Out of Range (2)、Closed position (4)，数量按真实演示集合计算。页签在统计卡上方，同步切换统计、图表和列表，详情返回保留选择，支持方向键及 Home／End。无当前仓位时仍可查看历史。

四个已平仓周期的手续费合计 $590、PnL +$915，仓位与未领费用均为 $0。历史详情复用全部现有项目，增加平仓日期；期间 APR、趋势和区间价格截至平仓。同 NFT #204801 的旧周期与当前周期分别计数、记账、保存准备费用。历史示例余额曲线在退出前保持构造余额、退出时归零，APR 使用固定窗口演示值，不代表真实链上数据。

共享准备交易的构造日期改为 Jul 1, 2026，早于全部示例周期，10 SPY 额度在当前及历史 8 个周期之间共享。历史索引、后续手续费结算和持久化仍按 PRD 实现，原型仅使用固定样例。

- [历史总览截图](closed-overview.jpg)
- [历史详情截图](closed-detail.jpg)

### v0.17 列表 Tab 与多交易对

按用户更正，Tab 移到原 Current positions 标题位置，仅筛选下方列表。首页统计、前日变化、仓位分布与未领取分布固定使用全部 Open positions，切换 Closed 也保持价值 $26,120／未领取 $92／Total fees $275／PnL +$339。

当前与历史各有 SPY/USDG、ETH/USDG、NVDA/USDG、CRCL/USDG 四组样例，列表、图例、详情、表头、活动与区间统一使用对应币种。固定样例价格依次为 $500／$2,500／$180／$120，USDG 为 $0.99。手续费、盈亏与资金金额保留原样例，代币数量和价格区间按对应样例价格换算，均非实时行情。

准备费用各币种使用独立的示例 hash 与 10 单位所得额度，当前与历史中同币种的周期共享该源交易额度，不再跨币种共享一笔 SPY 交易。仍支持同源额度约束、修改、撤销与私有记录隔离。此版本取代 v0.16 的总览随 Tab 切换及跨八周期共享同一源交易的行为。

### v0.18 融合页签与表格

四个 Tab 缩为 12px／30px 按钮，放入表格卡片的顶部工具栏；与列标题、数据行共用外边框和圆角，右侧仍为固定 Fee APR · 24h。删除左侧 sidebar、相关样式与导航处理，内容居中；品牌入口可返回首页，钱包入口与详情返回保留。Open 总览口径和四种交易对不变。

### v0.19 详情费用与居中关联弹框

详情第二项改为 Total fees，数值和前日变化均使用手续费汇总；Fees & costs 保留 Collected／Uncollected 拆分。Recent activity 当前三类为 Deposit、Collect、Withdraw，定义见 [UI 需求](../docs/current-lp-ui-requirements.md#44-活动)。Link preparation costs 改为 920px 居中弹框，输入 hash 后并排展示原交易与数量分配／费用预览，保留验证、数量校验、替换、撤销与失败草稿。

### v0.20 同交易颜色标签

Recent activity 每行左上角显示可点击的 Txn 缩略哈希标签，同 transaction 的 Withdraw／Collect／Deposit 共享底色。按两张用户色卡合并相近黄、米色后保留六色，按完整示例 hash 分配并循环；保留 hash 文本识别，深浅底分别搭配通过 4.5:1 对比度检查的文字色。

### v0.21 已关联的 Swap 活动

保存准备费用关联后，当前／历史 LP 的 Recent activity 增加私有 Swap 行和 Linked preparation 标记，展示源交易支付／所得、原费用及当前 LP 分摊成本。示例源交易统一为 Jul 1, 2026 · 13:50 UTC+8，早于所有示例 LP，按原时间放在 LP 操作之后；源哈希沿用六色标签。修改更新、重复保存不重复生成，撤销移除、断开验证隐藏、重新验证恢复。活动展示与原 LP 记账数据分开，Swap 金额不加入投入、收入、Total fees 或基础 PnL。
