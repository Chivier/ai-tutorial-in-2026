# 第 4 部分 · 跨越台阶：准备开发环境

## 什么是命令行 / 终端

本章会用非技术语言解释命令行和终端，帮助读者消除上手恐惧。

## 安装终端并认识基本操作

本章会带读者安装或打开终端，并练习最基本的命令行操作。

## 安装 Node.js

本章会说明 Node.js 是什么、为什么很多 AI 工具需要它，以及如何安装。

## 安装 Git

本章会解释 Git 的用途，并带读者完成安装和基本验证。

## API Key 是什么，怎么安全保存

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

## OpenRouter：一个 Key 调多家模型

OpenRouter 是模型聚合平台。你只需要申请一个 `OPENROUTER_API_KEY`，就可以在同一个接口里选择不同厂商的模型，适合教程阶段快速试模型、比较效果和控制成本。

典型流程是：

1. 打开 OpenRouter，创建 API Key。
2. 给账户充值或确认免费额度。
3. 在模型列表里复制要用的 model id。
4. 在工具里设置 `OPENROUTER_API_KEY`，必要时把 base URL 改成 `https://openrouter.ai/api/v1`。

如果一个工具支持 OpenAI 兼容接口，通常可以这样理解配置项：

| 配置项 | 填什么 |
| --- | --- |
| API Key | `OPENROUTER_API_KEY` |
| Base URL | `https://openrouter.ai/api/v1` |
| Model | 从 OpenRouter 模型页复制的 model id |

最小 curl 例子如下。把 `~openai/gpt-latest` 换成你实际选择的模型也可以。

```bash
curl https://openrouter.ai/api/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -d '{
    "model": "~openai/gpt-latest",
    "messages": [
      {"role": "user", "content": "用一句话解释 API Key 是什么"}
    ]
  }'
```

OpenRouter 的好处是统一入口，缺点是又多了一层平台规则。稳定长期使用某一家模型时，也可以改用那家官方 API Key。

## 各平台 API Key：OpenAI / Claude / Kimi / DeepSeek

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

## 检查清单：确认环境就绪

本章会提供一个命令行、Node.js、Git、API Key 和模型平台配置的环境检查清单。
