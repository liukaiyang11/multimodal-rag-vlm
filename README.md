# Multimodal RAG (VLM 方向)

> 基于视觉大模型（VLM）的多模态文档检索 RAG 系统，支持图文混合 PDF 的智能解析、检索与问答。

[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://www.python.org/)
[![React](https://img.shields.io/badge/React-18+-61dafb)](https://react.dev/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688)](https://fastapi.tiangolo.com/)
[![LangChain](https://img.shields.io/badge/LangChain-v1+-green)](https://www.langchain.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## ✨ 特性

- 🖼️ **多模态解析**：支持图文混排 PDF、图片文档的智能解析
- 🔍 **语义检索**：基于向量数据库的语义检索，精准定位答案
- 💬 **智能问答**：结合 VLM 与 RAG，实现文档级问答
- 🏗️ **微服务架构**：多服务模块化，便于扩展与维护
- 🎨 **现代前端**：React + Vite + TailwindCSS 构建的美观界面

---

## 🏗️ 技术架构

```
┌─────────────────────────────────────────────────────┐
│                     Frontend                        │
│                  (React + Vite)                     │
└──────────┬──────────────────────┬───────────────────┘
           │                      │
     ┌─────▼──────┐        ┌──────▼───────┐
     │ Chat API   │        │ Knowledge    │
     │ (对话服务) │        │ Base API     │
     └─────┬──────┘        │ (知识库服务) │
           │               └──────┬───────┘
           │                      │
┌──────────▼──────────────────────▼───────────────────┐
│              Backend Services (Python)              │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │ 信息提取 │ │ 文本分段 │ │ 知识管理 │ │ 文档   │ │
│  │ (VLM)    │ │          │ │ (Milvus) │ │ 检索   │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
└─────────────────────────────────────────────────────┘
```

---

## 📁 项目结构

```
.
├── backend/                    # 后端服务
│   ├── chat/                   # 对话 API 服务
│   ├── knowledge-base-api/     # 知识库 API
│   ├── knowledge-management/   # 知识管理服务
│   ├── Information-Extraction/ # 信息提取（VLM + 规则）
│   ├── Text_segmentation/      # 文本分段
│   ├── fastapi-document-retrieval/  # 文档检索服务
│   ├── Database/               # 数据库相关
│   ├── start_all_services.sh   # 一键启动所有服务
│   └── requirements.txt
├── frontend/                   # 前端（React + Vite）
│   ├── src/
│   ├── package.json
│   └── vite.config.ts
├── 部署文档.md                  # 部署说明
└── README.md
```

> 💡 **数据文件说明**：Milvus 数据、MySQL 数据、测试文档等位于 `../data/` 目录（与 code 同级），不纳入 Git 仓库。

---

## 🚀 快速开始

### 环境要求

- Python 3.10+
- Node.js 18+
- Milvus（向量数据库）
- VLM API Key（如 GPT-4V、Qwen-VL 等）

### 后端启动

```bash
cd backend

# 安装依赖
pip install -r requirements.txt

# 配置环境变量
cp knowledge-base-api/.env.example knowledge-base-api/.env
# 编辑 .env 填入 API Key 等配置

# 启动所有服务
chmod +x start_all_services.sh
./start_all_services.sh
```

### 前端启动

```bash
cd frontend

# 安装依赖
npm install

# 配置 API 地址
cp .env.example .env

# 启动开发服务器
npm run dev
```

访问 http://localhost:5173 即可使用。

---

## 📚 相关课程

本项目配套完整的实战课程，包含从原理到落地的详细讲解：

- 📖 课程文档：[飞书知识库](#)（待补充）
- 🎥 视频教程：[课程链接](#)（待补充）
- 💬 交流社群：[加入讨论](#)（待补充）

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.
