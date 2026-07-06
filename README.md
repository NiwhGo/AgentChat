<div align='center'>
    <h1>AgentChat</h1>
    <p><b>一个基于大模型的现代化智能对话系统</b></p>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/python-3.12+-blue.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python Version" />
  <img src="https://img.shields.io/badge/vue-3.4+-4FC08D.svg?style=for-the-badge&logo=vue.js&logoColor=white" alt="Vue Version" />
  <img src="https://img.shields.io/badge/fastapi-0.115+-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/license-MIT-green.svg?style=for-the-badge" alt="License" />
</div>

---

## 目录

- [一、项目简介](#一项目简介)
- [二、功能特性](#二功能特性)
- [三、技术栈](#三技术栈)
- [四、快速开始](#四快速开始)
- [五、部署指南](#五部署指南)
- [六、许可证](#六许可证)

---

## 一、项目简介

AgentChat 是一个现代化的智能对话系统，基于大语言模型构建，提供了丰富的AI对话功能。系统采用前后端分离架构，支持多种AI模型、知识库检索、工具调用、MCP服务器集成等高级功能。

### 核心亮点

- 🎯 **多模型支持**: 支持通义千问、DeepSeek、Kimi 等多种大语言模型
- 🔧 **工具调用**: 支持 Function Call、联网搜索、知识库检索等工具
- 🔌 **MCP 生态**: 支持 MCP Server 扩展，可对话式生成 MCP Server
- 💾 **记忆系统**: 三层记忆架构（短期/历史/长期），实现个性化对话
- 📚 **知识库**: 支持上传文档构建专属知识库
- 🎨 **多模态**: 支持图片理解、文生图等多媒体交互
- 🚀 **一键部署**: 支持 Docker 一键部署，开箱即用

---

## 二、功能特性

### 对话功能
- 💬 多轮对话支持
- 🔄 对话上下文管理
- 🖼️ 图片上传与理解
- 🎨 文生图能力
- 📎 文件上传与分析

### 智能体系统
- 🤖 智能体创建与管理
- 🎯 角色设定与 Prompt 工程
- 🔗 工具绑定
- 📚 知识库绑定
- 🔌 MCP Server 集成

### 工具生态
- 🌤️ 天气查询
- 🔍 联网搜索
- 📦 快递查询
- 🗺️ 地图服务
- 🔧 自定义工具（OpenAPI/Swagger）

### 知识库
- 📄 文档上传（支持多种格式）
- 🔎 语义检索
- 📊 向量召回
- 🔄 混合检索（语义+关键词）

### 系统特性
- 🌐 WebSocket 实时通信
- 📱 响应式设计
- 🎭 微信集成
- 📊 追踪审计（Langfuse）
- ☁️ 对象存储（OSS/MinIO）

---

## 三、技术栈

### 后端
- **FastAPI** — 高性能 Web 框架
- **LangChain** — LLM 应用开发框架
- **MySQL** — 关系型数据库
- **Redis** — 缓存
- **Milvus** — 向量数据库

### 前端
- **Vue.js 3** — 前端框架
- **TypeScript** — 类型安全
- **Vite** — 构建工具
- **Element Plus** — UI 组件库

### 部署
- **Docker** — 容器化部署
- **Nginx** — 反向代理

---

## 四、快速开始

### 环境要求

| 环境 | 版本要求 |
|:---|:---|
| Python | ≥ 3.12 |
| Node.js | ≥ 18 |
| MySQL | ≥ 8.0 |
| Redis | ≥ 6.0 |

### 配置说明

复制配置文件并填写必要的 API Key：

```yaml
# config.yaml
multi_models:
  conversation_model:
    api_key: "YOUR_API_KEY"
    base_url: "https://dashscope.aliyuncs.com/compatible-mode/v1"
    model_name: "qwen-plus"
```

> ⚠️ **注意**: 所有敏感配置（API Key、数据库密码等）请在 `config.yaml` 中配置，切勿提交到版本控制系统。

### 本地开发

```bash
# 后端启动
cd src/backend
pip install -r requirements.txt
python start.py

# 前端启动
cd src/frontend
npm install
npm run dev
```

---

## 五、部署指南

### Docker 部署

```bash
# 构建镜像
docker build -t agentchat .

# 启动容器
docker run -d \
  -p 7860:7860 \
  -v ./config.yaml:/app/config.yaml \
  agentchat
```

### 部署架构

```
                    ┌─────────────┐
                    │   Nginx     │
                    │  (反向代理)  │
                    └──────┬──────┘
                           │
           ┌───────────────┼───────────────┐
           │               │               │
    ┌──────┴──────┐ ┌──────┴──────┐ ┌──────┴──────┐
    │   前端      │ │   后端      │ │   Redis     │
    │  (Vue.js)  │ │ (FastAPI)  │ │   缓存      │
    └─────────────┘ └──────┬──────┘ └─────────────┘
                          │
                   ┌──────┴──────┐
                   │   MySQL     │
                   │   数据库     │
                   └─────────────┘
```

### 环境变量

| 变量名 | 说明 | 示例 |
|:---|:---|:---|
| `MYSQL_HOST` | 数据库地址 | `localhost` |
| `REDIS_HOST` | Redis 地址 | `localhost` |
| `API_KEY` | 模型 API Key | `sk-xxx` |

---

## 六、许可证

本项目基于 [MIT License](LICENSE) 开源。

---

<div align="center">

**如果这个项目对你有帮助，请点个 ⭐ Star！**

</div>
