# OpenClaw 生态日报 2026-05-31

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-05-31 03:24 UTC

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

**个人 AI 助手/自主智能体开源生态横向对比分析报告**  
*基准日期：2026-05-31 | 核心参照：OpenClaw*

---

### 1. 生态全景

当前个人 AI 助手开源生态呈现**“头部高速迭代、腰部巩固质量、尾部维护乏力”**的明显分层。以 OpenClaw 为技术参照，衍生/对标项目正从“基础对话能力”向**桌面原生控制、全双工语音、Computer-Use 系统级交互**跃迁；同时，安全加固（SSRF、MCP 供应链、工具权限治理）与多租户隔离成为从“玩具”走向“生产可用”的共性门槛。社区事件总量差异悬殊，单日最高可达百级事件，最低完全静默，生态进入洗牌期。

---

### 2. 各项目活跃度对比

| 项目 | 今日 Issues 动态 | 今日 PR 动态 | 今日 Release | 健康度评估 |
|---|---|---|---|---|
| **Zeroclaw** | 50 条事件，关闭 36 条 | 50 条事件，合并/关闭 29 条 | 无（预备 v0.8.0-beta-2） | 🔥 极高活跃，交付强但审查积压（7 项高优 blocked） |
| **IronClaw** | 4 条更新 | 18 条（11 已合并，7 待审） | 无（crates.io 滞后于 GitHub 标签） | 🔥 极高吞吐量，v2 架构冲刺中，发布管道信任度受损 |
| **NanoBot** | 6 条（4 条解决） | 15 条（6 条已合并/关闭，积压 9 项） | 无 | ✅ 高活跃，安全与稳定性补丁密集，节奏紧凑 |
| **NanoClaw** | 3 条（含 1 条新建多用户支持） | 16 条（4 条已合并） | 无 | ✅ 高活跃，架构层（IPC/多实例）推进扎实 |
| **CoPaw** | 9 条（8 条活跃/新开） | 1 条待审（#4689） | 无 | ⚠️ 讨论热但代码合并慢，Windows 体验问题重复反馈 |
| **PicoClaw** | 4 条关闭，新增 3 条（含 v0.2.9 回归） | 3 条合并，9 条待审 | Nightly v0.2.9 | ⚠️ 中等活跃，版本存在已知回归（会话隔离失效） |
| **EasyClaw** | 无 | 无 | **v1.8.19→v1.8.21（3 连发）** | ✅ 交付流水线极快，但社区反馈闭环静默 |
| **LobsterAI** | 无新增 | 无合并（2 条 PR stale 近 2 月） | 无 | ❌ 活跃度低迷，审查瓶颈显著 |
| **Moltis** | 无 | 1 条待审（Codex 流式参数） | 无 | ❌ 极低参与，社区冷却 |
| **TinyClaw / ZeptoClaw** | 无 | 无 | 无 | ❌ 24h 零活动 |

---

### 3. OpenClaw 在生态中的定位

作为生态的**事实基准（de facto reference）**，OpenClaw 定义了“模块化 Agent 平台”的标准范式。与同类相比：

- **优势与规模**：OpenClaw 拥有最完整的插件/工具市场生态和社区认知度，是其他项目命名与功能对标的原点。
- **技术路线差异**：下游项目多采取**垂直切片策略**——Zeroclaw 押注桌面原生（Tauri/macOS）与语音 pipeline，NanoClaw 深耕容器化与多实例部署，IronClaw 则走向企业级 WASM 沙箱与区块链身份（NEAR）。OpenClaw 保持“全栈通用”，而衍生项目通过牺牲部分通用性换取特定场景（桌面、企业、Windows）的极致体验。
- **社区规模**：OpenClaw 主仓仍应是 Star 数与贡献者基数最大的项目，但 Zeroclaw、IronClaw 等已在其 shadow 下建立起日活百级事件的独立开发者社区。

---

### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **桌面原生控制与 Computer-Use** | Zeroclaw、EasyClaw、CoPaw | Zeroclaw 已合并 macOS 权限 handler（合成键鼠、录屏、Accessibility），社区 RFC 明确要求对标 OpenAI Codex 的屏幕交互；CoPaw 修复 Windows 控制台闪烁以支撑本地 Shell 调用。 |
| **全双工语音交互** | Zeroclaw、NanoClaw | Zeroclaw 已完成 WebSocket 二进制音频帧 + VAD + STT 调度闭环；NanoClaw 有 whisper.cpp 离线转录 PR 待审，指向“电话式”连续对话成为标配。 |
| **安全与权限治理** | NanoBot、Zeroclaw、NanoClaw、PicoClaw | NanoBot 修复 SSRF IPv6 绕过；Zeroclaw 暴露 `allowed_tools` 执行阶段未强制的问题；NanoClaw 警示 MCP 供应链风险；PicoClaw 加固 workspace URL 沙箱。 |
| **多实例/多租户隔离** | NanoClaw、NanoBot | NanoClaw 新建 Issue 要求单 Mac 多用户隔离；NanoBot 修复 per-session dispatch 锁并发缺陷，均指向从“单用户玩具”到“家庭/团队基础设施”的演进。 |
| **消息路由与渠道适配** | NanoBot、NanoClaw、PicoClaw、Zeroclaw | NanoBot 适配 Matrix E2EE；NanoClaw 新增 `from-channel` 元数据；PicoClaw 优化 Telegram @mention；Zeroclaw RFC 呼吁统一按渠道模态路由输出。 |
| **发布工程与自动更新** | EasyClaw、IronClaw | EasyClaw 单日三发补丁优化 macOS 增量更新与代理路由；IronClaw 则因 crates.io 长期滞后（0.24.0 vs GitHub v0.27.0）被社区诟病，形成正反案例。 |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|---|---|---|---|
| **Zeroclaw** | 桌面原生（Tauri）、全双工语音、Computer-Use | 极客/个人生产力用户 | 重客户端架构，深度集成 OS 权限与硬件（VAD/STT），TUI+WebUI 双前端。 |
| **IronClaw** | 企业级 Agent 运行时、WASM 沙箱、区块链身份 | 企业/ B2B 基础设施 | Rust workspace 单体架构，NEAR AI 身份体系，Reborn v2 产品化认证与触发器域驱动设计。 |
| **NanoBot** | 多协议 Bot（Matrix/Anthropic）、WebUI、安全加固 | 多平台自托管用户 | 强调协议适配层与 SSRF/并发安全，Dream 系统可全局关闭，偏向服务端部署。 |
| **NanoClaw** | 容器化、多实例、Apple Container、MCP | 开发者/家庭共享服务器 | 基于 `fs.watch` 的异步 IPC，OneCLI 多实例端口动态分配，关注 macOS 容器挂载兼容性。 |
| **PicoClaw** | 轻量、国际化、Azure 企业认证 | 全球中小企业/非英语用户 | Go 语言实现，Bangla i18n、Azure Identity 无密钥认证，但渠道稳定性（QQ/FreeBSD）仍薄弱。 |
| **CoPaw** | Windows 桌面、ACP 协议、Claude Code 兼容 | Windows 开发者 | 聚焦 Windows 控制台与 Shell 调用体验，兼容 DashScope/OpenAI SDK 非标准参数。 |
| **EasyClaw** | 终端用户交付、自动更新、代理路由 | 中国区/普通终端用户 | 发布工程驱动，blockmap 增量更新、China relay 探测，社区贡献低但交付流水线成熟。 |

---

### 6. 社区热度与成熟度

**第一梯队：快速迭代期（日事件 >15 或等效高吞吐）**
- **Zeroclaw**：100 条事件/日，65% 关闭率，功能爆发期（语音、桌面权限、Computer-Use），但审查剪刀差明显。
- **IronClaw**：18 PR/日，v2 架构重构中，企业级功能（认证、触发器、通信偏好）密集落地， crates.io 滞后是主要减分项。
- **NanoBot / NanoClaw**：双高活跃，前者偏安全与协议修复，后者偏部署与消息架构，均处于健康迭代轨道。

**第二梯队：质量巩固期（有活动但存在回归或合并瓶颈）**
- **PicoClaw**：v0.2.9 出现会话隔离与上下文压缩显示回归，社区对版本节奏焦虑，需从“功能添加”转向“质量守门”。
-

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
*日期：2026-05-31 | 仓库：github.com/HKUDS/nanobot*

---

### 1. 今日速览

NanoBot 在过去 24 小时内保持高活跃度，共有 **15 个 PR** 和 **6 个 Issue** 发生状态更新，其中 **6 个 PR 已合并/关闭**，**4 个 Issue 得到解决**，无新版本发布。社区在安全性加固（SSRF、Matrix 媒体限制）、核心稳定性（会话级并发锁、Anthropic API 兼容性）以及 WebUI 交互体验方面取得实质进展。当前待合并 PR 积压 9 项，涵盖记忆系统重构、语音转录扩展与跨 Agent 协作等关键方向，项目整体迭代节奏紧凑，健康度良好。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日合并/关闭的重要 PR 推动了以下关键进展：

- **[#4054](https://github.com/HKUDS/nanobot/pull/4054)** — 一次性修复 Anthropic 内容块缺失 `type` 字段的兼容性问题（[#3993](https://github.com/HKUDS/nanobot/issues/3993)），并引入 `DreamConfig.enabled` 全局开关（[#3885](https://github.com/HKUDS/nanobot/issues/3885)），使用户可彻底禁用 Dream 系统作业，解决长期存在的配置灵活性痛点。
- **[#4104](https://github.com/HKUDS/nanobot/pull/4104)** — 修复 `process_direct` 绕过 per-session dispatch 锁的并发缺陷（[#4080](https://github.com/HKUDS/nanobot/issues/4080)），消除 API/cron/webui 直接调用与总线消息并行处理导致的历史记录损坏风险，属于核心稳定性关键补丁。
- **[#4110](https://github.com/HKUDS/nanobot/pull/4110)** — 为 Matrix 通道增加 SAS 设备验证处理（[#4042](https://github.com/HKUDS/nanobot/issues/4042)），适配 Element X / matrix-rust-sdk 客户端，消除 E2EE 消息中的"未验证设备"警告。
- **[#4086](https://github.com/HKUDS/nanobot/pull/4086)** — 修复 SSRF 检查中 IPv6-mapped IPv4 地址（如 `::ffff:127.0.0.1`）的规范化问题，堵塞潜在的安全绕过漏洞。
- **[#4106](https://github.com/HKUDS/nanobot/pull/4106)** — 对 Matrix 入站媒体下载施加明确边界限制，拒绝无可信 `content.info.size` 的媒体事件

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
*日期：2026-05-31 | 数据来源：github.com/zeroclaw-labs/zeroclaw*

---

### 1. 今日速览

过去 24 小时项目表现出极高的工程活跃度，共有 **100 条** GitHub 事件更新（Issues + PR 各 50 条）。社区清理与交付效率突出：**36 条 Issue 与 29 条 PR 被关闭/合并**，综合关闭率达 **65%**。今日交付重心集中在 **桌面端（Tauri/macOS）原生能力** 与 **全双工语音 pipeline** 两大主题，同时有 7 个高优先级安全与运行时 Issue 因等待维护者审查而处于 `blocked` 状态，形成明显的“交付强、审积压”的剪刀差。无新版本发布。

---

### 2. 版本发布

今日无新版本发布。  
**信号提示**：PR [#6848](https://github.com/zeroclaw-labs/zeroclaw/pull/6848) 明确声明其合并且将成为 **v0.8.0-beta-2** 预发布版本的基础，目前处于“DO NOT MERGE / 寻求第一轮反馈”阶段。

---

### 3. 项目进展

今日合并/关闭的重要 PR 推动项目在桌面原生体验、语音交互和系统稳定性三个维度取得实质性进展：

- **桌面端 macOS 权限与控制能力全面落地**  
  合并了由 `@theonlyhennygod` 提交的 7 个连续 PR（[#6761](https://github.com/zeroclaw-labs/zeroclaw/pull/6761)–[#6767](https://github.com/zeroclaw-labs/zeroclaw/pull/6767)），完整覆盖了：合成鼠标/键盘事件、通知、Accessibility 读取、以及辅助功能、屏幕录制、麦克风、输入监控、完全磁盘访问、本地网络等六项系统权限的申请与撤销检测。这为后续 Computer-Use 功能奠定了操作系统层基础。

- **全双工语音对话 pipeline 完工**  
  PR [#5974](https://github.com/zeroclaw-labs/zeroclaw/pull/5974)（WebSocket 二进制音频帧）、[#5976](https://github.com/zeroclaw-labs/zeroclaw/pull/5976)（能量基 VAD）、[#5978](https://github.com/zeroclaw-labs/zeroclaw/pull/5978)（语音捕获缓冲 + STT 调度）均已关闭，标志着 Issue [#5896](https://github.com/zeroclaw-labs/zeroclaw/issues/5896) 所要求的“电话式”连续语音交互能力正式落地。

- **桌面端离线启动与 Web 体验对齐**  
  Issue [#6465](https://github.com/zeroclaw-labs/zeroclaw/issues/6465) 关闭，chat-ui 已作为静态资源捆绑进 Tauri 二进制；同时 [#5649](https://github.com/zeroclaw-labs/zeroclaw/issues/5649) 关闭，Web Chat UI 新增剪贴板粘贴与图片拖放支持。

- **TUI 可用性增强**  
  PR [#6858](https://github.com/zeroclaw-labs/zeroclaw/pull/6858)（首次运行空状态引导）与 [#6952](https://github.com/zeroclaw-labs/zeroclaw/pull/6952)（紧凑键盘的 Tab/Shift+Tab 模式循环）已合并，改善零配置新用户的上手体验。

---

### 4. 社区热点

今日讨论最活跃的议题集中在架构 RFC 与跨项目对标：

| 议题 | 评论 | 核心诉求 |
|------|------|----------|
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) **computer-use support** | 4 | 社区明确要求对标 OpenAI Codex / Peekaboo 的屏幕交互能力（截图、键鼠事件），与今日合并的 macOS 能力 handler 形成强烈需求-供给呼应。 |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) **RFC: Route scheduled tasks through orchestrator** | 3 | 指出 cron 调度器直接触发 side effect 绕过编排器消息管道，是 5 个关联 bug 的根因，呼吁架构层统一。 |
| [#6969](https://github.com/zeroclaw-labs/zeroclaw/issues/6969) **RFC: unified output routing model** | 3 | 从 Letta 迁移的用户反馈：ZeroClaw 失去了“按偏好渠道回复”的控制力，要求按 peer 的模态偏好 + agent `send_via` 工具统一输出路由。 |
| [#6848](https://github.com/zeroclaw-labs/zeroclaw/pull/6848) **feat(integration): zerocode TUI, RPC socket…** | undefined（高关注） | 超大号（XL）集成 PR，引入 TUI、RPC socket transport、DenyWithEdit 审批流，是 beta-2 的基石，社区正密集审阅。 |

---

### 5. Bug 与稳定性

按严重程度排列的今日 Bug 与修复：

- **S1 / P1 — 工作流阻断**
  - **[#7022](https://github.com/zeroclaw-labs/zeroclaw/issues/7022)** `kimi-k2.6` 因 `compatible.rs` 始终发送 `temperature: 0.7` 而返回 400 错误。**状态：Open，待修复。**
  - **[#6916](https://github.com/zeroclaw-labs/zeroclaw/issues/6916)** `shell.rs` 子进程无内存上限，可导致容器 OOM（生产环境已观测到）。**状态：Open，Blocked，待维护者审查。**

- **P1 — 安全策略失效**
  - **[#6914](https://github.com/zeroclaw-labs/zeroclaw/issues/6914)** `allowed_tools` / `denied_tools` 仅在 listing 时过滤，执行阶段未强制，存在权限绕过。**状态：Open，Blocked。**

- **P2 — 渠道与运行时修复（已有 PR）**
  - **[#7027](https://github.com/zeroclaw-labs/zeroclaw/pull/7027)** Webhook 未正确解析 HTTP-date 格式的 `Retry-After`。**PR 今日新开，待合并。**
  - **[#6983](https://github.com/zeroclaw-labs/zeroclaw/pull/6983)** 流式传输错误在内容未可见前未优雅回退到非流式。**PR 待合并。**
  - **[#7008](https://github.com/zeroclaw-labs/zeroclaw/pull/7008)** WhatsApp LID JID 无法解析为可投递手机号，导致回复失败。**PR 待合并。**

- **已修复**
  - **[#6340](https://github.com/zeroclaw-labs/zeroclaw/issues/6340)** 桌面端崩溃报告与 panic 捕获机制已随相关 PR 合并关闭。

---

### 6. 功能请求与路线图信号

结合已关闭 PR 与开放 Issue，可识别出以下路线图信号：

- **Computer-Use（高概率进入下一版本）**  
  Issue [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) 与今日关闭的 [#6499](https://github.com/zeroclaw-labs/zeroclaw/issues/6499) / PR [#6761](https://github.com/zeroclaw-labs/zeroclaw/pull/6761) 形成完整链路：后端 handler 已就绪，前端 RFC 已接受，预计将在 v0.8.0-beta-2 或后续版本正式暴露为 agent 工具。

- **架构统一（编排器管道化）**  
  RFC [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) 与 [#6969](https://github.com/zeroclaw-labs/zeroclaw/issues/6969) 均指向运行时核心管道的重构，属于大版本级别的 breaking change，短期内可能以 RFC 讨论为主。

- **办公文档解析（社区探测）**  
  Issue [#7024](https://github.com/zeroclaw-labs/zeroclaw/issues/7024) 提出 WASM 插件解析 DOCX/XLSX/PPTX，作者明确标注为 **feeler**，需维护者反馈以决定是否投入。

- **工具治理与安全加固**  
  [#6914](https://github.com/zeroclaw-labs/zeroclaw/issues/6914)、[#6915](https://github.com/zeroclaw-labs/zeroclaw/issues/6915)、[#6917](https://github.com/zeroclaw-labs/zeroclaw/issues/6917) 构成工具权限治理的三部曲，若全部解决，将显著提升多租户与企业部署的可信度。

---

### 7. 用户反馈摘要

从今日 Issue 与评论中提炼的真实用户声音：

- **迁移用户痛点**：从 Letta 迁移的用户（[#6969](https://github.com/zeroclaw-labs/zeroclaw/issues/6969)）强烈依赖“按渠道/模态路由回复”的能力，ZeroClaw 当前缺失该能力导致日常 workflow（如早间简报推送到 Telegram、紧急事项改打电话）断裂。
- **桌面原生体验诉求**：用户期望菜单栏聊天具备与 Web 端完全对等的会话列表、设置编辑、图片拖放、工具审批提示（[#6321](https://github.com/zeroclaw-labs/zeroclaw/issues/6321)–[#6328](https://github.com/zeroclaw-labs/zeroclaw/issues/6328) 系列），今日批量关闭表明维护团队正在快速补齐。
- **安全与运维焦虑**：生产环境用户（[#6916](https://github.com/zeroclaw-labs/zeroclaw/issues/6916)）指出 LLM 回退到 shell 命令时可能触发内存耗尽；企业用户（[#6917](https://github.com/zeroclaw-labs/zeroclaw/issues/6917)）需要更细粒度的 Composio action 白

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
**日期：** 2026-05-31  
**项目：** github.com/sipeed/picoclaw  
**分析师：** AI 智能体与开源项目研究

---

### 1. 今日速览

PicoClaw 今日保持中等活跃度，代码流持续向前推进。社区在过去 24 小时内完成 **4 条 Issue 关闭**与 **3 条 PR 合入/关闭**，同时新增 **3 条活跃 Issue** 与 **9 条待审阅 PR**。项目发布了基于 `main` 分支的自动化 Nightly 构建，显示 v0.2.9 迭代仍在密集进行。值得警惕的是，两位用户在 v0.2.9 中报告了 Web UI 消息历史污染与上下文压缩显示异常，提示最新版本可能存在回归风险。

---

### 2. 版本发布

**Nightly Build: v0.2.9-nightly.20260531.1ce353ba**  
🔗 https://github.com/sipeed/picoclaw/compare/v0.2.9...main

- **性质：** 自动化每日构建，基于 `v0.2.9` 至 `main` 分支的增量。
- **稳定性提示：** 官方明确标注 *"This is an automated build and may be unstable. Use with caution."*
- **迁移注意：** 若您正在生产环境运行 v0.2.8 或更早版本，建议等待正式 patch 版本而非直接采用 nightly，因为今日有用户报告 v0.2.9 存在 Web UI 消息历史残留问题（见下文 #2972）。

---

### 3. 项目进展

今日合并/关闭的 PR 主要围绕**云原生认证、国际化与前端交互体验**展开：

| PR | 作者 | 状态 | 进展说明 |
|---|---|---|---|
| **#2974** — feat(i18n): Add Bangla support `bn-in` | @kunalk16 | ✅ 已关闭 | 为 Web 应用新增孟加拉语界面支持，国际化覆盖进一步扩大。 |
| **#2971** — feat(provider): Add optional Azure Identity support for Azure OpenAI provider | @kunalk16 | ✅ 已关闭 | 引入可选的 Azure Identity 认证流（需 `azidentity` build tag），满足禁用本地密钥的 Azure 订阅策略合规需求。 |
| **#2969** — feat(web): add chat image paste and drag-and-drop upload | @lc6464 | ✅ 已关闭 | Web 前端支持剪贴板粘贴与拖拽上传图片，MIME 类型自动规范化，提升多模态交互体验。 |

**整体评估：** 项目今日在**企业级认证（Azure Identity）**与**前端易用性**上迈出明确一步，同时社区对非英语用户的覆盖（Bangla）持续增加。

---

### 4. 社区热点

**🔥 讨论最活跃：#2952 — [Feature] 好久没发新版本了**  
🔗 https://github.com/sipeed/picoclaw/issues/2952  
- **评论数：** 3 条（今日活跃）  
- **核心诉求：** 用户 @xhynice 集中抛出三大痛点：  
  1. `exec` 命令的 `actions:run` 在多数模型首次调用时默认缺失，导致报错与多余重试；  
  2. QQ 渠道存在“重启后发送消息即再次重启”的无限循环，需手动清除历史上下文才能终止；  
  3. 模型配置界面应默认展示已保存 Key 的提供商，支持下拉选择与 API 连通性测试。  
- **信号解读：** 该 Issue 折射出社区对**版本发布节奏放缓**的焦虑，以及对**渠道稳定性**和**配置体验**的高度关注。

**🔥 技术回归焦点：#2972 — Web UI message chaos after upgrade to v0.2.9**  
🔗 https://github.com/sipeed/picoclaw/issues/2972  
- **评论数：** 2 条  
- **核心现象：** FreeBSD 15.0 环境下，v0.2.9 每次新建会话都会自动附加旧消息历史，严重破坏对话隔离性。

---

### 5. Bug 与稳定性

按严重程度排列：

| 严重程度 | Issue | 状态 | 摘要 | Fix PR |
|---|---|---|---|---|
| **🔴 高** | **#2972** — Web UI 新会话附加旧消息历史 | 🟡 开放 | v0.2.9 回归：FreeBSD + Web 渠道下会话隔离失效，每条新对话携带历史上下文。 | ❌ 暂无 |
| **🟡 中** | **#2968** — `/context` 始终显示 `Compress at: 76800 tokens` | 🟡 开放 | 上下文压缩阈值显示固定值，疑似配置未生效或统计逻辑异常。 | ❌ 暂无 |
| **🟡 中** | **#2952**（内嵌 Bug）— QQ 渠道重启死循环 | 🟡 开放（综合 Issue） | QQ 渠道在重启后接收消息会再次触发重启，除非清空历史。 | ❌ 暂无 |
| **🟡 中** | **#2952**（内嵌 Bug）— `exec` 首次调用缺失 `actions:run` | 🟡 开放（综合 Issue） | 多数模型首次执行时默认不带 `actions:run`，导致报错。 | ❌ 暂无 |
| **🟢 低** | **#2976** — Makefile 无法处理 Go 1.25.10 版本字符串中的空格 | 🟡 开放 | `go env GOVERSION` 返回含空格的字符串导致编译中断。 | 🟡 #2976（自身即为修复 PR） |

**已关闭的历史 Bug：**  
- **#2742** — v0.2.8 gateway 无 channels 启动问题（已关闭，6 条评论讨论）  
- **#2880** — Android 10 存储权限拒绝导致目录创建失败（已关闭，陈旧 Issue 清理）

---

### 6. 功能请求与路线图信号

| 需求/PR | 方向 | 纳入下一版本概率 | 判断依据 |
|---|---|---|---|
| **#2977** — cron 工具新增 `get` / `update` 操作 | Agent 工具增强 | 🔶 高 | 直接解决 Agent 在重新调度工作流时的“删除再添加”痛点，逻辑清晰且今日刚提交。 |
| **#2975** — Telegram 群组中将回复 Bot 视为 @mention | 渠道交互优化 | 🔶 高 | 改动边界清晰，解决 `mention_only: true` 场景下的交互断层，社区需求明确。 |
| **#2967** — Codex 流式输出 text delta 保留 | 模型 Provider 修复 | 🔶 高 | 修复 OpenAI/Codex OAuth 空响应，属于稳定性补丁，合入阻力小。 |
| **#2965** — 阻止 workspace guard 误读无 scheme URL | 安全/沙箱修复 | 🔶 中高 | `restrict_to_workspace` 启用时，`curl wttr.in/Beijing?T` 等无 scheme URL 被误判为绝对路径，属于安全边界修复。 |
| **#2856** — message 工具支持媒体附件与 Telegram 富文本交付 | 多模态消息 | 🔶 中 | 已标记 stale（5 月 11 日），但功能意义重大；若维护者重新关注，可能进入 v0.3.0 或后续版本。 |
| **#2838** — AGENT.md frontmatter 工具策略过滤器 | Agent 治理 | 🔶 中 | 同样 stale（5 月 9 日），涉及 `allow`/`deny` 策略与 glob 模式，属于高级 Agent 治理特性，需更多设计审阅。 |

---

### 7. 用户反馈摘要

从今日 Issue 与评论中提炼的真实声音：

- **版本节奏焦虑：** “好久没发新版本了”——社区对 v0.2.9 之后的正式 release 有明确期待，nightly 构建无法缓解生产环境用户的等待焦虑。
- **渠道可靠性：** QQ 渠道的重启死循环与 Telegram gateway 历史问题（#2742）表明，**非 Web 渠道的长期稳定性**仍是用户核心痛点。
- **配置体验断层：** 用户期望模型提供商配置能“记住已有 Key、下拉选择、一键测试连通性并拉取 `/models` 列表”，当前手动填写流程被认为繁琐且易错。
- **Agent 行为一致性：** 用户观察到 PicoClaw “好像不太遵循 agent.md”，提示 Agent 指令遵循率与工具调用规范仍是社区质疑点。
- **跨平台兼容性：** FreeBSD 15.0 用户连续报告两条 v0.2.9 问题（#2972、#2968），说明非 Linux 主流平台的测试覆盖仍需加强。

---

### 8. 待处理积压

以下 Issue/PR 已长期未获最终审阅或合入，建议维护者优先关注，避免社区贡献流失：

| 项目 | 创建时间 | 状态 | 提醒 |
|---|---|---|---|
| **#2856** — feat(message): support media attachments and Telegram rich delivery | 2026-05-11 | 🟡 OPEN / stale | 媒体附件是消息工具的多模态关键一步，已停滞 20 天。🔗 https://github.com/sipeed/picoclaw/pull/2856 |
| **#2838** — feat(agent): support frontmatter tool policy filters | 2026-05-09 | 🟡 OPEN / stale | Agent 治理与权限控制的前置设计，已停滞 22 天。🔗 https://github.com/sipeed/picoclaw/pull/2838 |
| **#2963 / #2962** — Dependabot 依赖升级（Lark / Anthropic SDK） | 2026-05-28 | 🟡 OPEN | 两条依赖升级 PR 已等待 3 天，涉及飞书与 Anthropic 官方 SDK 的安全与功能更新，建议尽快 CI 验证后合入。 |

---

**健康度评分（主观评估，仅供趋势参考）：**  
`代码活跃度: ████████░░ 8/10` | `社区响应度: ██████░░░░ 6/10` | `稳定性: █████░░░░░ 5/10`（v0.2.9 存在已知回归）

*日报完。*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-05-31 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

NanoClaw 在过去 24 小时保持高活跃度：16 个 PR 发生更新（其中 4 条已合并/关闭），3 个 Issue 处于新开或活跃状态，无新版本发布。项目在多实例部署稳定性、消息路由和系统架构层面取得实质推进，但 Apple Container 平台出现严重的文件挂载兼容性问题，且社区对 MCP 供应链安全与多用户隔离的诉求显著升温。整体健康度良好，但需关注平台特定回归与长期积压 PR 的清理。

---

### 3. 项目进展

今日共有 **4 条 PR 已合并/关闭**，推动项目在容器化部署、消息格式和底层架构上向前迈进：

- **#2645** [CLOSED] — 为群组聊天引入 **per-agent-group 上下文窗口**。当 agent 在群聊中被 `@mention` 触发时，会自动接收该聊天最近 N 条未读消息作为上下文块，显著改善多 agent 协作的连贯性。  
  https://github.com/nanocoai/nanoclaw/pull/2645

- **#2652** [CLOSED] — 修复多实例安装场景下 OneCLI 代理端口硬编码问题。此前 `HTTPS_PROXY` 固定指向 `host.docker.internal:10255`，在配置 `instances.conf` 与 `ONECLI_BASE_PORT` 的多实例环境中会指向错误端口；现已支持按实例动态重写。  
  https://github.com/nanocoai/nanoclaw/pull/2652

- **#2521** [CLOSED] — 在 XML 消息属性中新增 `from-channel` 与 `from-type`，使多通道（如 Telegram + Discord）日志解析与监控面板能够准确识别消息来源通道。  
  https://github.com/nanocoai/nanoclaw/pull/2521

- **#6** [CLOSED] — 将 IPC 通信从忙循环轮询（`setTimeout` + 同步 `fs` 调用）重构为基于 `fs.watch` 的异步事件驱动架构，消除同步 I/O 对事件循环的阻塞，并引入防抖合并机制。  
  https://github.com/nanocoai/nanoclaw/pull/6

---

### 4. 社区热点

今日讨论焦点集中在**安全警示**、**平台回归**与**部署模式**三个维度：

- **#2641** [Supply chain risk]（👍 0，评论 1）— 社区成员引用外部安全文章，指出某 Gmail MCP 自动授权插件存在供应链风险，可能诱导 AI 安装陌生人代码并索取 Gmail 密码。这是今日最具警示性的议题，反映出用户对 MCP 生态供应链安全的高度敏感。  
  https://github.com/nanocoai/nanoclaw/issues/2641

- **#2044** [v2 Discord `<URL>` handling regression]（👍 2，评论 1）— v2 中 Discord 适配器将 `<URL>` 错误转换为 `[URL](URL)`，导致 Discord 的链接预览抑制语义反转。该 Issue 获得较多正向反应，说明影响面较广。  
  https://github.com/nanocoai/nanoclaw/issues/2044

- **#2653** [Multi-user support on a single install]（👍 0，评论 0，今日新建）— 用户提出在家庭共享 Mac 上为不同成员运行隔离的 Telegram bot、agent group 与记忆。该需求与现有数据模型兼容，但受限于 `src` 层实现，可能成为近期架构演进的重要信号。  
  https://github.com/nanocoai/nanoclaw/issues/2653

---

### 5. Bug 与稳定性

按严重程度排列的今日关键问题：

| 严重程度 | 问题 | 状态 |
|---|---|---|
| 🔴 **高** | **Apple Container 嵌套挂载导致 MCP 服务器静默失效**（#2649）：`container.json` 的嵌套文件挂载在 Apple Container 上产生 phantom inode，`stat()` 返回 `0644` 但实际读取返回 `EACCES`，导致所有通过 `ncl groups config add-mcp-server` 配置的 MCP 服务器被静默跳过。**修复 PR #2649 待合并**，配套重试逻辑 PR #2650 亦在审阅中。 | 待修复 |
| 🟡 **中** | **Discord URL 格式化回归**（#2044）：v2 中 `<URL>` 被转换为 `[URL](URL)`，破坏 Discord 预览抑制功能，影响聊天体验。目前**尚无专门修复 PR**。 | 待修复 |
| 🟡 **中** | **Apple Container 文件读取竞争**（#2650）：在 #2649 移除嵌套挂载后，目录挂载下的 `container.json` 因 virtio-fs 嵌套与 overlay 延迟，首次读取仍可能失败。PR #2650 引入重试机制。 | 待合并 |
| 🟢 **低** | **OneCLI 多实例代理端口错误**（#2652）：已在今日关闭并修复。 | 已修复 |

相关链接：  
- #2649: https://github.com/nanocoai/nanoclaw/pull/2649  
- #2650: https://github.com/nanocoai/nanoclaw/pull/2650  
- #2044: https://github.com/nanocoai/nanoclaw/issues/2044  

---

### 6. 功能请求与路线图信号

结合今日 Issue 与待合并 PR，以下方向可能纳入下一版本规划：

- **多租户/多实例部署**：#2653（单主机多用户）与已合并的 #2652（多实例 OneCLI 端口修复）形成明确的需求-修复对，表明家庭或小型团队共享部署是社区真实痛点，数据模型已就绪，亟需 `src` 层解耦。
- **灾难恢复基础设施**：#2084 提供每日快照、S3 后端与按 agent 恢复能力，填补了生产环境数据安全的空白，属于高优先级基础设施。
- **离线/本地语音转录**：#2317 集成 whisper.cpp / openai-whisper，无需云端 API 即可实现语音通道转录，适合隐私敏感场景。
- **GitHub 无端口集成**：#2301 的轮询模式（Mode B）让 NAT/防火墙后的用户也能使用 GitHub 集成，降低了企业内网部署门槛。
- **WebUI 控制面板**：#212 设计完整（11 个标签页，Lit + Vite + Fastify），但状态为 `Blocked / Pending Closure`，需维护者决策是否继续推进。

相关链接：  
- #2653: https://github.com/nanocoai/nanoclaw/issues/2653  
- #2084: https://github.com/nanocoai/nanoclaw/pull/2084  
- #2317: https://github.com/nanocoai/nanoclaw/pull/2317  
- #2301: https://github.com/nanocoai/nanoclaw/pull/2301  
- #212: https://github.com/nanocoai/nanoclaw/pull/212  

---

### 7. 用户反馈摘要

从今日 Issues 与 PR 描述中提炼的真实用户声音：

- **安全焦虑**：用户对 MCP 插件的供应链安全极度敏感（#2641），担忧 AI 在未经充分审查的情况下自动拉取并执行第三方代码，尤其是涉及 OAuth/密码凭证的场景。
- **家庭/共享设备隔离**：用户希望在同一台 Mac Mini 上为配偶与自己分别运行完全隔离的 agent，说明 NanoClaw 正从个人工具向家庭/小团队基础设施演进（#2653）。
- **平台兼容性痛点**：Apple Container 用户遭遇文件系统挂载异常（#2649/#2650），导致 MCP 服务器无法加载，影响 macOS 生态的可用性。
- **聊天适配器微行为影响体验**：Discord 老用户不满 v2 对 URL 包装的破坏性变更（#2044），证明通道适配器的细节处理直接决定日常交互质量。
- **运维与可观测性需求**：用户希望有预提交钩子保证代码质量（#2537）、有备份恢复防止误删（#2084），以及更丰富的消息元数据用于监控（#2521）。

---

### 8. 待处理积压

以下 Issue/PR 长期未决，建议维护者优先审阅或明确状态：

- **#212** [feat: add WebUI control panel]

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-05-31 | 仓库：nearai/ironclaw*

---

### 1. 今日速览

过去 24 小时 IronClaw 维持极高开发吞吐量，共处理 **18 个 PR**（11 个已合并/关闭，7 个待审）及 **4 条 Issues** 更新。核心维护者 `@serrrfirat` 与 `@henrypark133` 主导了 Reborn（v2）架构的认证、触发器与出站通信基础设施建设；新晋贡献者 `@neoguyverx` 连续合并 4 个 Agent 可靠性补丁。项目整体处于 v2 功能冲刺期，但 **crates.io 发布滞后** 与 **夜间 E2E 失败** 两个持续性问题仍在消耗社区信任，需要维护者优先介入。

---

### 2. 版本发布

**无新版本发布。**  
尽管 GitHub 标签已推进至 `v0.27.0`（2026-04-29），crates.io 仍停留在 `0.24.0`（2026-03-31），下游消费者无法通过官方 registry 获取后续版本（详见社区热点 #3259）。

---

### 3. 项目进展

今日合并/关闭的 11 个 PR 推动了三条主线：

**Reborn 认证与身份体系（产品化关键路径）**
- **#4245** `[CLOSED]` 完成产品面向的认证 HTTP 表面（manual-token、recovery、refresh、cleanup），为 WebUI/CLI/API 提供统一入口。  
  https://github.com/nearai/ironclaw/pull/4245
- **#4246** `[CLOSED]` 将 NEAR AI MCP 凭证从静态 `SecretHandle` 迁移至 `ProductAuthAccount` 运行时凭据源，与 #4233 的 GitHub WASM 迁移对齐。  
  https://github.com/nearai/ironclaw/pull/4246
- **#4257** `[OPEN]` 实现 AuthPromptView 挑战丰富化与 WebUI v2 OAuth 卡片，覆盖 GSuite OAuth、Notion MCP OAuth 及 GitHub PAT 流程。  
  https://github.com/nearai/ironclaw/pull/4257
- **#4256** `[OPEN]` 为上述认证流补充 E2E mock fixtures 与 3 个场景测试。  
  https://github.com/nearai/ironclaw/pull/4256

**触发器与出站通信基础设施（架构拼图）**
- **#4254** `[CLOSED]` 新增可信入站 facade，支持 sealed trusted request、replay-first 幂等性及可信绑定解析。  
  https://github.com/nearai/ironclaw/pull/4254
- **#4255** `[CLOSED]` 引入出站交付解析域类型（`CommunicationDeliveryResolutionRequest`、`CommunicationDeliveryIntent`）。  
  https://github.com/nearai/ironclaw/pull/4255
- **#4261** `[OPEN]` 新建 `ironclaw_triggers` workspace crate，包含触发器域类型、cron 校验、租户级 fire identity 及仓库契约。  
  https://github.com/nearai/ironclaw/pull/4261
- **#4260** `[OPEN]` 添加出站通信偏好存储（`CommunicationPreferenceRepository`），支持 `final_reply_target`、`progress_target` 等交付偏好。  
  https://github.com/nearai/ironclaw/pull/4260

**Agent 韧性与安全（可靠性提升）**
- **#4259** `[CLOSED]` `[DB MIGRATION]` 修复 `capability_info` 自引用失败：模型内省工具自身 schema 时触发 `InvalidInvocation` 导致终端运行失败。  
  https://github.com/nearai/ironclaw/pull/4259
- **#4258** `[CLOSED]` 修复调度失败未走 PR #4236 的 disposition 路径，以及 `oneOf/anyOf` 字符串化容器被错误解析的问题。  
  https://github.com/nearai/ironclaw/pull/4258
- **#4250** `[CLOSED]` 通过 `CancellationToken` 实现飞行中 LLM 调用的即时中断，解决 `/interrupt` 需等待 HTTP 流结束的延迟问题。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-05-31 | 数据来源：github.com/netease-youdao/LobsterAI*

---

### 1. 今日速览

LobsterAI 在 2026-05-31 整体活跃度处于低位，过去 24 小时内无新增 Issues、无版本发布，社区讨论暂时沉寂。代码层面仅有 2 个历史 PR 于昨日（05-30）发生更新，但均仍处于待合并状态，今日无实质性合并进展。两个待处理 PR 均聚焦 UI/UX 修复，分别涉及 MCP 模态框布局与 macOS 快捷键本地化，反映出项目在细节体验上仍有打磨空间。整体而言，项目今日未产生代码层面的向前推进，维护者需关注 stale PR 的审查积压问题，以避免贡献者活跃度流失。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日无已合并或已关闭的 Pull Requests，项目代码库未产生实质性推进。

目前待合并的 2 个 PR 均为 2026-04-04 提交的修复类贡献，距今已近两月，尚未进入主干：
- **PR #1466** — 修复 MCP 服务器表单模态框在内容溢出时关闭按钮不可达的问题。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1466)
- **PR #1467** — 修复 macOS 下快捷键设置面板错误显示 `Ctrl` 而非 `⌘` 的问题。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1467)

由于上述修复均未合并，项目在稳定性与跨平台体验方面暂未获得改进。

---

### 4. 社区热点

今日无新增评论或互动，社区热点集中在 2 个长期未合并且被标记为 `[stale]` 的 PR 上：

- **PR #1466** `[stale]` — 贡献者指出 MCP 配置模态框因 `max-h-[80vh] overflow-y-auto` 直接作用于整体面板，导致页眉与页脚按钮随内容滚动至可视区域外。该问题在配置多个环境变量或 Header 时直接阻断用户操作，属于典型的可用性缺陷。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1466)
- **PR #1467** `[stale]` — 贡献者修复 macOS 平台快捷键显示不符合系统惯例的问题，根因为 `config.ts` 与设置初始化器中硬编码 `Ctrl` 而未区分平台。该 PR 虽影响面较小，但体现了跨平台产品对细节体验的要求。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1467)

**诉求分析**：两个 PR 均由同一贡献者（@linlihua）提交，且均已 stale，反映出社区对 UI 细节修复有明确诉求，但项目维护者的代码审查与合并响应存在明显瓶颈，可能抑制外部贡献意愿。

---

### 5. Bug 与稳定性

今日无新报告的 Bug Issues。基于现有待合并 PR，已识别但未合入的修复如下（按严重程度降序）：

| 严重程度 | 问题描述 | 状态 | Fix PR |
|---|---|---|---|
| **中** | MCP 服务器配置模态框在内容增高时，关闭/取消按钮随整体滚动滑出可视区域，导致用户无法完成或取消操作。 | 待合并 | [#1466](https://github.com/netease-youdao/LobsterAI/pull/1466) |
| **低** | macOS 系统下设置面板的快捷键显示为 `Ctrl+N/F/,`，未遵循 macOS `⌘` 惯例，造成平台交互认知偏差。 | 待合并 | [#1467](https://github.com/netease-youdao/LobsterAI/pull/1467) |

---

### 6. 功能请求与路线图信号

今日无新增功能请求 Issues，亦无正在开发的新功能 PR。现有活动均为修复性质，暂未释放出明确的新版本路线图信号。从修复方向可间接推测，项目当前迭代重心可能仍围绕 **MCP（Model Context Protocol）集成能力完善** 与 **跨平台桌面端体验打磨**，但缺乏公开的功能规划讨论。

---

### 7. 用户反馈摘要

今日 Issues 区无新增评论，用户声音渠道较为沉寂。从现有 PR 描述中可间接提炼以下体验痛点：

- **MCP 配置场景**：当用户为 MCP 服务器添加多组环境变量或 Header 时，模态框布局崩溃，操作按钮不可达，直接阻碍配置流程。
- **macOS 体验落差**：macOS 用户期望在快捷键设置中看到 `⌘` 符号，但界面统一显示 `Ctrl`，产生“未针对 Mac 优化”的感知。

由于今日无直接用户评论，无法评估满意/不满意情绪的最新变化。

---

### 8. 待处理积压

以下 PR 已长期开放且被标记为 stale，建议维护者优先审查，防止修复腐烂与贡献者流失：

1. **PR #1466** — 开放于 2026-04-04，最后更新于 2026-05-30，修复 MCP 模态框滚动布局导致的按钮不可达问题。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1466)
2. **PR #1467** — 开放于 2026-04-04，最后更新于 2026-05-30，修复 macOS 快捷键符号本地化问题。[查看链接](https://github.com/netease-youdao/LobsterAI/pull/1467)

**提醒**：两个 PR 均由同一外部贡献者提交，距今已近两个月。若项目仍保持活跃维护，建议在未来 1-2 个迭代周期内完成 review 与合并，以维持社区信任并修复已知的桌面端体验缺陷。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-05-31 | 分析师：AI 智能体开源项目分析师*

---

### 1. 今日速览

Moltis 项目在 2026-05-31 整体活跃度处于低位，过去 24 小时内未产生新的 Issues 交互与版本发布，仅出现 1 条待合并 Pull Request。社区讨论热度暂时冷却，当日开发活动聚焦于 OpenAI Codex Provider 的流式工具调用参数处理这一细分技术点。项目整体健康度维持平稳，但需关注代码审阅与社区互动指标的持续低迷。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日无已合并或关闭的 Pull Request，主分支未发生实质性代码推进。目前有待维护者审阅的 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088），该提交针对 OpenAI Codex Provider 处理最终工具调用参数（final tool-call arguments）的场景进行加固，旨在记录 `response.function_call_arguments.done` 负载、在未 emit 参数增量（delta）时合成流式参数增量，并完善空参数字符串的解码诊断路径。该 PR 若合并，将提升 Moltis 与 OpenAI Codex 流式输出的兼容性，减少工具调用环节的边缘情况错误。

---

### 4. 社区热点

今日社区唯一可见的动态为 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088）。该 PR 目前处于 Open 状态，👍 数为 0，暂无评论互动，社区参与度极低。其背后的技术诉求明确：解决 OpenAI Codex 在实际流式传输中可能出现的“参数增量缺失”与“最终参数处理”问题，反映出贡献者正在深耕 AI Provider 层的协议兼容性，但尚未引发更广泛的社区审阅响应。

---

### 5. Bug 与稳定性

今日未收到新提交的 Bug Report 或崩溃回归 Issue（0 条新增）。但从待审阅 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088）的技术摘要判断，存在一个与 OpenAI Codex Provider 相关的稳定性改进点：当 Codex 未 emit 参数 delta 时，系统需通过最终参数合成流式增量，否则可能导致工具调用参数解析不完整（missing-argument error）。该问题严重程度评估为**中等**（影响特定 Provider 的流式场景），目前 Fix PR 已提交，等待合并。

---

### 6. 功能请求与路线图信号

今日无新增功能请求 Issue。现有 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088）虽非典型 Feature Request，但揭示了项目路线图的一个信号：Moltis 正在持续跟进 OpenAI Codex 的最新协议行为，强化作为 AI Agent 基础设施对多模型 Provider 的流式输出支持。短期内路线图可能继续围绕核心 Provider 兼容性、流式处理鲁棒性展开，而非大规模新功能。

---

### 7. 用户反馈摘要

基于今日 GitHub 数据，未观测到新增 Issues 评论或用户直接反馈。从 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088）的技术上下文可间接推断，使用 OpenAI Codex 集成的开发者可能遇到工具调用参数在流式传输中“断流”或诊断信息丢失的痛点，贡献者正通过完善 `function_call_arguments.done` 事件的处理逻辑来回应这一场景需求。

---

### 8. 待处理积压

今日新增待处理项 **PR #1088**（https://github.com/moltis-org/moltis/pull/1088），目前处于待合并状态，维护者尚未进行审阅或反馈。鉴于该 PR 涉及 OpenAI Codex Provider 的核心流式处理逻辑，建议维护者优先安排代码审阅，以避免工具调用参数相关的边缘情况修复长期悬置。基于当日数据，无其他长期未响应的历史积压项可评估。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw 项目动态日报**  
*日期：2026-05-31*

---

### 1. 今日速览

CoPaw 项目在过去 24 小时内社区讨论活跃度保持高位，共有 9 条 Issue 发生更新，其中 8 条仍处于活跃或新开状态，1 条关闭；Pull Request 侧仅有 1 条待合并更新，无新版本发布。社区焦点高度集中在 Windows 桌面端的稳定性体验上，特别是 `execute_shell_command` 调用时的控制台窗口闪烁问题已引发多次重复反馈。与此同时，ACP 协议与 Claude Code 的兼容性故障、以及 `/mission` 指令导致的 Console 卡死等核心功能缺陷仍未得到修复，整体代码合并侧进展偏慢。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日无已合并或关闭的 Pull Request，代码主干的直接推进有限。唯一处于 Open 状态的 PR 为 [#4689](https://github.com/agentscope-ai/QwenPaw/pull/4689)，该 PR 由 @leoleils 于 5 月 26 日提交，昨日（5-31）仍有更新，旨在解决 OpenAI Python SDK 因拒绝非标准关键字参数而导致 DashScope 等提供商的 `generate_kwargs`（如 `enable_search`）被静默忽略的问题。方案通过将非标准参数路由至 `extra_body`，可显著提升对国内及第三方模型提供商的兼容性。目前该 PR 仍处于审查阶段，尚未合并。

---

### 4. 社区热点

过去 24 小时内讨论最激烈的议题为：

- **[#4123](https://github.com/agentscope-ai/QwenPaw/issues/4123) Windows: execute_shell_command flashes a console window on every call**（8 条评论）：该 Bug 已持续近一个月，用户反馈在 Windows 环境下每次执行 Shell 命令都会弹出黑色 CMD 窗口

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

**EasyClaw（RivonClaw）项目动态日报 | 2026-05-31**

---

### 1. 今日速览
过去24小时内，EasyClaw 仓库未产生新的 Issues 与 Pull Requests，社区代码贡献与问题反馈处于静默状态。然而，维护团队展现了极高的发布工程活跃度，单日连续推送三个补丁版本（v1.8.19 → v1.8.20 → v1.8.21），集中加固桌面端自动更新、代理网络路由及 Agent 启动时序。整体项目处于**低社区波动、高交付流水线运转**的健康维护态，核心风险在于发布频率虽高，但缺乏公开的社区验证反馈闭环。
> 项目主页：https://github.com/gaoyangz77/easyclaw

---

### 2. 版本发布
今日发布三个补丁版本，均围绕桌面客户端发布工程与网络稳定性。以下为详细变更与迁移建议：

**v1.8.21 (Latest)**
- **更新内容**：优化 macOS 更新器效率，将 OpenClaw 运行时打包为支持 blockmap 的 tar 存档，以提升增量更新性能；加固 Agent 工具启动链路，确保云工具与客服桥接（customer-service bridges）在网关目录就绪后才启动，消除启动时序竞态；同步 CI 检查以适配新的 macOS 运行时存档格式。
- **破坏性变更**：无。
- **迁移注意**：macOS 桌面用户建议直接通过内置更新通道升级，以获取增量更新包体积缩减收益；若自行托管更新镜像，需确认同步工具支持 tar 存档的 blockmap 索引。
> https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.21

**v1.8.20**
- **更新内容**：改进第一方域名路由策略，桌面客户端在回退至 China relay 前会先探测真实 RivonClaw API 路径；强化代理感知网络处理，覆盖重定向、回环地址及第一方域名场景；确保发布与更新流量正确路由至全球或中国区基础设施。
- **破坏性变更**：无。
- **迁移注意**：处于强制代理或混合网络环境的企业用户，建议验证 v1.8.20 的自动路由探测逻辑是否与现有代理白名单/ PAC 规则冲突。
> https://github.com/gaoyangz77/easyclaw/releases

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*