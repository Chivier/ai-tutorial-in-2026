# API Key 是什么，怎么安全保存

API Key 是给程序用的访问凭证。网页登录 Claude、ChatGPT、Kimi 或 DeepSeek，是人在浏览器里使用产品；API Key 则是让脚本、开发工具、Agent 或自动化程序代表你调用模型。

先记住三条规则：

- API Key 不是网页登录密码，也不等于会员订阅。
- API Key 会产生用量费用，泄露后别人可能花你的额度。
- 不要把 API Key 写进 Markdown、截图、GitHub 仓库或聊天记录。

最常见的保存方式是环境变量。macOS / Linux 终端里可以临时这样设置：

```bash
export OPENAI_API_KEY="替换成你的 OpenAI API Key"
export ANTHROPIC_API_KEY="替换成你的 Claude API Key"
export MOONSHOT_API_KEY="替换成你的 Kimi API Key"
export DEEPSEEK_API_KEY="替换成你的 DeepSeek API Key"
export OPENROUTER_API_KEY="替换成你的 OpenRouter API Key"
```

临时设置只对当前终端窗口生效。后面正式配置开发工具时，再把需要长期使用的变量写入对应工具推荐的位置。

一个实用习惯是：每个平台单独建 Key，每个用途单独建 Key。比如「学习教程」「Claude Code」「自己的小项目」分别用不同 Key。以后某个 Key 泄露或不用了，直接删除它，不影响其他用途。
