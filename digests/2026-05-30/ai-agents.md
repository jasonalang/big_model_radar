# OpenClaw 生态日报 2026-05-30

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-05-30 14:44 UTC

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
**日期：2026-05-30**

---

### 1. 今日速览

过去 24 小时，OpenClaw 社区保持极高活跃度，共有 **500 条 Issues** 与 **500 条 PR** 更新，其中 Issues 关闭 69 条、PR 合并/关闭 76 条，显示维护吞吐健康。项目连发两个 Beta 版本（`v2026.5.28-beta.3/4`），核心目标均为提升 **Agent 与 Codex 运行时的恢复稳定性**。与此同时，多个 P1 级通道（Feishu、Telegram、Matrix）与运行时回归 Bug 正在紧急修复中，ClawSweeper 自动化合并流水线已武装 1 条关键修复（PR #88340），预计今日内完成合入。整体健康度：**活跃度高，修复节奏快，但通道与 Windows 平台的稳定性债务仍需消化。**

---

### 2. 版本发布

**v2026.5.28-beta.4** & **v2026.5.28-beta.3**  
*（连续迭代，更新内容一致）*

- **核心改进**：Agent 与 Codex 运行时恢复（runtime recovery）更加稳健。
- **详细变更**：
  - 子代理（subagents）严格保持 `cwd` 与 `workspace` 隔离；
  - Hook context 限制在 prompt-local 作用域，避免污染；
  - Session locks 在超时中止时正确释放；
  - 避免陈旧的重启 continuation 导致的异常状态；
  - Codex app-server / helper 失败不再破坏共享运行时状态。
- **迁移注意**：若你在使用 Codex harness 或嵌入式子代理，建议升级至 beta.4 以解决此前因共享状态撕裂导致的随机挂起。

> 链接：https://github.com/openclaw/openclaw/releases

---

### 3. 项目进展

今日关闭的关键 Issues 代表了以下推进：

| 方向 | 代表 Issue | 进展说明 |
|------|-----------|----------|
| **Codex 认证与压缩** | [#86820](https://github.com/openclaw/openclaw/issues/86820) / [#86373](https://github.com/openclaw/openclaw/issues/86373) | 修复了 Codex OAuth compaction 回退到直连 OpenAI API 失败的问题，以及嵌入式压缩回退的路由不一致。 |
| **并发安全** | [#85913](https://github.com/openclaw/openclaw/issues/85913) | 修复了 `EmbeddedAttemptSessionTakeoverError`——同一 session file 在心跳通道与直接通道之间的竞态。 |
| **安全加固** | [#75726](https://github.com/openclaw/openclaw/issues/75726) / [#50630](https://github.com/openclaw/openclaw/issues/50630) | 关闭运行时上下文 sanitizer 绕过漏洞（CVSS 9.3 Critical），并修复 Tailscale `auth.mode=none` 导致网关暴露于整网的问题。 |
| **部署修复** | [#87302](https://github.com/openclaw/openclaw/issues/87302) | 解决 2026.5.26 升级后 Docker 容器崩溃的回归。 |
| **体验修复** | [#76654](https://github.com/openclaw/openclaw/issues/76654) | 修复 WebChat 中心跳工具调用后 Agent 响应消失的 UI 问题。 |

此外，**PR #88340**（修复 Anthropic thinking block 签名过期导致的硬失败）已进入 **🚀 automerge armed** 状态，预计今日自动合入，将显著降低长会话的不可恢复错误率。

---

### 4. 社区热点

以下 Issues/PRs 在过去 24 小时讨论最活跃，反映了社区当前最关心的诉求：

- **[#86820] [CLOSED] Codex OAuth compaction falls back to direct OpenAI API and fails**（12 评论, 👍6）  
  链接：https://github.com/openclaw/openclaw/issues/86820  
  **诉求**：Codex OAuth 用户在上下文压缩时遭遇 API Key 缺失错误。该 Issue 快速关闭说明认证-压缩链路是近期高频痛点。

- **[#85913] [CLOSED] EmbeddedAttemptSessionTakeoverError races between heartbeat lane and channel/direct lane**（10 评论, P1）  
  链接：https://github.com/openclaw/openclaw/issues/85913  
  **诉求**：高并发嵌入式运行下的 session 文件锁竞态。标签含 `impact:session-state` 与 `impact:message-loss`，说明用户将数据完整性视为最高优先级。

- **[#73424] [OPEN] image tool: 'Failed to optimize image' error in preprocessing pipeline**（9 评论, stale）  
  链接：https://github.com/openclaw/openclaw/issues/73424  
  **诉求**：媒体理解管道中 JPEG 图像预处理失败，VLM 配置正常但内置 image tool 报错。已挂起近一个月，社区期待维护者介入。

- **[#87646] [OPEN] Feishu cannot dispatch messages after v2026.5.27 upgrade**（8 评论, P1）  
  链接：https://github.com/openclaw/openclaw/issues/87646  
  **诉求**：飞书通道在 5.27 升级后出现 `TypeError: Cannot read properties of undefined (reading 'run')`，导致消息完全无法分发。同日新增 [#88234](https://github.com/openclaw/openclaw/issues/88234) 为同一问题的独立复现。

- **[#86169] [CLOSED] Add Xiaomi MiMo Token Plan provider support**（8 评论）  
  链接：https://github.com/openclaw/openclaw/issues/86169  
  **诉求**：国内开发者希望原生接入小米 MiMo Token Plan，反映 OpenClaw 在中文生态的提供商覆盖需求增长。

---

### 5. Bug 与稳定性

按严重程度排序，今日活跃或刚关闭的关键 Bug：

**P0 / Critical（已关闭）**
- **[#50630] Tailscale serve + auth.mode=none exposes gateway to full Tailnet without authentication**  
  链接：https://github.com/openclaw/openclaw/issues/50630  
  CVSS 9.3，已关闭。Tailscale 场景下无认证暴露网关的致命漏洞已修复。

**P1（开放或刚修复，影响生产）**
- **[#87646] / [#88234] Feishu dispatch TypeError after v2026.5.27**（回归，消息完全丢失）  
  链接：https://github.com/openclaw/openclaw/issues/87646  
  **状态**：尚无明确 fix PR，但今日新增独立复现，

---

## 横向生态对比

**个人 AI 助手/自主智能体开源生态横向对比分析**  
*数据截止：2026-05-30*

---

### 1. 生态全景

当前生态呈现**“头部领跑、腰部分化、尾部休眠”**的格局。OpenClaw 以单日 500 Issues / 500 PRs 的吞吐量定义了行业基准，而 IronClaw、NanoBot、CoPaw 等项目同步维持高强度迭代，显示市场仍处于技术路线竞争期。与此同时，**安全与生产可用性**已取代功能炫技成为共同优先级——NanoBot 单日爆发 8 个安全审计 Issue，OpenClaw 紧急修复 CVSS 9.3 漏洞，均表明社区正从“Demo 可用”向“企业敢用”过渡。多通道集成（飞书、Slack、Telegram、Discord）已成为标配，但各平台原生体验（如 URL 预览、快捷键符号）的精细化适配仍是普遍欠账。

---

### 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | 版本发布 | 健康度评估 |
|------|-------------|-----------|----------|------------|
| **OpenClaw** | 500 (关闭 69) | 500 (合并/关闭 76) | v2026.5.28-beta.3/4 | **极高活跃**，修复节奏快，但通道与 Windows 稳定性债务待消化 |
| **IronClaw** | 6 (0 关闭) | 46 (合并/关闭 22) | 无 | **极高吞吐**，Reborn 架构推进迅猛，但 E2E 失败 3 天未修、crates.io 滞后 25 天 |
| **NanoBot** | 17 (关闭 2) | 34 (合并/关闭 9) | 无 | **高活跃**，安全审计集中爆发，25 个 PR 待审提示 Review 带宽压力 |
| **ZeroClaw** | 25 (关闭 6) | 50 (合并/关闭 31) | 无 | **高活跃**，24-PR 权限层迁移完成重大债务清偿，但 5 个 P1 Bug 仍开放 |
| **CoPaw** | 13 (活跃/新开) | 6 (待合并) | 无 | **高活跃**，Windows 桌面与 IDE 交互体验进入密集修复期 |
| **NanoClaw** | 1 (活跃) | 15 (合并/关闭 4) | 无 | **中高活跃**，Apple Container 兼容性与 IPC 异步化等基建修复为主 |
| **PicoClaw** | 7 | 7 (合并/关闭 1) | Nightly 1 个 | **中活跃**，合流速率偏低，6 项功能修复滞留队列，版本节奏引焦虑 |
| **Moltis** | 3 (关闭 1) | 2 (合并/关闭 1) | 无 | **中低活跃**，核心修复闭环快，但 Apple Silicon + 企业代理兼容性阻塞 |
| **LobsterAI** | 1 (新开) | 3 (合并/关闭 1) | 无 | **低活跃**，2026.5.27 版本假死回归，前端 2 个月 stale PR 未合 |
| **EasyClaw** | 0 | 0 | v1.8.19–1.8.21 (3 个补丁) | **静默发版**，零社区互动但高频硬化分发通道 |
| **TinyClaw / ZeptoClaw** | 0 | 0 | 无 | **休眠**，24 小时零活动 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是当前生态的**绝对参照系与流量中心**，其单日 500/500 的 Issues+PRs 规模是第二名 ZeroClaw 的 10 倍、NanoBot 的 15 倍。

- **核心优势**：**运行时恢复（Runtime Recovery）** 能力领先。连续两个 Beta 版本聚焦 Agent/Codex 共享运行时的状态隔离与异常恢复（子代理 `cwd` 隔离、Session locks 释放、陈旧 continuation 清理），直接解决长会话随机挂起的行业痛点。此外，ClawSweeper 自动化合并流水线（如 PR #88340 的 automerge）展现了工业级交付效率。
- **技术路线差异**：相比 IronClaw 的 Rust/Reborn 底层架构（聚焦 WASM、Trigger Loop、SSO），OpenClaw 更偏向 **Node.js/TypeScript 全栈重型框架**，强调“嵌入式子代理 + 共享运行时”的复杂编排；相比 NanoBot 的轻量级可扩展设计，OpenClaw 提供了更完整的开箱即用通道层（飞书、Telegram、Matrix 深度集成）。
- **社区规模**：中文生态覆盖最广，已原生接入小米 MiMo Token Plan，且飞书、企微等国内通道的 Bug 响应优先级与 Slack 等国际通道持平，这在开源项目中较为罕见。

---

### 4. 共同关注的技术方向

以下需求在 **3 个及以上项目** 中同步涌现，构成行业级共识：

| 技术方向 | 涉及项目 | 具体诉求 |
|---------|---------|---------|
| **安全沙箱与权限边界** | NanoBot、ZeroClaw、Moltis、NanoClaw | NanoBot 爆发 SSRF/认证绕过/权限提升 8 连击；ZeroClaw 统一 20+ 频道的 `AllowlistAspect`；Moltis 修复技能禁用粒度；NanoClaw 限制 `ask_user_question` 跨通道劫持。**诉求：多租户场景下的“敢跑”隔离。** |
| **多通道稳定性与原生语义** | OpenClaw、NanoClaw、CoPaw、ZeroClaw | OpenClaw 飞书/Telegram P1 回归；NanoClaw Discord `<URL>` 预览抑制被 Markdown 化破坏；CoPaw 飞书群组会话重构；ZeroClaw Slack Socket Mode 全拒。**诉求：尊重平台原生交互，拒绝“一刀切”抽象。** |
| **运行时状态与并发安全** | OpenClaw、NanoBot、NanoClaw、ZeroClaw | OpenClaw 修复 `EmbeddedAttemptSessionTakeoverError` 与共享状态撕裂；NanoBot 修复 `process_direct()` 绕过 session lock；NanoClaw 解决 Apple Container phantom inode 静默禁用 MCP；ZeroClaw 修复 DeepSeek `reasoning_content` 竞态丢失。**诉求：高并发与长会话下的数据完整性。** |
| **企业网络与跨平台兼容** | NanoClaw、Moltis、PicoClaw、IronClaw、EasyClaw | NanoClaw Apple Silicon 容器挂载灾难；Moltis arm64 DMI sysfs 硬编码崩溃 + Zscaler 代理 DNS 失效；PicoClaw 边缘设备（Raspberry Pi）构建诉求；IronClaw crates.io 供应链阻塞；EasyClaw 企业代理路由硬化。**诉求：Apple Silicon 与企业防火墙后的开箱即用。** |
| **上下文压缩与记忆管理** | OpenClaw、ZeroClaw、NanoClaw、NanoBot | OpenClaw Codex OAuth compaction 回退失败；ZeroClaw DeepSeek reasoning_content 被压缩器丢弃；NanoClaw 群聊上下文窗口优化；NanoBot 手动记忆模式与轻量 RAG。**诉求：长上下文下的成本、精度与可控性平衡。** |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|---------|---------|----------------|
| **OpenClaw** | 企业级多 Agent 编排、运行时恢复 | 中大型企业、复杂工作流开发者 | 重型 TS/Node 全栈，强调子代理隔离与共享状态管理 |
| **IronClaw** | 高性能 Agent 内核、认证/触发器基础设施 | Rust 开发者、基础设施工程师 | Rust 原生，Reborn 架构聚焦 WASM 扩展、OAuth/SSO、Trigger Loop |
| **NanoBot** | 可扩展轻量助手、安全沙箱、

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
*日期：2026-05-30 | 仓库：HKUDS/nanobot*

---

### 1. 今日速览

今日 NanoBot 社区活跃度极高，过去 24 小时内共有 **34 个 PR**（9 个已合并/关闭，25 个待审阅）和 **17 个 Issue**（15 个新开/活跃，2 个关闭）发生更新。最显著的信号是社区成员 @hamb1y 发起了一场**集中式安全审计**，单日提交了 8 个安全与稳定性 Issue 并配套 5 个修复 PR，覆盖 SSRF、认证绕过、权限提升和并发竞争条件。与此同时，手动记忆模式、轻量级 RAG、跨 Agent 协作等前沿功能也在并行推进，显示项目在“安全加固”与“能力扩展”两条主线上同步快跑。今日无新版本发布。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

以下 PR 已合并或关闭，推动项目在生产可用性与架构演进上迈出实质性步伐：

- **[#4054](https://github.com/HKUDS/nanobot/pull/4054)** — 一箭双雕：修复 Anthropic Provider 因 content block 缺少 `type` 字段导致的请求被拒问题（关闭 [#3993](https://github.com/HKUDS/nanobot/issues/3993)），并新增 `DreamConfig.enabled` 开关，允许用户彻底禁用 Dream 系统作业（关闭 [#3885](https://github.com/HKUDS/nanobot/issues/3885)）。
- **[#4086](https://github.com/HKUDS/nanobot/pull/4086)** — 修复 SSRF 检查中的 IPv6-mapped IPv4 地址规范化漏洞，防止攻击者通过 `::ffff:127.0.0.1` 等形式绕过网络访问限制。
- **[#4106](https://github.com/HKUDS/nanobot/pull/4106)** — 加固 Matrix 渠道的入站媒体下载逻辑，在缺少可信 `content.info.size` 时拒绝下载，防止无限制资源消耗。
- **[#3696](https://github.com/HKUDS/nanobot/pull/3696)** — 新增模型预设（Model Presets）功能，支持在配置中定义多组模型+Provider+生成参数组合，并实现运行时快速切换与自动故障转移。
- **[#4051](https://github.com/HKUDS/nanobot/pull/4051)** — 修复 Windows 平台下 `cmd.exe /c` 将换行符视为命令分隔符的缺陷，改为使用 PowerShell 执行多行命令，解决 `python -c` 多行脚本被静默截断的问题。

---

### 4. 社区热点

| 议题/PR | 热度信号 | 核心诉求分析 |
|---|---|---|
| **@hamb1y 安全审计系列**<br>[#4072](https://github.com/HKUDS/nanobot/issues/4072) ~ [#4083](https://github.com/HKUDS/nanobot/issues/4083) | 单日 8 Issue + 5 PR | 社区开始将 NanoBot 用于更严肃的生产/多租户场景，对**沙箱逃逸、SSRF、认证链、权限边界**提出工业级安全要求。 |
| **[#4054](https://github.com/HKUDS/nanobot/pull/4054)** | 同时关闭 2 个 Issue | 体现了社区协作的高效性：一个 PR 同时解决 Provider 兼容性与系统作业可观测性两大痛点。 |
| **[#4034](https://github.com/HKUDS/nanobot/pull/4034)** | 引入 GitAgent Protocol | 社区希望 NanoBot 拥抱开放 Agent 标准（agent.yaml + SOUL.md），降低跨平台 Agent 迁移成本。 |
| **[#4050](https://github.com/HKUDS/nanobot/pull/4050)** | 关联 #3885、#3948 | 用户对记忆系统的**控制权**诉求强烈，从“完全禁用 Dream”延伸到“手动管理记忆流”。 |

---

### 5. Bug 与稳定性

按严重程度降序排列，标注修复状态：

**🔴 High / Security**
- **[#4078](https://github.com/HKUDS/nanobot/issues/4078)** — OpenAI-compatible `/v1/chat/completions` 端点接受未认证请求并直接进入 Agent 循环。**（尚无 fix PR）**
- **[#4077](https://github.com/HKUDS/nanobot/issues/4077)** — WebSocket token 签发路由在缺少 `tokenIssueSecret` 时仍可无认证铸造短期 Token。**（PR [#4103](https://github.com/HKUDS/nanobot/pull/4103) 待合并）**
- **[#4076](https://github.com/HKUDS/nanobot/issues/4076)** — `message` 工具缺乏出站收件人授权，且可附加工作区/媒体根目录之外的任意绝对路径。**（PR [#4102](https://github.com/HKUDS/nanobot/pull/4102) 待合并）**
- **[#4074](https://github.com/HKUDS/nanobot/issues/4074)** — MCP HTTP/SSE 配置在 SSRF 拒绝前可能先尝试环回连接。**（PR [#4100](https://github.com/HKUDS/nanobot/pull/4100) 待合并）**
- **[#4072](https://github.com/HKUDS/nanobot/issues/4072)** — `ExecTool` 的 `restrict_to_workspace=True` 可通过工作区内的相对符号链接读取外部文件。**（PR [#4098](https://github.com/HKUDS/nanobot/pull/4098) 待合并）**

**🟡 Medium**
- **[#4111](https://github.com/HKUDS/nanobot/issues/4111)** — Heartbeat 定时任务在无任务时仍向飞书发送 "All clear."，造成通知骚扰。**（尚无 fix PR）**
- **[#4105](https://github.com/HKUDS/nanobot/issues/4105)** — Custom Provider 在 reasoning content 为空字符串时会错误丢弃该字段。**（尚无 fix PR）**
- **[#4080](https://github.com/HKUDS/nanobot/issues/4080)** — `process_direct()` 绕过 per-session dispatch lock，导致同一会话并发处理可能损坏历史记录。**（PR [#4104](https://github.com/HKUDS/nanobot/pull/4104) 待合并）**
- **[#4079](https://github.com/HKUDS/nanobot/issues/4079)** — API 在空响应重试时会重复追加 user turn。**（尚无 fix PR）**
- **[#4082](https://github.com/HKUDS/nanobot/issues/4082)** — Cron 作业重复使用固定的 `cron:{job.id}` session key，导致多次运行共享上下文。**（尚无 fix PR）**
- **[#4081](https://github.com/HKUDS/nanobot/issues/4081)** — `MemoryStore.append_history()` 在并发写入时可能分配重复 cursor。**（尚无 fix PR）**
- **[#4083](https://github.com/HKUDS/nanobot/issues/4083)** — `pathAppend` 追加在现有 `PATH` 之后，导致配置的工具路径无法优先于系统可执行文件。**（PR [#4098](https://github.com/HKUDS/nanobot/pull/4098) 待合并）**

**🟢 Low / 已修复**
- **[#3993](https://github.com/HKUDS/nanobot/issues/3993)** — Anthropic content block 缺少 type 字段。**（已通过 [#4054](https://github.com/HKUDS/nanobot/pull/4054) 修复）**
- **[#3885](https://github.com/HKUDS/nanobot/issues/3885)** — Dream 系统作业缺少全局开关。**（已通过 [#4054](https://github.com/HKUDS/nanobot/pull/4054) 修复）**

---

### 6. 功能请求与路线图信号

以下新功能需求与待合并 PR 共同勾勒出下一版本可能的演进方向：

- **手动记忆模式** — PR [#4050](https://github.com/HKUDS/nanobot/pull/4050) 已就绪，引入与自动记忆隔离的手动流，直接回应 [#3885](https://github.com/HKUDS/nanobot/issues/3885)、[#3948](https://github.com/HKUDS/nanobot/issues/3948)，**极大概率纳入下一版本**。
- **轻量级 RAG 记忆检索** — PR [#4109](https://github.com/HKUDS/nanobot/pull/4109) 基于本地 embedding 实现记忆 RAG，与现有记忆系统演进路线高度契合。
- **跨 Agent 消息总线** — PR [#3992](https://github.com/HKUDS/nanobot/pull/3992) 支持多实例 NanoBot 通过共享总线协作，属于架构级能力，可能作为实验性功能发布。
- **bwrap 额外 Bind Mounts** — Issue [#4107](https://github.com/HKUDS/nanobot/issues/4107) 请求允许用户自定义沙箱挂载路径，提升工具执行灵活性，预计会跟随沙箱安全加固一起落地。
- **GitAgent Protocol 兼容** — PR [#4034](https://github.com/HKUDS/nanobot/pull/4034) 推动 NanoBot 兼容开放 Agent 标准，利于生态互操作。
- **WebUI 时间线与

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
**日期：** 2026-05-30  
**仓库：** zeroclaw-labs/zeroclaw  

---

### 1. 今日速览

过去 24 小时项目活跃度极高，Issues 更新 25 条（关闭 6 条）、PR 更新 50 条（合并/关闭 31 条），无新版本发布。工程债务出现大规模清偿：社区贡献者 yijunyu 主导的 24-PR `AllowlistAspect` 迁移系列集中关闭，统一了 20 余个频道的权限控制逻辑。与此同时，频道层（Email、Telegram、TTS）与桌面端进入密集迭代，新开多条功能 PR。但稳定性压力依然突出，当前仍有 5 个 P1 级 Bug 处于 Open 状态，涉及 Slack、Telegram 语音、工具安全策略及 MCP 过滤失效。

---

### 2. 版本发布

今日无新版本发布。最新 Release 仍为 v0.7.5，但主分支文档与部分功能已推进至 v0.8.0-beta-1 阶段（相关风险见 [#6997](https://github.com/zeroclaw-labs/zeroclaw/issues/6997)）。

---

### 3. 项目进展

**权限层统一（重大工程债务清偿）**  
贡献者 yijunyu 发起的 24-PR 迁移系列今日大量合并/关闭，包括 [#6791](https://github.com/zeroclaw-labs/zeroclaw/pull/6791)、[#6792](https://github.com/zeroclaw-labs/zeroclaw/pull/6792)、[#6793](https://github.com/zeroclaw-labs/zeroclaw/pull/6793)、[#6794](https://github.com/zeroclaw-labs/zeroclaw/pull/6794)、[#6795](https://github.com/zeroclaw-labs/zeroclaw/pull/6795)、[#6796](https://github.com/zeroclaw-labs/zeroclaw/pull/6796)、[#6797](https://github.com/zeroclaw-labs/zeroclaw/pull/6797)、[#6798](https://github.com/zeroclaw-labs/zeroclaw/pull/6798)、[#6799](https://github.com/zeroclaw-labs/zeroclaw/pull/6799)、[#6800](https://github.com/zeroclaw-labs/zeroclaw/pull/6800) 等。该系列将 Slack、Telegram、Discord、WhatsApp、Email、Lark、Nextcloud Talk 等 20+ 频道中手写的 `is_*_allowed` 谓词全部替换为共享的 `aspect_std::AllowlistAspect`，显著降低了权限逻辑的碎片化与维护成本。

**DeepSeek 推理链修复**  
- [#6233](https://github.com/zeroclaw-labs/zeroclaw/issues/6233) 已关闭：`chat_messages_to_native()` 在多轮对话中丢弃 `reasoning_content` 的问题得到修复，DeepSeek V4 第二轮回话 400 Bad Request 的故障消除。  
- [#6269](https://github.com/zeroclaw-labs/zeroclaw/issues/6269) 已关闭：上下文压缩器（Context compressor）在压缩助手消息时丢失 `reasoning_content` 的问题已修复。

**频道与通道能力扩展**  
- [#3090](https://github.com/zeroclaw-labs/zeroclaw/issues/3090) 已关闭：企业微信（Wecom）频道支持正式落地，覆盖 WebSocket 与 Webhook 双模式。  
- [#5761](https://github.com/zeroclaw-labs/zeroclaw/issues/5761) 已关闭：Webhook 频道出站发送增加指数退避重试，避免瞬态故障导致消息静默丢失。

**桌面与构建修复**  
- [#6964](https://github.com/zeroclaw-labs/zeroclaw/issues/6964) 已关闭：修复 Windows 桌面构建因重复 MANIFEST 资源导致的 `CVT1100/LNK1123` 错误，CI 流程恢复。

---

### 4. 社区热点

| 议题/PR | 评论 | 核心诉求 |
|---|---|---|
| [#6848](https://github.com/zeroclaw-labs/zeroclaw/pull/6848) | 寻求反馈中 | **v0.8.0-beta-2 基座 PR**：引入 zerocode TUI、RPC socket 传输、DenyWithEdit 审批流，标记为 "DO NOT MERGE"，覆盖核心、代理、频道、工具等全模块，是近期最大的架构级变更。 |
| [#6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699) | 7 | **MCP 工具过滤失效**：`tool_filter_groups` 配置在真实 MCP 工具表面完全无操作，暴露配置解析层与执行层之间的前缀匹配 bug，且与 `deferred_loading` 无集成。 |
| [#6233](https://github.com/zeroclaw-labs/zeroclaw/issues/6233) | 8 | **DeepSeek 多轮对话中断**：`reasoning_content` 在纯文本助手消息中被丢弃，导致第二轮回话必现 400 错误，影响生产环境使用。 |
| [#6969](https://github.com/zeroclaw-labs/zeroclaw/issues/6969) | 2 | **统一输出路由模型 RFC**：用户从 Letta 迁移而来，希望恢复“按用户偏好或显式指令控制回复投递方式（如早间简报发邮件、紧急消息发短信）”的能力。 |

---

### 5. Bug 与稳定性

按严重程度排序：

**S1 — 功能中断（Open）**
- [#6992](https://github.com/zeroclaw-labs/zeroclaw/issues/6992) **Slack Socket Mode 拒绝所有消息**：所有入站消息被标记为 "unauthorized user"，Socket Mode 完全不可用。**暂无 fix PR。**
- [#6999](https://github.com/zeroclaw-labs/zeroclaw/issues/6999) **Telegram 语音转录完全失效**：频道从未连接 `transcription_provider` 别名，所有语音消息被静默丢弃。**Fix PR [#7019](https://github.com/zeroclaw-labs/zeroclaw/pull/7019) 已开。**

**S2 — 行为降级（Open）**
- [#6991](https://github.com/zeroclaw-labs/zeroclaw/issues/6991) **工具序列化绕过安全策略**：`

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
*日期：2026-05-30 | 分析师：AI 开源项目分析师*

---

### 1. 今日速览

PicoClaw 社区今日活跃度处于高位，过去 24 小时内共有 **14 条工作项更新**（Issues 与 PRs 各 7 条），但代码合流速率偏低，仅 **1 条 Issue 与 1 条 PR 完成闭环**。项目推送了基于 `main` 分支的自动化 Nightly 构建，然而正式版本发布节奏已引发社区显性反馈。值得关注的是，v0.2.9 版本在 Web UI 侧出现会话历史污染与上下文压缩显示异常等回归问题；与此同时，Azure Identity 企业认证、图片拖拽上传、繁体中文国际化等 6 项功能修复与体验增强正滞留于待合并队列，等待维护者 Review。

---

### 2. 版本发布

**Nightly Build: `v0.2.9-nightly.20260530.e81d3710`**  
🔗 [Release 页面](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)

- **性质**：自动化 CI 构建，非稳定版本。  
- **变更范围**：包含自 `v0.2.9` 标签以来所有进入 `main` 分支的提交，具体变更可查看 Full Changelog。  
- **迁移与使用注意**：官方明确提示该构建 **可能不稳定，建议谨慎使用**。生产环境或边缘设备（如 Raspberry Pi）建议继续停留在 `v0.2.9` 正式版，并等待后续稳定版本。

---

### 3. 项目进展

今日代码合流有限，核心进展体现在问题闭环与多项质量修复的**待合并储备**上：

- **Issue #2351 已关闭** — Validate skill binary requirements before injecting into system prompt  
  🔗 [sipeed/picoclaw#2351](https://github.com/sipeed/picoclaw/issues/2351)  
  该增强请求推动社区关注 `metadata.nanobot.requires.bins` 的前置校验机制，避免 LLM 在缺失二进制工具（如 `agent-browser`）时错误承诺能力，提升了系统提示注入的健壮性。

- **PR #2877 已关闭（未合并）** — feat(security): add optional tirith pre-exec scanning  
  🔗 [sipeed/picoclaw#2877](https://github.com/sipeed/picoclaw/pull/2877)  
  因长期滞留（stale），该安全增强 PR 被关闭，未能将 Tirith 终端安全扫描纳入主分支。

**待合并的重要贡献（6 项）**：
- **#2971** — Azure OpenAI 提供商新增可选 Azure Identity 认证支持（企业合规方向）。
- **#2969** — Web 前端新增聊天图片粘贴与拖放上传（UX 方向）。
- **#2967** — 修复 Codex 流式输出在 `response.output` 为 `null` 时丢失文本增量的问题。
- **#2965** — 修复 `restrict_to_workspace` 启用时，workspace guard 将无 scheme URL（如 `wttr.in/Beijing`）误解析为绝对路径的缺陷。
- **#2935** — 新增繁体中文（zh-TW）国际化与文档。
- **#2662** — 统一 providers 文档中的供应商表格，减少冗余。

---

### 4. 社区热点

| 工作项 | 互动指标 | 核心诉求分析 |
|---|---|---|
| **#2625** [Feature] Provide compiled builds with WhatsApp support<br>🔗 [Issue](https://github.com/sipeed/picoclaw/issues/2625) | 7 评论, 1 👍 | **边缘设备部署痛点**。用户在 Raspberry Pi Zero 2（arm64）上使用 PicoClaw 时，默认构建未包含 WhatsApp 支持，导致快速更新困难。社区希望构建系统通过编译标签默认集成该能力，而非让用户自行编译。 |
| **#2952** 好久没发新版本<br>🔗 [Issue](https://github.com/sipeed/picoclaw/issues/2952) | 2 评论, 0 👍 | **发布节奏与质量焦虑**。用户一次性抛出 3 个高频痛点：exec 命令 `actions:run` 缺失导致模型空转报错、QQ 渠道重启死循环、模型提供商配置体验落后。该 Issue 成为今日“用户情绪集中度”最高的反馈入口。 |
| **#2929** Add first-class agent-to-agent communication<br>🔗 [Issue](https://github.com/sipeed/picoclaw/issues/2929) | 2 评论, 1 👍 | **多智能体架构演进**。在已有 `spawn` / `delegate` 能力基础上，社区呼吁建立对等通信层，支持协作式工作流。这代表了从“单助手”向“多智能体系统”跃迁的路线图书信号。 |

---

### 5. Bug 与稳定性

按严重程度排列的今日 Bug 与回归：

- **🔴 高 / 回归** — **Web UI 会话历史污染**  
  **#2972**: After upgrade to v0.2.9, Web UI message chaos, every new session always attached some old message history  
  🔗 [Issue](https://github.com/sipeed/picoclaw/issues/2972) | 报告者: @xpader | **暂无 fix PR**  
  影响核心交互：升级 v0.2.9 后，新建聊天会话会错误附加旧消息历史，严重干扰多轮对话上下文隔离。

- **🟡 中 / 显示异常** — **上下文压缩 Token 数固定显示**  
  **#2968**: /context always show Compress at: 76800 tokens  
  🔗 [Issue](https://github.com/sipeed/picoclaw/issues/2968) | 报告者: @xpader | **暂无 fix PR**  
  在 MiniMax 模型与 128k 上下文配置下，`/context` 命令始终显示压缩阈值固定在 76800，疑似前端或配置读取逻辑错误。

- **🟡 中 / 渠道稳定性** — **QQ 渠道重启死循环**  
  **#2952**（内嵌反馈）| 报告者: @xhynice | **暂无 fix PR**  
  QQ 渠道在重启成功后，若收到新消息会再次触发重启，只有清除历史上下文才能终止循环，存在状态管理或消息触发器缺陷。

- **🟢 已定位 / 有修复 PR** — **Codex 流式输出丢失**  
  **#2967**: fix(codex): preserve streamed output text deltas  
  🔗 [PR](https://github.com/sipeed/picoclaw/pull/2967) | 作者: @miruchigawa  
  修复 OpenAI/Codex OAuth 场景下，后端流式返回有效文本增量但 `response.output` 为 `null` 时，前端收到空响应的问题。

- **🟢 已定位 / 有修复 PR** — **Workspace Guard URL 解析错误**  
  **#2965**: fix(tools):

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-05-30 | 仓库：nanocoai/nanoclaw*

---

### 1. 今日速览

过去 24 小时，NanoClaw 维持**中高活跃度**：共 15 个 PR 发生更新，其中 4 条已合并/关闭，11 条仍待审阅；Issues 侧有 1 条活跃更新，无新版本发布。今日工作呈现“**重修复、强基建、多技能扩展**”的特征——社区集中攻克了 Apple Container 上的挂载竞争与安全边界问题，同时合并了群聊上下文、可观测性和 IPC 性能等关键改进。整体项目健康度良好，但长期悬而未决的 WebUI 控制面板（#212）仍需维护者决策。

---

### 2. 版本发布

无。

---

### 3. 项目进展

今日共有 **4 个 PR 完成闭环**，推动项目在核心引擎、可观测性和多通道体验上取得实质进展：

- **群聊上下文窗口优化** — [#2645](https://github.com/nanocoai/nanoclaw/pull/2645)（已关闭）为 group chat 引入按 agent-group 的 `context_messages` 窗口，被 `@mention` 触发的 agent 可自动获得最近 N 条未读消息作为上下文块，显著改善多 agent 群聊的连贯性。
- **多通道日志溯源** — [#2521](https://github.com/nanocoai/nanoclaw/pull/2521)（已关闭）在 XML 消息属性中追加 `from-channel` 与 `from-type`，使外部监控面板能基于 `.jsonl` 回放准确识别 Telegram、Discord 等不同来源。
- **Claude Provider 可观测性** — [#2456](https://github.com/nanocoai/nanoclaw/pull/2456)（已关闭）接入 LangFuse，覆盖延迟、API 错误（重试/限流）、工具调用耗时及上下文压缩 token 数，补齐了生产环境观测短板。
- **IPC 异步化重构** — [#6](https://github.com/nanocoai/nanoclaw/pull/6)（已关闭）将 IPC 从忙轮询（busy-loop polling）替换为 `fs.watch` 事件驱动，并全面改用 `fs.promises` 异步 API，降低主进程事件循环阻塞风险。

---

### 4. 社区热点

今日讨论焦点集中在 **macOS/Apple Container 兼容性**、**安全边界** 与 **Discord 适配器回归** 三个主题：

- **Apple Container 挂载灾难** — [#2649](https://github.com/nanocoai/nanoclaw/pull/2649) 与 [#2650](https://github.com/nanocoai/nanoclaw/pull/2650)（均为今日新建，待合并）揭示 Apple Container 上嵌套文件挂载产生 phantom inode（`stat()` 正常但读取报 `EACCES`），导致所有通过 `ncl groups config add-mcp-server` 配置的 MCP 服务器被**静默禁用**。配套修复通过跳过损坏的嵌套挂载并增加重试逻辑解决。  
  *背后诉求：Apple Silicon 开发者占比上升，容器运行时兼容性已成为核心体验瓶颈。*
- **交互式安全问题** — [#2651](https://github.com/nanocoai/nanoclaw/pull/2651)（今日新建，待合并）限制 `ask_user_question` 的响应只能来自原下发通道，防止跨通道/跨线程的回答劫持。  
  *背后诉求：生产部署中对多通道身份边界的安全焦虑正在上升。*
- **Discord URL 预览抑制失效** — [#2044](https://github.com/nanocoai/nanoclaw/issues/2044)（👍: 2，评论: 1）反馈 v2 将 Discord 原生的 `<URL>`（抑制预览）错误转换为 `[URL](URL)`（反而强制预览），破坏了平台原生语义。  
  *背后诉求：社区期待 chat adapter 尊重各平台的消息语法约定，而非统一 Markdown 化。*

---

### 5. Bug 与稳定性

按严重程度排列，今日暴露的稳定性风险如下：

| 严重度 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| **P0** | Apple Container 嵌套挂载产生 phantom inode，`container.json` / `CLAUDE.md` 读取报 `EACCES`，**静默禁用全部 MCP 服务器** | 待修复 | [#2649](https://github.com/nanocoai/nanoclaw/pull/2649) |
| **P0** | Apple Container `virtio-fs` 挂载竞争导致 `container.json` 首次读取失败 | 待修复 | [#2650](https://github.com/nanocoai/nanoclaw/pull/2650) |
| **P1** | `ask_user_question` 响应未验证来源通道，存在跨通道回答风险 | 待修复 | [#2651](https://github.com/nanocoai/nanoclaw/pull/2651) |
| **P1** | Discord 适配器 v2 错误处理 `<URL>`，导致链接预览抑制失效，与预期语义相反 | 待修复 | 暂无（见 [#2044](https://github.com/nanocoai/nanoclaw/issues/2044)） |

---

### 6. 功能请求与路线图信号

结合今日活跃 PR，以下功能方向信号强烈，**极有可能被纳入下一版本或近期迭代**：

- **灾难恢复与备份** — [#2084](https://github.com/nanocoai/nanoclaw/pull/2084)（open，创建于 2026-04-28）提供每日快照、S3 后端及全量/单 agent 恢复 CLI，直接回应 v2 用户“无退路”的痛点。
- **防火墙友好的 GitHub 集成** — [#2301](https://github.com/nanocoai/nanoclaw/pull/2301)（open）新增轮询模式（Mode B），无需入站端口即可对接 GitHub REST API，解决 NAT/企业防火墙后部署障碍。
- **本地语音转录** — [#2317](https://github.com/nanocoai/nanoclaw/pull/2317)（open）集成 openai-whisper / whisper.cpp，为 NanoClaw 引入免费的语音输入通道。
- **可观测性生态扩展** — [#2648](https://github.com/nanocoai/nanoclaw/pull/2648)（open，今日新建）新增 `/upload-trace` 命令，支持将 session trace 上传至 Hugging Face，与已合并的 LangFuse 支持（#2456）形成互补。
- **AWS 凭证代理** — [#2634](https://github.com/nanocoai/nanoclaw/pull/2634)（open）引入 `paws4claws` 技能，简化 AWS 凭证代理在 agent group 中的挂载配置。

**路线图风险点**：[#212](https://github.com/nanocoai/nanoclaw/pull/212) WebUI 控制面板（11 个标签页、Lit+Vite+Fastify 全栈实现）已标记为 `Blocked` / `Pending Closure` 近 4 个月，若维护者不尽快决策合并或拆分，该大型功能可能面临废弃。

---

### 7. 用户反馈摘要

从今日 Issues 与 PR 摘要中提炼的真实用户声音：

- **平台原生语义不可破坏**：Discord 用户明确依赖 `<URL>` 语法控制链接预览，v2 的 Markdown 统一化处理被视为**回归**而非改进（[#2044](https://github.com/nanocoai/nanoclaw/issues/2044)）。
- **多通道运维需要更开放的元数据**：Telegram + Discord 双通道用户通过解析 `.jsonl` 自建监控面板，迫切需要 `from-channel` 等字段（[#2521](https://github.com/nanocoai/nanoclaw/pull/2521)）。
- **数据安全感缺失**：用户担忧“careless `rm -rf`”、磁盘故障和迁移失败，现有 v2 缺乏官方备份机制是核心焦虑（[#2084](https://github.com/nanocoai/nanoclaw/pull/2084)）。
- **企业网络环境下的可用性**：大量用户处于防火墙/NAT 后，要求 GitHub 集成支持**纯出站连接**的轮询模式（[#2301](https://github.com/nanocoai/nanoclaw/pull/2301)）。

---

### 8. 待处理积压

以下 Issue/PR 长期未获最终响应，提醒维护者优先关注：

- **WebUI 控制面板决策僵局** — [#212](https://github.com/nanocoai/nanoclaw/pull/212)（创建于 2026-02-13，最后更新今日，状态：`Blocked` / `Pending Closure`）。该 PR 体量巨大（11 tabs / 4 groups），已停滞 3 个月以上，社区需要维护者明确是合并、关闭还是拆分为更小单元。
- **备份与恢复方案待审** — [#2084](https://github.com/nanocoai/nanoclaw/pull/2084)（创建于 2026-04-28，已超 1 个月）。作为 v2 唯一的灾难恢复方案，其长期悬置增加了用户数据风险。
- **开发者体验基建** — [#2537](https://github.com/nanocoai/nanoclaw/pull/2537)（创建于 2026-05-18）pre-commit hooks（prettier + eslint + typecheck + vitest）待合并，可显著降低后续 PR 的 review 噪音。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-05-30 | 仓库：nearai/ironclaw*

---

### 1. 今日速览

IronClaw 今日展现出极高的工程吞吐量，单日 46 个 PR 更新（22 条已合并/关闭，24 条待审阅），但 Issue 侧呈现“零关闭”状态，6 条活跃 Issue 全部悬而未决。核心开发火力集中在 **Reborn 架构的认证体系（OAuth/SSO）、触发器循环（Trigger Loop）与外部产品适配器（Slack/Notion）** 三大主线。需警惕的是，Nightly E2E 测试持续失败已 3 天未获人工响应，且 crates.io 版本滞后问题已持续近一个月，对下游 Rust 消费者造成实际供应链阻塞。

---

### 2. 版本发布

**无新版本发布。**  
值得注意的是，仓库 Git Tag 已推进至 `v0.27.0`（2026-04-29），但 [crates.io](https://crates.io/crates/ironclaw) 仍停留在 `0.24.0`（2026-03-31）。版本发布管道存在明显滞后，下游用户因依赖 wasmtime 28.x 的 CVE 修复而被强制锁定在旧版本。

---

### 3. 项目进展

今日合并/关闭的 22 条 PR 中，以下几条标志关键里程碑：

- **Reborn 认证体系端到端闭环**：[#4245](https://github.com/nearai/ironclaw/pull/4245)（product-facing auth HTTP 路由）、[#4231](https://github.com/nearai/ironclaw/pull/4231)（auth consumers staged credentials）、[#4246](https://github.com/nearai/ironclaw/pull/4246)（NEAR AI MCP 凭证迁移）、[#4233](https://github.com/nearai/ironclaw/pull/4233)（GitHub WASM 凭证迁移）全部关闭，标志着 product-auth 从底层存储到 HTTP 表面的完整链路基本打通。
- **MCP 生态扩展**：[#4228](https://github.com/nearai/ironclaw/pull/4228) 关闭，完成 Notion MCP extension 向 Reborn 的移植，补全了生产力工具链的读写/评论/视图/团队/用户全表面。
- **Agent 核心体验加固**：社区贡献者 `@neoguyverx` 的补丁系列（[#4250](https://github.com/nearai/ironclaw/pull/4250)、[#4251](https://github.com/nearai/ironclaw/pull/4251)、[#4252](https://github.com/nearai/ironclaw/pull/4252)、[#4253](https://github.com/nearai/ironclaw/pull/4253)）全部合并，涵盖**可中断 LLM 调用**、**结构化上下文压缩**、**记忆写入行为助推**和**身份文件注入扫描**，显著提升了 Agent 的安全性与长会话可靠性。
- **Trigger 架构接口冻结**：[#4248](https://github.com/nearai/ironclaw/pull/4248)（delivery resolution contract）与 [#4249](https://github.com/nearai/ironclaw/pull/4249)（trigger trusted ingress contract）关闭，为 Reborn 的调度与出站投递系统锁定了设计契约。

---

### 4. 社区热点

| 条目 | 热度信号 | 核心诉求分析 |
|------|----------|--------------|
| [#3259](https://github.com/nearai/ironclaw/issues/3259) Publish 0.25.0–0.27.0 to crates.io | 12 条评论，0 👍 | **供应链安全焦虑**。下游因 wasmtime 28.x CVE 被钉死在 0.24.0，用户对 crates.io 发布节奏与 Git Tag 不同步表达强烈关切。 |
| [#3857](https://github.com/nearai/ironclaw/issues/3857) Slack ProductAdapter MVP | 5 条评论 | **企业集成场景**。需求明确指向默认关闭的 Slack 适配器，支持 DM 与 App Mention，对应 XL 级 PR [#4035](https://github.com/nearai/ironclaw/pull/4035) 正在审阅。 |
| [#4257](https://github.com/nearai/ironclaw/pull/4257) AuthPromptView + WebUI OAuth card | 今日新建 XL 级 PR | **统一认证体验**。堆叠在已关闭的 #4245 之上，直接实现 GSuite/Notion MCP/GitHub PAT 三大 AuthFlow 的 Rust wire-shape 与 WebUI v2 组件，是 #4112 路线图的核心执行体。 |

---

### 5. Bug 与稳定性

按严重程度排列：

- **🔴 High — [#4108 Nightly E2E failed](https://github.com/nearai/ironclaw/issues/4108)**  
  创建于 2026-05-27，今日仍 **OPEN**。`Full E2E / E2E (v2-engine)` 作业失败，0 条评论，**尚无修复 PR**。自动化回归信号已衰减 3 天，需立即人工介入。

- **🟠 High — [#3259 crates.io 版本滞后](https://github.com/nearai/ironclaw/issues/3259)**  
  虽非代码缺陷，但造成下游 CVE 暴露面，属于**供应链稳定性风险**。25 天未解决。

- **🟡 Medium — [#4241 Live Workspace Prompt Inputs Invalidate KV Cache Reuse](https://github.com/nearai/ironclaw/issues/4241)**  
  创建于 2026-05-29。Workspace 实时输入破坏跨轮次 KV 缓存前缀匹配，直接导致推理成本上升与延迟增加，**尚无 fix PR**。

---

### 6. 功能请求与路线图信号

- **Slack 集成进入最后一公里**：Issue [#3857](https://github.com/nearai/ironclaw/issues/3857) + PR [#4035](https://github.com/nearai/ironclaw/pull/4035) 明确指向 Reborn 原生 Slack 支持，预计随下一 Reborn 里程碑发布。
- **WebUI v2 统一认证**：路线图 [#4112](https://github.com/nearai/ironclaw/issues/4112) 通过 [#4257](https://github.com/nearai/ironclaw/pull/4257)（UI 实现）、[#4256](https://github.com/nearai/ironclaw/pull/4256)（E2E 测试）、[#4229](https://github.com/nearai/ironclaw/pull/4229)（GitHub SSO）三线并进，下一版本极可能交付浏览器内 OAuth 全链路。
- **Trigger Loop 与出站投递**：[#4254](https://github.com/nearai/ironclaw/pull/4254)（trusted inbound facade）、[#4255](https://github.com/nearai/ironclaw/pull/4255)（outbound delivery resolution）待合并，结合已关闭的契约 PR，预示定时触发与通信投递子系统即将从设计转入实现。
- **Agent 认知架构升级**：[#4251](https://github.com/nearai/ironclaw/pull/4251)（结构化压缩）与 [#4252](https://github.com/nearai/ironclaw/pull/4252)（记忆助推）已合并，项目正从“功能可用”向“长期自主运行”

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-05-30*

---

### 1. 今日速览

LobsterAI 今日整体活跃度偏低，过去24小时内仅新增 **1** 条 Issue，PR 更新 **3** 条但仅 **1** 条完成闭环，无新版本发布。社区注意力高度集中在 **2026.5.27 版本的稳定性缺陷** 上，新报告的窗口假死问题已确认可复现，存在明确的回归风险。同时，两项创建于4月初的前端体验修复 PR 今日同步更新但仍未合并，显示前端体验债务仍在累积，项目健康度需关注缺陷响应速度与代码审查吞吐量。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日共有 **1** 条 PR 完成合并/关闭，推动项目在协作架构层面取得实质进展：

- **PR #2078** `[CLOSED]` **feat(cowork): emit selected-skill routing metadata instead of inlining prompts**  
  链接：https://github.com/netease-youdao/LobsterAI/pull/2078  
  贡献者 @fisherdaddy 提交的协作模块架构优化已关闭。该变更将选中技能（selected-skill）的路由元数据从 Prompt 内联模式改为外发模式，涉及 `renderer`、`docs`、`cowork` 三个核心领域。这标志着项目在多智能体协作架构上向前迈进，为后续技能动态路由、上下文解耦及更灵活的 Cowork 流程编排奠定了基础。

---

### 4. 社区热点

今日讨论焦点集中在稳定性缺陷与长期未决的前端体验债务：

- **Issue #2079 — 执行结果窗口滚动到顶端会假死**  
  链接：https://github.com/netease-youdao/LobsterAI/issues/2079  
  今日唯一新增 Issue，由 @fcinfo 报告，已获得 **1** 条评论。用户明确指出 **2026.5.27 版本** 存在可复现的致命假死：执行结果窗口滚动至顶端时界面完全无响应。该 Issue 迅速成为社区焦点，反映出用户对最新版本稳定性的强烈担忧，亟需维护者介入诊断。

- **PR #1466 / #1467 — 两项前端体验修复同步更新**  
  链接：https://github.com/netease-youdao/LobsterAI/pull/1466 | https://github.com/netease-youdao/LobsterAI/pull/1467  
  分别针对 MCP 模态框布局缺陷与 macOS 快捷键显示错误。两项 PR 均创建于 4 月初，今日同时被更新，显示贡献者仍在积极推动合并，但长期未决的状态已引发社区对前端代码审查吞吐量的关注。

---

### 5. Bug 与稳定性

按严重程度降序排列：

1. **🔴 高：执行结果窗口滚动假死（无修复 PR）**  
   **Issue #2079**（https://github.com/netease-youdao/LobsterAI/issues/2079）  
   2026.5.27 版本回归缺陷，滚动执行结果窗口至顶端即可触发界面假死，用户已确认可复现。该问题直接影响核心工作流，目前**尚无关联修复 PR**，建议维护者立即标记为 `priority/high` 并分配开发者跟进。

2. **🟡 中：MCP 模态框关闭按钮不可达（有 PR 待合并）**  
   **PR #1466**（https://github.com/netease-youdao/LobsterAI/pull/1466）  
   当 MCP 服务器表单内容过多时，模态框整体滚动导致底部操作按钮（Cancel 等）被推出可视区域。修复方案已提交近两个月，状态为 `stale/open`，存在可用性风险。

3. **🟢 低-中：macOS 快捷键显示不符合平台惯例（有 PR 待合并）**  
   **PR #1467**（https://github.com/netease-youdao/LobsterAI/pull/1467）  
   设置面板在 macOS 上错误显示 `Ctrl` 而非 `⌘`，根因为平台判断逻辑缺失。修复 PR 同样滞留近两个月，影响 macOS 用户的专业感知。

---

### 6. 功能请求与路线图信号

今日未出现新增功能请求 Issue。但从已关闭的 **PR #2078**（https://github.com/netease-youdao/LobsterAI/pull/2078）可提取到明确的路线图信号：项目正在将 `cowork` 模块的 Prompt 内联逻辑重构为基于路由元数据的外发模式。这一架构调整暗示下一版本可能强化**技能（Skill）的动态发现与跨模块路由能力**，为多智能体协作或插件化技能市场做准备。两个 stale 的 UI 修复 PR（#1466、#1467）属于体验债务清理，预计会在合并窗口期被批量纳入，但不会带来新功能。

---

### 7. 用户反馈摘要

从今日数据可提炼以下真实用户信号：

- **稳定性焦虑**：@fcinfo 明确提及"2026.5.27 版本"并强调"现象能复现"，表明用户对近期版本的质量信心下降，假死类问题极易导致数据丢失或工作中断。
- **平台体验割裂**：macOS 用户（PR #1467）长期面临快捷键显示与系统惯例不符的问题，显示项目在多平台适配上存在"Windows 优先"的开发惯性。
- **复杂表单的可用性瓶颈**：MCP 配置表单在变量增多时的布局崩溃（PR #1466），反映出高级用户在配置复杂 Server 时的前端体验瓶颈。

---

### 8. 待处理积压

以下长期未决项需要维护者重点关注，避免贡献者流失与体验债务膨胀：

- **PR #1466**（https://github.com/netease-youdao/LobsterAI/pull/1466）  
  创建于 **2026-04-04**，距今近两个月，修复 MCP 模态框滚动布局问题。今日虽有更新但仍未合并，建议尽快完成 UI Review。

- **PR #1467**（https://github.com/netease-youdao/LobsterAI/pull/1467）  
  创建于 **2026-04-04**，修复 macOS 快捷键符号显示。同样处于 `stale/open` 状态，属于**低风险、高用户感知**的"Quick Win"，建议优先合入以提升 macOS 用户满意度。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-05-30 | 数据来源：github.com/moltis-org/moltis*

---

### 1. 今日速览

过去 24 小时，Moltis 社区保持中等活跃度，共产生 3 条 Issue 更新（2 条新开、1 条关闭）与 2 条 PR 更新（1 条待合并、1 条已关闭）。核心进展体现在技能（Skills）系统的精细化管控能力得到修复，同时社区新暴露了 Apple Silicon 与企业代理环境下的两项沙盒运行时缺陷。整体项目健康度良好，核心 Bug 修复闭环迅速，但跨平台容器兼容性仍需关注。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

**已合并/关闭的 Pull Request**

- **#1084 fix(skills): track bundled skill disables individually**  
  链接：https://github.com/moltis-org/moltis/pull/1084  
  作者 @penso 提交了针对技能禁用状态的修复，将“分类级别禁用”与“单个捆绑技能禁用”解耦。该 PR 在聊天发现（chat discovery）、Web API 及技能详情响应中统一了启用状态辅助逻辑，并为“单独禁用某一 Apple 技能而不禁用整个 Apple 分类”的场景补充了回归测试。该修复直接关闭了 Issue #1083，标志着技能配置系统的颗粒度与一致性向前迈出关键一步。

**待合并的 Pull Request**

- **#1087 chore(deps): bump tar from 0.4.45 to 0.4.46**  
  链接：https://github.com/moltis-org/moltis/pull/1087  
  Dependabot 发起的常规依赖升级，更新 `tar` crate 至 0.4.46，目前处于待审阅状态。

---

### 4. 社区热点

今日所有 Issue 与 PR 的评论数与点赞数均为 0，尚未形成高互动讨论。技术热点集中在 **Apple Silicon / macOS 容器后端**的兼容性问题上：

- **#1085 Docker sandbox fails on arm64: /sys/class/dmi mount error**  
  链接：https://github.com/moltis-org/moltis/issues/1085  
  该 Issue 揭示了 arm64 架构下因硬编码 x86 DMI sysfs 路径导致的沙盒启动失败，直接影响 Apple Silicon 用户的开箱体验。

- **#1086 Apple Containers backend: sandbox image build fails (no DNS behind corporate proxy)**  
  链接：https://github.com/moltis-org/moltis/issues/1086  
  反映了企业级网络环境（Zscaler 等 HTTPS 代理）下，Apple Containers 后端 VM 内 DNS 解析失效的痛点。

**诉求分析**：社区正在从“功能可用”向“跨平台稳定运行”与“企业环境适配”提出更高要求，macOS 用户群体对沙盒后端的选择（Docker vs Apple Containers）面临双重阻塞。

---

### 5. Bug 与稳定性

按严重程度排列如下：

| 严重程度 | Issue | 状态 | 说明 | Fix PR |
|---|---|---|---|---|
| **高** | **#1085** Docker sandbox fails on arm64: /sys/class/dmi mount error (read-only sysfs) | 开放 | Apple Silicon 上因硬编码 `/sys/class/dmi` 与 `/sys/devices/virtual/dmi` 挂载点导致沙盒无法启动。DMI 为 x86 SMBIOS 特性，arm64 环境不存在该路径。 | 暂无 |
| **中** | **#1086** Apple Containers backend: sandbox image build fails (no DNS behind corporate proxy) | 开放 | 企业代理后 Apple Containers builder VM 内 DNS 不可用，阻塞沙盒镜像预构建。 | 暂无 |
| **已修复** | **#1083** Skills enabled/disabled per-category, it's unable to enable/disable one skill | 已关闭 | 无法对单个捆绑技能进行独立启用/禁用操作。 | **#1084** 已合并 |

---

### 6. 功能请求与路线图信号

今日未出现显式的功能请求（Feature Request）标签 Issue。但从 Bug 报告中可提取以下**路线图信号**：

1. **跨平台沙盒运行时检测**：#1085 表明容器后端需要引入架构感知的路径/挂载点检测逻辑，避免将 x86 特有的 sysfs 结构硬编码到 arm64 运行时。
2. **企业网络与代理支持**：#1086 提示 Apple Containers 后端需要支持配置外部 DNS 或代理透传，以适应企业安全策略。
3. **技能状态管理精细化**：#1084 的合并显示官方正持续投入技能市场的配置灵活性，未来可能在分类与个体技能之间引入更细粒度的策略控制（如环境级覆盖、用户级偏好记忆）。

---

### 7. 用户反馈摘要

从今日 Issue 中提炼的真实用户场景与痛点：

- **痛点：Apple Silicon 上的基础可用性**  
  用户 @karlmdavis 在 arm64 环境下遭遇 Docker 沙盒启动即崩溃，核心原因是项目对非 x86 平台的 sysfs 结构缺乏兼容。这反映出跨平台 CI/CD 或集成测试可能未覆盖 arm64 Docker Desktop 场景。

- **痛点：企业网络环境下的工具链断裂**  
  同一用户在使用 Apple Containers 后端时，因 Zscaler 代理导致 builder VM 内 DNS 失效，无法完成沙盒镜像构建。说明在受限网络下的离线/代理友好型部署仍是短板。

- **正面反馈：核心功能修复迅速**  
  Issue #1083（技能无法单独禁用）在创建当日即被 PR #1084 修复并关闭，显示维护团队对核心交互逻辑缺陷的响应效率较高，增强了社区对项目治理的信心。

---

### 8. 待处理积压

今日新开的两条 Issue 均尚无维护者响应或分配，鉴于其直接影响特定用户群体的基础使用，建议优先关注：

- **#1085** Docker sandbox fails on arm64: /sys/class/dmi mount error  
  链接：https://github.com/moltis-org/moltis/issues/1085  
  *提醒：该问题导致 Apple Silicon 用户完全无法使用 Docker 沙盒，属于平台兼容性阻塞项，建议评估是否可通过条件编译或运行时架构检测跳过 DMI 相关挂载。*

- **#1086** Apple Containers backend: sandbox image build fails (no DNS behind corporate proxy)  
  链接：https://github.com/moltis-org/moltis/issues/1086  
  *提醒：企业用户采用 Apple Containers 后端时构建流程完全中断，建议检查 builder VM 的网络命名空间与 DNS 转发配置。*

---

*日报完。*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw 项目动态日报 | 2026-05-30

## 1. 今日速览
CoPaw（QwenPaw）今日社区活跃度处于高位，24小时内产生 **13 个活跃/新开 Issue** 与 **6 个待合并 PR**，无新版本发布。社区讨论高度集中在 **Windows 桌面端稳定性**（shell 命令执行闪屏）与 **IDE 级交互体验**（对话回退、diff 审阅、文件索引引用）两大主题。开发侧正推进飞书渠道群组会话共享、Cron 任务轨迹修复及上下文压缩优化，项目整体处于密集的问题修复与功能迭代期。

## 2. 版本发布
本日无新版本发布。

## 3. 项目进展
- **飞书渠道重构**：旧 PR [#4537](https://github.com/agentscope-ai/QwenPaw/pull/4537) 已关闭，由 [#4821](https://github.com/agentscope-ai/QwenPaw/pull/4821) 接替，以更简洁的 `share_session_in_group` 布尔标志实现群组会话共享，与企微渠道保持模式一致。
- **Cron 任务修复**：PR [#4822](

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

**EasyClaw（RivonClaw）项目动态日报**  
*日期：2026-05-30 | 仓库：gaoyangz77/easyclaw*

---

### 1. 今日速览
过去24小时，EasyClaw 社区在 Issue 与 PR 层面保持静默，无新增讨论或代码合并；然而维护团队以极高的发布频率推送了三个连续补丁版本（v1.8.19 → v1.8.21），集中加固桌面端自动更新链路、跨国网络路由与 Agent 启动可靠性。这种"零 Issue/PR 但高频发版"的模式表明项目当前处于发布窗口期的收尾阶段，核心工作已从功能开发转向分发通道硬化与质量门禁完善。整体健康度良好，但社区互动热度处于低位。

---

### 2. 版本发布
今日共发布 **3 个**向后兼容的补丁更新，无破坏性变更，建议桌面端用户平滑升级。

- **[v1.8.21](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.21)** — 桌面更新与 Agent 启动硬化
  - **更新内容**：将 OpenClaw 运行时重新打包为支持 blockmap 的 tar 存档，显著提升 macOS 端增量更新效率；引入网关目录（gateway catalog）就绪探针机制，确保云工具与客服桥接（customer-service bridges）在依赖就绪后才启动，避免竞态条件；同步更新 CI 检查以适配新的 macOS 运行时归档格式。
  - **迁移注意**：macOS 桌面用户通过 electron-updater 自动接收增量包时，下载体积将缩小，无需手动干预。

- **[v1.8.20](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.20)** — 网络路由与代理感知强化
  - **更新内容**：优化第一方域名路由策略，桌面客户端现在会优先探测真实 RivonClaw API 路径，仅在必要时回退至中国中继节点；增强代理感知能力，覆盖重定向、环回地址及第一方域名的边缘场景；确保发布流量与更新流量走正确的全球/区域通道。
  - **迁移注意**：处于企业代理或混合云环境的 Agent 实例建议尽快升级，以解决潜在的连接环路问题。

- **[v1.8.19](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.19)** — 签名验证与 CI 合约检查
  - **更新内容**：刷新桌面端签名发布元数据，打通 macOS 与 Windows 上 electron-updater 的端到端签名验证；在 CI 中固化 OpenClaw 运行时合约检查，强制要求更新产物包含必需的工作区模板（workspace templates）。
  - **迁移注意**：此版本为 staging 验证构建，主要验证签名安装器更新通道的完整性，生产环境用户可直接跟随 v1.8.21 升级。

---

### 3. 项目进展
今日无合并或关闭的 Pull Request（[PR 面板](https://github.com/gaoyangz77/easyclaw/pulls)），代码贡献侧处于静止状态。尽管如此，连续三个补丁版本的发布表明维护者正通过发布流水线直接推进以下技术债务清偿：
1. **端到端更新闭环**：从 v1.8.19 的签名元数据刷新到 v1.8.21 的 blockmap 增量包，桌面分发链路已完成从"能更新"到"高效且安全更新"的跃迁。
2. **企业级网络鲁棒性**：v1.8.20 的代理与路由硬化使 AI Agent 在复杂网络拓扑（企业代理、跨境中继）下的启动成功率显著提升。
3. **Agent 启动时序可靠性**：v1.8.21 对云工具与客服桥接的依赖就绪等待机制，降低了分布式 Agent 集群的启动抖动。

---

### 4. 社区热点
今日 Issues 与 PRs 板块均无新增活动，不存在讨论热点、高评论或高反应条目。（[Issues](https://github.com/gaoyangz77/easyclaw/issues) | [PRs](https://github.com/gaoyangz77/easyclaw/pulls)）

---

### 5. Bug 与稳定性
过去24小时无新增用户报告的 Bug、崩溃或回归 Issue。但维护团队通过发版实施了多项预防性稳定性加固，按影响面排序如下：

| 严重程度 | 问题描述 | 状态 |
|---|---|---|
| 高 | 代理环境下的重定向与环回处理缺陷，可能导致桌面客户端更新死循环 | v1.8.20 已修复并发版 |
| 高 | Agent 启动时云工具因网关目录未就绪而失败 | v1.8.21 已修复并发版 |
| 中 | macOS 增量更新包体积过大且 blockmap 不友好 | v1.8.21 已修复并发版 |
| 中 | 桌面更新签名验证链在 staging 环境失效 | v1.8.19 已修复并发版 |

---

### 6. 功能请求与路线图信号
今日无新增功能请求 Issue。但从连续三个补丁的聚焦领域可提取明确的路线图信号：
- **企业桌面部署优先**：electron-updater 签名验证、增量更新、代理支持等投入表明，项目当前核心目标是成为可大规模部署的桌面端 AI Agent 平台，而非仅停留在服务端。
- **中国区域合规与加速**：显式提及"China relay"与区域流量分流，暗示官方正在完善跨境数据合规与低延迟接入能力，这对个人 AI 助手的全球化部署至关重要。
- **运行时合约化**：CI 中强制包含 workspace templates 的检查，预示未来可能开放第三方模板市场或企业自定义工作区，需关注后续是否有相关 Plugin API 发布。

---

### 7. 用户反馈摘要
今日无新增用户评论可供直接提炼。基于发布内容反向推断，近期用户痛点与使用场景集中在：
-

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*