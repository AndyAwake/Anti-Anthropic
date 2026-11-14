# Anti-Anthropic

## 反制 Anthropic：AI 技术主权、数据保护与商业竞争保姆级攻略

**V2.0 · 2026 年 11 月 14 日 · AndyAwake / 星觉科技**

大部分中国的普通人和普通公司，只想安静地当一个地球成员，把自己的事业经营好。

我们尊重 Anthropic 的技术能力与战略执行，也明确反对它推动的对华技术限制。技术上虚心学习，商业上建立替代，数据上实行对等控制，把回应落实到产品、采购、授权与公共政策讨论中。

**核心主张：学习它的能力，减少对它的依赖，守住我们的数据与选择权。**

## 从这里开始

| 你想了解什么 | 入口 |
| --- | --- |
| 为什么要做，普通人和公司具体怎么做 | [保姆级完整攻略](GUIDE.md) |
| 它在美国怎样组织资金、游说、议题与人脉 | [美国政治运作详解](POLITICS.md) |
| 网站、出版物和知识库怎样设置专项控制 | [逐步操作与验收](DATA-CONTROL.md) |
| 30 天怎样落地 | [行动清单](checklist.md) |
| 每个关键事实的依据 | [来源与核验说明](sources.md) |
| 产品、服务和网站 | [星觉科技](COMPANY.md) |

## 本版的三个重点

- **11 月 12 日地区政策**：覆盖人员所在地、实体注册地与总部、控制关系，以及 API、云平台和授权转售渠道。[官方政策](https://www.anthropic.com/legal/supported-regions)
- **美国政治运作**：分开解释公司政策捐款、员工 PAC、个人捐款、Super PAC 广告、游说与诉讼。不能把它们混成一笔钱。[官方捐款公告](https://www.anthropic.com/news/donation-public-first-action)、[FEC 员工 PAC 登记](https://www.fec.gov/data/committee/C00946111/)
- **游说原始数据**：公司自报 Q1 156 万、Q2 197 万、Q3 211 万美元，合计 **564 万美元**；附 [30 份季度申报索引](lobbying-filings-2026.csv)。[Q1](https://lda.gov/filings/public/filing/90cc74f3-1bd5-40c1-bba0-8d6e00fbb200/print/)、[Q2](https://lda.gov/filings/public/filing/812e5787-90df-48ef-a801-500468d63047/print/)、[Q3](https://lda.gov/filings/public/filing/d0b9f104-2212-4fcc-8304-5c978c366768/print/)

## 今天先做三件事

1. **找清数据终点**：记下 AI 应用、实际模型、插件和知识库连接。WorkBuddy 等工作台支持自定义后端，界面名称不能替代对实际供应商的确认。[模型配置说明](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Model)
2. **给自有网站选规则**：只限制训练，或同时限制搜索和用户请求抓取。需要进一步限制 `Claude-Agent` 浏览器流量时，使用服务端或 WAF 规则。[操作教程](DATA-CONTROL.md)
3. **用实际工作验证替代**：优先测试能正常使用的国内模型与工作台；账号和地区支持时，加入 Gemini 与 OpenAI。用 [30 个任务表](model-evaluation.csv) 记录质量、返工时间、费用和数据去向。

## 工具下载

| 文件 | 用途 |
| --- | --- |
| [robots-training-only.txt](robots-training-only.txt) | 限制 ClaudeBot 训练抓取 |
| [robots-all-crawlers.txt](robots-all-crawlers.txt) | 限制三类官方爬虫/获取器 |
| [cloudflare-rule.txt](cloudflare-rule.txt) | 按标识限制四类请求，保留 robots.txt 可读 |
| [nginx-anthropic.conf](nginx-anthropic.conf) | 在现有站点按需接入的服务端示例 |
| [publication-notice.txt](publication-notice.txt) | 给自有出版物表达专项授权立场的文字示例 |
| [model-evaluation.csv](model-evaluation.csv) | 30 个替代任务与结果记录空表 |
| [lobbying-filings-2026.csv](lobbying-filings-2026.csv) | 核查美国联邦游说申报与金额口径 |

[下载整个资料包 ZIP](https://github.com/AndyAwake/Anti-Anthropic/archive/refs/heads/main.zip)

robots.txt 表达访问偏好；WAF 和服务端规则阻止匹配条件的请求；私有资料仍由登录与权限保护。具体配置与检查见 [教程](DATA-CONTROL.md)。

## 星觉科技 · 用 AI 帮助企业增长，助力个人成长

- **产品**：[IPClaw 专家 Agent 网络](https://metaver.vip/ipclaw)、[MDskill / ChiefMusic / 座右铭](https://metaver.vip/products)、[醒觉知识库](https://kb.metaver.vip/s/19ea264c-d09c-435b-9d0d-a9d0cd1c9e7c)。
- **服务**：高管陪跑、求职陪跑、职场人副业陪跑、个人 AI + IP 陪跑、企业 AI + IP 获客。[了解服务](https://www.a6no1.cn/services)
- **网站**：[Andy 官网](https://metaver.vip) · [星觉科技服务站](https://www.a6no1.cn/services) · [醒觉社](https://www.a6no1.cn/awake) · [AndyAwake 开源站](https://github.com/AndyAwake)。
- **联系**：微信 **AIPMAndy**，可备注「Anti-Anthropic + 你的具体需求」。

## 参与与许可证

欢迎提交有日期的一手来源、能复现的工具改进和实际替代案例。讨论具体政策与商业行为，不发布个人隐私，不把公司指控写成司法结论。

[MIT](LICENSE) · AndyAwake / 星觉科技
