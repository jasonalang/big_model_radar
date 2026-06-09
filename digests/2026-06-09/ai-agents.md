# OpenClaw 生态日报 2026-06-09

> Issues: 500 | PRs: 473 | 覆盖项目: 12 个 | 生成时间: 2026-06-09 02:44 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyclaw)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [EasyClaw](https://github.com/gaoyangz77/easyclaw)

---

## OpenClaw 项目深度报告

**OpenClaw 项目动态日报**  
**日期：2026-06-09**

---

### 1. 今日速览

OpenClaw 在 2026-06-09 维持极高社区活跃度：24 小时内 Issues 更新 **500 条**（新开/活跃 436 条，关闭 64 条），PR 更新 **473 条**（待合并 332 条，已合并/关闭 141 条），代码吞吐量与社区参与度均处于高位。项目连发两个 Beta 版本（v2026.6.5-beta.5 / beta.3），重点修复 QQBot 推理内容泄漏与 MCP 工具结果解析。但多个 P1 级 Bug（如 OpenAI gpt-5.4/5.5 传输失败、会话上下文混淆）仍在等待修复，整体呈现**“高活力、高积压”**的健康态势，维护者需关注长期停滞 Issue 的消化。

---

### 2. 版本发布

**v2026.6.5-beta.5 / v2026.6.5-beta.3**  
- **QQBot 安全修复**：在原生交付前剥离模型推理/思考脚手架（`<thinking>` 标签），防止原始推理内容泄漏到频道回复中。([#89913](https://github.com/openclaw/openclaw/issues/89913), [#90132](https://github.com/openclaw/openclaw/issues/90132))  
- **MCP 工具结果增强**：强制转换 `resource_link`、`resource`、`audio` 及格式异常图像，提升多模态工具链的健壮性。  
- **迁移注意**：MCP 适配器对异常载荷的强制转换行为可能改变下游技能接收的数据结构，依赖原始未过滤载荷的自定义技能建议验证兼容性。

---

### 3. 项目进展

今日合并/关闭的关键 PR 与 Issue，推动项目在**数据完整性、平台兼容性与消息交付**三个维度取得进展：

- **[#91526](https://github.com/openclaw/openclaw/pull/91526)** (已合并) `refactor(sqlite)`: 移除未使用的异步 Kysely 驱动，简化 `node:sqlite` 方言维护，减少技术债。  
- **[#90856](https://github.com/openclaw/openclaw/pull/90856)** / **[#91529](https://github.com/openclaw/openclaw/pull/91529)** (已合并/已关闭) `fix(agents)`: 修复转录图像编辑时 `ImageContent.data` 被误处理的问题，解决持久化会话中图像载荷损坏导致的 Provider 422 错误。  
- **[#91536](https://github.com/openclaw/openclaw/pull/91536)** (已合并) `fix(config)`: 修正 Windows 配置打开器使用错误的 `Start-Process -LiteralPath` 参数，恢复 Dashboard“打开配置”功能。  
- **[#88929](https://github.com/openclaw/openclaw/issues/88929)** (已关闭) 修复飞书流式卡片打字机效果异常及最终内容截断至最后一个字符的问题。  
- **[#87326](https://github.com/openclaw/openclaw/issues/87326)** (已关闭) 修复 Telegram 流式传输中，工具调用之间的中间文本块被静默覆盖、仅保留最终块的问题。  
- **[#48300](https://github.com/openclaw/openclaw/issues/48300)** (已关闭) 修复 `memory_search` 混合模式下 FTS 全文搜索匹配未返回的问题。

---

### 4. 社区热点

今日讨论最活跃的议题反映了**国际化、部署安全与模型适配**三大核心诉求：

| 议题 | 评论 | 核心诉求 |
|------|------|----------|
| **[#48788](https://github.com/openclaw/openclaw/issues/48788)** 集中式多编码 Content-Disposition 文件名编码工具 | 18 | 飞书/多频道适配器中日文、韩文、GB18030 等文件名乱码的系统性架构修复，而非个案补丁。 |
| **[#32473](https://github.com/openclaw/openclaw/issues/32473)** Control UI 要求设备身份（HTTPS/localhost 安全上下文） | 17 | VPS + Docker 部署场景下的安全上下文限制，阻碍非本地开发环境使用 Control UI。 |
| **[#90083](https://github.com/openclaw/openclaw/issues/90083)** OpenAI gpt-5.4/gpt-5.5 传输失败 `invalid_provider_content_type` | 15 | 新版本模型适配滞后，升级后出现连接错误，阻塞生产环境使用最新模型。 |
| **[#50090](https://github.com/openclaw/openclaw/issues/50090)** ClawHub 社区技能生态建设 | 15 | 技能市场（Skill Marketplace）的标准化、可发现性与社区治理机制缺失，生态愿景与实践差距大。 |
| **[#32296](https://github.com/openclaw/openclaw/issues/32296)** 代理回复历史消息而非当前消息（会话上下文混淆） | 14 | 核心会话状态管理缺陷，导致对话错位，直接影响多轮交互可靠性。 |

---

### 5. Bug 与稳定性

按严重程度排列的今日活跃 Bug，**P1 级问题亟需维护者介入**：

**P1 — 高优先级（影响核心功能或安全）**
- **[#90083](https://github.com/openclaw/openclaw/issues/90083)** OpenAI ChatGPT Responses 传输失败，gpt-5.4/5.5 出现 `invalid_provider_content_type` / `Connection error`。—— *新版本模型适配阻断*  
- **[#32296](https://github.com/openclaw/openclaw/issues/32296)** 代理回复先前消息而非当前消息，会话上下文混淆。—— *对话准确性核心缺陷*  
- **[#48003](https://github.com/openclaw/openclaw/issues/48003)** Steer 模式未在主会话回合中注入消息，`messages.queue.mode: "steer"`

---

## 横向生态对比

**个人 AI 助手与自主智能体开源生态横向对比分析**  
*报告日期：2026-06-09*

---

### 1. 生态全景

当前生态呈现**“头部极化、长尾沉寂”**的鲜明格局：OpenClaw、ZeroClaw、IronClaw 三个项目单日合计贡献超 1,000 条 Issues/PRs 更新，而半数以上项目（Moltis、CoPaw、ZeptoClaw、EasyClaw）24 小时内零活动。技术重心正从早期功能扩张全面转向**生产级加固**——安全沙箱、容器网络隔离、多模态输入管道与可观测性成为共同优先级，标志着该领域正从“Demo 可用”向“企业可托管”过渡。

---

### 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 健康度评估 |
|------|-------------|-----------|---------|-----------|
| **OpenClaw** | 500 条更新（436 活跃/新开，64 关闭） | 473 条更新（332 待合并，141 已合并/关闭） | v2026.6.5-beta.5 / beta.3 | **高活力、高积压**：吞吐量生态第一，但 P1 Bug 与 300+ 待合并 PR 显示维护瓶颈明显 |
| **IronClaw** | 34 条更新（22 活跃，12 关闭） | 50 条更新（25 已合并/关闭） | 无 | **高吞吐**：开发节奏极快（数据截断，无法评估积压风险） |
| **ZeroClaw** | 50 条更新（仅关闭 2 条） | 50 条更新（11 已合并/关闭） | 无 | **高活跃、低闭合**：社区热情高涨，但审查与合并吞吐严重滞后，技术债累积 |
| **NanoBot** | 7 条（3 活跃，4 关闭） | 36 条（16 已合并/关闭，20 待审） | 无 | **中高活跃、质量巩固**：安全与架构升级为主，闭合率健康 |
| **PicoClaw** | 未披露 | 19 条（9 已合并/关闭，10 待审） | v0.2.9-nightly | **紧凑迭代**：合并率 47%，聚焦工程治理与防御性编程 |
| **NanoClaw** | 1 条新增 | 3 条（2 已关闭/合并，1 待审） | 无 | **中等活跃**：安全架构与容器化优先，功能迭代放缓 |
| **LobsterAI** | 0 | 17 条（16 已合并/关闭，1 待审） | 无 | **开发活跃、社区静默**：零 Issues 与零评论，生态反馈机制薄弱 |
| **TinyClaw** | 0 | 1 条待审 | 无 | **基础维护**：近乎停滞，仅依赖单一外部贡献者修复安装体验 |
| **Moltis / CoPaw / ZeptoClaw / EasyClaw** | 0 | 0 | 无 | **沉寂**：过去 24 小时无活动 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是生态中**绝对规模领先的多平台 Bot 框架**，其 24 小时 500 条 Issues / 473 条 PR 的吞吐量超过其他所有项目总和，形成了围绕“ClawHub”技能市场的插件生态雏形。

* **核心优势**：全平台覆盖（QQBot、飞书、Telegram、Matrix 等）与 MCP 工具链的深度集成，使其更像“消息操作系统”而非单一聊天助手；对多编码 Content-Disposition、流式卡片等边缘场景的适配经验最为丰富。
* **技术路线差异**：相比 NanoBot 的“语音+跨实例协作”或 ZeroClaw 的“企业安全隔离”，OpenClaw 选择**广度优先**——通过 Kysely/SQLite 统一数据层、Dashboard 降低配置门槛，优先解决多平台消息交付的完整性。
* **社区规模对比**：其社区体量（单日 400+ 活跃 Issues）是 NanoBot（7 条）与 NanoClaw（1 条）的数十倍乃至数百倍，但高积压（332 待合并 PR）也导致 P1 级 Bug（如 gpt-5.4/5.5 适配、会话上下文混淆）响应滞后，呈现出“大而不快”的特征。

---

### 4. 共同关注的技术方向

以下需求在**三个及以上项目**中同步涌现，构成行业级共识：

| 技术方向 | 涉及项目 | 具体诉求 |
|---------|---------|---------|
| **安全与沙箱硬化** | NanoBot、ZeroClaw、NanoClaw | NanoBot 修复 SSRF 与 `ExecTool` 沙箱逃逸；ZeroClaw 推进 OIDC/TOTP 与可插拔安全层；NanoClaw 实现容器 Egress Lockdown 与 webhook 绑定收紧 |
| **多模态输入管道** | OpenClaw、NanoBot、PicoClaw、NanoClaw | OpenClaw 增强 MCP 对 `audio/resource` 的解析；NanoBot 将语音转录升级为平台级能力并接入 MiMo ASR；PicoClaw 补全 Telegram 位置消息；NanoClaw 紧急修复 WhatsApp 媒体附件容器挂载 |
| **容器化与部署安全** | NanoClaw、OpenClaw、ZeroClaw | NanoClaw 解决 v2 容器卷映射断裂；OpenClaw 社区热议 VPS+Docker 下 Control UI 的 HTTPS/localhost 安全上下文限制；ZeroClaw 修复 Matrix 多别名会话隔离 |
| **可观测性与运维感知** | PicoClaw、NanoBot、LobsterAI、OpenClaw | PicoClaw 统一结构化日志；NanoBot 在 WebUI 增加版本徽章与 PyPI 更新通知；LobsterAI 暴露 OpenClaw 网关状态与启动进度；OpenClaw 修复 Dashboard 配置打开器 |
| **企业网关/云兼容** | NanoBot、ZeroClaw、OpenClaw | NanoBot 为 Azure 风格网关注入 `api-version`；ZeroClaw 补全 Azure OpenAI `reasoning_effort`；OpenClaw 修复 Windows 配置打开器与多编码文件名 |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|---------|---------|---------------|
| **OpenClaw** | 多平台 Bot 统一框架、技能市场 | 开发者、频道运营者 | 多平台适配器 + SQLite 统一持久化 + MCP 工具集线器 |
| **NanoBot** | 语音输入、多 Agent 协作、多模型路由 | 个人高级用户、多 Agent 部署者 | 平台级转录层 + 跨实例消息总线 + 对话级模型覆盖 |
| **ZeroClaw** | 企业安全、自动化任务（cron）、Matrix | 企业自托管、安全敏感场景 | 可插拔安全层 + OIDC/TOTP + 严格的会话隔离与文件写入策略 |
| **PicoClaw** | 边缘/嵌入式运行、跨平台（RISC-V） | 硬件开发者、极客 | Go 语言原生、防御性编程、Nightly 持续构建、轻量级二进制 |
| **NanoClaw** | 容器化 Agent-as-a-Service | SaaS 提供者、多租户部署 | Docker 内部网络隔离 + OneCLI 网关代理 + 容器级附件路由 |
| **LobsterAI** | 桌面端应用、数据迁移、OAuth | 终端用户（非开发者） | Electron 桌面架构 + 本地回调服务器 + 用户数据备份/恢复体系 |
| **TinyClaw** | 极简入门、低依赖 | 初学者、轻量场景 | Node.js 轻量封装，依赖 `better-sqlite3`，功能集最小化 |

---

### 6. 社区热度与成熟度

* **快速迭代期（高热度、高积压）**：**OpenClaw、ZeroClaw、IronClaw**。三者单日 PR/Issue 总量占生态绝对大头，但闭合率偏低（ZeroClaw 仅 4% Issue 关闭率），处于功能爆发与维护压力并存的阶段。
* **质量巩固期（中高活跃、高闭合率）**：**NanoBot、PicoClaw**。NanoBot 聚焦安全与转录架构升级，PicoClaw 进行系统性错误处理与日志治理，代码质量提升明显，社区节奏可控。
* **静默维护期（低互动、定向修复）**：**NanoClaw、LobsterAI、TinyClaw**。NanoClaw 仅聚焦安全

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
**日期：2026-06-09**  
**仓库：github.com/HKUDS/nanobot**

---

### 1. 今日速览

过去 24 小时，NanoBot 维持**中高活跃度**：共处理 36 个 PR（16 个已合并/关闭，20 个待审阅）与 7 个 Issue（4 个关闭，3 个新增/活跃）。项目核心进展集中在**语音转录架构升级**（从频道级配置演进为平台级共享能力）、**安全加固**（SSRF 与沙箱逃逸修复）以及**Agent 跨实例协作基础设施**落地。无新版本发布，但主分支在稳定性与多提供商兼容性上显著推进。

---

### 2. 版本发布

**无新版本发布。**  
今日未发布 Release，但主分支已合并多项面向下一版本的功能与修复。

---

### 3. 项目进展

今日合并/关闭的 16 个 PR 中，以下四项标志着项目整体向前迈出关键步伐：

**A. 转录系统架构升级与生态扩展**  
- **#4232** 将转录从频道专属配置提升为 NanoBot 顶层共享能力，WebUI 与桌面端语音输入可直接复用同一套转录后端，显著降低多入口维护成本。  
- **#4224**、**#4175**、**#4113** 分别接入 AssemblyAI、小米 MiMo ASR (`mimo-v2.5-asr`) 与 OpenRouter 三大转录提供商，使中文语音识别与低资源场景覆盖得到实质性增强。  
  - [#4232](https://github.com/HKUDS/nanobot/pull/4232) | [#4224](https://github.com/HKUDS/nanobot/pull/4224) | [#4175](https://github.com/HKUDS/nanobot/pull/4175) | [#4113](https://github.com/HKUDS/nanobot/pull/4113)

**B. 安全与稳定性加固**  
- **#4221** 阻止了 `ExecTool` 通过相对路径符号链接逃逸工作区的攻击面；**#4219** 在会话历史修剪前清理孤立工具结果，避免上下文污染。  
  - [#4221](https://github.com/HKUDS/nanobot/pull/4221) | [#4219](https://github.com/HKUDS/nanobot/pull/4219)

**C. Agent 协作基础设施**  
- **#3992** 实现了跨实例消息总线，使多 Agent 部署场景下的协同工作成为可能，为后续分布式 Agent 编排奠定协议层基础。  
  - [#3992](https://github.com/HKUDS/nanobot/pull/3992)

**D. 提供商兼容性与 WebUI 体验**  
- **#4217** 为 OpenAI 兼容提供商新增 `extra_query` 配置，解决 Azure 风格网关因缺少 `api-version` 参数返回 404 的问题；**#4235** 在 WebUI 设置页引入版本展示。  
  - [#4217](https://github.com/HKUDS/nanobot/pull/4217) | [#4235](https://github.com/HKUDS/nanobot/pull/4235)

---

### 4. 社区热点

| 议题/PR | 状态 | 热度分析 |
|---|---|---|
| **#4253** 支持按对话覆盖模型 | OPEN | 用户提出在 OpenRouter（快速/公共）与本地 llama.cpp（私密/慢速）之间按任务动态切换的强需求，反映出多模型路由已成为高频使用场景。 |
| **#4250 / #4257** Telegram 消息分割破坏围栏代码块 | OPEN / PR 待合并 | 长回复在 Telegram 被硬截断后导致 Markdown 代码块渲染崩坏，直接影响开发者体验，社区已有修复 PR 等待审阅。 |
| **#4233 / #4255** WebUI 版本徽章与 PyPI 更新通知 | CLOSED / PR 待合并 | 用户希望直观感知当前版本与可更新状态，#4235 已合并基础版本展示，#4255 进一步提供实时 PyPI 通知，显示项目正从“功能可用”向“运维可感知”演进。 |
| **#4251** 输入框上传文件/图片 | CLOSED | 中文社区用户提出多模态输入需求（PDF 总结、图片解析），虽 Issue 已关闭，但表明终端用户对原生多模态交互的期待正在上升。 |

- [#4253](https://github.com/HKUDS/nanobot/issues/4253) | [#4250](https://github.com/HKUDS/nanobot/issues/4250) | [#4257](https://github.com/HKUDS/nanobot/pull/4257) | [#4233](https://github.com/HKUDS/nanobot/issues/4233) | [#4255](https://github.com/HKUDS/nanobot/pull/4255) | [#4251](https://github.com/HKUDS/nanobot/issues/4251)

---

### 5. Bug 与稳定性

按严重程度排列：

| 严重程度 | 问题 | 状态 | 修复进展 |
|---|---|---|---|
| **高** | **#4074** MCP HTTP/SSE 配置在 SSRF 拒绝前尝试 loopback 连接，存在网络层绕过风险 | CLOSED | 已关闭，安全策略已对齐至网络层 fetch 工具的校验标准。 |
| **高** | **#4223** 微信渠道 session 过期后未重新加载 `account.json`，导致 60 分钟暂停后进入永久静默死循环 | OPEN | PR [#4223](https://github.com/HKUDS/nanobot/pull/4223) 待合并，修复 `_poll_once()` 唤醒后的状态重载逻辑。 |
| **中** | **#4250** Telegram `split_message` 在围栏代码块内截断，造成 HTML 渲染错误 | OPEN | PR [#4257](https://github.com/HKUDS/nanobot/pull/4257) 待合并，已引入代码块感知分割策略。 |
| **中** | **#4256** `MemoryStore` 游标在压缩或历史推进后可能出现非单调分配，导致记忆 ID 回退或冲突 | OPEN | PR [#4256](https://github.com/HKUDS/nanobot/pull/4256) 待合并，增加游标与历史尾部校验。 |
| **中** | **#4221** 相对符号链接可导致 `ExecTool` 受限命令逃逸工作区 | CLOSED | 已合并，新增路径解析与符号链接边界检查。 |
| **低** | **#4219** 会话历史修剪时遗留孤立工具结果，可能污染后续模型上下文 | CLOSED | 已合并，修剪前执行孤儿结果清理。 |

- [#4074](https://github.com/HKUDS/nanobot/issues/4074) | [#4223](https://github.com/HKUDS/nanobot/pull/4223) | [#4250](https://github.com/HKUDS/nanobot/issues/4250) | [#4256](https://github.com/HKUDS/nanobot/pull/4256) | [#4221](https://github.com/HKUDS/nanobot/pull/4221) | [#4219](https://github.com/HKUDS/nanobot/pull/4219)

---

### 6. 功能请求与路线图信号

以下需求与 PR 共同勾勒出近期可能的路线图方向：

- **对话级模型覆盖（#4253）**：用户希望打破全局单模型限制，按隐私/成本/延迟需求在单条对话内切换后端。该需求尚无对应 PR，但属于高价值交互改进，预计将被核心维护者评估。
- **转录平台化（已落地）**：#4232 及多个转录提供商 PR 表明，语音输入正从“频道插件”升级为 NanoBot 核心能力，下一版本可能继续扩展 TTS/语音合成对称架构。
- **WebUI 可观测性（进行中）**：#4255 引入 PyPI 版本检查，预示项目开始关注终端用户的升级管理与版本可见性，可能进一步扩展至系统健康度仪表盘。
- **多模态输入（#4251）**：虽然 Issue 已关闭，但上传文件/图片进行解析的需求明确，结合转录系统的平台化趋势，统一媒体解析管道（PDF/图片/音频）可能是后续自然延伸。

- [#4253](https://github.com/HKUDS/nanobot/issues/4253) | [#4232](https://github.com/HKUDS/nanobot/pull/4232) | [#4255](https://github.com/HKUDS/nanobot/pull/4255) | [#4251](https://github.com/HKUDS/nanobot/issues/4251)

---

### 7. 用户反馈摘要

从今日 Issues 中提炼的真实用户声音：

- **痛点：企业网关兼容性**  
  Azure 风格网关强制要求 `api-version` 查询参数，原有 OpenAI 兼容层无法注入，直接导致 404 不可用（#4204）。用户 @mraad 的补丁路径已被采纳，说明生产环境部署的兼容性需求紧迫。
  
- **痛点：渠道长期稳定性**  
  微信渠道在 session 过期后无法自愈，需人工重新扫码（#4223）。这反映出长时间运行的渠道机器人对“断线重连/状态自愈”有强需求，而非仅一次性登录。

- **场景：隐私与成本的动态权衡**  
  @rombert 在 #4253 中描述的场景极具代表性：公共 API 用于快速常规任务，本地 llama.cpp 用于私密数据。用户不再满足于“全局配置”，而需要“任务级路由”。

- **体验诉求：版本可见性**  
  @viblo 指出 `/status` 命令对普通用户不够友好，WebUI 应直接展示版本及更新提示（#4233）。这表明项目用户群体已从早期开发者向普通终端用户扩展。

- **中文用户多模态需求**  
  @JFPURE 提出直接上传 PDF/图片进行总结与解析（#4251），显示中文社区对 NanoBot 作为“个人知识助手”的期待高于纯文本聊天。

---

### 8. 待处理积压

以下 PR/Issue 已长期活跃或涉及核心模块，建议维护者优先审阅，避免贡献者流失与功能分叉：

| 项目 | 创建时间 | 核心内容 | 风险提示 |
|---|---|---|---|
| **#4170** |

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
*日期：2026-06-09 | 分析师：开源项目观察*

---

### 1. 今日速览

过去 24 小时，ZeroClaw 社区保持极高活跃度，共有 **50 条 Issue** 与 **50 条 PR** 发生更新，但关闭/合并比例偏低（Issue 仅关闭 2 条，PR 合并/关闭 11 条），表明社区参与热情高涨，但维护吞吐与代码审查压力仍在累积。今日无新版本发布，核心工作集中在**稳定性加固**（Matrix 会话隔离、cron 调度、runtime 历史裁剪）、**安全架构升级**（OIDC、可插拔安全层、TOTP 门控）以及**工具链补全**（MCP 前缀过滤、插件命名空间、Azure OpenAI 推理参数）。值得注意的是，Matrix 频道修复了一个存在数据错乱风险的 S1 级 Bug，但引入了需要用户手动迁移的破坏性变更。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日已关闭/合并的关键 PR 推动了以下实质性进展：

- **Matrix 频道安全性与隔离性修复**  
  PR [#7388](https://github.com/zeroclaw-labs/zeroclaw/pull/7388) 已关闭，彻底修复了多别名 Matrix 实例共享同一会话存储导致的身份错乱与密钥备份不一致问题（关闭 Issue [#6487](https://github.com/zeroclaw-labs/zeroclaw/issues/6487)）。该修复要求现有用户手动迁移会话目录，属于破坏性变更。  
- **Runtime 历史裁剪防崩溃**  
  PR [#7403](https://github.com/zeroclaw-labs/zeroclaw/pull/7403) 已关闭，在 `trim_history` 中增加安全守卫，防止孤儿消息级联删除导致对话历史被意外清空。  
- **文件写入安全显式化**  
  PR [#7129](https://github.com/zeroclaw-labs/zeroclaw/pull/7129) 针对 S0 级 Bug [#4627](https://github.com/zeroclaw-labs/zeroclaw/issues/4627) 进行修复：当 `file_write` 目标为临时工作区时不再静默失败，而是显式拒绝，避免用户误以为数据已持久化。  
- **Gateway 鲁棒性增强**  
  PR [#7402](https://github.com/zeroclaw-labs/zeroclaw/pull/7402) 修复了 TLS `accept()` 在遇到瞬态错误（如文件描述符耗尽）时直接崩溃的问题，网关现在具备错误恢复能力。  
- **Cron 调度与 Azure 提供程序补全**  
  PR [#7348](https://github.com/zeroclaw-labs/zeroclaw/pull/7348) 修复了 cron 在启动时对逾期任务的重复执行；PR [#7350](https://github.com/zeroclaw-labs/zeroclaw/pull/7350) 为 Azure OpenAI 提供程序接入了 `reasoning_effort` 参数。  
- **文档与配置工程化**  
  PR [#7365](https://github.com/zeroclaw-labs/zeroclaw/pull/7365) 对官方文档进行了大规模重构，支持主题感知高亮与 OS 标签页；PR [#7267](https://github.com/zeroclaw-labs/zeroclaw/pull/7267) 实现了 `[[mcp.servers]]` 的按字段编辑，降低运维配置门槛。

---

### 4. 社区热点

今日讨论最活跃的议题反映了开发者在**工具链可靠性**与**下一代交互形态**上的深度关切：

| 议题 | 评论 | 核心诉求 |
|------|------|----------|
| [#6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699) `tool_filter_groups` 对真实 MCP 工具无实际效果（前缀检查 Bug） | 7 | MCP 工具过滤逻辑存在前缀匹配缺陷，且与 `deferred_loading` 未集成，导致配置层面的访问控制形同虚设。 |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) RFC: Computer-use 桌面屏幕交互与输入控制 | 6 | 社区强烈要求对标 OpenAI Codex / Hermes 的计算机使用能力，实现截图与键鼠控制，拓展 Agent 的 GUI 自动化边界。 |
| [#5844](https://github.com/zeroclaw-labs/zeroclaw/issues/5844) 记忆权重过高导致行为偏离 | 5 | 在 cron 等自动化场景中，系统提示对历史记忆的过度强调使 Agent 忽视当前指令，需重新平衡 prompt 权重。 |
| [#7184](https://github.com/zeroclaw-labs/zeroclaw/issues/7184) RFC: 将翻译文件移入 git submodule | 5 | 减少主仓库因 i18n 更新产生的历史噪音，改善可维护性。 |
| [#4467](https://github.com/zeroclaw-labs/zeroclaw/issues/4467) 添加 MCP resource 与 prompt 支持 | 4 👍 | 高赞需求，当前 ZeroClaw 仅将 MCP 当作工具客户端，未暴露资源与提示能力，限制了与外部 MCP 服务器的互操作性。 |

---

### 5. Bug 与稳定性

今日

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
*日期：2026-06-09 | 仓库：sipeed/picoclaw*

---

### 1. 今日速览

过去 24 小时项目维持**高活跃度**：PR 吞吐量达 **19 条**（合并/关闭 9 条，待审阅 10 条），合并率约 47%，代码迭代节奏紧凑。社区贡献者 `@chengzhichao-xydt` 单日批量提交 10+ 条防御性编程改进，主导了今日的错误处理与类型安全治理。同时，Nightly 构建持续跟进 `main` 分支，但跨平台兼容性（RISC-V、Windows）仍是悬而未决的用户痛点，需维护者介入推进。

---

### 2. 版本发布

**v0.2.9-nightly.20260609.46b29a0a** — Nightly Build  
🔗 [Release 页面](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)

- **性质**：自动化构建，基于 `main` 分支最新提交 `46b29a0a`。
- **稳定性**：官方标注为不稳定版本，建议仅用于测试环境。
- **变更范围**：包含自 `v0.2.9` 以来的全部累积更新，主要涉及类型断言加固、错误处理规范化及 Telegram 位置消息支持。
- **迁移注意**：生产环境请继续使用稳定版 `v0.2.8`，等待后续正式版发布。

---

### 3. 项目进展

今日已合并/关闭的 9 条 PR 显著提升了运行时稳定性与可观测性：

| PR | 作者 | 进展说明 |
|---|---|---|
| [#3052](https://github.com/sipeed/picoclaw/pull/3052) | @wzg-gie | **Telegram 渠道功能补全**：将 `message.location` 转换为文本坐标注入 Agent Pipeline，解决位置消息被静默丢弃的问题。 |
| [#3050](https://github.com/sipeed/picoclaw/pull/3050) | @chengzhichao-xydt | **可观测性升级**：将裸 `log.Printf` / `fmt.Printf` 替换为结构化日志，统一日志后端输出。 |
| [#3051](https://github.com/sipeed/picoclaw/pull/3051) | @chengzhichao-xydt | **错误链修复**：在 channels 与 MCP 模块中将 `%v` 改为 `%w`，恢复 `errors.Is` / `errors.As`  introspection 能力。 |
| [#3055](https://github.com/sipeed/picoclaw/pull/3055) ~ [#3058](https://github.com/sipeed/picoclaw/pull/3058), [#3018](https://github.com/sipeed/picoclaw/pull/3018) | @chengzhichao-xydt | **防御性编程**：批量为 `sync.Map`、`context.Value`、`os.Getwd` 等 10+ 处添加 `ok` 检查与错误处理，消除潜在 panic 与资源泄漏风险。 |
| [#3062](https://github.com/sipeed/picoclaw/pull/3062) | @trufae | **服务健康检查**：修复健康端点永远返回 `not ready` 的误报问题。 |

**整体评估**：项目今日在“工程质量”维度迈出扎实一步，错误处理、日志体系与类型安全得到系统性加固，但功能层面仍以修复与补全为主。

---

### 4. 社区热点

**讨论最活跃的 Issues/PRs：**

1.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-09 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

过去 24 小时，NanoClaw 社区活跃度处于**中等水平**，共产生 1 条新增 Issue 与 3 条 PR 动态。今日技术焦点集中在**安全架构加固**与**WhatsApp 渠道稳定性**两个维度：一方面，社区推进了容器级网络隔离与认证层漏洞修复；另一方面，v2 版本在 WhatsApp 媒体附件的容器卷挂载策略上出现回归，导致 Agent 无法访问用户传入的多模态文件。整体而言，项目在安全性和企业级部署能力上持续演进，但渠道文件 I/O 的可靠性出现新的待修复项。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日共有 **2 条 PR 已关闭/合并**，**1 条 PR 待合并**，项目在安全与治理层面取得实质推进：

- **#2713** — Egress Lockdown（已关闭）  
  作者 `@omri-maya` 实现了可选的**出站流量锁定**：通过将 Agent 容器置于 Docker `--internal` 网络，并借助 OneCLI 网关作为唯一出向代理，实现默认无外网路由的容器级网络隔离。该功能默认关闭，以 opt-in 方式供多租户或高安全场景启用。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2713

- **#2712** — 贡献者指南合规 PR（已关闭）  
  作者 `@juhojeon86` 提交了一个遵循项目贡献指南（contributing-guide: v1）的 PR，涉及技能（skill）模板或运营/容器技能的新增，已处理完毕。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2712

- **#2714** — 四项认证与安全修复（待合并）  
  作者 `@JorellDacasin` 提交了一站式安全补丁，涵盖 webhook-server 默认绑定地址收紧（`0.0.0.0` → `127.0.0.1`）并暴露 `WEBHOOK_BIND_HOST` 环境变量，以及将 `sender-approval` 的 ID 生成从 `Math.random()` 升级为 `crypto.randomUUID()` 以防御时序预测攻击。该 PR 目前处于 Open 状态，等待维护者最终审查。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2714

---

### 4. 社区热点

今日社区讨论全部围绕以下两条核心线索展开，虽评论数尚少，但技术权重极高：

- **#2714** `security: fix four auth/security issues`（Open）  
  该 PR 是今日安全领域的集中爆发点，反映了贡献者对生产环境攻击面（webhook 暴露、弱熵随机数）的高度敏感。其诉求在于：在 Agent 即服务（Agent-as-a-Service）的部署模式下，默认配置必须遵循最小权限原则，避免开箱即用的安全隐患。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2714

- **#2715** `Inbound WhatsApp media is unreachable by the agent`（Open）  
  这是今日唯一新增 Issue，直指 v2 版本在容器化文件路径映射上的架构缺陷。用户（及下游 Agent）对跨渠道多模态交互（图片、文档、音频）有明确需求，而当前 `DATA_DIR/attachments` 与容器内 `/workspace/attachments/` 的路径断裂直接阻断了该能力。  
  🔗 https://github.com/nanocoai/nanoclaw/issues/2715

---

### 5. Bug 与稳定性

按严重程度排序：

| 严重度 | Issue/PR | 描述 | Fix PR |
|---|---|---|---|
| **高** | **#2715** | WhatsApp 入站媒体文件不可达：附件被下载至主机的 `DATA_DIR/attachments`，但 Agent 容器未挂载该目录，导致容器内 `/workspace/attachments/...` 路径不存在，Agent 完全无法读取用户发送的图片、文档及音频。属于 v2 容器化部署的回归或架构遗漏。 | **尚无** |
| **中** | **#2714**（内含） | Webhook 服务器默认监听 `0.0.0.0`，在公网/边缘部署场景中可能导致未授权访问；`sender-approval` 使用 `Math.random()` 生成审批 ID，存在被预测的风险。 | **#2714**（Open，待合并） |

---

### 6. 功能请求与路线图信号

- **企业级网络隔离**：#2713 的 egress lockdown 已落地，信号明确——项目正从“功能可用”向“安全可托管”演进，未来版本可能会进一步扩展网络策略（如入站规则、细粒度域名白名单）。
- **部署灵活性**：#2714 中引入的 `WEBHOOK_BIND_HOST` 环境变量，表明社区需要更灵活的网络绑定配置，以支持反向代理、Sidecar 及 Kubernetes 等多样化部署拓扑。
- **多模态渠道稳定性**：#2715 虽未以“功能请求”形式出现，但其修复将决定 WhatsApp 渠道是否具备生产级文件处理能力，预计维护者将在近期推出卷挂载或对象存储代理的修复方案。

---

### 7. 用户反馈摘要

- **痛点**：在 v2 版本中使用 WhatsApp 渠道时，用户发送的媒体文件（图片、文档、音频）对 Agent 完全不可见，导致多模态工作流中断。这反映出容器化后，持久化存储与容器内路径的映射策略尚未覆盖附件子目录。
- **场景**：需要 Agent 处理用户上传文档（如合同、发票）或图片（如视觉识别）的 WhatsApp 业务场景当前受阻。
- **安全焦虑**：贡献者主动提交 #2713 与 #2714，侧面说明项目已进入更严肃的生产部署阶段，社区对“默认安全”的期望显著提升。

---

### 8. 待处理积压

以下条目需要维护者优先关注，以避免影响发布节奏或用户体验：

- **#2715** — WhatsApp 附件路径挂载问题（Open，0 评论）  
  该 Issue 于 2026-06-08 创建，目前尚无维护者回应或修复 PR。考虑到它直接阻断 v2 的 WhatsApp 媒体处理流，建议尽快评估是调整 Docker Compose 卷映射，还是在附件下载逻辑中改用 Agent 容器可达的统一存储路径。  
  🔗 https://github.com/nanocoai/nanoclaw/issues/2715

- **#2714** — 四项安全修复（Open，待合并）  
  该 PR 涉及认证与网络绑定层面的安全加固，建议维护者优先审查并合并，以降低未修复漏洞在主干代码中的暴露窗口。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2714

---

*日报基于 NanoClaw 官方仓库 24 小时内的公开活动数据生成。*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-06-09 | 仓库：nearai/ironclaw*

---

### 1. 今日速览

IronClaw 在 6 月 9 日维持极高开发吞吐量：24 小时内更新 **34 条 Issue**（新开/活跃 22，关闭 12）与 **50 条 PR**（合并/关闭 25

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
**日期：** 2026-06-09  
**仓库：** github.com/netease-youdao/LobsterAI  

---

### 1. 今日速览

过去24小时，LobsterAI 维护活动高度活跃，共处理 **17 个 PR**（16 个已合并/关闭，1 个待审），但 **Issues 与社区互动指标为零**。核心代码进展集中在三条主线：用户数据迁移体系完整落地、桌面端 OAuth 认证体验优化、OpenClaw 网关可观测性增强。与此同时，维护者批量关闭了 8 个标记为 `stale` 的历史 PR，显著降低积压。然而，所有 PR 的评论数与 Reactions 均为 0，代码迭代速度快但社区参与度极低，生态健康度呈现“开发活跃、反馈静默”的分化态势。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

#### A. 数据迁移体系完整落地（今日核心主线）
- **#2125** [feat(data-migration): add user data backup and restore](https://github.com/netease-youdao/LobsterAI/pull/2125)  
  新增数据迁移服务，支持将用户数据打包为便携 tar 包，并通过定时重启完成恢复与回滚；已在设置页提供本地化对话框与 IPC 通道。
- **#2126** [fix(data-migration): restore data in place and preserve runtime locks](https://github.com/netease-youdao/LobsterAI/pull/2126)  
  将“全目录重命名”改为“原地替换”，避免 `SingletonLock`、`Socket` 等运行时锁文件在恢复过程中被覆盖或丢失，失败时仅在有回滚备份的情况下执行还原。
- **#2128** [fix(data-migration): exclude Network directory from backup and preserve on restore](https://github.com/netease-youdao/LobsterAI/pull/2128)  
  备份时排除 `Network` 目录，防止网络配置被带入恢复流程。

#### B. 桌面认证体验专项优化
- **#2122** [feat(auth): add local callback login flow](https://github.com/netease-youdao/LobsterAI/pull/2122)  
  在客户端内启动临时 `127.0.0.1` 回调服务器，替代外部协议唤起，消除浏览器“打开外部应用”确认弹窗。
- **#2127** [fix(auth): improve Windows focus after callback login](https://github.com/netease-youdao/LobsterAI/pull/2127)  
  登录完成后强制将主窗口置顶，并通过短暂切换 `always-on-top` 与停止任务栏闪烁，解决 Windows 下浏览器回调后窗口被遮挡的问题。
- **#2129** [chore(auth): add login callback diagnostics](https://github.com/netease-youdao/LobsterAI/pull/2129)  
  增加日志诊断，记录客户端使用 overmind 还是 fallback portal URL、是否启用本地回调，便于开发模式排障。

#### C. OpenClaw 网关可观测性与稳定性
- **#2123** [feat(settings): surface OpenClaw gateway URL and refine runtime status](https://github.com/netease-youdao/LobsterAI/pull/2123)  
  在设置页展示可复制网关地址、阶段状态徽章与带标签的启动进度条，提升集成与排障效率。
- **#1521** [fix(openclaw): prevent skills-changed from triggering spurious gateway restart](https://github.com/netease-youdao/LobsterAI/pull/1521)  
  阻止 `skills-changed` 事件导致不必要的网关重启，减少运行时抖动。

#### D. 历史积压批量清理（Stale PR 关闭）
以下 PR 于今日被统一关闭，涉及功能与修复已沉淀为需求信号，但代码未合并：
- **#1510** 定时任务 IM 通知空会话校验
- **#1514** QQ Bot 群组白名单 UI 补全
- **#1515** 日志导出 DEFLATE 压缩超时修复
- **#1517** GitHub Copilot OAuth 轮询泄漏修复
- **#1522** 动态模型列表自动获取
- **#1524** 连接测试详细错误提示
- **#1526** 会话列表颜色标注

---

### 4. 社区热点

今日 **所有 PR 的社区互动指标

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

**TinyClaw (TinyAGI/tinyagi) 项目动态日报**  
**日期：2026-06-09**

---

### 1. 今日速览

TinyClaw 项目在 2026-06-09 整体活跃度偏低，过去 24 小时内社区未产生新的 Issues 讨论，代码合并与版本发布活动均处于停滞状态。唯一动态来自贡献者 @dsy122 提交的一条安装体验修复 PR，目前尚待维护者审阅。项目今日无紧急缺陷上报，健康度维持在基础维护水平，但社区互动指标（评论、点赞）均为零，表明用户与贡献者参与度不高，开发节奏趋于平稳。

---

### 3. 项目进展

今日 **无已合并或已关闭的 Pull Requests**，代码库未发生实质性功能推进。  
目前有待合并的修复项：

- **PR #280** — `fix(install): add postinstall script to auto-rebuild better-sqlite3`  
  链接：https://github.com/TinyAGI/tinyagi/pull/280  
  该 PR 旨在通过 `postinstall` 脚本自动重建原生 C++ 模块 `better-sqlite3`，消除用户在全新安装（fresh install）后手动执行 `npm rebuild better-sqlite3` 的步骤。若合并，将直接改善开发者体验（DX）并降低新用户上手门槛。但由于仍处于 **OPEN** 状态，项目整体在今日未向前迈进显著一步。

---

### 4. 社区热点

今日社区唯一焦点为上述待审阅 PR，尽管其互动数据为零（👍: 0，评论: 无），但在零 Issues 更新的背景下，它是过去 24 小时内唯一的社区贡献信号。

- **PR #280** — fix(install): add postinstall script to auto-rebuild better-sqlite3  
  链接：https://github.com/TinyAGI/tinyagi/pull/280  
  **诉求分析**：贡献者关注到 `better-sqlite3` 作为原生 addon 在不同 Node.js 运行时下的编译兼容性问题，说明存在用户因预构建二进制文件缺失导致安装失败的场景。该 PR 反映的诉求是**"开箱即用的安装体验"**，而非新增功能，属于对基础设施稳健性的维护性投入。

---

### 5. Bug 与稳定性

今日 **无新增 Bug、崩溃或回归问题报告**（0 条 Issues 更新）。  
但存在一项已识别、待修复的安装阶段缺陷：

| 严重程度 | 问题描述 | 状态 | Fix PR |
|---------|---------|------|--------|
| 中 | `better-sqlite3` 在全新安装时因缺少对应预构建二进制文件而报错，需手动重建 | 已知，待修复 | **PR #280** ([链接](https://github.com/TinyAGI/tinyagi/pull/280)) |

该问题主要影响新用户 onboarding 与 CI/CD 环境的一键部署，虽非运行时崩溃，但构成了首次使用的硬性阻断。

---

### 6. 功能请求与路线图信号

今日 **无新增功能请求（Feature Request）Issues**，也未出现与长期路线图直接相关的新讨论。  
从仅有的 PR #280 可提取间接信号：**项目当前优先级可能偏向"稳定性与开发者体验"而非功能扩张**。维护团队若计划下一版本，建议将原生依赖的自动化编译/重建流程纳入发布 checklist，以避免跨平台部署的碎片化问题。暂无明确的新功能路线图信号。

---

### 7. 用户反馈摘要

今日 Issues 区无新增评论，无法从当日数据中提取直接用户反馈。  
从 PR #280 的描述可间接推断用户痛点：

- **痛点**：在新环境（或不同 Node.js 版本/架构）首次安装时遭遇 `better-sqlite3` 编译失败，错误信息对非原生开发背景的用户不够友好。
- **使用场景**：开发者期望执行 `npm install` 后即可直接启动项目，而非额外执行平台特定的重建命令。
- **满意度推断**：当前安装流程存在摩擦，贡献者通过自动化脚本试图消除该摩擦，暗示现有文档或安装指南可能未充分覆盖此问题。

---

### 8. 待处理积压

今日需维护者关注的主要积压如下：

- **PR #280** — `fix(install): add postinstall script to auto-rebuild better-sqlite3`  
  链接：https://github.com/TinyAGI/tinyagi/pull/280  
  **提醒**：该 PR 创建于 2026-06-08，截至今日已逾 24 小时仍处于待审阅状态。其解决的是安装阶段的基础可用性问题，直接影响新用户首次部署成功率。建议维护者优先审阅、测试并合并，以减少因环境差异导致的用户流失。  
  Issues 区当前无长期未响应的重要条目。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*