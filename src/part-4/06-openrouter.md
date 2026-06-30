# OpenRouter：一个 Key 调多家模型

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
