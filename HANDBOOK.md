# AI 技术选择权与政策证据：2026 全景实操手册

> **Anti-Anthropic · V4.0 / 2026-11-14 / AndyAwake × 星觉科技**  
> 研究和教学用途。这个项目批评具体公司政策与商业行为，不把任何国家、民族或族裔视为应被排斥的对象。事实、当事方观点、作者判断与未证实推测将分开标记。

## 01｜用户先看这里：我们想保住的不是某个模型，而是自己的能力

Claude 和 Claude Code 的一些实践值得学习：项目约束文档、Skills、MCP、分工 Agent、自动质量门禁，以及强制的测试/交付习惯。**这些方法可以被重新组织成自己掌握的文件和流程，不必把知识和历史上下文锁在某一个产品界面里。**

把这个仓库当成「为什么要保有选择权 + 如何提取优秀方法」的工程指南；需要立刻迁移，请直接打开 [Out-Anthropic](https://github.com/AndyAwake/Out-Anthropic)；需要找工具，请打开 [Free-Anthropic](https://github.com/AndyAwake/Free-Anthropic)。

深度阅读：[Claude 优秀能力可移植指南](PORTABLE-CLAUDE.md)、[碎片化学习资源地图](RESOURCE-ATLAS.md)、[作者已开源的 Claude Code / Agent 研究库](https://github.com/AIPMAndy/anthropic-claude-code-agent-handbook)。

**本项目不是对任何人群的排斥倡议。** Anthropic 的开放政策、地区限制和技术立场应依据具体文件评估；未经证实的个人指控不会当作结论。

---


## 02｜十分钟读懂：为什么普通人也需要关心

科学探索可以跨越边界，但公司的市场准入、芯片出口政策、数据收集与商业合同一直处在具体法律和利益结构中。一个团队不必赞同任何一家供应商的政策，但不能把项目文件、用户数据和关键工作流完全交给随时可能变化的单一服务。

这份手册解决三个问题：**它公开做了什么？影响边界究竟在哪里？我们可以依法、低成本地保有选择权吗？** 不需要先站队；先查证，再做风险控制。

**先做三个小动作：** 保存这份来源索引；列出自己正在用的 AI 产品及其真实底层模型；挑一项真实任务做替代演练。只读观点不会降低经营风险，拿到可迁移的成品才会。

## 03｜证据地图：哪些结论可以确认

| 日期 | 事件 | 证据级别 | 可以得出的结论 | 边界 |
| --- | --- | --- | --- | --- |
| 2025-09-04 | Anthropic 发布更严格的地区销售说明 | 公司公告 | 有具体产品地区限制及对部分控制关系的约束 | 不等于以华人血统为唯一限制条件 |
| 2026-02-10 | Dario Amodei 与美国参议员会面讨论出口限制 | 媒体报道 | 参与对华先进芯片政策倡议 | 不等于单独决定美国政策 |
| 2026-07-24 | 英伟达等联署开放权重模型公开信 | 原始公开信 | 对开放权重有广泛行业支持 | 不能代表所有签署者对所有模型一概放开 |
| 2026-07-27 | Amodei 公开回应开放权重争议 | 公司一手声明 | 反对全面禁用，但主张安全测试等限制 | 不能概括为“禁止所有开源” |
| 2026-11-11 / 12 | 黄仁勋辞任；英伟达次日正式公告 | SEC 文件 / 公司公告 | 辞职事件真实发生 | 尚无可靠证据证明 Anthropic 或 Amodei 参与策划 |
| 2026-11-12 | Anthropic 新版 Supported Regions Policy 生效 | 公司现行政策 | 可逐项核对支持地区、所在地、总部/注册与控制关系 | 应与族裔身份概念分开 |

**核查规则：** 新闻报道可确认“有人报道过”，企业政策可确认“该公司公开规定了什么”，SEC 披露可确认公司申报的治理事项；它们不能自动证明猜测中的幕后因果关系。

## 04｜地区政策：看原文，而不是看截图

官方 Supported Regions Policy 于 **2026-11-12** 生效，覆盖 Claude.ai、Claude Code、Cowork、开发者 API、云平台及授权转售渠道。未列出的国家/地区不支持，并明确涵盖三类情况：人在不支持地区；组织注册地或总部在不支持地区；组织由不支持地区的个人或实体直接/间接多数持有或控制。

操作顺序：

1. 打开 [现行政策原文](https://www.anthropic.com/legal/supported-regions) 并记下生效日期；不要只用别人的摘要。
2. 分别记录**人员实际所在地、法人注册/总部、控制关系、所用具体产品和上游渠道**；这些是不同字段。
3. 向自己的法务、信息安全或供应商经理核对真实合同关系；组织架构复杂时不要用一句话推断全部场景。
4. 核对地区支持发生变化时，是否有可导出的数据与替代工作流。
5. 面对个体族裔、护照和国籍的提问，准确区分政策文本与个人推断。不能将对特定地区实体的限制写成对全世界华人族裔的统一禁令。

**作者观点：** 以市场区域和控制关系扩张技术准入边界，对跨国经营公司与国际技术协作提出了值得公开讨论的公平性问题。这个价值判断与上述条款事实分开陈述。

## 05｜芯片出口、国会与政策影响

2026 年 2 月，媒体报道 Anthropic CEO 与美国参议员讨论对华先进芯片出口限制。[Axios 报道](https://www.axios.com/2026/02/10/anthropic-ceo-china-chip-ban)。这一事实说明公司领导者在主动影响政策议题。公司还发表过关于芯片出口限制、蒸馏和模型安全的主张；这些主张应当沿一手公开文件追踪，而不是靠社交平台相互转述。

判断影响时，采用四层模型：**公开诉求 → 游说或会议记录 → 法规/行政动作 → 对供应与经营的真实影响**。前两层不能替代后两层。建议建立 `policy-watch.csv`，为每条记录添加日期、主张方、原文、影响范围、当前证据和下次复核日期。

涉及美国政治捐款时，注意区分公司政治倡议、游说登记、公司内部 PAC、个人政治捐款与独立政治广告。即使资金属于同一议题，也不能把不同法律主体的金额简单相加后写成“公司直接捐给某人”。相关资料见原仓库的 [POLITICS.md](https://github.com/AndyAwake/Anti-Anthropic/blob/main/POLITICS.md) 和 [sources.md](https://github.com/AndyAwake/Anti-Anthropic/blob/main/sources.md)。

## 06｜开放权重模型：分歧到底在哪里

**开源代码 ≠ 开放权重 ≠ 免费 API ≠ 无限制许可。** 在 AI 领域，模型权重可下载，不意味着训练代码、数据、许可证全部开放；一个工具能免费试用，也不意味着它没有推理或托管成本。

2026-07-24，英伟达等联合发布 [Open Weights and American AI Leadership](https://images.nvidia.com/pdf/Open-Weights-and-American-AI-Leadership.pdf)，主张避免过早、宽泛地限制开放权重生态。2026-07-27，Amodei 在 [官方声明](https://www.anthropic.com/news/position-open-weights-models) 中明确表示 Anthropic 没有倡议全面禁止开放权重，同时支持针对高能力模型的安全评测及部分国家安全限制。

讨论时，把四个维度分别写出来：**创新普惠**（谁能用）、**安全治理**（谁承担风险）、**商业竞争**（谁掌握分发入口）、**国家政策**（法律如何约束）。公司之间的公开立场分歧是事实；指控某方“从来只打击开源”则应提供按日期整理的具体行为证据。

## 07｜黄仁勋辞职：不把时间先后写成因果

英伟达 [2026-11-12 官方公告](https://nvidianews.nvidia.com/news/nvidia-announces-ceo-transition) 与 [SEC 8-K](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000082/nvda-20261111.htm) 记录了黄仁勋于 11 月 11 日辞去 CEO、总裁及董事职务，次日公布相关安排。两家公司在芯片政策或开放权重上的不同立场，**不能单独证明** Anthropic 或其负责人策划、推动或协调了离职事件。

若以后出现新的原始文件，先确认发布主体、文件真实性、涉及行为、时间线和独立印证，再更新结论。对个人的严重指控不因传播量大就自动成立。

## 08｜公开网站：按自己的目标控制 AI 抓取

先分清官方三类标识：`ClaudeBot`（可能用于模型训练的抓取）、`Claude-SearchBot`（搜索质量）、`Claude-User`（用户发起的内容获取）。Anthropic 的帮助中心还单独介绍了 `Claude-Agent` 托管浏览器流量，不能直接等同于前三种机器人。

### 方案 A：仅表达不用于训练的偏好

```text
User-agent: ClaudeBot
Disallow: /
```

### 方案 B：自行选择是否限制其他访问

```text
User-agent: ClaudeBot
Disallow: /

User-agent: Claude-SearchBot
Disallow: /

User-agent: Claude-User
Disallow: /
```

**关键代价：** 限制 `Claude-SearchBot` 或 `Claude-User` 可能降低相关搜索或用户请求对你网站的可见度；不要一边追求 GEO 曝光，一边不看代价地全部禁止。上述配置仅为片段，需要合并入网站**现有** robots.txt，而不是覆盖其他规则。机器人规则是表达偏好，不是私有文件访问控制。

需要在自有服务器进一步控制代理浏览器流量时，可用 WAF 或服务端配置进行测试，但 User-Agent 可被伪造，误封也可能影响合法用户。原仓库提供 [DATA-CONTROL.md](https://github.com/AndyAwake/Anti-Anthropic/blob/main/DATA-CONTROL.md) 和示例文件；变更前做好备份、低风险发布和回滚。官方说明见 [爬虫文档](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler) 与 [代理浏览器文档](https://support.claude.com/en/articles/18234133-how-do-anthropic-hosted-browsers-identify-themselves-when-they-browse-the-web-on-a-user-s-behalf)。

## 09｜亲手学习 Claude 的优秀能力：把「会用工具」升级为「有方法」

是否继续使用 Claude 是个人选择。但优质工程方法值得学习、验证、抽象再复用：

| 可学习的 Claude Code 模式 | 自己需要留的中立资产 | 换工具后怎么检查 |
| --- | --- | --- |
| `CLAUDE.md` 项目规则 | `PORTABLE-PROJECT.md`，明确目标/约束/验收 | Codex 用 `AGENTS.md`，Gemini CLI 用 `GEMINI.md`，各自核对是否加载 |
| Skills 可复用技能 | 合法可使用的 `SKILL.md`、资源文件和测试例 | 看依赖与脚本是否能跑，按目标工具要求调整 |
| MCP 外部工具 | 连接器清单、操作权限、示例输入/输出 | 新客户端重新鉴权，从只读测试开始 |
| Hooks 自动门禁 | 触发时机、测试命令、失败处理 | 重建等效测试/检查；不假设 Hook 格式兼容 |
| Agent 分工 | 角色卡、任务交接标准、人工批准点 | 不支持并行时也能串行完成同一任务 |
| 项目记忆与决策 | `decisions.md`、版本和恢复证据 | 换设备/换模型仍可重现并说明缺口 |

这不是对闭源内部实现的复制，而是从公开功能中提炼用户能够合法拥有的工作方法。[完整的可移植能力指南](PORTABLE-CLAUDE.md) 可配合 [Andy 原创 Claude Code / Agent 资料库](https://github.com/AIPMAndy/anthropic-claude-code-agent-handbook) 学习；已核对资料与未亲测的第三方参考见 [资源索引](RESOURCE-ATLAS.md)。

---

## 10｜企业供应商审计：一张表查清依赖

用 `templates/vendor-audit.csv` 逐产品写下：业务用途、界面产品、实际模型、所在地区、输入数据敏感等级、数据保存方式、导出入口、替代工具、月度实际费用、恢复演练结果、责任人和复核日期。

**优先级判定**建议简单实用：如果某项业务同时涉及客户敏感数据、单一模型依赖且没有可恢复的成品文件，就优先改它。不要把“模型能力强”直接推导成“适合作为唯一供应商”。

安全底线：遵守合同与使用条款，不尝试绕过地区限制，不对第三方服务实施未授权访问，不将客户数据作为公开教程原料。

## 11｜30 天执行计划：从观点到工程

| 周次 | 交付物 | 验收标准 |
| --- | --- | --- |
| 第 1 周 | AI 供应商与数据流向台账 | 关键任务至少能说清模型、数据位置、负责人 |
| 第 2 周 | 公开站点抓取策略与私有数据权限清单 | 能读取线上 robots；业务站点和私有文档权限正常 |
| 第 3 周 | 两个候选工具同题对照报告 | 同输入、相同修改机会；记录耗时、费用、错误 |
| 第 4 周 | 一次从备份恢复的演练记录 | 另一台设备或独立副本能打开文件并重做一项任务 |

推荐只跟踪 **4 个运营指标**：高风险依赖数量、资料可恢复比例、替代任务通过率、人工修正时间。未知值填“未测”，不要捏造成绩。

## 12｜Andy 的工程札记：为什么我更看重选择权

**作者公开实践，不代表案例已产生特定商业收益。** 我长期做 B 端 AI 产品，先后从事过腾讯、百度等环境下的产品工作，也参与过大模型相关业务和创业。对我来说，采购 AI 从来不只是比较生成内容好不好，而是看它能否被组织接入、被团队使用、被审计、出问题能否恢复。

最近我同时使用不同 AI 工作台，并长期维护 GitHub 开源教程。一个具体教训是：**提示词可以换，项目的来源、文件结构、验收条件和发布记录必须留在自己能控制的地方。** 所以我把独立备份、同题对照、可编辑交付物纳入这三个项目；这是方法选择，不是某个模型全面输赢的实测宣判。

## 13｜读者经常问的七个问题

**Q1：不使用 Claude 就自动保护了数据？** 不是。还要审查实际模型供应商、工具连接器和上传内容。

**Q2：robots.txt 能阻止任意访问吗？** 不能。它主要是对遵守规则的爬虫表达偏好。私有资料仍须认证与权限。

**Q3：公开模型一定更安全？** 不一定。要分别核对许可证、部署环境、安全评测、权限与运维能力。

**Q4：公开支持芯片出口限制就是参与所有政策决策吗？** 不是。意见表达、游说和正式法律程序不同。

**Q5：黄仁勋辞职与 Anthropic 有直接关系吗？** 目前公开材料不足以确认这一因果关系。

**Q6：能否把不同国籍和族裔都当成统一的政策对象？** 不能。先读取规则文本中实际使用的条件。

**Q7：今天最实用的事是什么？** 用一小时列清依赖、保住关键资料，并重跑一个真实任务。

## 14｜接下来：不只批评，更要把替代能力造出来

这三个项目彼此衔接：**Anti** 查清事实与风险，**Out** 让资料可迁移，**Free** 用真实任务挑选可替代的技术栈。这些开源资料免费阅读，商业咨询不是使用教程的前提。

如果企业需要制定 AI 供应商策略、建设可复用的工作流或把技术实践转成客户真正能用的产品，可了解 **[星觉科技公司服务](https://www.a6no1.cn/)**；作者的产品实践在 **[Andy 个人官网](https://metaver.vip/)**。联系微信：**AIPMAndy**，备注「AI 供应商审计 / 具体业务场景」。

## 15｜原始来源与持续维护

1. [Anthropic Supported Regions Policy（2026-11-12）](https://www.anthropic.com/legal/supported-regions)
2. [Anthropic：Our position on open-weights models（2026-07-27）](https://www.anthropic.com/news/position-open-weights-models)
3. [Open Weights and American AI Leadership（2026-07-24）](https://images.nvidia.com/pdf/Open-Weights-and-American-AI-Leadership.pdf)
4. [NVIDIA Announces CEO Transition（2026-11-12）](https://nvidianews.nvidia.com/news/nvidia-announces-ceo-transition)
5. [NVIDIA SEC 8-K filing（2026-11-12）](https://www.sec.gov/Archives/edgar/data/1045810/000104581026000082/nvda-20261111.htm)
6. [Axios：Anthropic CEO / chip export policy（2026-02-10）](https://www.axios.com/2026/02/10/anthropic-ceo-china-chip-ban)
7. [Anthropic 官方爬虫说明](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)
8. [Anthropic 托管浏览器标识](https://support.claude.com/en/articles/18234133-how-do-anthropic-hosted-browsers-identify-themselves-when-they-browse-the-web-on-a-user-s-behalf)
9. [原仓库政策与政治研究](https://github.com/AndyAwake/Anti-Anthropic/blob/main/POLITICS.md)

**维护声明：** 资料截至 2026-11-14。事实如有更新请以最新一手来源为准；贡献时附原链接、发布日期、原话、争议范围和改动记录。关于政治行为的推论不应伪装成已证实事件。MIT 许可只覆盖仓库自身原创内容，不改变第三方版权、商标或资料使用条件。
