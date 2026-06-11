# OpenClaw 生态日报 2026-06-11

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-11 03:32 UTC

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
**日期：2026-06-11**

---

### 1. 今日速览

OpenClaw 在 2026-06-11 维持极高活跃度，24 小时内 Issues 与 Pull Requests 各更新 **500 条**，其中 Issues 新开/活跃 **469 条**、关闭 **31 条**；PR 待合并 **396 条**、已合并/关闭 **104 条**，维护者审查队列压力显著。项目今日发布 **v2026.6.6-beta.1**，以全链路安全边界收紧为主轴。社区核心诉求仍集中在**消息可靠性、会话状态一致性、多代理编排稳定性**三大领域，生产环境信任度是当前健康度的关键挑战。

---

### 2. 版本发布

**v2026.6.6-beta.1** 已发布（`OpenClaw 2026.6.6-beta.1`）。

**更新内容：**  
本次更新为安全加固版本，显著收紧了跨多个子系统的安全边界，包括：
- **Transcripts & Session Data**：转录数据访问边界收紧；
- **Sandbox & Host Environment**：沙箱绑定与主机环境继承限制增强；
- **MCP stdio / Codex HTTP**：外部工具与 HTTP 访问控制策略更新；
- **Native Search & Elevated Sender**：原生搜索策略与提升权限发送者检查；
- **ACP & Loopback**：修复已删除代理的 ACP 绕过问题，收紧回环工具策略；
- **Platform Moderation**：Discord 审核与 Teams 群组访问控制。

**迁移注意事项：**  
涉及沙箱绑定、外部工具调用及平台集成权限变更，建议所有自托管用户在升级后验证 `sandbox.workspaceAccess`、`skills` 环境变量注入及 Discord/Teams 机器人权限范围。

---

###

---

## 横向生态对比

**个人 AI 助手/自主智能体开源生态横向对比分析**  
*报告日期：2026-06-11*

---

### 1. 生态全景

当前个人 AI 助手与自主智能体开源生态呈现“一超多强、垂直分化”的格局。**OpenClaw** 以碾压级的社区吞吐量（单日 1,000 条 Issues+PR 更新）占据核心生态位，成为事实上的技术风向标。与此同时，安全加固已从可选功能演变为全生态的基础设施需求——从 OpenClaw 的全链路安全边界收紧到 PicoClaw 的 24 小时 SSRF 漏洞响应，安全正在定义 Agent 的交付标准。产品形态上，社区正加速从“对话式交互”向“操作系统级操控”（Computer Use）与“超长任务链记忆”演进，Windows 桌面端的稳定性成为决定用户留存的生死线。

---

### 2. 各项目活跃度对比

| 项目 | Issues 更新 | PR 更新 | 版本发布 | 健康度评估 |
|---|---|---|---|---|
| **OpenClaw** | 500（新开/活跃 469，关闭 31） | 500（待合并 396，已合并/关闭 104） | v2026.6.6-beta.1 | 🔥 极高活跃度；审查队列压力显著，生产环境信任度是关键挑战 |
| **Zeroclaw** | 42（新开/活跃 23，关闭 19） | 50（待合并 39，已合并/关闭 11） | 无 | ✅ 健康良好；P1 运行时 Bug 待消化，RFC 级架构讨论活跃 |
| **PicoClaw** | 5（活跃 4，关闭 1） | 15（待审 9，已合并/关闭 6） | v0.2.9-nightly | 🟡 中等偏高；安全响应极快（SSRF 24h 修复），主线迭代平稳 |
| **NanoClaw** | 2 | 12（待合并 8，关闭 4） | 无 | 🟡 高并发；安全加固与 Skills 生态扩张并行，配置冲突风险暴露 |
| **LobsterAI** | 0 | 25（已合并/关闭 24，待合并 1） | 2026.6.10 | 🚀 功能冲刺期；零 Issue、高合并，处于版本收尾与体验打磨阶段 |
| **CoPaw** | 32（新开/活跃 17，关闭 15） | 49（已合并/关闭 30，待审 19） | v1.1.11 / v1.1.11-beta.3 | ⚠️ 快速迭代；紧急修复 Windows OpenSSL 崩溃，架构升级前夕 |
| **NanoBot / IronClaw** | 未披露 | 未披露 | 未披露 | ⚪ 数据缺失 |
| **TinyClaw / Moltis / ZeptoClaw / EasyClaw** | 0 | 0 | 无 | ⚫ 休眠/无活动 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是当前生态中**唯一具备平台级规模**的项目，其单日 1,000 条的 Issues+PR 吞吐量超过其他所有项目总和，形成了事实上的标准制定者地位。

- **核心优势**：全链路安全边界设计（Transcripts、Sandbox、MCP、ACP 等多子系统同步收紧）与深度平台集成（Discord、Teams、Native Search），使其成为企业自托管场景的首选基座。
- **技术路线差异**：相比 LobsterAI 的端侧产品化路线或 CoPaw 的多渠道中间件路线，OpenClaw 更强调**多代理编排稳定性**与**主机环境隔离**，技术架构更接近“Agent 操作系统”而非单一应用。
- **社区规模对比**：OpenClaw 的待合并 PR（396 条）已接近 Zeroclaw 总 PR 更新的 8 倍，其挑战已从“功能缺失”转向“审查带宽与生产信任度”的治理问题。

---

### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **全链路安全加固** | OpenClaw、PicoClaw、NanoClaw、CoPaw | OpenClaw 收紧沙箱与 MCP 边界；PicoClaw 24h 内修复 SSRF；NanoClaw 引入 IPC 命名空间隔离；CoPaw 紧急处理 OpenSSL 3.5.7 证书崩溃 |
| **Windows 桌面稳定性** | LobsterAI、CoPaw、Zeroclaw | LobsterAI 重构 NSIS 安装与更新链路；CoPaw 连环修复 OpenSSL 回归故障；Zeroclaw 修复 Windows 测试与 lint 覆盖 |
| **长会话/记忆连续性** | OpenClaw、LobsterAI、Zeroclaw | OpenClaw 聚焦会话状态一致性；LobsterAI 针对 Cowork 压缩后上下文“断片”补强；Zeroclaw 修复 Matrix 以 event_id 为键导致的失忆问题 |
| **消息可靠性** | OpenClaw、Zeroclaw、CoPaw | OpenClaw 将消息可靠性列为三大核心诉求；Zeroclaw 修复 Custom API 丢失 user message；CoPaw 修复微信渠道 `ret=-3` 推送失败 |
| **Computer Use / 环境操控** | LobsterAI、Zeroclaw | LobsterAI 上线 Windows Computer Use MVP（MCP 桥接应用/窗口/截图）；Zeroclaw 社区呼吁提供全功能 Docker 镜像降低非技术用户门槛 |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|---|---|---|---|
| **OpenClaw** | 企业级多代理编排、平台集成 | 自托管企业、进阶开发者 | 平台化架构，强调安全边界与多系统（MCP/ACP/Discord/Teams）深度集成 |
| **LobsterAI** | 端侧 AI 助手、Computer Use | 消费者、Windows 桌面用户 | 产品化闭环，深度绑定 Windows 运行时，MCP 桥接操作系统级 API |
| **CoPaw** | 多渠道 Agent（微信/Discord 等）、Provider 生态 | 中文社区、渠道集成开发者 | AgentScope 架构，重 Provider 插件与桌面端（Tauri），Skills 自进化 |
| **Zeroclaw** | 跨平台 TUI、轻量核心、开发者工具链 | CLI 用户、开源贡献者 | Rust 基座，追求 zerocode 体验，RFC 推动将集成外部化为 Skills/MCP |
| **NanoClaw** | 容器化安全运行时、Skills 生态 | 安全敏感型部署者 | IPC 隔离 + Egress Lockdown，容器组级命名空间，冲突于 systemd/launchd |
| **PicoClaw** | 轻量/边缘 Agent、快速迭代 | 嵌入式/边缘开发者 | Sipeed 生态背景，Nightly 高频发布，聚焦类型安全与错误处理健壮性 |

---

### 6. 社区热度与成熟度

- **🔥 快速迭代/功能冲刺阶段**：**LobsterAI**（25 PR 零 Issue，全力冲刺 Computer Use 与 Windows 体验）、**CoPaw**（紧急修复 OpenSSL 并推进 AgentScope 2.0 迁移，处于“发布-救火”循环）。
- **🛠️ 质量巩固与治理阶段**：**OpenClaw**（吞吐量极大但关闭率仅 6.2%，审查队列积压，核心矛盾从功能建设转向生产信任度）、**Zeroclaw**（消化 P1 Bug 与 RFC 架构讨论，推进内核瘦身）。
- **🟢 平稳维护阶段**：**PicoClaw**（安全驱动的小步快跑）、**NanoClaw**（架构加固与 Skills 扩张并行，暴露部署层冲突）。
- **⚫ 休眠/静默**：TinyClaw、Moltis、ZeptoClaw、EasyClaw、NanoBot、IronClaw 过去 24 小时无活动或数据未披露。

---

### 7. 值得关注的趋势信号

1. **安全即基础设施**：不再是单一功能点，而是贯穿沙箱、IPC、网络隔离（Egress Lockdown）、证书链与 MCP 工具调用的全链路工程。对开发者的启示：Agent 的默认交付物必须包含最小权限原则与主机隔离设计。
2. **从“对话”到“操控”的范式转移**：LobsterAI 的 Computer Use MVP 与 MCP 桥接操作系统 API，标志着 Agent 正从信息处理者进化为环境执行者。开发者应优先评估本地环境操控的风险模型与回滚机制。
3. **会话记忆工程化成为产品化瓶颈**：长上下文压缩后的状态连续性（LobsterAI Cowork、OpenClaw 会话一致性）已成为区分 Demo 级与产品级 Agent 的关键。提示词工程之外，需构建结构化的“轻量级工作区状态”层。
4. **Windows 桌面端决定大众市场天花板**：CoPaw 与 LobsterAI 同日遭遇/修复 Windows 致命崩溃，说明跨平台桌面运行时（Tauri/Electron/NSIS）的稳定性直接阻断用户增长。Agent 开发者需将 Windows 视为一级平台而非移植目标。
5. **架构瘦身与 MCP 外部化**：Zeroclaw 社区 RFC 呼吁将 Jira/GitHub 等硬编码集成移出核心，通过 MCP/Skills 外部化。这预示 Agent 核心将向“微内核 + 标准协议插件”演进，降低维护负担与供应链攻击面。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**Zeroclaw 项目动态日报**  
**日期：2026-06-11**

---

### 1. 今日速览

过去 24 小时，Zeroclaw 社区保持极高活跃度：Issues 更新 **42 条**（23 条新开/活跃，19 条关闭），Pull Requests 更新 **50 条**（39 条待合并，11 条已合并/关闭），无新版本发布。今日工作流集中在 **zerocode TUI 体验打磨**（编辑器回退、快捷键冲突、主题渲染）、**跨平台质量基线修复**（Windows 测试失败、lint 平台覆盖）以及 **Gateway/Runtime 可观测性增强**。社区同时围绕核心架构展开了 3 项 RFC 级讨论，项目整体健康度良好，但 P1 级运行时 Bug 仍需优先消化。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日已合并/关闭的关键 PR 及对应进展：

- **Docs & Community**  
  - [#7096](https://github.com/zeroclaw-labs/zeroclaw/pull/7096) 已合并：将 README 中失效的 Discord 邀请替换为稳定的 Vanity 链接，解决了新贡献者无法加入社区的问题（关闭 [#7037](https://github.com/zeroclaw-labs/zeroclaw/issues/7037)）。  
  - [#7458](https://github.com/zeroclaw-labs/zeroclaw/pull/7458) 已合并：回退了跨平台 Clippy lint 强制门限，恢复为 Linux-only 必检，避免日常 PR 被 Windows/macOS 特有代码阻塞（关联 [#7409](https://github.com/zeroclaw-labs/zeroclaw/issues/7409)）。

- **Runtime & Tooling Fixes**  
  - [#6309](https://github.com/zeroclaw-labs/zeroclaw/issues/6309) 已关闭：`model_routing_config` 在执行 `upsert_agent` 时错误覆盖 `schema_version = 2` 设置的问题得到修复。  
  - [#4627](https://github.com/zeroclaw-labs/zeroclaw/issues/4627) 已关闭：`file_write` 工具在 Docker 环境下静默失败、文件在宿主机不可见的 S0 级数据丢失风险已解除。  
  - [#6958](https://github.com/zeroclaw-labs/zeroclaw/issues/6958) 已关闭：Matrix 频道因以 `event_id` 作为会话键导致的“消息间失忆”问题已修复。  
  - [#6722](https://github.com/zeroclaw-labs/zeroclaw/issues/6722) 已关闭：清理了 `MemoryConfig.rerank_enabled / rerank_threshold` 配置项的无效脚手架代码，减少配置误导。

- **CI & Build**  
  - [#5908](https://github.com/zeroclaw-labs/zeroclaw/issues/5908) 已关闭：Debian 容器镜像的 CI/CD 构建与发布流程已落地。  
  - [#6576](https://github.com/zeroclaw-labs/zeroclaw/issues/6576) 已关闭：Matrix live homeserver 的 v0.8.0 发布门限烟雾测试已完成。

---

### 4. 社区热点

今日讨论最活跃的议题反映了用户在**容器开箱体验**、**核心运行时稳定性**与**架构瘦身**三方面的高度关注：

| 议题 | 评论 | 核心诉求 |
|------|------|----------|
| [#3642](https://github.com/zeroclaw-labs/zeroclaw/issues/3642) Provide a "full" docker image | 12 条 / 3 👍 | 新用户希望提供预编译全功能标志（含 WhatsApp 等）的 Docker 镜像，降低非技术用户门槛。 |
| [#6034](https://github.com/zeroclaw-labs/zeroclaw/issues/6034) 单轮/多轮对话丢失 user message | 6 条 | 生产环境出现 Custom API 400 Bad Request，user message 在请求体中丢失，阻塞工作流。 |
| [#6721](https://github.com/zeroclaw-labs/zeroclaw/issues/6721) tool_search 不在 default_auto_approve 导致静默挂起 | 5 条 | MCP deferred loading 模式下，`tool_search` 因未默认自动批准，在非交互式 webhook 场景中静默挂起 120 秒后自动拒绝。 |
| [#6309](https://github.com/zeroclaw-labs/zeroclaw/issues/6309) model_routing_config 覆盖 schema_version | 5 条 | Agent 运行时更新配置会破坏用户显式声明的 schema v2 结构。 |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) RFC: Prefer a lighter ZeroClaw core through external integrations | 4 条 | 社区呼吁将 Jira、GitHub 等硬编码集成移出核心，改为通过 Skills/MCP 外部化，保持内核轻量。 |

---

### 5. Bug 与稳定性

按严重程度排序，今日需重点关注的问题如下：

**🔴 S1 / P1 — 工作流阻塞或数据风险**

- **[#6034](https://github.com

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
**日期：2026-06-11**  
**分析师：AI 智能体与开源项目研究**

---

### 1. 今日速览

PicoClaw 今日保持中等偏高的开发活跃度：24 小时内 15 个 PR 发生更新（6 条已合并/关闭、9 条待审），5 个 Issue 变动（4 个活跃、1 个关闭）。安全响应表现突出，SSRF 漏洞（[#3077](https://github.com/sipeed/picoclaw/issues/3077)）在披露后 24 小时内即被修复关闭（[#3085](https://github.com/sipeed/picoclaw/pull/3085)）。代码健壮性成为今日贡献焦点，至少 4 个独立 PR 针对类型断言和错误处理进行加固。项目持续发布 v0.2.9 Nightly 构建，主线迭代平稳，但子代理消息重复与旧版 iOS Safari 兼容性问题仍需关注。

---

### 2. 版本发布

**v0.2.9-nightly.20260611.d955d5bb**  
- **发布链接**：[Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)  
- **类型**：自动化 Nightly 预发布构建  
- **更新内容**：包含自 v0.2.9 稳定版以来 main 分支的全部提交，涵盖今日合并的 Windows

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-11 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

NanoClaw 过去 24 小时保持高并发活跃度：12 个 PR 发生更新（8 个待合并、4 个关闭），2 个 Issue 有新活动，无新版本发布。安全加固与 Skills 生态扩张是两大主线——既有底层 IPC 隔离权限提升防护合入主线，也有 guardrails、web-search-plus 等 4 个新技能 PR 集中提交。与此同时，生产环境配置传递（systemd/launchd）与 Egress Lockdown 网络隔离的冲突开始暴露，稳定性风险需要维护者快速响应。整体社区健康度良好，但架构级功能请求与部分安全修复 PR 存在积压。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日关闭/合入的 4 个 PR 中，3 项对主线有实质推进：

- **#3 Secure IPC with per-group namespaces to prevent privilege escalation**（[链接](https://github.com/nanocoai/nanoclaw/pull/3)）  
  合入基于 IPC 目录隔离的权限提升防护。每个容器组现在拥有独立的 IPC 命名空间（`/data/ipc/{groupFolder}/`），消息发送授权不再依赖自报告数据，而是基于请求来源目录，从底层架构上阻断跨组消息伪造与特权逃逸。这是 NanoClaw 安全模型的重大加固。

- **#2721 docs: customizing intro, skills model, and skill guidelines**（[链接](https://github.com/nanocoai/nanoclaw/pull/2721)）  
  官方文档体系完成分层重构，新增 `customizing.md`、`skills-model.md` 与 `skill-guidelines.md`，确立了 "edit first, skillify after" 的社区定制契约，显著降低了后续贡献者的认知与合并冲突成本。

- **#2719 feat: add uninstall.sh**（[链接](https://github.com/nanocoai/nanoclaw/pull/2719)

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-11 | 仓库：netease-youdao/LobsterAI*

---

### 1. 今日速览

过去 24 小时，LobsterAI 展现出极高的代码吞吐节奏：**25 条 PR 被处理**（24 条已合并/关闭，1 条待合并），但 Issues 面板保持静默（0 条新增/活跃/关闭）。项目刚刚发布了 **2026.6.10** 版本，核心团队正集中火力推进 Windows 端稳定性、AI Agent 的 Computer Use 能力，以及 Cowork 长会话上下文连续性。社区呈现“零 Issue、高合并”状态，说明当前处于功能冲刺与版本收尾阶段，开发健康度良好，但用户侧反馈渠道暂时平静。

---

### 2. 版本发布

**LobsterAI 2026.6.10** 已于 2026-06-10 发布。  
Release 链接：`https://github.com/netease-youdao/LobsterAI/releases`（对应发布 PR #2140）

**主要变更：**
- **用户数据备份与恢复**（`feat(data-migration)` by @fisherdaddy, #2125）：支持用户数据的导出与迁移，降低跨设备或重装时的数据丢失风险。
- **本地回调登录流**（`feat(auth)` by @liuzhq1986, #2122）：新增本地回调认证模式，优化登录体验。
- **OpenClaw 设置透出**（`feat(settings): surface OpenCla...`）：将 OpenClaw 相关配置项暴露至设置面板，提升可配置性。

**迁移注意事项：**  
使用本地回调登录的用户需确保回调地址指向新的 LobsterAI 门户域名（详见下方 #2144 修复）；建议用户在升级后利用新增的数据备份功能预先保存关键会话与配置。

---

### 3. 项目进展

今日合并/关闭的核心 PR 推动了产品在三方面的实质性跃进：

| PR | 作者 | 进展说明 |
|---|---|---|
| [#2143](https://github.com/netease-youdao/LobsterAI/pull/2143) | @btc69m979y-dotcom | **Computer Use MVP 上线**：为 Windows x64 引入内置计算机控制套件，含应用市场元数据、技能包完整性校验、安装/卸载生命周期管理，以及 MCP 服务器桥接（支持列出应用/窗口、启动应用、截图等）。标志着 LobsterAI 向操作系统级 Agent 自动化迈出关键一步。 |
| [#2145](https://github.com/netease-youdao/LobsterAI/pull/2145) | @liuzhq1986 | **Cowork 上下文压缩连续性增强**：在 OpenClaw 压缩聊天历史后，增加 LobsterAI 自有的连续性层（安全诊断、会话级任务状态、轻量级工作区状态），解决长会话压缩后 Agent“断片”无法继续任务的问题。 |
| [#2142](https://github.com/netease-youdao/LobsterAI/pull/2142) | @fisherdaddy | **Windows 安装与加载体验重构**：修复 NSIS 安装程序的破坏性初始化问题，并重设计引擎加载页，提升 Windows 端首次安装与启动稳定性。 |
| [#2144](https://github.com/netease-youdao/LobsterAI/pull/2144) | @liuzhq1986 | **认证门户域名切换**：将本地门户回退、升级链接及回调 URL 指向新的 LobsterAI 门户域名，区分测试与生产环境，避免登录/升级链路指向过期地址。 |
| [#2141](https://github.com/netease-youdao/LobsterAI/pull/2141) | @fisherdaddy | **Windows 应用内更新修复**：解决 Windows 端应用内更新异常，保障后续版本分发通道畅通。 |
| [#2139](https://github.com/netease-youdao/LobsterAI/pull/2139) | @fisherdaddy | **UI 精细化**：代码块切换为 One Dark/One Light 语法高亮、透明背景、默认自动换行；Markdown 阅读与模型选择器样式全面调优。 |
| [#2134](https://github.com/netease-youdao/LobsterAI/pull/2134) | @liuzhq1986 | **任务完成通知闭环**：主窗口关闭后仍可通过系统通知恢复应用；macOS Notification Center 点击保持有效，等待渲染层就绪后再打开目标 Cowork 会话。 |

此外，维护者今日批量关闭了 10 余条 4 月初的 stale PR（#1485–#1503 等），涉及定时任务、技能管理、CI 升级等，属于积压清理动作，有助于保持仓库健康度。

---

### 4. 社区热点

今日所有 PR 的公开评论数均为 0，Issues 面板亦无新增讨论，社区表面讨论度较低。但以下两个 PR 代表了当前最受关注的技术方向：

- **[#2143 feat: add computer use MVP](https://github.com/netease-youdao/LobsterAI/pull/2143)**  
  引入 Windows 本地计算机控制与 MCP 桥接，社区对“Agent 能否直接操作用户电脑”高度关注，此功能直接对标业界 Computer Use 标准，预计将成为后续用户测试和反馈的焦点。

- **[#2145 feat(cowork): improve post-compaction context continuity](https://github.com/netease-youdao/LobsterAI/pull/2145)**  
  解决长会话场景下历史压缩后的状态保持难题，是 Agent 产品化体验的核心瓶颈。该 PR 的合并意味着 LobsterAI 在“无限记忆”工程上做了针对性补强。

**背后诉求：** 用户和开发者不再满足于纯对话式 AI，而是期待 LobsterAI 具备**本地环境深度操控能力**与**超长任务链的可靠记忆**。

---

### 5. Bug 与稳定性

今日无新增 Bug Issue，但以下修复已合入主分支，建议关注验证：

| 严重程度 | 问题描述 | 状态 | 链接 |
|---|---|---|---|
| **高** | Windows NSIS 安装程序存在破坏性初始化，可能导致安装失败或环境损坏 | **已修复**（#2142） | [#2142](https://github.com/netease-youdao/LobsterAI/pull/2142) |
| **高** | Windows 端应用内更新异常，影响版本自动分发 | **已修复**（#2141） | [#2141](https://github.com/netease-youdao/LobsterAI/pull/2141) |
| **中** | 认证门户回退 URL 与回调地址指向旧域名，可能导致登录/升级链路失效 | **已修复**（#2144） | [#2144](https://github.com/netease-youdao/LobsterAI/pull/2144) |
| **中** | 禁用技能后仍保留在 `activeSkillIds` 中，系统提示词继续调用已禁用技能 | **PR 已关闭**（#1485，stale 清理） | [#148

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw 项目动态日报**  
*日期：2026-06-11 | 仓库：agentscope-ai/QwenPaw*

---

### 1. 今日速览

CoPaw 今日维持极高活跃度，24 小时内产生 **32 条 Issue 更新**（17 条新开/活跃，15 条关闭）与 **49 条 PR 更新**（30 条已合并/关闭，19 条待审阅），并发布 **2 个版本**。社区焦点集中在 **v1.1.11 正式版发布**、**Windows 桌面端 OpenSSL 3.5.7 回归故障的紧急修复**，以及 **AgentScope 2.0 迁移**的前期讨论。首次贡献者持续涌入，UI 细节修复与大型架构重构并行推进，项目整体处于“快速迭代、紧急救火”的健康但紧张的节奏。

---

### 2. 版本发布

**v1.1.11**（正式版）  
🔗 [Release 链接](https://github.com/agentscope-ai/QwenPaw/releases)

- **新增 Providers**  
  - **Free Model OAuth**：支持零配置免费模型，通过一键 OAuth 认证即可接入（[#5049](https://github.com/agentscope-ai/QwenPaw/pull/5049)）。  
  - **Xiaomi MiMo Provider**：将小米 MiMo Token Plan 作为内置提供商接入（[#4722](https://github.com/agentscope-ai/QwenPaw/pull/4722)）。

**v1.1.11-beta.3**（预发布）  
🔗 [Release 链接](https://github.com/agentscope-ai/QwenPaw/releases)

- **CI**：移除冗余的 `channel-tests` 工作流（[#5056](https://github.com/agentscope-ai/QwenPaw/pull/5056)）。  
- **Skills**：增强 `make-skill` 流程，支持**自进化技能创建**（self-evolving skill creation）（[#4857](https://github.com/agentscope-ai/QwenPaw/pull/4857)）。

> **迁移注意事项**：v1.1.11 发布后，Windows 桌面用户遭遇 OpenSSL 3.5.7 兼容性问题导致无法启动（见下文 Bug 章节），维护团队已紧急推送版本号至 **1.1.11.post1**（[#5093](https://github.com/agentscope-ai/QwenPaw/pull/5093)），建议 Windows 用户关注后续热修复而非直接安装原始 v1.1.11。

---

### 3. 项目进展

今日已合并/关闭的关键 PR 推动了发布流程、构建稳定性与 UI 修复：

- **发布与版本管理**  
  - [#5080](https://github.com/agentscope-ai/QwenPaw/pull/5080) `chore: release v1.1.11` —— 正式版发布流程。  
  - [#5093](https://github.com/agentscope-ai/QwenPaw/pull/5093) `chore: bump version to 1.1.11.post1` —— 针对 Windows 崩溃的紧急版本提升。

- **Windows 构建与 SSL 紧急修复**（连环修复）  
  - [#5082](https://github.com/agentscope-ai/QwenPaw/pull/5082) 限制 `aiohttp<=3.14.0`，避免其模块级 SSL 上下文创建触发 Windows 证书存储错误。  
  - [#5083](https://github.com/agentscope-ai/QwenPaw/pull/5083) 在 Windows 构建验证中改用 `certifi` CA bundle，绕过损坏的系统证书存储。  
  - [#5084](https://github.com/agentscope-ai/QwenPaw/pull/5084) 将 `discord.py` 的打包验证改为仅编译检查，但随后被 [#5092](https://github.com/agentscope-ai/QwenPaw/pull/5092) Revert，以配合 OpenSSL 根因修复。  
  - [#5096](https://github.com/agentscope-ai/QwenPaw/pull/5096) **（待合并，关键）** 在 Windows 桌面打包环境中固定 `openssl=3.5.6`，直接解决 OpenSSL 3.5.7 的 DER 证书加载回归 bug。

- **前端体验修复**  
  - [#4766](https://github.com/agentscope-ai/QwenPaw/pull/4766)（首次贡献者）移除环境变量页面 hover 时的 `transform` 位移，消除滚动条闪烁。  
  - [#5094](https://github.com/agentscope-ai/QwenPaw/pull/5094) 修复安全设置页 Shield 图标未垂直居中问题。

- **架构与治理讨论**  
  - [#5087](https://github.com/agentscope-ai/QwenPaw/pull/5087) 关闭，其后续讨论在 [#5088](https://github.com/agentscope-ai/QwenPaw/pull/5088) 继续，涉及初始治理与沙盒接口（Governance & Sandbox Interface）。

---

### 4. 社区热点

今日讨论最激烈的议题集中在**后端架构升级**、**渠道稳定性**与**模型兼容性**：

| 议题 | 状态 | 评论 | 核心诉求 |
|------|------|------|----------|
| [#4727](https://github.com/agentscope-ai/QwenPaw/issues/4727) AgentScope 1.x → 2.0 迁移 | **OPEN** | 8 | 社区高度关注底层依赖升级时间表，担心 Breaking Change 对现有 Skill 与插件生态的影响。 |
| [#4342](https://github.com/agentscope-ai/QwenPaw/issues/4342) 单元测试覆盖 Phase 5 | **CLOSED** | 11 | 补齐 `local_models/`、`providers/` 等核心模块的测试债务，提升代码可信度。 |
| [#4878](https://github.com/agentscope-ai/QwenPaw/issues/4878) 微信定时任务推送失败 | **CLOSED** | 7 | 企业微信渠道在生产环境出现 `ret=-3` 拒绝，根因为 `channel.py` 中 `to_handle_from_target` 逻辑错误。 |
| [#4989](https://github.com/agentscope-ai/QwenPaw/issues/4989) 本地千问 3.6-27B 无响应 | **CLOSED** | 5 | 回归 bug：v1.1.5.post2 正常的本地 vLLM 模型在 v1.1.9/1.1.10 完全失效，用户被迫回退版本。 |
| [#5064](https://github.com/agentscope-ai/QwenPaw/issues/5064) Agent 生成的定时任务无法触发/编辑 | **OPEN** | 5 | Agent 自动创建的 cron 任务存在“ phantom 任务”现象——前端展示正常，但后端调度器未真正注册，且缺少编辑入口。 |

---

### 5. Bug 与稳定性

按严重程度排序：

- **🔴 P0：Windows 桌面端无法启动（OpenSSL 3.5.7 回归）**  
  - [#5086](https://github.com/agentscope-ai/QwenPaw/issues/5086) **OPEN** | 桌面版卡在 "Waiting for HTTP ready..."，Python 3.10 捆绑的 OpenSSL 3.5.7 对 DER 格式证书数据抛出 `ASN1: NOT_ENOUGH_DATA`。  
  - [#5095](https://github.com/agentscope-ai/QwenPaw/issues/5095) **CLOSED** | v1.1.11 Windows 客户端安装后无法启动，确认为上述同一根因。  
  - **Fix PR**：[#5096](https://github.com/agentscope-ai/QwenPaw/pull/5096)（待合并）固定 `openssl=3.5.6`。

- **🟠 P1：模型执行与工具调用**  
  - [#5052](https://github.com/agentscope-ai/QwenPaw/issues/5052) **OPEN** | 工具调用若干次后全部报 `got an unexpected keyword argument 'arguments'`，影响 deepseek-v4-flash 等自建模型。  
  - [#5065](https://github.com/agentscope-ai/QwenPaw/issues/5065) **OPEN** | `MODEL_EXECUTION_FAILED` 报错，具体根因待定位。

- **🟡 P2：前端性能与体验**  
  - [#5053](https://github.com/agentscope-ai/QwenPaw/issues/5053) **OPEN** | Windows Tauri 客户端打开 4 个会话后 Tab 切换卡顿超 10 秒。  
  - [#

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