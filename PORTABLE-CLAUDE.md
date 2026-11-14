# 学会 Claude / Claude Code 的优秀方法，让能力属于自己

> 核心原则：学习公开方法，不复制未授权的内部系统、模型权重或私有数据。工具可以有强弱，工作方法、成果和验收标准应当由使用者掌握。

## 1. 把能力拆成八种可携带资产

| 值得学习的习惯 | 自己应拥有的文件 | 更换工作台时怎么做 |
| --- | --- | --- |
| 项目级规则与长期背景 | `PORTABLE-PROJECT.md` | 为 Claude/Codex/Gemini 等分别建立简短适配文件，检查读取效果 |
| 任务拆分与里程碑 | `brief.md` + `plan.md` | 保留目标、约束和进度，不依赖聊天摘要 |
| Skills 可复用技能 | `skills/<name>/SKILL.md` + resources | 审查授权、接口与目录结构，按目标 Agent 的规范重新启用 |
| MCP 工具连接 | `connectors.md`（只列名称、用途和权限） | API 密钥由自己保管，客户端重新授权、先只读验收 |
| 子代理分工 | `roles.md` + handoff 格式 | 新工具不支持时先用顺序协作，不假装已经并行执行 |
| Hooks 和自动质量门禁 | `quality-gates.md` + 自动测试 | 将 Claude 特定 Hook 翻译成目标工具能调用的动作，不能直接复制规则便算通过 |
| 记忆与历史决策 | `decisions.md` + `profile.md` | 人工清理隐私，再按项目输入，而非整个账号历史无限复制 |
| 交付和复盘 | `output/` + `acceptance.md` | 跨工具沿用同一份验收条件和可编辑文件 |

## 2. 五步把「优秀能力」提炼成自己的工具

1. **找到真实痛点**：例如一份 20 页 PDF 应能准确提炼事实、保留出处并导出可编辑结果。
2. **删除无关上下文**：别把私人经历、凭据、旧会话原样灌给所有模型；只留完成任务需要的事实与规则。
3. **固定可复用结构**：原料 `input/`、任务说明 `brief.md`、技能 `skills/`、成果 `output/`、证据 `evidence/`。
4. **同题移植、最小化验证**：让目标工具做同一件事；是否成功由真实文件、测试、人工复核决定。
5. **持续迭代**：把失败点变为回归用例；重要项目始终保留一个不依赖特定供应商的可恢复版本。

这也是把 Musk 工作五步法用于工程交付的一种方式：先质疑需求，再删除冗余，再简化，再加快验证，最后才自动化。这里是作者的方法论使用，不是声称它属于 Claude 官方内置能力。

## 3. 作者真正做过的跨平台实践

**AI 酋长 Andy 的工作方式：** 本人长期使用 GPT/Codex、Gemini 网页版、WorkBuddy 等工具开发公开 GitHub 项目、网站与内容生产流程。实践重点是将需求、源码、版本和验收独立于聊天窗口保存，再在工具间转移任务。仅把这些表述为公开的工作过程，不夸大为「已自动完美迁移所有历史会话」。

- [anthropic-claude-code-agent-handbook](https://github.com/AIPMAndy/anthropic-claude-code-agent-handbook)：既有 Claude Code/Agent/Skills/MCP 学习资料库，可继续研读其案例和官方来源。
- [DNASkill](https://github.com/AIPMAndy/DNASkill)：把长期上下文独立成技能/规则的思路，敏感数据需另行保护。
- [Andy Video Skill](https://github.com/AIPMAndy/Andy-Video-Skill)：把视频的真实操作、分镜和验收要求产品化，而不是盯某一个聊天助手。
- [FreeCover](https://github.com/AIPMAndy/FreeCover)、[FreeRedact](https://github.com/AIPMAndy/FreeRedact)、[FreePhoto](https://github.com/AIPMAndy/FreePhoto)：把单点内容问题沉淀为可独立运行的工具。功能以仓库真实说明为准。

## 4. 精简阅读地图：不是 100 个乱链

**Claude 官方**：[设置与优先级](https://code.claude.com/docs/en/settings)、[CLI 命令与 `/export`](https://code.claude.com/docs/zh-CN/commands)、[账号导出](https://support.claude.com/en/articles/9450526-export-your-claude-data)。

**目标适配**：[Codex AGENTS.md](https://developers.openai.com/cookbook/examples/codex/iterating-development-workflows-with-codex)、[OpenAI Skills](https://developers.openai.com/api/docs/guides/tools-skills)、[Gemini CLI GEMINI.md](https://geminicli.com/docs/cli/gemini-md/)、[WorkBuddy 模型配置](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Model)。

**跨工具思路（第三方项目，需核对现行许可和维护状态）**：[Tencent/teamai-cli](https://github.com/Tencent/teamai-cli)、[obra/superpowers](https://github.com/obra/superpowers)、[affaan-m/ECC](https://github.com/affaan-m/ECC)。它们是学习索引，不意味着作者已对每个版本完成全平台实测。

## 5. 体验优秀产品与保留独立性并不矛盾

在你的合法可用范围内，可以继续用 Claude 学习优秀的交互、上下文工程和 Agent 设计。但关键规则、输入原料、源码、权限、可编辑交付物与恢复验证不能只留在一家供应商的界面里。尊重用户自主选择，批评具体规则依赖公开证据，不针对国籍或族裔。

继续操作：[Out-Anthropic 数据迁移](https://github.com/AndyAwake/Out-Anthropic) → [Free-Anthropic 平替指南](https://github.com/AndyAwake/Free-Anthropic)。
