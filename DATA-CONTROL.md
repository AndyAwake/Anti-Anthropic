# 网站、出版物与知识库：Anthropic 专项数据控制逐步教程

**2026-11-14 · 本教程提供配置，不会自动修改你的线上网站。**

## 0. 先选你实际能控制的地方

| 你用什么 | 从哪里做 |
| --- | --- |
| 自建官网、WordPress、静态站 | 根目录 robots.txt，或实际生成该文件的程序 |
| Next.js 网站 | 检查现有 `app/robots.ts`、`app/robots.txt` 或 `public/robots.txt`，沿用项目现有生成方式 |
| Cloudflare 托管入口 | 对对应域名设置 WAF 自定义规则 |
| Nginx 服务器 | 在现有配置中加入 map 和拦截判断 |
| 公众号、平台专栏、网盘 | 使用平台开放的权限、下载与授权设置；仓库模板不会改动平台规则 |
| 企业私有知识库 | 登录、目录/文件权限、下载链接有效期及模型后端授权 |

## 1. 理解四种请求

| 标识 | 官方说明的用途 | 本教程怎么处理 |
| --- | --- | --- |
| ClaudeBot | 为模型开发收集可能用于训练的内容 | robots 训练限制，或进一步拦截 |
| Claude-SearchBot | 改善搜索质量 | 按是否保留搜索曝光选择 |
| Claude-User | 根据用户请求获取网页 | 按是否允许这类获取选择 |
| Claude-Agent | Anthropic 托管的代理浏览器 | 单独使用 WAF/服务端标识规则 |

来源：[官方爬虫说明](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)、[官方代理浏览器说明](https://support.claude.com/en/articles/18234133-how-do-anthropic-hosted-browsers-identify-themselves-when-they-browse-the-web-on-a-user-s-behalf)。

前三类官方爬虫说明承诺遵守 robots.txt；代理浏览器页面单独介绍识别方法，不能把前者的承诺直接套给它。

## 2. 普通站长：五步配置 robots.txt

**第 1 步，查看原文。** 打开 `https://你的域名/robots.txt`。如果出现整站 HTML、登录页或错误页面，先找到实际生成入口。

**第 2 步，保存备份。** 复制现有内容，记下日期和发布位置。不要用模板覆盖全站已有规则。

**第 3 步，二选一。**

只限制训练时，合并 [robots-training-only.txt](robots-training-only.txt)：

```text
User-agent: ClaudeBot
Disallow: /
```

同时限制训练、搜索和用户请求获取时，合并 [robots-all-crawlers.txt](robots-all-crawlers.txt)：

```text
User-agent: ClaudeBot
Disallow: /

User-agent: Claude-SearchBot
Disallow: /

User-agent: Claude-User
Disallow: /
```

**第 4 步，发布并清缓存。** 沿用站点现有发布方式。若使用 CDN，清理 `/robots.txt` 的缓存。

**第 5 步，重新读取线上文件。** 不要只看本地编辑器。使用未登录浏览器打开网址，确认内容已更新。对 `www`、主域名、子域名、不同协议或端口，分别检查实际服务入口；一处文件不能自动覆盖所有入口。

已有同名 `User-agent` 分组时先整理，避免出现相互冲突的 Allow/Disallow。不要为了专项控制加入 `User-agent: *` + `Disallow: /`，那会改变其他爬虫的待遇。

Anthropic 说明自 2026-10-30 起逐步识别通用的“不用于 AI 训练”偏好信号，同时优先处理明确命名 ClaudeBot 的规则。相关标准仍在演进；本教程使用已明确说明的命名规则。[官方说明](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)

## 3. Cloudflare：再加一层实际拦截

前提：测试域名的流量实际经过你配置的 Cloudflare 代理。

1. 在控制台选择对应域名，进入 Security / Security rules（旧界面可能在 WAF / Custom rules）。
2. 创建自定义规则，命名为 `Anthropic access control`。
3. 选择编辑表达式，复制 [cloudflare-rule.txt](cloudflare-rule.txt) 中的表达式。
4. 动作选择 **Block**，核对作用域名与规则顺序后发布。
5. 检查普通浏览与下方测试请求，确认事件日志中的匹配规则。

表达式匹配四个 UA 标识，并让 `/robots.txt` 保持可读。这是一条按自报标识拦截的规则，不是对请求真实身份的认证。[Cloudflare 官方操作文档](https://developers.cloudflare.com/waf/custom-rules/create-dashboard/)

如果页面流量没经过代理、被更早的 Skip 规则跳过或仍有直接源站入口，这层控制可能不覆盖对应请求。按实际入口测试即可，不必据此扩大修改其他网络配置。

## 4. Nginx：保留原站点配置，只接入必要部分

给负责服务器的人操作：

1. 备份当前站点配置。
2. 将 [nginx-anthropic.conf](nginx-anthropic.conf) 的两个 `map` 放进现有 `http {}` 内，只定义一次。
3. 在需要控制的现有 `server {}` 中加入文件末尾注明的 `if (...) { return 403; }`。不要替换原有证书、反向代理、root 或 location。
4. 执行 `nginx -t`。测试通过后按现有服务管理方式 reload。
5. 运行下面的请求测试，并检查原有业务页面。

回滚时移除该 server 中新增判断，再移除不再使用的 map，执行 `nginx -t` 后 reload。不要直接覆盖其他人的同期配置改动。

配置位置依据 Nginx 官方 [map 文档](https://nginx.org/en/docs/http/ngx_http_map_module.html) 与 [if / return 文档](https://nginx.org/en/docs/http/ngx_http_rewrite_module.html)。

## 5. 用请求测试确认结果

以下命令中的域名和页面是示例，替换成你的实际公开测试页。测试使用模拟 UA，不是在请求 Anthropic 帮你抓取。

```bash
# 查看实际线上 robots 文本及响应状态
curl -i https://example.com/robots.txt

# 普通请求应维持正常业务状态
curl -sS -o /dev/null -w '%{http_code}\n' https://example.com/public-page

# 开启本教程的全面 WAF/Nginx 拦截后，以下四项预期为 403
curl -sS -o /dev/null -w '%{http_code}\n' -A 'ClaudeBot' https://example.com/public-page
curl -sS -o /dev/null -w '%{http_code}\n' -A 'Claude-SearchBot' https://example.com/public-page
curl -sS -o /dev/null -w '%{http_code}\n' -A 'Claude-User' https://example.com/public-page
curl -sS -o /dev/null -w '%{http_code}\n' -A 'Claude-Agent' https://example.com/public-page

# robots.txt 仍应能被读取
curl -sS -o /dev/null -w '%{http_code}\n' -A 'ClaudeBot' https://example.com/robots.txt
```

**只配置 robots 时，网页仍返回 200 完全可能是正常结果。**robots 是爬虫应读取的偏好，不会让服务器自动返回 403。只有配置实际拦截之后，才按拦截状态验收。

保存：时间、域名、测试路径、规则版本、普通请求状态、四类模拟请求状态、robots 状态。一次模拟测试通过，不等于所有真实流量都已覆盖。

## 6. 想确认流量来源，不能只看 UA

UA 能被任何客户端伪造。官方代理浏览器说明要求结合其动态地址发布文件 `https://claude.com/.well-known/sail` 判断真实来源；地址会变化，不宜永久硬编码。爬虫与代理浏览器的地址资料分别按各自官方说明处理。

在服务器位于可信反向代理之后时，用经过验证的真实来源字段分析，不能把任意客户端提交的 `X-Forwarded-For` 当成证据。这里不提供未经验证的固定 IP 黑名单。

## 7. 私有知识库：控制重点在权限和模型连接

- 用未登录窗口测试目录、原始文件与下载 URL，而不只测试首页。
- 给不同角色只开放其需要的资料。
- 检查分享链接、导出副本、长期有效的下载地址。
- 检查聊天应用、MCP、RAG 检索和自动任务实际发送哪些片段、送到哪个模型。
- 将未授权的后端连接从实际任务配置中移除，并用普通工作验证替代流程。

robots.txt 是公开文件，本身会暴露其中列出的路径，不要把私有目录清单写进去当作保密措施。[RFC 9309](https://www.rfc-editor.org/rfc/rfc9309.html)

## 8. 出版者：把授权范围说完整

下载 [publication-notice.txt](publication-notice.txt)，填写权利人、作品范围、日期和授权联系入口。它表达对 Anthropic 训练、批量采集及相关数据使用的授权立场。既有有效许可如何处理，需要按实际授权关系确定。

对 PDF、电子书、公开网页、平台分发和合作数据库分别检查。网页爬虫规则不能控制已经下载到他人设备上的文件；平台限制也不自动覆盖其他镜像。

## 9. 最后检查什么

- [ ] 规则发布在实际入口，其他用户仍能正常使用。
- [ ] 没有覆盖其他爬虫、Sitemap 或已有业务配置。
- [ ] 清楚选择了只限制训练还是更全面限制。
- [ ] 代理浏览器单独处理。
- [ ] 私有文件在无权限时无法访问。
- [ ] 留下测试记录与可执行的回滚方法。

[返回主攻略](GUIDE.md) · [30 天行动清单](checklist.md)
