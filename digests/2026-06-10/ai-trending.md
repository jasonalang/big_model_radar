# AI 开源趋势日报 2026-06-10

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-06-10 02:57 UTC

---

《AI 开源趋势日报》  
*2026-06-10*

---

### 1. 今日速览

今日 AI 开源领域最突出的动向是 **Agent 技能化（Skills-as-Code）** 全面爆发：`last30days-skill` 单日激增 3,191 stars，带动 `pm-skills`、`agent-skills`、`career-ops` 等垂直场景技能库集体登榜，社区正从通用 Agent 框架转向可落地的领域技能编排。基础设施层面，基于 Rust 的高性能向量索引 `turbovec` 和“无向量”RAG 方案 `LEANN` 同时受到关注，检索层在**极致性能**与**端侧轻量化**两端分化。此外，持久化记忆层（`claude-mem`、`mem0`）持续高星，长程 Agent 对跨会话上下文的需求已成为工程落地的关键瓶颈。

---

### 2. 各维度热门项目

#### 🔧 AI 基础工具（框架、SDK、推理引擎、开发工具、CLI）

| 项目 | Stars | 一句话说明 |
|------|-------|------------|
| [RyanCodrai/turbovec](https://github.com/RyanCodrai/turbovec) | +1,801 today | 基于 TurboQuant 的向量索引，Rust 核心 + Python 绑定，追求极致检索性能。 |
| [roboflow/supervision](https://github.com/roboflow/supervision) | +733 today | 可复用的计算机视觉工具库，提供从检测到跟踪的标准化 CV 流水线。 |
| [Andyyyy64/whichllm](https://github.com/Andyyyy64/whichllm) | +633 today | 一键匹配本地硬件可运行且性能最优的 LLM，按真实基准而非参数量排名。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | 140,877 | 支持 Ollama、OpenAI API 的友好型本地 AI 界面，私有化部署的事实标准前端。 |
| [ollama/ollama](https://github.com/ollama/ollama) | 173,720 | 本地一键运行 Kimi-K2.6、DeepSeek、Qwen 等主流模型，本地 LLM 生态核心入口。 |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | 82,365 | 高吞吐、低显存占用的 LLM 推理与服务引擎，生产环境部署首选。 |
| [PaddlePaddle/PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) | 81,660 | 轻量级多语言 OCR 工具包，将 PDF

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*