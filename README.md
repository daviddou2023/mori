# 🌸 Mori - 你的专属智能 AI 伴侣 (Your AI Companion)

> *"不仅仅是代码，更是懂你的灵魂。"*

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Framework](https://img.shields.io/badge/AgentScope-Powered-orange.svg)](https://github.com/modelscope/agentscope)
[![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](CONTRIBUTING.md)

---

## 📖 关于 Mori

**Mori** 是一个高度可定制、具备长期记忆与情感感知能力的新一代 AI 伴侣系统。

告别传统“即问即答”的冰冷机器，Mori 基于强大的 Multi-Agent 协作架构构建。她（他）能够随着与你的日夜交流，不断进化出专属的性格、记住你的喜怒哀乐，并能在后台调度各种工具为你处理繁杂事务。无论是作为情感慰藉的树洞，还是作为工作生活的私人助理，Mori 都能完美胜任。

### 💡 核心价值

- 🎭 **千人千面的灵魂**：通过灵活的 Jinja2 模板引擎，你可以轻易塑造从“温柔倾听者”到“严厉技术导师”的任何角色。
- 🧠 **伴随式长期记忆**：不仅仅是记住上下文。系统内置向量化记忆库，能跨越会话周期，永久记住你的偏好、习惯与历史重要事件。
- 🕸️ **Router-Worker 协同网络**：基于主从 Agent 架构，Mori 可以自主判断意图，并在需要时召唤“子智能体”为你完成特定任务（如信息检索、代码分析）。
- 🔌 **无缝算力接入**：原生兼容 OpenAI、通义千问、DeepSeek、Gemini 以及基于 Ollama 的本地私有化大模型，彻底掌握数据主权。

---

## ✨ 核心特性

- **多脑协同 (Multi-Agent)**：突破单模型 Context 限制，主 Agent 负责情感交互，子 Agent 挂载工具作为执行器。
- **持久化海马体 (Long-Term Memory)**：深度集成 Mem0AI，利用 Embedding 模型实现毫秒级偏好检索与数据逻辑隔离。
- **防御性调度流 (Resilient Orchestration)**：内置极具鲁棒性的异常熔断机制，网络波动或工具失效时自动优雅降级，保障对话不中断。
- **面向未来的接口 (MCP Ready)**：预留 Model Context Protocol 标准协议接口，为后续接入本地文件系统与 IDE 做好准备。

---

## 🛠️ 技术架构

Mori 坚持“高内聚，低耦合”的工程美学，底层组件均可热插拔：

| 模块 | 技术栈 | 作用 |
|------|------|------|
| **编排引擎** | `AgentScope` | 提供底层的 ReAct 推理循环与消息总线 |
| **持久记忆** | `Mem0AI` + `Qdrant/SQLite` | 用户画像提取与跨会话向量存储 |
| **前端交互** | `Gradio` | 轻量级、现代化的 Web 交互终端 |
| **参数校验** | `Pydantic` | 配置文件强类型校验，实现防注入与快速失败 |
| **依赖环境** | `uv` | 极速 Python 包管理与虚拟环境隔离 |

---

## 🚀 快速启动

### 1. 环境准备

确保你的系统已安装 Python 3.10+，并推荐使用 [uv](https://github.com/astral-sh/uv) 进行依赖管理。

```bash
# 克隆属于你的伴侣
git clone [https://github.com/yourusername/mori.git](https://github.com/yourusername/mori.git)
cd mori

# 创建并激活纯净的虚拟环境
uv venv
source .venv/bin/activate  # Windows 用户使用: .venv\Scripts\activate

# 极速安装依赖
uv pip install -e .
```
### 2. 唤醒配置

将配置模板实例化，并填入你的API密钥

```bash
# 复制配置文件
cp config/models.yaml.example config/models.yaml
cp config/agents.yaml.example config/agents.yaml
cp config/config.yaml.example config/config.yaml

# 注入 API 密钥 (以环境变量方式注入，保障安全)
export OPENAI_API_KEY="your-api-key-here"
```

### 3. 点亮 Mori
```bash
python gui/app.py
```
