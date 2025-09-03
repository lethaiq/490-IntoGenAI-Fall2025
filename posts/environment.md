---
layout: post
title:  "Environment Setup!"
nav_exclude: true
---

# Environment Setup

### Install Ollama: [https://ollama.com/download](https://ollama.com/download)

```jsx
ollama serve
```

### Download Qwen3 : [https://docs.unsloth.ai/basics/qwen3-how-to-run-and-fine-tune](https://docs.unsloth.ai/basics/qwen3-how-to-run-and-fine-tune)

```jsx
ollama run hf.co/unsloth/Qwen3-8B-GGUF:UD-Q4_K_XL
```

### Download Llama2

```jsx
ollama pull llama2
```

### Download Qwen 2.5 Coder

```bash
ollama pull hf.co/unsloth/Qwen2.5-Coder-14B-Instruct-128K-GGUF:Q4_K_M
```

### Download Phi-4 Mini

```bash
ollama run hf.co/unsloth/Phi-4-mini-reasoning-GGUF:Q4_K_XL
```

### Download Nomic Text Embedding Encoder

```jsx
ollama pull nomic-embed-text
```

### Download Gemma 3 27B

```jsx
ollama pull hf.co/unsloth/gemma-3-27b-it-GGUF:Q4_K_M
```

### Install Chroma ([https://www.trychroma.com/](https://www.trychroma.com/))

```jsx
pip install chromadb
```

### Test Your Ollama Deployment

```bash
curl http://localhost:11434/api/generate -d '{ "model": "llama2", "prompt": "Who are you?", "stream": false }'
```

### Install Docker: [https://www.docker.com/get-started/](https://www.docker.com/get-started/)

### Install Open WebUI: https://github.com/open-webui/open-webui

```jsx
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

### Get [OpenRouter.AI](http://OpenRouter.AI) Key

### Integrating [OpenRouter.AI](http://OpenRouter.AI) with WebUI
First make sure you enable "Direct Connections" first in the "Admin" setting.
![Screenshot 2025-09-03 at 4.12.05 PM.png](Environment%20Setup%2024891c1b1a5d8085833eed36af691ded/Screenshot 2025-09-03 at 4.12.05 PM.png)
Then, you can now setup a direct connection with OpenRouter below in "User" setting.
![Screenshot 2025-07-26 at 8.41.21 PM.png](Environment%20Setup%2024891c1b1a5d8085833eed36af691ded/Screenshot_2025-07-26_at_8.41.21_PM.png)
If done successfully, you should be able to choose an available model on OpenRouter in the "Direct" mode. **❗❗❗ Make sure you know how much each of these models charge ($$) before starting chatting with them.**
![Screenshot 2025-09-03 at 4.15.38 PM.png](Environment%20Setup%2024891c1b1a5d8085833eed36af691ded/Screenshot 2025-09-03 at 4.15.38 PM.png)

### Chatting with Commercial LLMs
You can try chatting with [GPT-4o-mini](https://openrouter.ai/openai/gpt-4o-mini-search-preview) with WebUI ***(❗❗❗This will incur cost (~$0.03). There are other free models that you can use as well, but rate is very limited)***

![Screenshot 2025-07-26 at 8.43.06 PM.png](Environment%20Setup%2024891c1b1a5d8085833eed36af691ded/Screenshot_2025-07-26_at_8.43.06_PM.png)

### Keep track of how much you spend on OpenRouter.AI: 
[https://openrouter.ai/activity](https://openrouter.ai/activity)

![Screenshot 2025-07-26 at 8.44.03 PM.png](Environment%20Setup%2024891c1b1a5d8085833eed36af691ded/Screenshot_2025-07-26_at_8.44.03_PM.png)

### Important Open WebUI Settings
1. **Random Seed**
2. **Temperature**
3. **top_k**
4. **top_p**


# Benchmarking Your Local Ollama Models
Benchmarking is important. This is to ensure that your local environment (laptop, computing instances you have access to, desktop) is sufficient for the course. A comfortable generation speed on your local environment would be around **7-10 tokens/second**. For the sufficiency of the course, make sure that you can obtain **at least 5 tokens/second** on a reasoning-enabled model such as ``hf.co/unsloth/Phi-4-mini-reasoning-GGUF:Q4_K_XL`` or ``hf.co/unsloth/Qwen3-8B-GGUF:UD-Q4_K_XL``. 

Follow the instruction from [Ollama Benchmark](https://github.com/larryhopecode/ollama-benchmark) and print out the report. An example is below is on a Macbook Air M3. Make sure you run the benchmark when your local environment is **not** overloaded and that you are **not** currently running any Ollama models. 
```
        Model: llama2:latest
        Performance Metrics:
            Prompt Processing:  507.99 tokens/sec
            Generation Speed:   20.12 tokens/sec
            Combined Speed:     21.05 tokens/sec

        Workload Stats:
            Input Tokens:       49
            Generated Tokens:   1014
            Model Load Time:    0.03s
            Processing Time:    0.10s
            Generation Time:    50.41s
            Total Time:         50.54s
```

```
        Model: hf.co/unsloth/Qwen3-8B-GGUF:UD-Q4_K_XL
        Performance Metrics:
            Prompt Processing:  181.02 tokens/sec
            Generation Speed:   10.26 tokens/sec
            Combined Speed:     10.35 tokens/sec

        Workload Stats:
            Input Tokens:       25
            Generated Tokens:   2820
            Model Load Time:    0.14s
            Processing Time:    0.14s
            Generation Time:    274.86s
            Total Time:         275.14s
```

```
        Model: hf.co/unsloth/Phi-4-mini-reasoning-GGUF:Q4_K_XL
        Performance Metrics:
            Prompt Processing:  171.61 tokens/sec
            Generation Speed:   21.01 tokens/sec
            Combined Speed:     21.05 tokens/sec

        Workload Stats:
            Input Tokens:       6
            Generated Tokens:   2525
            Model Load Time:    0.03s
            Processing Time:    0.03s
            Generation Time:    120.19s
            Total Time:         120.25s
```

Interesting read on how to optimize Ollama on your local environment: [How to Use Ollama Efficiently](https://www.arsturn.com/blog/handle-high-memory-usage-in-ollama-effectively). Basically, make sure you know what models are currently being served/run. Running multiple models at the same time will make your inference much slower.