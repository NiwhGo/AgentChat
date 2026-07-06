<div align='center'>
    <img src="https://github.com/user-attachments/assets/eb9b3b09-e2bf-4c9d-95a0-5c2d9712723d" alt="AgentChat" width="70%">
</div>

<div align="center">

<p align="center">
  <img src="https://img.shields.io/badge/python-3.12+-blue.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python Version" />
  <img src="https://img.shields.io/badge/vue-3.4+-4FC08D.svg?style=for-the-badge&logo=vue.js&logoColor=white" alt="Vue Version" />
  <img src="https://img.shields.io/badge/fastapi-0.115+-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/license-MIT-green.svg?style=for-the-badge" alt="License" />
</p>

<p align="center">
  <b>一个基于大模型的现代化智能对话系统</b>
</p>

<p align="center">
  <a href="https://shy2593666979.github.io/agentchat-docs/%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8.html">快速开始</a> •
  <a href="https://shy2593666979.github.io/agentchat-docs/%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97/%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.html">部署指南</a> •
  <a href="https://shy2593666979.github.io/agentchat-docs/">在线文档</a> •
  <a href="https://agentchat.cloud">在线体验</a> •
  <a href="https://github.com/Shy2593666979/agentchat-docs/blob/main/images/README.md">加入微信交流群🌟</a>
</p>

</div>

---

## 最新版本更新日志 (2026-4-12)

### 1. 基于人机协同（HITL）的OpenAPI信息对话式MCP Server生成

- 支持将OpenAPI信息以人机协同方式进行对话式MCP Server生成。
- 在生成MCP Server的过程中，关键决策节点支持人工介入与确认，实现动态配置与实时交互。
- 提升了服务器的生成灵活性与系统可控性，让用户在自动化流程中保留充分的主动权。

### 2. 优化对话上下文管理
重构对话上下文管理策略，从简单的"最近5段对话"升级为智能三层记忆架构：
- 短期记忆 (Short-Term Memory): 保持最近3000 tokens以内的对话内容，确保即时上下文连贯
- 历史信息总结: 自动总结超过3000 tokens的历史对话，提取关键信息
- 长期记忆 (Long-Term Memory): 持久化记录用户偏好、习惯和重要信息，实现个性化对话体验

### 3. 修复依赖冲突问题
解决了多个依赖包版本冲突问题，特别是 Pydantic、LangChain、FastAPI 等核心库的兼容性问题，提升系统稳定性。

### 4. 优化首次启动体验
修复首次启动时缺少模型配置导致的错误，新增配置检查和友好提示，引导用户完成初始化配置，降低使用门槛。

---

<details>
<summary><b>历史版本更新日志 (2026-3-8)</b></summary>

### 1. 支持MiniO本地对象存储
现在支持OSS和MiniO两种对象存储方式，参考文档: [本地安装MiniO](docs/development/install_minio_win.md)，感谢提供Issue的朋友:
- @xiaoyan011016
- @shenmi888

### 2. 优化Docker直接部署项目
(1) 前版本docker部署经常会出现 agentchat-frontend 连不上 agentchat-backend 的网络失败情况，已经修复该bug
(2) 缺少Win系统下的一键部署脚本，目前已经加上 (start_win.bat)

### 3. 支持自定义工具
之前点击自定义工具是无事件，目前可通过上传 Swagger/OpenAPI 构建自己的工具。

### 4. 支持Skill
现已支持通过创建 Skill 绑定到智能体渐进式加载 Prompt 去教模型如何做事。

### 5. 优化页面样式
前版本中系统设置为空白，现在已经去除。

</details>

---

## 目录

- [一、项目简介](#一项目简介)
- [二、功能展示](#二功能展示)
- [三、重要版本说明](#三重要版本说明)
- [四、功能特性](#四功能特性)
- [五、技术栈](#五技术栈)
- [六、快速开始](#六快速开始)
- [七、高级部署指南](#七高级部署指南)
- [八、文档](#八文档)
- [九、许可证](#九许可证)

---

## 一、项目简介

AgentChat 是一个现代化的智能对话系统，基于大语言模型构建，提供了丰富的AI对话功能。系统采用前后端分离架构，支持多种AI模型、知识库检索、工具调用、MCP服务器集成等高级功能。

<div align="center">
<img width="800" height="400" src="https://github.com/user-attachments/assets/f35e8a9a-0905-46a2-a167-a3c8e876760a" />
</div>

### 1. 核心亮点

- 🎯 **多模型支持**: 支持通义千问、DeepSeek、Kimi 等多种大语言模型
- 🔧 **工具调用**: 支持 Function Call、联网搜索、知识库检索等工具
- 🔌 **MCP 生态**: 支持 MCP Server 扩展，可对话式生成 MCP Server
- 💾 **记忆系统**: 三层记忆架构（短期/历史/长期），实现个性化对话
- 📚 **知识库**: 支持上传文档构建专属知识库
- 🎨 **多模态**: 支持图片理解、文生图等多媒体交互
- 🚀 **一键部署**: 支持 Docker 一键部署，开箱即用

---

## 二、功能展示

| 首页 | 智能体创建 |
|:---:|:---:|
| <img src="https://github.com/user-attachments/assets/a1.jpg" width="400"/> | <img src="https://github.com/user-attachments/assets/a2.jpg" width="400"/> |

| 对话界面 | 知识库管理 |
|:---:|:---:|
| <img src="https://github.com/user-attachments/assets/a3.jpg" width="400"/> | <img src="https://github.com/user-attachments/assets/a4.jpg" width="400"/> |

---

## 三、重要版本说明

### v2.5.0 版本特性

本次更新带来了革命性的 **MCP Server 对话式生成** 功能，以及全面升级的 **三层记忆架构**：

#### MCP Server 对话式生成
- 基于人机协同（HITL）理念
- 支持 OpenAPI 信息解析
- 关键决策节点人工介入
- 动态配置与实时交互

#### 三层记忆架构
```
┌─────────────────────────────────────┐
│         长期记忆 (Long-Term)         │
│   用户偏好、习惯、重要信息持久化      │
├─────────────────────────────────────┤
│         历史总结 (Historical)         │
│   超过3000 tokens时自动总结提取      │
├─────────────────────────────────────┤
│         短期记忆 (Short-Term)        │
│   最近3000 tokens即时上下文          │
└─────────────────────────────────────┘
```

---

## 四、功能特性

### 4.1 对话功能
- 💬 多轮对话支持
- 🔄 对话上下文管理
- 🖼️ 图片上传与理解
- 🎨 文生图能力
- 📎 文件上传与分析

### 4.2 智能体系统
- 🤖 智能体创建与管理
- 🎯 角色设定与 Prompt 工程
- 🔗 工具绑定
- 📚 知识库绑定
- 🔌 MCP Server 集成

### 4.3 工具生态
- 🌤️ 天气查询
- 🔍 联网搜索
- 📦 快递查询
- 🗺️ 地图服务
- 🔧 自定义工具（OpenAPI/Swagger）

### 4.4 知识库
- 📄 文档上传（支持多种格式）
- 🔎 语义检索
- 📊 向量召回
- 🔄 混合检索（语义+关键词）

### 4.5 系统特性
- 🌐 WebSocket 实时通信
- 📱 响应式设计
- 🎭 微信集成
- 📊 追踪审计（Langfuse）
- ☁️ 对象存储（OSS/MinIO）

---

## 五、技术栈

### 5.1 后端技术
<div align="center">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/LangChain-326CE5?style=for-the-badge&logo=langchain&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Milvus-0091EA?style=for-the-badge&logoColor=white" />
</div>

### 5.2 前端技术
<div align="center">
  <img src="https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/Element%20Plus-409EFF?style=for-the-badge&logo=element&logoColor=white" />
</div>

### 5.3 部署技术
<div align="center">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white" />
</div>

---

## 六、快速开始

### 6.1 环境要求

| 环境 | 版本要求 |
|:---|:---|
| Python | ≥ 3.12 |
| Node.js | ≥ 18 |
| MySQL | ≥ 8.0 |
| Redis | ≥ 6.0 |

### 6.2 配置说明

复制配置文件并填写必要的 API Key：

```yaml
# config.yaml 配置文件
multi_models:
  conversation_model:
    api_key: "YOUR_API_KEY"        # 填入你的 API Key
    base_url: "https://dashscope.aliyuncs.com/compatible-mode/v1"
    model_name: "qwen-plus"
```

> ⚠️ **注意**: 所有敏感配置（API Key、数据库密码等）请在 `config.yaml` 中配置，切勿提交到版本控制系统。

### 6.3 启动服务

**方式一：Docker 部署（推荐）**

```bash
# 一键启动
docker-compose up -d
```

**方式二：本地开发**

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

## 七、高级部署指南

### 7.1 Docker 部署

```bash
# 构建镜像
docker build -t agentchat .

# 启动容器
docker run -d \
  -p 7860:7860 \
  -v ./config.yaml:/app/config.yaml \
  agentchat
```

### 7.2 常见部署架构

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

### 7.3 环境变量配置

| 变量名 | 说明 | 示例 |
|:---|:---|:---|
| `MYSQL_HOST` | 数据库地址 | `localhost` |
| `REDIS_HOST` | Redis 地址 | `localhost` |
| `API_KEY` | 模型 API Key | `sk-xxx` |

---

## 八、文档

更多文档请访问：[📚 在线文档](https://shy2593666979.github.io/agentchat-docs/)

- [快速入门](https://shy2593666979.github.io/agentchat-docs/%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8.html)
- [环境搭建](https://shy2593666979.github.io/agentchat-docs/%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97/%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.html)
- [部署指南](https://shy2593666979.github.io/agentchat-docs/%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97/%E9%83%A8%E7%BD%B2%E6%8C%87%E5%8D%97.html)
- [API 文档](https://shy2593666979.github.io/agentchat-docs/)

---

## 九、许可证

本项目基于 [MIT License](LICENSE) 开源，欢迎使用。

---

<div align="center">

**如果这个项目对你有帮助，请点个 ⭐ Star！**

</div>
