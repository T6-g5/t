# A3-基于大模型的个性化资源生成与学习多智能体系统

> 中国软件杯 A组 A3 赛题

## 项目简介

基于大模型的个性化资源生成与学习多智能体系统开发，旨在为高等教育提供个性化、智能化的学习解决方案。

## 技术栈

- **前端**：React + TypeScript + TailwindCSS + Mantine
- **后端**：FastAPI + Python + SQLAlchemy
- **AI**：LangChain + 科大讯飞星火 + DeepSeek
- **数据库**：SQLite（开发）/ PostgreSQL（生产）
- **向量存储**：Chroma

## 快速开始

### 环境要求

- Python ≥ 3.11
- Node.js ≥ 18
- npm ≥ 8

### 后端运行

```bash
cd src/api
pip install -r requirements.txt
python -m uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

### 前端运行

```bash
cd src/web
npm install
npm run dev
```

### 访问地址

- API：http://localhost:8000
- 前端：http://localhost:5173
- API文档：http://localhost:8000/docs

## 目录结构

```
src/
├── api/                    # 后端API
│   ├── main.py             # FastAPI入口
│   ├── routers/            # 路由定义
│   ├── models/             # 数据模型
│   ├── schemas/            # Pydantic Schema
│   ├── database/           # 数据库连接
│   └── utils/              # 工具函数
├── agents/                 # 多智能体实现
│   ├── profile_agent.py    # 画像构建智能体
│   ├── resource_agent.py   # 资源生成智能体
│   ├── path_agent.py       # 路径规划智能体
│   ├── coordinator.py      # 智能体调度器
│   └── rag_service.py      # RAG知识库服务
├── config/                 # 配置文件
│   └── settings.py         # 环境配置
├── rag/                    # RAG知识库
│   ├── knowledge_base.py   # 知识库管理
│   └── vector_store.py     # 向量存储
└── web/                    # 前端代码
    ├── src/
    │   ├── components/     # 通用组件
    │   ├── pages/          # 页面组件
    │   ├── services/       # API服务
    │   └── store/          # 状态管理
    └── package.json
```

## 核心功能

- ✅ 对话式学习画像构建（≥6维度）
- ✅ 多智能体协同资源生成（≥5种资源类型）
- ✅ 个性化学习路径规划和资源推送
- ⏳ 智能辅导（可选加分）
- ⏳ 学习效果评估（可选加分）

## 开发计划

| 阶段 | 任务 |
|------|------|
| 阶段1 | 需求分析、系统设计 |
| 阶段2 | 项目初始化、基础架构 |
| 阶段3 | ProfileAgent 画像构建智能体 |
| 阶段4 | RAG知识库构建 |
| 阶段5 | ResourceAgent 资源生成智能体 |
| 阶段6 | PathAgent 路径规划智能体 |
| 阶段7 | TutorAgent/AssessAgent 加分功能 |
| 阶段8 | 前端开发、系统集成 |
| 阶段9 | 测试、修复、优化 |
| 阶段10 | 文档、演示视频 |

## 配置说明

复制 `src/api/.env.example` 为 `.env` 并填写配置：

```env
XUNFEI_APP_ID=你的科大讯飞APP_ID
XUNFEI_API_KEY=你的科大讯飞API_KEY
XUNFEI_API_SECRET=你的科大讯飞API_SECRET
DEEPSEEK_API_KEY=你的DeepSeek API_KEY
```

## License

MIT