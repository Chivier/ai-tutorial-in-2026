# 各平台 API Key：OpenAI / Claude / Kimi / DeepSeek

除了 OpenRouter，也可以直接申请各家官方平台的 API Key。直接用官方 Key 的好处是路径更短、平台能力更完整；缺点是每家都有自己的账号、计费和配置方式。

| 平台 | 对应网页产品 | 常用环境变量 | 常见 Base URL / 接入方式 |
| --- | --- | --- | --- |
| OpenAI Platform | ChatGPT | `OPENAI_API_KEY` | 官方 SDK 默认读取，不需要改 base URL |
| Anthropic Console | Claude | `ANTHROPIC_API_KEY` | 使用 Anthropic SDK 或支持 Claude API 的工具 |
| Kimi 开放平台 / Moonshot AI | Kimi | `MOONSHOT_API_KEY` | `https://api.moonshot.cn/v1` |
| DeepSeek Platform | DeepSeek | `DEEPSEEK_API_KEY` | `https://api.deepseek.com` |
| OpenRouter | 多家模型聚合 | `OPENROUTER_API_KEY` | `https://openrouter.ai/api/v1` |

这些入口容易随平台调整，正式操作时以官方页面为准：

- OpenAI API Keys: <https://platform.openai.com/api-keys>
- Claude API Keys: <https://platform.claude.com/settings/keys>
- Kimi API Keys: <https://platform.kimi.com/console/api-keys>
- DeepSeek API Keys: <https://platform.deepseek.com/api_keys>
- OpenRouter API Keys: <https://openrouter.ai/settings/keys>

如果一个工具让你填写「provider」「base URL」「model」：

- 选 OpenAI 官方时，通常只填 `OPENAI_API_KEY` 和模型名。
- 选 Claude 官方时，不要强行填 OpenAI 兼容地址，优先看工具是否支持 Anthropic / Claude provider。
- 选 Kimi、DeepSeek 或 OpenRouter 时，很多工具可以走 OpenAI 兼容接口，但要同时填对 API Key、base URL 和模型名。

排错时先看四件事：Key 有没有复制完整、账户有没有余额或额度、base URL 是否填对、模型名是否是该平台实际支持的名字。
