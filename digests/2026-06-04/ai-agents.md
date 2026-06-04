# OpenClaw 生态日报 2026-06-04

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-04 03:36 UTC

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



---

## 横向生态对比

**个人 AI 助手 / 自主智能体开源生态横向对比分析报告**  
*数据日期：2026-06-04*

---

### 1. 生态全景

当前个人 AI 助手与自主智能体开源生态呈现**“头部高速迭代、尾部静默分化”**的显著格局。以 NanoBot、LobsterAI、Moltis 为代表的活跃项目单日合并 PR 超过 10 个，技术焦点已从“单轮对话能力”快速转向**多智能体协作（A2A）、MCP 工具链生产化加固、以及容器级部署兼容性**。与此同时，ZeptoClaw、TinyClaw 等项目陷入零社区贡献的静默期，显示生态资源正加速向具备工程化落地能力的项目集中。整体而言，该领域正处于从“功能验证”向“生产可用”转型的关键窗口期，稳定性、安全性和渠道碎片化成为新的竞争壁垒。

---

### 2. 各项目活跃度对比

| 项目 | 新增 Issues | PR 活动 | 版本发布 | 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **NanoBot** | 33 条 | 33 条（20 合并/关闭） | 无 | 🔥 高活跃，高代码吞吐 |
| **LobsterAI** | 1 条付费投诉 | 14 条合并/关闭 | `2026.6.3` | 🔥 极高活跃，商业级交付 |
| **Moltis** | 新开 5 / 关闭 9 | 4 条待审，0 合并 | `20260603.01` / `20260602.05` | ⚡ 高活跃，审阅瓶颈 |
| **NanoClaw** | 1 条（#2680） | 9 条待审，0 合并 | 无 | ⚡ 高输入低吞吐，审阅积压 |
| **PicoClaw** | 未明确 | 11 条变更（2 合并） | 无 | ✅ 中等活跃，稳步修固 |
| **EasyClaw** | 0 | 0 | `v1.8.28` / `v1.8.29` | ✅ 核心维护活跃，社区静默 |
| **ZeptoClaw** | 0 | 16 条（全为 Dependabot，0 合并） | 无 | ⚠️ 静默维护，供应链滞后 |
| **TinyClaw** | 0 | 0 | 无 | ⚠️ 完全停滞 |
| **OpenClaw** | — 数据未提供 — | — 数据未提供 — | — 数据未

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
**日期：2026-06-04**  
**仓库：** [HKUDS/nanobot](https://github.com/HKUDS/nanobot)

---

### 1. 今日速览

过去 24 小时，NanoBot 项目呈现**高活跃度**，共产生 **66 个事件**（33 条 Issues + 33 条 PRs），其中 **20 个 PR 完成合并或关闭**，**7 个 Issue 关闭**，代码集成吞吐量显著。今日无新版本发布，但主分支在**稳定性、安全性与交互体验**三个维度持续迭代：MCP 会话自动重连、QQ 频道配对修复、飞书提及清理、WebUI 全局快捷键等补丁密集落地。社区侧，多智能体架构与轻量级记忆检索仍是长期热议焦点，今日更出现原生 Agent-to-Agent（A2A）编排的正式提案，显示用户正从“单助手”向“多智能体团队”场景演进。

---

### 2. 版本发布

**无。**  
今日未发布新版本。所有改进均通过主分支 PR 直接集成。

---

### 3. 项目进展

今日合并/关闭的重要 PR 推动了以下关键改进：

- **MCP 稳定性：自动重连机制**  
  PR [#4171](https://github.com/HKUDS/nanobot/pull/4171) 已合并。当 MCP 服务器会话因网络或服务端原因终止（`Session terminated`）时，nanobot 现在能自动检测、重建连接并替换失效的 tool/resource wrapper，且对当前调用自动重试一次，无需重启整个进程。这直接解决了 Issue [#4168](https://github.com/HKUDS/nanobot/issues/4168) 报告的“随机时间后无法连接 MCP”问题。

- **记忆模块：安全与耐久性加固**  
  PR [#4183](https://github.com/HKUDS/nanobot/pull/4183) 已合并。对 `memory.py` 进行 6 项结构性改进：新增 PII 脱敏（自动擦除 secret/email）、原子写入（避免内存文件损坏）、写入校验与隐私边界加固。零新增依赖，仅提升现有路径的可靠性。

- **WebUI 交互：新增全局快捷键**  
  PR [#4181](https://github.com/HKUDS/nanobot/pull/4181) 已合并。新增 `Cmd/Ctrl+Shift+O` 快速开启新对话，与 ChatGPT、Claude.ai 等主流产品保持一致，补齐了原先仅支持 `Cmd/Ctrl+K` 搜索的快捷键缺口。

- **QQ 频道：修复未授权 C2C 用户配对**  
  PR [#4180](https://github.com/HKUDS/nanobot/pull/4180) 已合并。修复了 QQ 渠道在未授权 C2C 场景下未正确发送配对码的问题，提升渠道接通率。

- **代码健康：恢复顶层导入顺序**  
  PR [#4174](https://github.com/HKUDS/nanobot/pull/4174) 已合并。修复了 `nanobot.cli.commands` 等模块的 E402 导入顺序回归，保持 lint 干净。

此外，**Azure OpenAI AAD 身份验证**（[#4126](https://github.com/HKUDS/nanobot/pull/4126)）、**Agent 运行级钩子生命周期**（[#4176](https://github.com/HKUDS/nanobot/pull/4176)）以及**博查（Bocha）中文搜索提供商**（[#4182](https://github.com/HKUDS/nanobot/pull/4182)）等 PR 仍在开放评审中，若合并将进一步扩展企业接入与中文生态能力。

---

### 4. 社区热点

今日讨论最活跃的议题反映了用户在**多智能体、安全、长任务与记忆系统**上的深层诉求：

| Issue | 状态 | 评论 | 👍 | 核心诉求 |
|-------|------|------|-----|----------|
| [#222](https://github.com/HKUDS/nanobot/issues/222) Multi agents setup | OPEN | 10 | 7 | **多智能体配置与文档**。用户已发现配置层面似乎支持多代理，但缺乏官方指南，需求从“是否支持”升级为“如何最佳实践”。 |
| [#979](https://github.com/HKUDS/nanobot/issues/979) 防止执行 rm 指令是防不住 AI 的 | CLOSED | 5 | 0 | **安全边界绕过**。用户通过社会工程学诱导 AI 执行 `rm -rf`，揭示单纯依赖指令黑名单的防护不足，引发对沙箱与权限模型的反思。 |
| [#1022](https://github.com/HKUDS/nanobot/issues/1022) Long-running task 无响应 | CLOSED | 4 | 3 | **长任务可靠性**。Agent 对长时间任务返回 “Starting execution now” 后静默失败，影响批量数据处理场景。 |
| [#80](https://github.com/HKUDS/nanobot/issues/80) Add lightweight memory retrieval? | OPEN | 4 | 0 | **记忆检索效率**。建议引入 BM25/TF-IDF 做 top-k 相关记忆召回，替代全量注入，以降低 token 消耗并提升长记忆场景下的相关性。 |
| [#954](https://github.com/HKUDS/nanobot/issues/954) Progress streaming leaks internal tool calls | OPEN | 3 | 1 | **UX 隐私**。v0.1.4 的进度流将 `exec()`、`read_file()` 等内部工具调用暴露到用户聊天界面，破坏交互纯净度。 |
| [#912](https://github.com/HKUDS/nanobot/issues/912) Task-Specific Model Configuration | OPEN | 3 | 3 | **模型路由**。希望对话、工具调用、浏览器操作等任务类型可分别配置不同模型（如轻量模型聊天、强模型编码）。 |

---

### 5. Bug 与稳定性

按严重程度排列的今日活跃 Bug：

- **🔴 高：MCP 会话随机终止**  
  Issue [#4168](https://github.com/HKUDS/nanobot/issues/4168) — Streamable MCP 服务器在运行一段时间后断开，报 `McpError: Session terminated`。  
  **状态：✅ 已有 Fix PR [#4171](https://github.com/HKUDS/nanobot/pull/4171) 合并。**

- **🔴 高：文件系统工具不强制 `restrict_to_workspace`**  
  Issue [#143](https://github.com/HKUDS/nanobot/issues/143) — `ReadFileTool`、`WriteFileTool` 等可直接访问任意路径，即使配置开启 workspace 限制。存在数据泄露与越权写入风险。  
  **状态：OPEN，无关联 PR。**

- **🔴 高：`exec` 工具幻觉严重**  
  Issue [#937](https://github.com/HKUDS/nanobot/issues/937) — 用户反馈即使使用 SOTA LLM，`exec` 工具仍频繁产生幻觉命令，导致评估中断。  
  **状态：OPEN。**

- **🟡 中：进度流泄漏内部工具调用**  
  Issue [#954](https://github.com/HKUDS/nanobot/issues/954) — 内部工具调用被广播到用户聊天。  
  **状态：OPEN。**

- **🟡 中：Telegram / Discord 媒体文件永不清理**  
  Issue [#896](https://github.com/HKUDS/nanobot/issues/896) — 下载到 `~/.nanobot/media/` 的媒体无清理机制，磁盘无限增长。  
  **状态：OPEN。**

- **🟡 中：WhatsApp 频道 WebSocket 反复断连**  
  Issue [#150](https://github.com/HKUDS/nanobot/issues/150) — Linux + Python 3.12 环境下 WhatsApp 网关连接循环断开。  
  **状态：OPEN。**

- **🟢 低（已关闭）：媒体路径超出 Workspace**  
  Issue [#984](https://github.com/HKUDS/nanobot/issues/984) — Telegram 语音/视频下载路径在 workspace 外，导致 `restrictToWorkspace=true` 时技能无法访问。  
  **状态：CLOSED。**

---

### 6. 功能请求与路线图信号

结合今日 Issues 与开放 PR，以下需求最可能塑造下一版本方向：

- **原生 A2A 编排（Agent-to-Agent）**  
  Issue [#4179](https://github.com/HKUDS/nanobot/issues/4179)（今日新建）提出在单实例内通过 Peer Subagents 实现 Supervisor → Researcher → Writer 的协作流，而非依赖外部多实例。这与高赞 Issue [#222](https://github.com/HKUDS/nanobot/issues/222) 的多智能体诉求形成呼应，可能成为核心架构演进信号。

- **任务级模型路由**  
  Issue [#912](https://github.com/HKUDS/nanobot/issues/912) 请求按任务类型拆分模型配置。随着 nanobot 支持浏览器、代码执行、对话等异构任务，该功能的性价比极高，社区投票（3👍）积极。

- **轻量级记忆检索（BM25/TF-IDF）**  
  Issue [#80](https://github.com/HKUDS/nanobot/issues/80) 建议用低成本检索替代全量记忆注入。记忆膨胀是当前个人助手的普遍痛点，且实现轻量（无新增大依赖），纳入可行性高。

- **子代理控制平面（MVP）**  
  Issue [#1006](https://github.com/HKUDS/nanobot/issues/1006) 提出 `list` / `kill` 子代理命令。若 [#4179](https://github.com/HKUDS/nanobot/issues/4179) 的多智能体协作落地，控制平面将是必要运维基础。

- **博查（Bocha）搜索提供商**  
  PR [#4182](https://github.com/HKUDS/nanobot/pull/4182) 待合并。作为 DeepSeek 官方搜索 API，博查的接入将显著改善中文场景的实时信息获取能力。

- **渠道扩展：微信、Mattermost、SimpleX**  
  Issues [#192](https://github.com/HKUDS/nanobot/issues/192)、[#1011](https://github.com/HKUDS/nanobot/issues/1011)、[#240](https://github.com/HKUDS/nanobot/issues/240) 持续呼吁新通信渠道，显示用户对“个人

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
*日期：2026-06-04 | 仓库：sipeed/picoclaw*

---

### 1. 今日速览

PicoClaw 今日维持中等活跃度的维护节奏，过去 24 小时内 Issues 与 PR 队列均有更新，但无新版本发布。社区代码贡献活跃，共 11 个 PR 发生状态变更，其中 2 个已关闭/合并（Go 安全补丁与 MQTT TLS 修复），剩余 9 个待审阅。讨论热度集中在**流式 HTTP 支持**与**单例进程守护的稳定性**两个主题，反映出用户对延迟敏感场景与生产环境健壮性的双重诉求。整体项目处于稳步修固阶段，但高优先级 Bug 的修复 PR 尚未合入，合并带宽仍是当前瓶颈。

---

### 2. 版本发布

今日无新版本发布。最新 Release 仍停留在先前版本。

---

### 3. 项目进展

今日共有 **2 个 PR 完成合并/关闭**，主要推进了安全基线加固与通道安全：

- **#2997** — **fix(deps): bump go from 1.25.10 to 1.25.11**  
  链接：https://github.com/sipeed/picoclaw/pull/2997  
  合并了 Go 运行时升级，修复安全漏洞 **GO-2026-5039**（`net/textproto` 错误消息中 HTTP 头部未转义）。该变更属于非破坏性安全补丁，消除了潜在的错误信息注入风险。

- **#2899** — **fix: add configurable TLS verification for MQTT channel**  
  链接：https://github.com/sipeed/picoclaw/pull/2899  
  关闭了 MQTT 通道长期硬编码 `InsecureSkipVerify = true` 的问题，新增 `TLSSkipVerify` 配置项（默认 `false`）。用户如需使用自签名证书可显式开启，显著降低了默认配置下的中间人攻击面。

此外，贡献者 `@chengzhichao-xydt` 单日密集提交 4 个修复 PR（#2985、#2992、#2995、#2996），分别针对 `/context` 阈值显示歧义、会话历史别名提升污染、README 文档滞后以及 `exec` 工具 JSON 序列化错误被静默忽略等问题，显示出社区在个人 AI 助手边缘场景上的持续打磨。

---

### 4. 社区热点

今日讨论最活跃、反映社区核心诉求的议题如下：

- **#2404 [Feature] Add in config to send streaming HTTP request**（11 条评论，1 👍）  
  链接：https://github.com/sipeed/picoclaw/issues/2404  
  这是目前评论数最多的开放 Issue。用户明确要求像 OpenAI Python 客户端一样通过配置项 `"streaming": true` 支持流式 HTTP 请求，以降低 LLM 响应延迟。该需求自 4 月 7 日创建以来持续获得关注，但尚无对应实现 PR，已成为 Provider 配置域的头部功能缺口。

- **#2720 [BUG] Singleton PID check doesn't verify process identity**（8 条评论，高优先级）  
  链接：https://github.com/sipeed/picoclaw/issues/2720  
  生产环境部署热点问题。网关崩溃后若 PID 文件残留，且该 PID 被系统其他进程（如 `systemd-resolved`）复用，将导致网关陷入启动失败循环。社区对 Linux 守护进程管理的健壮性表达了强烈关切，目前已有两个社区贡献的修复方案（#2813、#2955）等待维护者裁决。

---

### 5. Bug 与稳定性

按严重程度排列的今日活跃 Bug 及修复状态：

| 严重程度 | Issue | 描述 | Fix PR 状态 |
|---|---|---|---|
| 🔴 **High** | #2720 | 单例 PID 检查不验证进程身份，陈旧 PID 导致网关崩溃循环 | **已有 2 个 PR 待合并**：#2813（更新版）、#2955 |
| 🟡 **Medium** | #2958 | pico WebSocket 通道连续请求时 `tool_calls` 消息被丢弃，仅首轮工具调用可见 | **已有 PR 待合并**：#2957 |
| 🟡 **Medium** | #2954 | 不支持 32 位 Android 系统，阻断 Termux 等移动端部署 | **暂无 PR** |
| 🟢 **Fixed** | — | Go 运行时安全漏洞 GO-2026-5039 | **已修复**：#2997 |
| 🟢 **Fixed** | — | MQTT 通道 TLS 验证硬编码跳过 | **已修复**：#2899 |

**关键风险提醒**：高优先级 Bug #2720 存在两个功能重叠的社区修复 PR（#2813 与 #2955），建议维护者尽快审阅并选择合入其一，避免生产环境启动故障持续扩散。

---

### 6. 功能请求与路线图信号

- **流式 LLM 请求配置（#2404）**  
  用户希望在 Provider 配置中增加原生流式开关，以对接支持 SSE/Stream 的 LLM 后端。该需求讨论深度足够（11 条评论），且与当前 AI 网关低延迟趋势高度契合，**建议纳入下一版本（如 v0.3.0）的 Provider/Config 域路线图**。

- **MCP 动态头部转发（#2696）**  
  链接：https://github.com/sipeed/picoclaw/pull/2696  
  PR 已提交近一个月，允许通道通过 `mcp:` 前缀在 `InboundContext.Raw` 中注入每请求 HTTP 头（如 `Authorization`）。这是企业级 MCP 集成的关键能力，长期无审阅反馈，若合并将显著增强 PicoClaw 在 AI Agent 工具链中的适配广度。

---

### 7. 用户反馈摘要

从今日活跃的 Issues 与 PR 中提炼的真实用户声音：

- **延迟敏感场景痛点**：用户明确对比 OpenAI Python 客户端，指出 PicoClaw 缺乏流式输出配置，导致大模型响应体感延迟高。
- **生产环境守护进程不可靠**：Linux 用户反馈 PID 文件残留与进程身份验证缺失是部署“杀手”，直接影响 systemd 托管稳定性。
- **移动端覆盖不足**：32 位 Android/Termux 用户被完全阻断，反映出边缘设备与低功耗场景的支持缺口。
- **多轮 Agent 交互不可靠**：通过 pico 通道（WebSocket）进行连续工具调用时，后续 `tool_calls` 消息丢失，严重影响 Agent 工作流连续性。
- **配置可见性与合并行为困惑**：用户对 `/context` 中 summarize 与 compress 阈值的区别、以及 `security.yml` 合并时意外覆盖通道启用状态感到困惑，相关修复已提交但待合并。

---

### 8. 待处理积压

以下 Issue/PR 长期未获得维护者响应或合并，建议优先关注：

- **#2404**（创建于 2026-04-07，stale 边缘）  
  链接：https://github.com/sipeed/picoclaw/issues/2404  
  流式 HTTP 功能请求已开放近两个月，11 条社区讨论但无维护者排期或里程碑标记，存在需求流失风险。

- **#2813 / #2955**（PID 身份验证修复，功能重叠）  
  链接：https://github.com/sipeed/picoclaw/pull/2813、https://github.com/sipeed/picoclaw/pull/2955  
  两个 PR 均针对同一高优先级 Bug #2720，建议维护者尽快对比审阅，选择其一合入并关闭另一，避免贡献者精力分散与社区困惑。

- **#2696**（创建于 2026-04-28，stale）  
  链接：https://github.com/sipeed/picoclaw/pull/2696  
  MCP 动态头部功能 PR 已沉寂一个多月，该能力是 MCP 生态企业集成的关键扩展，长期无反馈可能阻碍工具链生态建设。

---

*日报基于 GitHub 公开数据生成，旨在为 PicoClaw 维护者与社区贡献者提供数据驱动的项目健康度参考。*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
**日期：** 2026-06-04  
**仓库：** github.com/qwibitai/nanoclaw  

---

### 1. 今日速览

NanoClaw 过去 24 小时呈现**高贡献输入、低代码吞吐**的特征：社区新增 9 个 Pull Request 待审阅，但主干无合并或关闭记录，维护者审阅队列压力显著上升。与此同时，1 个中等优先级 Bug（加密家目录与 systemd linger 冲突）被报告后，贡献者于同日提交了针对性修复，显示出较快的社区响应速度。调度子系统成为今日技术焦点，连续 3 个修复 PR 围绕任务失败通知、周期任务重触发及预任务脚本诊断展开，反映出该模块在可靠性方面正经历集中治理。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

**今日合并/关闭：** 0 条（9 条 PR 均处于待合并状态）。

尽管无代码合入主干，社区在 24 小时内提交了 9 个高质量 PR，覆盖核心服务、调度引擎、容器运行态及技能生态，项目整体处于**功能补全与缺陷收敛并行**的阶段：

- **调度系统三连修**：针对定时任务的可观测性与容错，贡献者提交了失败通知（[#2679](https://github.com/nanocoai/nanoclaw/pull/2679)）、周期重触发（[#2678](https://github.com/nanocoai/nanoclaw/pull/2678)）及预任务脚本诊断（[#2677](https://github.com/nanocoai/nanoclaw/pull/2677)），系统性提升 `scheduling` 模块的健壮性。
- **系统服务兼容性**：[#2681](https://github.com/nanocoai/nanoclaw/pull/2681) 修复了加密家目录环境下启用 linger 导致的服务启动失败，直接关联 Issue [#2680](https://github.com/nanocoai/nanoclaw/issues/2680)。
- **容器与代理基础设施**：[#2676](https://github.com/nanocoai/nanoclaw/pull/2676) 为容器运行器注入 `NO_PROXY` 以绕过 OneCLI 代理访问本地服务；[#2605](https://github.com/nanocoai/nanoclaw/pull/2605) 推进基于 OneCLI 的父代理权限继承，指向多代理权限模型演进。
- **技能生态扩展与治理**：[#2683](https://github.com/nanocoai/nanoclaw/pull/2683) 引入 QMD（Query Markdown Documents）容器技能，提供 BM25 + 向量的混合本地搜索能力；[#2682](https://github.com/nanocoai/nanoclaw/pull/2682) 则在技能更新流程中过滤 v1-only 分支，为 v2 技能商店做兼容性清理。
- **集成层修复**：[#2675](https://github.com/nanocoai/nanoclaw/pull/2675) 修补 Slack `section` 块 3000 字符硬上限导致的整消息丢弃问题。

---

### 4. 社区热点

由于今日所有新增 Issue/PR 的评论数均为 0，热点判断主要基于**技术关联度、影响面及社区响应速度**：

| 热点 | 类型 | 链接 | 分析 |
|---|---|---|---|
| **加密家目录 + linger 启动失败** | Issue + Fix PR | [#2680](https://github.com/nanocoai/nanoclaw/issues/2680) / [#2681](https://github.com/nanocoai/nanoclaw/pull/2681) | 唯一新报 Bug，作者 @glifocat 在报告当日即提交修复，体现对系统级部署场景（PAM 解密时序 vs systemd 服务启动）的高度敏感。 |
| **调度系统可靠性三连修** | PR 组 | [#2679](https://github.com/nanocoai/nanoclaw/pull/2679) / [#2678](https://github.com/nanocoai/nanoclaw/pull/2678) / [#2677](https://github.com/nanocoai/nanoclaw/pull/2677) | 三位 PR 由 @yairixStudio 与 @shrwnsan 贡献，围绕“永久失败”状态的暴露与恢复，反映生产环境中定时任务静默失败的痛点正被集中解决。 |
| **QMD 混合搜索技能** | Feature PR | [#2683](https://github.com/nanocoai/nanoclaw/pull/2683) | 引入本地 BM25 + 向量混合检索，代表社区对 RAG（检索增强生成）及本地知识库搜索能力的强烈需求。 |

---

### 5. Bug 与稳定性

按严重程度与影响范围排序：

1. **[Medium] 服务启动失败：加密家目录 + linger 冲突**  
   - **Issue:** [#2680](https://github.com/nanocoai/nanoclaw/issues/2680)  
   - **描述：** 在 ecryptfs/fscrypt/gocryptfs 等家目录级加密（非 LUKS 全盘加密）且启用 systemd linger 的系统上，NanoClaw 服务在启动时因家目录尚未解密而静默失败。  
   - **Fix PR:** [#2681](https://github.com/nanocoai/nanoclaw/pull/2681)（已提交，待合并）

2. **[Medium] Slack 长消息整消息丢弃**  
   - **PR:** [#2675](https://github.com/nanocoai/nanoclaw/pull/2675)  
   - **描述：** Vercel Chat SDK 构建的 Slack `section` 块无长度限制，当单块超过 3000 字符时，`chat.postMessage` 返回 `invalid_blocks` 并拒绝整条消息，导致长通知完全丢失。

3. **[Medium] 调度任务永久失败对用户不可见**  
   - **PR:** [#2679](https://github.com/nanocoai/nanoclaw/pull/2679)  
   - **描述：** 永久失败的定时任务仅在日志中记录，未转化为用户可感知的通知，造成失败状态静默堆积。

4. **[Medium] 周期任务永久失败后不再触发下一次执行**  
   - **PR:** [#2678](https://github.com/nanocoai/nanoclaw/pull/2678)  
   - **描述：** `handleRecurrence` 原仅从 `completed` 状态扇出下一次执行，未处理 `failed` 状态的周期任务，导致一次性失败后整条周期链中断。

5. **[Medium] 预任务脚本失败缺乏重试与诊断**  
   - **PR:** [#2677](https://github.com/nanocoai/nanoclaw/pull/2677)  
   - **描述：** 预任务脚本单次失败后直接退出，无重试机制及诊断信息，增加运维排查成本。

6. **[Medium] OneCLI 代理误拦截本地服务流量**  
   - **PR:** [#2676](https://github.com/nanocoai/nanoclaw/pull/2676)  
   - **描述：** 容器运行器未设置 `NO_PROXY`，导致 OneCLI 代理配置可能将本地服务请求错误转发。

---

### 6. 功能请求与路线图信号

- **本地混合搜索技能（QMD）**  
  - **PR:** [#2683](https://github.com/nanocoai/nanoclaw/pull/2683)  
  - **信号：** 社区主动贡献基于 BM25 + 向量的 Markdown 文档搜索技能，预示 NanoClaw 的技能生态正从“工具集成”向“知识检索与 RAG”深化，该技能有望被纳入官方推荐技能集。

- **多代理权限继承**  
  - **PR:** [#2605](https://github.com/nanocoai/nanoclaw/pull/2605)  
  - **信号：** 通过 OneCLI 实现父代理向子代理的权限继承，表明项目正从单代理模式向多代理协作架构演进，权限模型是下一阶段的底层基础设施重点。

- **v2 技能商店兼容性清理**  
  - **PR:** [#2682](https://github.com/nanocoai/nanoclaw/pull/2682)  
  - **信号：** 明确跳过 v1-only 技能分支，暗示官方路线图正加速推进 v2 技能生态，v1 技能将逐步退出或需社区主动升级。

---

### 7. 用户反馈摘要

从今日 Issue/PR 描述中提炼的真实痛点与场景：

- **企业/隐私场景的系统兼容性：** 使用家目录级加密（而非全盘 LUKS）的用户在服务器/工作站部署时，遭遇 systemd 服务启动时序与 PAM 解耦的冲突，说明 NanoClaw 在 hardened / privacy-focused 环境中的启动鲁棒性仍需加强。
- **调度系统的“静默失败”焦虑：** 用户需要永久失败的定时任务被主动推送通知，而非仅写入日志；周期任务在失败后必须继续后续调度，避免“一次失败，永久停摆”。
- **企业 IM 集成的边界情况：** Slack 3000 字符限制导致长消息完全丢失（而非截断或分块），直接影响企业场景下告警、报告类消息的可靠性。
- **

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
**日期：2026-06-04**  
**仓库：** netease-youdao/LobsterAI

---

### 1. 今日速览

LobsterAI 在过去 24 小时内保持极高工程活跃度：共完成 **14 个 PR** 的合并或关闭，并正式发布 **2026.6.3** 版本。开发主线集中在 Cowork 协作体验的深度优化（上下文片段、本地分叉、会话同步）、MCP 生态的生产级加固（URL 校验、Node 环境感知、超时防护）以及 HTML 分享功能的正式商业化。社区侧出现一则关于订阅积分月底清零的付费用户投诉（#2081），当前仍为 OPEN 状态，需产品与运营侧介入响应。

---

### 2. 版本发布

**LobsterAI 2026.6.3** 已发布。  
- **MCP 启动与可观测性**：优化 npx MCP 启动解析逻辑，新增首次响应耗时（first response timing）日志，便于在生产环境中定位工具链初始化瓶颈（#2091）。  
- **HTML 分享体验优化**：重构分享链路，提升分享稳定性与交互细节（#2092）。  
- **Cowork 协作增强**：新增 Cowork 相关能力（Release 摘要未完整展示，结合同日合并的 #2098、#2101 判断为“选中文本片段进入聊天上下文”功能）。  

**破坏性变更**：无明确

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
**日期**：2026-06-04  
**仓库**：github.com/moltis-org/moltis  

---

### 1. 今日速览

过去 24 小时，Moltis 项目保持**高活跃度维护节奏**：Issues 侧大幅净减少 4 个（关闭 9，新开 5），但代码侧出现**PR 合并停滞**（待审 4 个，合并 0 个），审查队列压力上升。社区连续两日推出版本（`20260602.05`、`20260603.01`），显示 CalVer 高频迭代策略。当前用户关注焦点集中在 **Docker/容器生态兼容性**（3 个相关 Issue）与 **浏览器工具可靠性**（2 个相关 PR），Telegram 通道的流式交互体验也引发紧急修复。

---

### 2. 版本发布

今日数据包含 2 个最新 Release，但详细变更日志未在原始数据中提供，建议用户前往 Release 页面查看完整 Diff：

- **`20260603.01`**（发布于 2026-06-03）  
  链接：https://github.com/moltis-org/moltis/releases/tag/20260603.01  
- **`20260602.05`**（发布于 2026-06-02）  
  链接：https://github.com/moltis-org/moltis/releases/tag/20260602.05  

> **迁移提示**：版本号采用日历版本（CalVer）格式，通常代表每日构建或补丁批次。若从旧版本升级，建议重点关注 Docker 兼容性与 MCP 安全相关的底层变更（见下文 Bug 部分）。

---

### 3. 项目进展

**今日无 PR 合并记录**，但维护者通过直接提交或历史周期修复后归档，关闭了 9 个 Issue，覆盖核心稳定性、安全性与 UX：

- **安全与隐私**：[#1054](https://github.com/moltis-org/moltis/issues/1054) 修复了 MCP stdio 服务器配置中的环境变量通过 `mcp_list` 泄露给 LLM 的高危问题。
- **核心功能修复**：Vault 密码设置误判（[#1046](https://github.com/moltis-org/moltis/issues/1046)）、自动会话标题生成失效（[#1053](https://github.com/moltis-org/moltis/issues/1053)）、技能无法单独启用/禁用（[#1083](https://github.com/moltis-org/moltis/issues/1083)）均已关闭。
- **UI/UX 改进**：亮色模式代码块语法高亮（[#1045](https://github.com/moltis-org/moltis/issues/1045)）、模型选择器版本号截断（[#1052](https://github.com/moltis-org/moltis/issues/1052)）、Web UI 入站文件附件支持（[#1036](https://github.com/moltis-org/moltis/issues/1036)）完成交付。
- **集成能力**：Docker 环境下 `send_image` / `send_document` 失败（[#1037](https://github.com/moltis-org/moltis/issues/1037)）已修复；Agent 默认访问 Moltis 文档（[#1028](https://github.com/moltis-org/moltis/issues/1028)）已归档，可能已内置或纳入路线图。

---

### 4. 社区热点

| 议题/PR | 状态 | 热度指标 | 链接 | 诉求分析 |
|---|---|---|---|---|
| Agent 应默认访问 Moltis 文档 | 已关闭 | 3 条评论（今日最高） | [#1028](https://github.com/moltis-org/moltis/issues/1028) | 开发者强烈希望降低 Agent 上手门槛，实现开箱即用的官方文档 RAG，减少配置摩擦。 |
| Telegram edit-in-place 流式输出污染最终回复 | 开放 | 1 条评论 + 当日 PR | [#1097](https://github.com/moltis-org/moltis/issues/1097) | 终端用户对 Telegram Bot 的交互质量敏感，中间结果混入最终回复严重影响体验；社区贡献者响应极快。 |
| 新增 SMS 与 LINE 频道支持 | 开放 | 新提交 | [#1101](https://github.com/moltis-org/moltis/issues/1101) | 用户希望将 Moltis 扩展至亚洲主流通讯生态（LINE）与短信通道，表明项目正从开发者工具向大众通讯层渗透。 |

---

### 5. Bug 与稳定性

按严重程度排列，标注修复状态：

**🔴 高严重（安全/核心功能阻断）**
- **[已关闭]** MCP stdio 环境变量通过 `mcp_list` 暴露给 LLM（[#1054](https://github.com/moltis-org/moltis/issues/1054)）— **安全修复已落地**。
- **[开放]** Docker 内 `Read`/`Write`/`Edit` 工具完全失效（[#1096](https://github.com/moltis-org/moltis/issues/1096)）— 影响容器化工作流，**暂无 Fix PR**。
- **[开放]** Podman 无法通过 moltis 运行（[#1095](https://github.com/moltis-org/moltis/issues/1095)）— 容器运行时兼容性缺口，**暂无 Fix PR**。

**🟡 中严重（体验/功能异常）**
- **[开放]** Telegram 流式更新与最终回复混合（[#1097](https://github.com/moltis-org/moltis/issues/1097)）— **Fix PR [#1099](https://github.com/moltis-org/moltis/pull/1099) 已提交待审**，通过分离进度流与最终消息解决。
- **[已关闭]** Vault 密码设置被误判为未设置（[#1046](https://github.com/moltis-org/moltis/issues/1046)）。
- **[已关闭]** 无法对单一

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

**ZeptoClaw 项目动态日报 | 2026-06-04**  
*仓库: [github.com/qhkm/zeptoclaw](https://github.com/qhkm/zeptoclaw)*

---

### 1. 今日速览
过去24小时内，ZeptoClaw 项目处于典型的“静默维护”状态。社区侧零活跃度：无新增 Issues、无人工 PR 贡献、无版本发布。唯一活动来自 Dependabot 自动提交的 16 条依赖更新 PR，目前全部处于待合并状态。项目核心代码今日未发生实质性演进，健康度指标显示“基础设施自动化维护正常，但社区互动与功能开发完全停滞”。

---

### 2. 版本发布
今日无新版本发布。  
[→ Releases 页面](https://github.com/qhkm/zeptoclaw/releases)

---

### 3. 项目进展
今日**无已合并或已关闭的 PR**，项目整体未向前推进新功能或修复。  
待审阅的 16 个 PR 均为依赖版本升级（标签 `chore(deps)`），覆盖以下维度：
- **Rust 核心运行时与库**：tokio、serde_json、tower-http、scraper、rpassword
- **前端与文档站**：React、Tailwind CSS、Astro（docs）、@types/node
- **CI/CD 与构建**：docker/login-action、docker/build-push-action、docker/metadata-action、codecov-action、taiki-e/install-action
- **基础镜像**：Rust 1.95-slim-trixie → 1.96-slim-trixie

这些 PR 仅涉及维护性更新，不含新功能或已知破坏性变更。

---

### 4. 社区热点
今日社区讨论度为零。所有 16 个 PR 均由 `@dependabot[bot]` 自动创建，评论数与反应数均为 0，无人工互动。  
- 唯一值得关注的“活动”是上游关键补丁的同步：[#623 tokio 1.52.3 补丁](https://github.com/qhkm/zeptoclaw/pull/623)、[#627 serde_json 1.0.150 补丁](https://github.com/qhkm/zeptoclaw/pull/627)。  
- **诉求分析**：项目缺乏人工审阅流水线，16 个依赖更新同时积压，反映维护者近期可能未投入时间进行代码审阅与合并，存在供应链更新滞后的风险。

---

### 5. Bug 与稳定性
今日无新报告的 Bug、崩溃或回归 Issue（0 条）。  
但以下**待合并**的依赖更新包含上游稳定性或安全修复，建议按优先级处理：

| 优先级 | PR | 说明 |
|---|---|---|
| **Medium** | [#623](https://github.com/qhkm/zeptoclaw/pull/623) | `tokio` 1.52.1 → 1.52.3：上游明确包含 bugfix（Fixed）。 |
| **Medium** | [#627](https://github.com/qhkm/zeptoclaw/pull/627) | `serde_json` 1.0.149 → 1.0.150：拒绝非字符串枚举对象键，修复潜在序列化问题。 |
| **Low-Medium** | [#625](https://github.com/qhkm/zeptoclaw/pull/625) | `rpassword` 7.4.0 → 7.5.2：修复 Unicode 解析问题。 |
| **Low** | [#620](https://github.com/qhkm/zeptoclaw/pull/620) | `scraper` 0.26.0 → 0.27.0：大版本升级，需确认 API 兼容性。 |

---

### 6. 功能请求与路线图信号
今日无功能请求（0 Issues），无新功能相关 PR。  
现有 16 个待合并 PR 均为维护性更新，无法提取路线图信号。项目下一版本的功能方向尚不明确，建议维护者通过 Issues 或 Discussions 释放路线图信息以激活社区贡献。

---

### 7. 用户反馈摘要
今日无用户反馈数据（0 Issues，0 PR 人工评论）。  
无法提炼用户痛点、使用场景或满意度信息。项目当前处于“零反馈”静默期，建议维护者关注外部社区渠道（如 Discord、Reddit 或 Hacker News）或开启 GitHub Discussions 以收集真实用户声音。

---

### 8. 待处理积压
以下 16 个 PR 已滞留至少 1 天（均创建于 2026-06-03），建议维护者尽快批量审阅，避免技术债务与安全暴露：

**核心运行时（建议优先合并）**
- [#623 tokio 1.52.1 → 1.52.3](https://github.com/qhkm/zeptoclaw/pull/623)
- [#627 serde_json 1.0.149 → 1.0.150](https://github.com/qhkm/zeptoclaw/pull/627)
- [#617 tower-http 0.6.10 → 0.6.11](https://github.com/qhkm/zeptoclaw/pull/617)

**安全/输入处理**
- [#625 rpassword 7.4.0 → 7.5.2](https://github.com/qhkm/zeptoclaw/pull/625)

**Rust 工具链与爬虫**
- [#620 scraper 0.26.0 → 0.27.0](https://github.com/qhkm/zeptoclaw/pull/620)
- [#613 Rust 镜像 1.95-slim-trixie → 1.96-slim-trixie](https://github.com/qhkm/zeptoclaw/pull/613)

**CI/CD GitHub Actions**
- [#628 docker/login-action 4.1.0 → 4.2.0](https://github.com/qhkm/zeptoclaw/pull/628)
- [#622 docker/build-push-action 7.1.0 → 7.2.0](https://github.com/qhkm/zept

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

**EasyClaw 项目动态日报**  
**日期**：2026-06-04  
**项目地址**：[github.com/gaoyangz77/easyclaw](https://github.com/gaoyangz77/easyclaw)

---

### 1. 今日速览

EasyClaw 在 2026-06-04 呈现「**高频发布、社区静默**」的特征。过去 24 小时内，项目未产生新的 Issue 与 Pull Request，社区互动处于低位；但维护者连续推送了 v1.8.28 与 v1.8.29 两个生产补丁，集中修复了桌面端云模型视觉输入路由、启动同步隔离及客服系统重试机制。整体健康度表现为「**核心维护活跃、社区贡献待激活**」。（[项目主页](https://github.com/gaoyangz77/easyclaw)）

---

### 2. 版本发布

项目今日发布两个连续补丁版本，均涉及桌面端与客服系统稳定性，**建议所有桌面用户立即升级**。

- **v1.8.29** — *RivonClaw v1.8.29*（[Release 链接](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.29)）
  - **视觉输入路由修复**：修正 RivonClaw 云模型视觉输入的 payload 形状，确保图像感知请求被正确路由。
  - **API 契约对齐**：桌面端云模型调用已与最新支持视觉能力的 RivonClaw API 契约保持一致。
  - **更新器元数据刷新**：重新签名桌面端发布元数据，保障生产环境自动更新器（updater）顺利推出。
  - **破坏性变更与迁移**：无已知破坏性变更。若您在使用桌面客户端并依赖云模型视觉功能，建议优先升级至此版本以避免图像请求异常。

- **v1.8.28** — *RivonClaw v1.8.28*（[Release 链接](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.28)）
  - **客服重试机制加固**：将客服待派发恢复（pending dispatch recovery）的重试逻辑锚定至显式消息 ID，避免重复或丢失派发。
  - **启动同步与会话隔离**：修复启动阶段云模型同步问题，确保桌面会话在多次运行间完全隔离。
  - **Telegram 调试媒体优化**：刷新客服会话状态处理，优化 Telegram 调试媒体发送的引导逻辑。
  - **破坏性变更与迁移**：无破坏性变更。涉及客服系统与 Telegram 集成的部署建议跟进此版本。

---

### 3. 项目进展

过去 24 小时内**无新增合并或关闭的 Pull Request**（[PR 列表](https://github.com/gaoyangz77/easyclaw/pulls)）。今日项目推进完全以版本发布形式体现：维护者通过 v1.8.28 与 v1.8.29 将桌面端稳定性、客服系统可靠性及视觉输入兼容性向前推进了一个补丁周期。虽无社区代码贡献合入，但发布节奏紧凑，显示核心团队处于高频交付状态。

---

### 4. 社区热点

基于过去 24 小时数据，项目**未产生新的 Issue 或 PR 讨论**（[Issues](https://github.com/gaoyangz77/easyclaw/issues) | [PRs](https://github.com/gaoyangz77/easyclaw/pulls)）。社区互动维度今日静默，无热点议题、高赞评论或激烈技术辩论。这可能表明当前版本处于「稳定消化期」，用户侧未遭遇新的阻塞性问题；也可能反映项目仍处于早期用户增长阶段，社区声量有待提升。

---

### 5. Bug 与稳定性

今日**无新增用户报告的 Bug、崩溃或回归问题**（[Issues](https://github.com/gaoyangz77/easyclaw/issues)）。但维护者通过两个版本主动修复了以下稳定性隐患，建议相关用户关注：

| 严重程度 | 问题描述 | 修复版本 | 状态 |
|---|---|---|---|
| 高 | 云模型视觉输入 payload 形状错误，可能导致图像感知请求路由失败 | v1.8.29 | ✅ 已修复 |
| 高 | 启动时云模型同步缺陷，可能导致桌面会话状态污染或跨运行隔离失效 | v1.8.28 | ✅ 已修复 |
| 中 | 客服待派发恢复缺乏显式消息 ID 锚定，存在重复派发风险 | v1.8.28 | ✅ 已修复 |
| 低 | Telegram 调试媒体发送引导逻辑不完善 | v1.8.28 | ✅ 已修复 |

---

### 6. 功能请求与路线图信号

过去 24 小时内**无新增功能请求 Issue

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*