# Anti-Anthropic

## 反制 Anthropic：AI 技术主权、数据保护与商业竞争保姆级攻略

**研究版本 V1.0 · 2026 年 11 月 14 日**

AndyAwake / 星觉科技的第一个开源项目。

核心战略：技术上学习 Anthropic，商业上减少依赖，数据上守住边界，政策上倡导对等与公平。

## 项目资料

- [完整攻略](GUIDE.md)
- [30 天企业执行清单](checklist.md)
- [仅限制训练抓取的 robots.txt 模板](robots-training-only.txt)
- [同时限制训练、搜索和用户请求抓取的 robots.txt 模板](robots-all-crawlers.txt)

## 快速使用

第一档：只限制模型训练抓取，保留搜索可见性（更适合公开官网）。

```text
User-agent: ClaudeBot
Disallow: /
```

第二档：同时限制 Anthropic 的训练、搜索和用户请求抓取（适合有特别授权要求的内容）。

```text
User-agent: ClaudeBot
Disallow: /

User-agent: Claude-SearchBot
Disallow: /

User-agent: Claude-User
Disallow: /
```

将选定模板的内容合并到网站根目录的 `robots.txt`，保留原有的其他规则。

两种方式都是向遵守规则的爬虫表达访问限制，不是无法绕过的安全屏障。第二档还会降低 Claude 对网站内容的发现和引用能力。对于真正的商业机密，必须再使用登录验证、访问权限及服务端保护。

此外，Anthropic 还公布了用于代理浏览器的 `Claude-Agent` 标识，这类访问需要独立识别和管理，不能误以为拦截上述三个爬虫就完成了全部控制。

## 参与项目

欢迎通过 Issues 和 Pull Requests 补充一手资料链接、可复现的工具案例和模型替代实践。请写明来源与日期。

有自主数据、有替代模型、有公开证据、有开源工具、有稳定获客能力。

让技术能力和商业实力成为最有说服力的回应。

## 许可证

[MIT](LICENSE) · AndyAwake / 星觉科技
