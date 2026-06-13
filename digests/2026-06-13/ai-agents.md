# OpenClaw 生态日报 2026-06-13

> Issues: 500 | PRs: 483 | 覆盖项目: 12 个 | 生成时间: 2026-06-13 02:57 UTC

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
**日期：2026-06-13**

---

### 1. 今日速览

OpenClaw 在过去 24 小时展现出极高的社区活跃度：Issues 更新达 **500 条**（新开/活跃 408，关闭 92），PR 更新 **483 条**（待合并 345，已合并/关闭 138）。项目正式发布 **v2026.6.6** 稳定版及对应的 beta 版本，核心主题为全面收紧安全边界。与此同时，社区暴露了多个 **P0/P1** 级稳定性问题，包括网关内存泄漏和记忆搜索（memory_search）服务损坏，亟需维护者介入。整体来看，项目处于“高速迭代与紧急修复并行”的状态。

---

### 2. 版本发布

**v2026.6.6** 与 **v2026.6.6-beta.2** 已同步发布。  
- **更新内容**：本次版本为安全加固 release，安全边界在多个维度被“实质性收紧”（substantially tighter），涉及：对话记录（transcripts）、沙箱绑定（sandbox binds）、宿主环境继承、MCP stdio、Codex HTTP 访问、原生搜索策略、高权限发送者校验、已删除代理的 ACP 绕过、回环工具、Discord  moderation 以及 Teams 群组操作；同时包含 exec 工具的相关加固。  
- **破坏性变更与迁移**：官方 release note 未列出显式破坏性 API 变更，但安全策略的收紧意味着部分此前能通过的 exec 调用、沙箱绑定或 MCP 集成可能需要重新审批或调整环境变量继承方式。  
- **建议**：所有生产环境用户建议升级至 v2026.6.6，并复查 `exec-approvals` 与沙箱策略配置。  
  - 链接：https://github.com/openclaw/openclaw/releases

---

### 3. 项目进展

今日合并/关闭的关键工作集中在**稳定性修复**与**基础设施**两大方向：

- **已关闭的关键 Issues**：
  - [#75378](https://github.com/openclaw/openclaw/issues/75378) 网关事件循环饱和导致 1012 重启（并行子代理 spawn 场景）。
  - [#71491](https://github.com/openclaw/openclaw/issues/71491) Kimi K2.6 长对话下 `reasoning_content` 400 回归问题。
  - [#66561](https://github.com/openclaw/openclaw/issues/66561) `openai-codex` SSE 流被本地异常中止后表现为 408 超时。

- **已关闭的 PR**：
  - [#92568](https://github.com/openclaw/openclaw/pull/92568) `fix(cron)`: 支持取消活动任务账本（task-ledger）中的 cron 运行。

- **待合并但意义重大的 PR**：
  - [#92499](https://github.com/openclaw/openclaw/pull/92499) Memory/QMD 按代理隔离 mcporter sidecar（P1，XL 体量），解决多代理场景下的记忆核心隔离问题。
  - [#92086](https://github.com/openclaw/openclaw/pull/92086) 引入 Security Matrix 运行时事实审计模型，为工具调用策略提供确定性评估框架。
  - [#92513](https://github.com/openclaw/openclaw/pull/92513) 与 [#92578](https://github.com/openclaw/openclaw/pull/92578) 重构 WhatsApp 入站准入与 ACP 绑定，提升消息投递可靠性。
  - [#92341](https://github.com/openclaw/openclaw/pull/92341) 修复 CJK（中日韩）文本在混合记忆搜索中 `textScore=0` 的问题。

**整体评估**：项目在安全架构、记忆核心、IM 通道（WhatsApp/Telegram/Matrix）可靠性上均有实质性推进。

---

### 4. 社区热点

以下 Issues/PRs 在过去 24 小时讨论最活跃，反映了社区的核心诉求：

| 议题 | 评论 | 核心诉求 |
|------|------|----------|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) Text between tool calls leaks to messaging channels | 32 | **安全与 UX**：代理在工具调用之间的内部处理文本（错误处理、执行确认）被错误路由到 Slack/iMessage 等频道，造成信息泄漏和体验混乱。 |
| [#9443](https://github.com/openclaw/openclaw/issues/9443) Request: Prebuilt Android APK releases | 25 | **分发便利性**：Android 源码存在但无预编译 APK，非技术用户难以使用。 |
| [#32473](https://github.com/openclaw/openclaw/issues/32473) control ui requires device identity (HTTPS/localhost) | 17 | **部署门槛**：VPS + Docker 用户因安全上下文要求无法直接访问 Control UI，文档与错误提示不足。 |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) Tiered bootstrap file loading | 17 | **成本优化**：大型工作区的引导文件每次会话全量加载，浪费 LLM token，用户呼吁分层/按需加载。 |
| [#22676](https://github.com/openclaw/openclaw/issues/22676) Signal daemon stop() race condition | 17 | **稳定性**：SIG

---

## 横向生态对比

**个人 AI 助手/自主智能体开源生态横向对比分析**  
*分析日期：2026-06-13*

---

### 1. 生态全景

当前个人 AI 助手与自主智能体开源生态呈现“**头部狂奔、腰部分化、尾部沉寂**”的格局。以 OpenClaw 为代表的旗舰项目日活已达 Issue 500+/PR 480+ 的量级，安全边界收紧与多 IM 渠道深度适配成为共识；与此同时，稳定性债务（内存泄漏、死循环、上下文丢失）在多个项目中同步暴露，表明生态正从“功能堆砌”转向“生产加固”。中小项目则明显分化：CoPaw、NanoClaw 等保持高频迭代，而 TinyClaw、ZeptoClaw 等已陷入静默。

---

### 2. 各项目活跃度对比

| 项目 | 今日 Issues | 今日 PRs | 版本发布 | 健康度评估 |
|------|-------------|----------|----------|------------|
| **OpenClaw** | 500（408 活跃/新开，92 关闭） | 483（345 待合并，138 已合并/关闭） | **v2026.6.6** 稳定版 + beta | 🔶 极高活跃，P0/P1 稳定性问题并行 |
| **CoPaw** | 21（14 活跃，7 关闭） | 23（13 待合并，10 已合并/关闭） | 无（版本号修正至 1.1.12b1） | 🟢 高活跃，Issue 关闭率 33%，响应迅速 |
| **NanoClaw** | 4 活跃 | 18（10 已合并，8 待合并） | 无 | 🟢 高吞吐，Signal 能力快速补齐，技术债待消化 |
| **LobsterAI** | 1 长期 Issue 关闭 | 17（11 已合并/关闭） | 无 Tag，代码交付 **2026.6.12** | 🔶 中-高活跃，6 个 4 月初 PR 积压，存技术债风险 |
| **PicoClaw** | 6（5 活跃，1 关闭） | 14（11 待合并，3 已合并/关闭） | **Nightly v0.2.9-nightly.20260613** | 🟢 高活跃，聚焦协议完整性与健壮性修复 |
| **NanoBot** | 6 状态变动 | 29（9 已合并/关闭） | 无 | 🟢 健康迭代，学术背景驱动 |
| **Moltis** | 3 活跃 | 0 | 无 | 🔶 议题活跃、代码静默，处于需求收集期 |
| **Zeroclaw** | — | — | — | ⚪ 数据未提供 |
| **IronClaw** | — | — | — | ⚪ 数据未提供 |
| **TinyClaw / ZeptoClaw / EasyClaw** | 0 | 0 | 无 | ⚪ 过去 24h 无活动 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是当前生态中**绝对体量与工程成熟度**的标杆，其日活数据（Issue 500+ / PR 480+）较第二名 CoPaw（Issue 21 / PR 23）高出约一个数量级。

- **核心优势**：企业级安全架构最深。v2026.6.6 全面收紧对话记录、沙箱绑定、MCP stdio、Codex HTTP 等 10 余个安全维度，并引入 Security Matrix 运行时事实审计（PR #92086），在同类中尚无对等实现。
- **技术路线差异**：相比 LobsterAI 押注 Computer Use 桌面自动化、CoPaw 聚焦 Console 可视化，OpenClaw 更偏向“**安全基础设施 + 多租户 IM 网关**”——其记忆核心按代理隔离（PR #92499）、WhatsApp/Teams ACP 绑定重构均指向大规模多代理部署。
- **社区规模**：社区热点议题评论数可达 32 条（#25592 工具调用文本泄漏），远超其他项目（通常为 2–11 条），表明其用户基数与生产环境渗透率显著领先。

---

### 4. 共同关注的技术方向

以下需求在 **3 个及以上项目**中同步涌现，构成行业级共识：

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **安全沙箱与权限隔离** | OpenClaw、PicoClaw、Moltis、NanoClaw | OpenClaw 全面收紧 exec/沙箱策略；PicoClaw 要求 Telegram 私聊/群组/频道分级控制（#3114）；Moltis 探索 K8s + runtimeClassName 沙箱（#1118）；NanoClaw 修复 `create_agent` 权限绕过 |
| **IM 渠道可靠性与边界隔离** | OpenClaw、NanoClaw、PicoClaw | OpenClaw 修复 WhatsApp 入站准入与 ACP 绑定；NanoClaw 补齐 Signal 双向反应与附件收发；PicoClaw 修复 Telegram Forum `message_thread_id` 丢失 |
| **记忆与上下文管理** | OpenClaw、PicoClaw、CoPaw、LobsterAI | OpenClaw 记忆搜索服务损坏及按代理隔离；PicoClaw 修复 CJK 文本 `textScore=0`（#92341）；CoPaw 修复记忆搜索配置丢失；LobsterAI 修复停止流式后元数据丢失 |
| **多模型兼容性** | OpenClaw、PicoClaw、CoPaw、LobsterAI | OpenClaw 修复 Kimi K2.6 `reasoning_content` 400 与 Codex SSE 408；PicoClaw 适配 Gemini 3.5 Flash `thought_signature`（#3111）；CoPaw 修复 Gemini tool calling 回归；LobsterAI 长期 Issue #1 涉及 OpenAI API 类型配置 |
| **数据防丢失与持久化** | LobsterAI、CoPaw、NanoClaw | LobsterAI 5 项“未保存确认”专项；CoPaw 修复配置面板丢失；NanoClaw 落地灾难恢复备份 |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 企业级安全、多 IM 网关、记忆隔离 | 生产环境部署者、多租户平台 | 安全矩阵运行时审计、mcporter sidecar 记忆隔离 |
| **LobsterAI** | Computer Use、实时 ASR 语音协作 | 办公自动化、Cowork 场景用户 | 托管桌面运行时（1.0.7）、UIA breadcrumbs 诊断 |
| **CoPaw** | 可视化 Console、模块化 Agent 编排 | 开发者、低代码搭建者 | AgentScope 2.0 迁移、Runtime 2.0 + ToolCoordinator |
| **NanoClaw** | Signal 隐私通信、富媒体闭环 | 隐私敏感用户、Signal 生态 | Signal 附件/反应全双工适配、Agent 崩溃自愈 |
| **PicoClaw** | 边缘协议、多平台 Bot 接入 | 嵌入式/硬件开发者、IM 集成商 | Pico WebSocket 协议、`turn.done` 生命周期信号 |
| **Moltis** | 语音助手、本地优先 | 边缘部署、云原生用户 | 探索 FunASR/SenseVoice 本地 STT、K8s 沙箱后端 |
| **NanoBot** | 轻量高效、学术研究 | 研究人员、轻量用户 | HKUDS 学术背景，精简架构 |

---

### 6. 社区热度与成熟度

- **🔥 快速迭代期（第一梯队）**  
  **OpenClaw**（日活量级碾压，但 P0/P1 稳定性问题与 345 个待合并 PR 显示其处于“高速奔跑中换轮胎”）、**CoPaw**（23 PR/21 Issue 且关闭率 33%，用户痛点响应极快）、**NanoClaw**（24h 内 10 PR 合并，Signal 能力快速闭环）。

- **🛠️ 质量巩固期（第二梯队）**  
  **PicoClaw**（系统性消除 JSON 序列化静默错误，Nightly 构建稳步提升）、**LobsterAI**（2026.6.12 版本交付 Computer Use MVP，但 6 个 4 月初 PR 未合并提示治理节奏需优化）、**NanoBot**（29 PR 更新，健康但缺乏突破性发布）。

- **💤 需求沉淀期（第三梯队）**  
  **Moltis**（3 个活跃 Issue 但 0 PR，议题集中在 K8s 沙箱与本地 STT，尚未转化为代码）。

- **⚪ 停滞/休眠**  
  **TinyClaw、ZeptoClaw、EasyClaw**（24h 零活动）；**Zeroclaw、IronClaw**（数据缺失，无法评估）。

---

### 7. 值得关注的趋势信号

1. **安全左移成为 Agent 落地前提**  
   从 OpenClaw 的 Security Matrix 到 Moltis 的 K8s + gVisor 沙箱请求，社区已意识到“让 LLM 执行不可信代码”必须配套确定性隔离。对开发者的价值：Agent 执行层（sandbox/runtime）的设计优先级应高于工具数量堆砌。

2. **记忆核心隔离从“高级功能”变为“架构刚需”**  
   OpenClaw PR #92499（按代理隔离 mcporter

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
*日期：2026-06-13 | 仓库：github.com/HKUDS/nanobot*

---

### 1. 今日速览

NanoBot 在过去 24 小时内维持极高开发活跃度，共有 **29 个 PR** 更新（其中 9 条已合并/关闭）及 **6 个 Issue** 状态变动，社区迭代节奏健康。

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
**日期：** 2026-06-13  
**项目：** github.com/sipeed/picoclaw  

---

### 1. 今日速览

过去 24 小时 PicoClaw 维持高活跃度，共有 **14 个 PR** 更新（11 个待合并、3 个已关闭/合并）及 **6 个 Issue** 更新（5 个活跃、1 个关闭）。社区焦点集中在**协议完整性**（WebSocket 生命周期信号）、**多平台安全边界**（Telegram 群组/频道权限）与**模型兼容性**（Gemini 3.5 Flash 适配）三大方向。项目发布了基于 main 分支的 Nightly 构建，同时多个针对 JSON 序列化与类型断言的健壮性修复被合入主干，整体代码质量呈稳步提升态势。

---

### 2. 版本发布

**Nightly Build: v0.2.9-nightly.20260613.c362114c**  
- **发布说明：** 基于 `v0.2.9` 与 `main` 分支差异的自动化构建，包含截至 6 月 12 日的最新提交。  
- **稳定性提示：** 官方明确标注此为自动化构建，**可能不稳定**，建议仅用于测试环境。  
- **变更日志：** https://github.com/sipeed/picoclaw/compare/v0.2.9...main  
- **迁移注意：** 作为 Nightly 版本，无官方迁移指南；生产环境用户建议继续使用稳定版 `v0.2.9`。

---

### 3. 项目进展

今日共有 **3 个 PR/Issue 完成关闭或合并**，推动项目在稳定性与架构层面向前迈进：

- **PR #3113** `fix(channels): check json marshal/unmarshal errors` —— 修复频道配置序列化过程中三处错误被静默丢弃的隐患，提升配置加载的健壮性。  
  https://github.com/sipeed/picoclaw/pull/3113

- **PR #3112** `fix(tools): handle json.Marshal error in toolloop` —— 补全工具调用参数序列化时的错误处理，避免工具调用数据在对话历史中意外丢失为空字符串。  
  https://github.com/sipeed/picoclaw/pull/3112

- **PR #2551** `refactor: standardize channel identification` —— 关闭了一个关于解耦频道名称与提供商类型的架构重构 PR（标记为 stale），为后续多实例同提供商部署扫清技术债务。  
  https://github.com/sipeed/picoclaw/pull/2551

- **Issue #3109** `feat: Channel-level permission scoping` —— 关闭频道级权限范围控制请求，社区已将更具体的实现诉求转移至 Telegram 对话类型分级控制（见 #3114）。  
  https://github.com/sipeed/picoclaw/issues/3109

---

### 4. 社区热点

今日讨论最活跃、反响最集中的议题如下：

- **Issue #2984** —— 为 Pico WebSocket 客户端添加显式的 turn 完成信号（`turn.done`），收获 **2 条评论**与 **2 个 👍**。外部集成商迫切需要确定性的事件边界，以避免在流式响应中过早截断或重复触发。已有配套实现 PR #3116 提交。  
  https://github.com/sipeed/picoclaw/issues/2984

- **Issue #3012** —— Evolution 模式启用后每分钟持续消耗 Token（成本相关 Bug），收获 **2 条评论**。该 Issue 已被标记为 `stale`，但涉及用户直接成本，情绪关注度较高。  
  https://github.com/sipeed/picoclaw/issues/3012

- **Issue #3114** —— 请求 Telegram 渠道按私聊/群组/频道进行权限分级控制，与刚关闭的 #3109 形成呼应，反映出社区对**多租户场景下安全边界**的强烈诉求。  
  https://github.com/sipeed/picoclaw/issues/3114

---

### 5. Bug 与稳定性

今日报告的 Bug 与回归问题按严重程度排列如下：

| 严重程度 | 编号 | 摘要 | Fix PR |
|---|---|---|---|
| **高** | **#3111** | Gemini 3.5 Flash 工具执行失败：Google API 返回 `400 Bad Request`，因新模型 Agentic reasoning 要求缺失 `thought_signature` schema 字段。 | **暂无** |
| **高** | **#3110** | Telegram Forum 主题中 `message_thread_id` 被忽略：Bot 在正确主题触发 typing，但最终消息被错误发送至 `#General`，破坏话题隔离。 | **暂无** |
| **中** | **#3012** | Evolution 模式（Draft）下每分钟持续消耗 Token，导致运行成本不可控。 | **暂无** |
| **中** | **#3115** | 通用工具输出中的内联 `data:image/...` 字符串被误识别为真实媒体附件，导致会话历史损坏。 | **PR #3115**（待合并） |
| **低** | **#3045** | Matrix 标准用户 ID（`@alice:example.com`）因 `ParseCanonicalID` 按冒号分割而被 `allow_from` 静默拒绝。 | **PR #3045**（待合并） |

**已合入主干的稳定性修复：**  
- **PR #3113 / #3112**：系统性消除 JSON 序列化错误的静默处理。  
- **PR #3091**：为 `native_search` 类型断言补充 `ok` 检查。  
- **PR #3053**：为 Evolution 模块的 `LoadOrStore` 类型断言补充 `ok` 检查，避免 panic。  

---

### 6. 功能请求与路线图信号

结合今日 Issue 与待合并 PR，以下功能极有可能或已具备条件进入下一版本：

- **Pico 协议信号完整性（高优先级）**  
  Issue #2984 + PR #3116：补全 `turn.done` 生命周期

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-13 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

NanoClaw 在 24 小时内完成了 **10 个 PR** 的合并/关闭，同时新增 **8 个待合并 PR**，工程吞吐量维持高位，无新版本发布。核心进展集中在 Signal 消息生态闭环、Agent 崩溃自愈与路由可靠性修复，以及灾难恢复备份能力的落地。社区侧暴露出 4 个活跃 Issue，涵盖消息去重静默丢响应、MCP 工具无超时阻塞、`create_agent` 权限绕过及 Telegram swarm 迁移路径不明等问题；稳定性与安全类反馈占比显著，项目整体处于“**高速迭代、待消化技术债**”的状态。

---

### 3. 项目进展

今日合并/关闭的 10 个 PR 显著扩展了渠道能力与系统韧性：

- **Signal 渠道能力闭环**  
  - [#2203](https://github.com/nanocoai/nanoclaw/pull/2203) 支持双向消息反应（inbound + outbound），补齐聊天交互最后一环。  
  - [#2071](https://github.com/nanocoai/nanoclaw/pull/2071) 将所有非音频附件统一路由至 inbox 路径，Agent 可本地读取。  
  - [#2040](https://github.com/nanocoai/nanoclaw/pull/2040) 补齐出站附件发送能力，Signal 适配器正式具备生产级富媒体交互能力。

- **Agent 核心稳定性与路由修复**  
  - [#2670](https://

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-06-13 | 仓库：nearai/ironclaw*

---

### 1. 今日速览

过去24

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-13 | 仓库：netease-youdao/LobsterAI*

---

### 1. 今日速览

过去24小时，LobsterAI 维护活跃度处于**中高水位**：17个PR发生更新，其中11个已完成合并或关闭，1个长期Issue（#1）被关闭，但无新GitHub Release标签发布。核心事件是 `release/2026.6.11` 分支合并入主分支，正式交付 **2026.6.12 版本**，带来 Computer Use MVP、实时ASR语音输入等重大能力。同时，社区集中修复了5处数据防丢失场景，体现出对用户体验稳定性的高度关注。然而，6个创建于4月初的PR至今仍处于待合并状态，涉及网关崩溃、国际化等基础问题，技术债积压风险值得警惕。

---

### 2. 版本发布

**无新的 GitHub Release 发布。**

但代码层面已完成 **2026.6.12 版本** 的交付：PR #2158 将发布分支合并至 `main`，包含多项功能更新与缺陷修复（详见“项目进展”）。用户需通过源码或自动更新渠道获取最新构建，官方尚未打附 Release Notes 的 GitHub Tag。

---

### 3. 项目进展

今日合并/关闭的重要 PR 推动项目在产品能力与稳定性上实现双重迈进：

- **2026.6.12 版本发布合并** ([#2158](https://github.com/netease-youdao/LobsterAI/pull/2158))  
  将 `release/2026.6.11` 合并入 `main`，正式交付：Computer Use MVP 及内置 Computer Use 工具包；Cowork 场景的实时 ASR 语音输入；HTML Artifact 公共分享模式选择；图片与 SVG Artifact 分享支持。标志着项目向 AI Agent 的计算机控制与实时协作方向迈出关键一步。

- **Computer Use 运行时升级** ([#2156](https://github.com/netease-youdao/LobsterAI/pull/2156))  
  托管运行时升级至 1.0.7，引入 UIA breadcrumbs 诊断能力，用于定位 helper 异常退出问题，提升桌面自动化可靠性。

- **文生图扩展名修正** ([#2157](https://github.com/netease-youdao/LobsterAI/pull/2157))  
  保存生成图片时优先根据文件字节识别真实格式，以真实扩展名覆盖服务端返回的错误后缀，解决 PNG 内容被误存为 `.jpg/.jpeg/.webp` 的问题，并补充了回归测试。

- **协作流稳定性修复** ([#2154](https://github.com/netease-youdao/LobsterAI/pull/2154), [#2153](https://github.com/netease-youdao/LobsterAI/pull/2153))  
  修复手动停止流式输出后模型元数据丢失的问题；修复 OpenClaw 模型归一化过程中同名包模型与自定义模型选择冲突的问题。

- **数据防丢失专项（5项）** ([#1473](https://github.com/netease-youdao/LobsterAI/pull/1473), [#1474](https://github.com/netease-youdao/LobsterAI/pull/1474), [#1475](https://github.com/netease-youdao/LobsterAI/pull/1475), [#1476](https://github.com/netease-youdao/LobsterAI/pull/1476), [#1477](https://github.com/netease-youdao/LobsterAI/pull/1477))  
  集中为 Agent 创建弹窗、Agent 设置面板、MCP 服务器配置弹窗添加“未保存确认”机制；为会话切换/视图导航时的输入框草稿增加即时持久化；为历史消息“重新编辑”操作增加覆盖确认。显著降低用户因误操作导致配置与内容静默丢失的风险。

- **实时 ASR 防重入** ([#2155](https://github.com/netease-youdao/LobsterAI/pull/2155))  
  修复 Cowork 语音输入流程中实时 ASR 可能重复启动的竞态问题。

---

### 4. 社区热点

- **Issue #1 — OpenAI API 类型配置错误（今日关闭，7条评论）**  
  链接：[https://github.com/netease-youdao/LobsterAI/issues/1](https://github.com/netease-youdao/LobsterAI/issues/1)  
  该Issue历时近4个月，今日被关闭。用户在 Mac OS (Intel) 上配置 MiniMax API key 测试通过后，切换至 OpenAI message type 即遭遇 400 API Error。7条评论的讨论热度反映出**多API提供商兼容性**仍是社区最关注的上手痛点之一，维护者需持续关注不同厂商API参数映射的健壮性。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-13 | 分析师：开源项目观察*

---

### 1. 今日速览
过去24小时，Moltis 社区呈现“议题活跃、代码静默”的状态：共有 **3 条 Issue** 保持更新，但无 Pull Request 进出，亦无新版本发布。讨论焦点集中在 AI Agent 的安全沙箱、本地化语音输入以及 MCP 协议授权兼容性三个维度，反映出社区在扩展多模态能力与生产级部署安全上的迫切需求。整体活跃度中等，项目当前处于需求收集与 Bug 诊断阶段，代码主支尚未产生直接推进。

---

### 2. 版本发布
今日无新版本发布。

---

### 3. 项目进展
今日 **无 PR 合并或关闭**，代码层面暂无可见推进。项目进展以需求澄清与 Bug 复现为主，尚未形成可落地的代码贡献。建议维护者在活跃议题中及时给出技术方向反馈，以加速从“讨论”到“PR”的转化。

---

### 4. 社区热点
今日社区讨论围绕以下三条议题展开，按评论热度排序：

- **#1115 [Bug]: Fastmail MCP Authorisation**（[链接](https://github.com/moltis-org/moltis/issues/1115)）  
  评论数最多（2 条）。用户 @kmath313 反馈在使用 Fastmail 服务进行 MCP（Model Context Protocol）授权时遇到障碍，且已按最新版本复现。该议题揭示了 Moltis 在对接第三方邮件 MCP Server 时的 OAuth/授权流程可能存在边界情况，社区核心诉求在于**提升 MCP 生态对主流邮件服务的兼容性**。

- **#1118 [Feature]: Add Kubernetes-native sandbox backend with runtimeClassName support**（[链接](https://github.com/moltis-org/moltis/issues/1118)）  
  由 @AzgadAGZ 提出，要求新增 `kubernetes` 沙箱后端，通过 `runtimeClassName` 支持 Kata Containers、gVisor 等 OCI 运行时，实现 VM 级隔离。这反映了企业用户和高级开发者在运行**不可信 LLM 生成代码**时对强隔离与云原生编排的核心诉求。

- **#1102 Feature: Add FunASR/SenseVoice as local STT engine**（[链接](https://github.com/moltis-org/moltis/issues/1102)）  
  @LauraGPT 提议集成 FunASR/SenseVoice 作为本地语音识别引擎，强调 SenseVoice-Small 约 70ms 的超低延迟与 Paraformer-streaming 的原生流式能力。该请求切中**隐私敏感场景**与**实时交互体验**，是语音助手类项目的关键基础设施补充。

---

### 5. Bug 与稳定性

| 议题 | 严重程度 | 状态 | 修复 PR | 说明 |
|------|---------|------|---------|------|
| [#1115](https://github.com/moltis-org/moltis/issues/1115) Fastmail MCP Authorisation | 🟡 **中** | 待诊断 | 无 | 影响 Fastmail 用户的 MCP 授权流程。用户已完成预检清单并使用最新版复现，需维护者确认是否为 OAuth 回调、Scope 配置或 MCP Client 握手问题。 |

---

### 6. 功能请求与路线图信号

1. **Kubernetes-native Sandbox（[#1118](https://github.com/moltis-org/moltis/issues/1118)）** —— **高优先级架构信号**  
   随着 Agent 执行不可信代码成为常态，基于 K8s + `runtimeClassName` 的弹性沙箱是生产落地的关键路径。若维护者计划推进企业级部署，此功能极可能纳入后续大版本路线图，建议与现有 Docker/Podman 沙箱方案统一评估。

2. **本地 STT 引擎 FunASR/SenseVoice（[#1102](https://github.com/moltis-org/moltis/issues/1102)）** —— **中-高优先级体验信号**  
   当前 Moltis 作为语音助手项目，依赖云端 STT 会带来延迟与隐私瓶颈。SenseVoice 的 70ms 延迟指标对实时对话体验提升显著，且支持流式识别与多语言，符合边缘部署趋势。若项目计划强化“本地优先”能力，该请求值得优先排期。

---

### 7. 用户反馈摘要

- **真实痛点**：  
  - MCP 协议与特定第三方服务（Fastmail）的授权集成存在“最后一公里”兼容性问题；  
  - 现有沙箱方案无法满足云原生环境下的强隔离与弹性扩缩容需求；  
  - 缺乏低延迟、可离线运行的本地语音识别方案，影响实时语音交互体验。

- **使用场景**：  
  用户希望在 K8s 集群中安全执行 Agent 生成的命令；在本地设备上获得接近实时的语音输入体验；通过 MCP 连接个人邮件服务实现日程与邮件管理。

- **情绪与满意度**：  
  #1102 与 #1118 的反馈呈现**建设性期待**，用户主动提供了技术选型与架构建议；#1115 则带有明确的 Bug 报告属性（已执行预检清单、使用最新版本），显示用户愿意配合维护者进行深度诊断。

---

### 8. 待处理积压

以下议题已长期或即将进入“无维护者响应”状态，提醒维护者关注以避免需求沉没：

- **[#1102](https://github.com/moltis-org/moltis/issues/1102)**（创建于 2026-06-04，距今已 **9 天**）：本地 STT 引擎请求已获 1 条社区评论，但无维护者正式回应。建议评估 SenseVoice 集成可行性并给出 `enhancement` 或 `help wanted` 标签。
- **[#1115](https://github.com/moltis-org/moltis/issues/1115)**（创建于 2026-06-11）：Bug 类议题已积累 2 条评论，若 24–48 小时内无维护者复现确认，可能影响 MCP 模块的用户信任度。
- **[#1118](https://github.com/moltis-org/moltis/issues/1118)**（创建于 2026-06-12）：架构级 Feature 请求，建议维护者将其与现有 sandbox 后端方案进行对比，决定是否纳入设计讨论（RFC）阶段。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw（QwenPaw）项目动态日报**  
*日期：2026-06-13 | 仓库：agentscope-ai/QwenPaw*

---

### 1. 今日速览

过去 24 小时，CoPaw 项目保持**高活跃度**：Issues 更新 21 条（14 条新开/活跃，7 条关闭），PR 更新 23 条（13 条待合并，10 条已合并/关闭），无新版本发布。社区重心集中在**稳定性修复**（前端配置丢失、附件下载、数学公式渲染）与**架构升级预研**（AgentScope 2.0 迁移、Runtime 2.0 模块化）。整体项目健康度良好，Issue 关闭率 33%，关键用户痛点得到快速响应。

---

### 2. 版本发布

**今日无新版本发布。**  
虽然社区合并了版本号修正 PR（[#5159](https://github.com/agentscope-ai/QwenPaw/pull/5159)、[#5157](https://github.com/agentscope-ai/QwenPaw/pull/5157)），将版本调整至 `1.1.12b1`，但正式的 Release 构建尚未产出。

---

### 3. 项目进展

今日已合并/关闭的 10 个 PR 显著推进了 Console 体验、发布安全与架构演进：

- **Runtime 2.0 架构落地**：[#5078](https://github.com/agentscope-ai/QwenPaw/pull/5078) 将单体 `Runner` 执行路径重构为模块化 Runtime 2.0，并引入 `ToolCoordinator` 层，为后续 AgentScope 2.0 迁移奠定运行时基础。
- **发布安全加固**：[#5121](https://github.com/agentscope-ai/QwenPaw/pull/5121) 在构建与 PyPI/DockerHub 发布之间引入“发布验证门禁”，要求制品必须通过端到端安装、启动与健康检查，降低缺陷版本外流风险。
- **Console 体验三连修**：
  - [#5144](https://github.com/agentscope-ai/QwenPaw/pull/5144) 强制渲染 `Collapse` 面板，根治“向量模型与自动记忆搜索配置未展开即丢失”问题；
  - [#5147](https://github.com/agentscope-ai/QwenPaw/pull/5147) 修复 Coding Mode 刷新页面后 Session 回退到首个会话的 bug；
  - [#5154](https://github.com/agentscope-ai/QwenPaw/pull/5154) 重构记忆搜索工具结果样式，解决 UI 表格渲染异常。
- **桌面端与 CLI 健壮性**：[#4144](https://github.com/agentscope-ai/QwenPaw/pull/4144) 修复 Windows 下 `0.0.0.0` 通配地址 readiness 检查失败；[#5022](https://github.com/agentscope-ai/QwenPaw/pull/5022) 为 Agent 工作空间恢复路径增加校验，防止写入受管目录。

---

### 4. 社区热点

今日讨论最活跃的话题反映了用户对**核心功能可靠性**与**架构升级节奏**的高度关注：

| 话题 | 评论数 | 状态 | 链接 | 诉求分析 |
|---|---|---|---|---|
| 定时任务“静默失败”：生成后无法触发，且不可手动编辑 | 11 | Open | [#5064](https://github.com/agentscope-ai/QwenPaw/issues/5064) | 用户将定时任务视为关键自动化能力，当前“无报错但不执行”严重损害信任。 |
| AgentScope 2.0 后端迁移计划 | 10 | Open | [#4727](https://github.com/agentscope-ai/QwenPaw/issues/4727) | 社区迫切希望了解迁移时间表、破坏性变更范围及迁移指南。 |
| v1.1.11.post2 附件下载 404（docx/pdf） | 6 | **Closed** | [#5140](https://github.com/agentscope-ai/QwenPaw/issues/5140) | 非文本附件下载链路存在 MIME/路由处理缺陷，已快速修复。 |

---

### 5. Bug 与稳定性

按严重程度排列的今日 Bug 报告与修复状态：

**🔴 严重（影响可用性）**
- **Docker 自动宕机重启**（[#5155](https://github.com/agentscope-ai/QwenPaw/issues/5155)）：v1.1.11 Docker 环境部署后不定时重启，尚无 fix PR。
- **对话思考逻辑死循环**（[#5162](https://github.com/agentscope-ai/QwenPaw/issues/5162)）：Agent 在特定上下文中陷入循环，需维护者介入诊断。
- **长对话后无响应**（[#5161](https://github.com/agentscope-ai/QwenPaw/issues/5161)）：上下文累积后系统卡死，疑似内存/上下文窗口管理缺陷。

**🟡 中危（功能回归或兼容性问题）**
- **Gemini tool calling 回归**（[#5163](https://github.com/agentscope-ai/QwenPaw/issues/5163)）：v1.1.10 → v1.1.11.post2 出现回归，模型无法正常调用内置工具。
- **Python 3.13 兼容：缺失 `imghdr` 模块**（[#5166](https://github.com/agentscope-ai/QwenPaw/issues/5166)）：TeamChat 插件在 Python 3.13 安装失败，需替换已弃用标准库。
- **执行详情未折叠干扰用户**（[#5145](https://github.com/agentscope-ai/QwenPaw/issues/5145)）：UI 冗余展示执行细节。

**🟢 已修复（24h 内关闭）**
- 附件下载 404（[#5140](https://github.com/agentscope-ai/QwenPaw/issues/5140)）
- 记忆搜索配置丢失（[#5137](https://github.com/agentscope-ai/QwenPaw/issues/5137)）
- 记忆搜索 UI 空结果（[#5098](https://github.com/agentscope-ai/QwenPaw/issues/5098)）
- 数学公式根号渲染错误

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