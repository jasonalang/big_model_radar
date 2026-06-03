# OpenClaw 生态日报 2026-06-03

> Issues: 425 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-03 03:40 UTC

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
**日期：** 2026-06-03  
**仓库：** github.com/openclaw/openclaw

---

### 1. 今日速览

过去 24 小时，OpenClaw 社区保持极高活跃度，共更新 **425 条 Issues**（271 条新开/活跃，154 条关闭）与 **500 条 PR**（392 条待审，108 条已合并/关闭），无新版本发布。当前核心矛盾集中在**会话状态（session-state）稳定性**与**消息投递可靠性**上：多个 P1 级回归 Bug 同时影响 Windows UI、Telegram、Slack、Feishu 及 Codex 插件通道。与此同时，社区对 SQLite 化迁移、内存检索增强及私有网络访问等中长期架构改进的讨论显著升温，表明项目在功能深化的同时正经历一轮质量承压期。

---

### 2. 版本发布

今日无新版本发布。最新可用版本仍为此前构建，建议关注主线的 Codex 通道与 Feishu 通道修复 PR，以解决 2026.5.27+ 引入的回归问题。

---

### 3. 项目进展

今日已合并/关闭的重要 PR 与 Issue 推动了以下关键修复：

**已关闭 PR（代码合并/修复完成）：**
- **#89065** — 修复会话文件头损坏时整个 transcript 被静默清空的数据丢失问题。  
  https://github.com/openclaw/openclaw/pull/89065
- **#87626** — 修复 Telegram 私聊在持久化会话中重复注入 `chat_window` 上下文的问题，减少冗余历史干扰。  
  https://github.com/openclaw/openclaw/pull/87626
- **#79176** — 修复 GitHub Copilot  provider 在 GPT/o-series 模型上因重放加密 reasoning 内容导致的跨轮次失败。  
  https://github.com/openclaw/openclaw/pull/79176
- **#67202** — 为 write 工具增加写后校验，防止“报告成功但实际未落盘”的虚假成功状态。  
  https://github.com/openclaw/openclaw/pull/67202
- **#89675** — 修复 Web UI Skills 面板中切换开关状态在过滤后错误传递到下一项的渲染 Bug。  
  https://github.com/openclaw/openclaw/pull/89675

**已关闭 Issue（问题确认解决）：**
- **#87646** — Feishu 通道在 v2026.5.27 升级后无法分发消息（`TypeError: Cannot read properties of undefined`）已修复。  
  https://github.com/openclaw/openclaw/issues/87646
- **#84252** — `doctor/status` 对 openai-codex OAuth sidecar 的“半修复”状态已处理。  
  https://github.com/openclaw/openclaw/issues/84252
- **#76654** — WebChat 在 MiMo V2 Pro 心跳工具调用后响应消失的问题已关闭。  
  https://github.com/openclaw/openclaw/issues/76654
- **#87650** — 2026.5.27 升级后 Codex provider/runtime 不匹配且 `onboard`/`doctor --fix` 无法恢复的问题已解决。  
  https://github.com/openclaw/openclaw/issues/87650

---

### 4. 社区热点

今日讨论最激烈的议题集中在**会话架构迁移**与**多平台回归缺陷**上，反映出用户对核心运行时稳定性的高度关注：

| 议题 | 评论数 | 核心诉求 |
|------|--------|----------|
| **#52875** Session_send gives no session found（回归） | 21 | 升级后主代理无法联系其他代理，`session_list` 仅返回 cron 会话，阻断多代理协作。 |
| **#88838** Track core session/transcript SQLite migration via accessor seam | 17 | 维护者主导的大型架构重构，社区关注如何以“分支抽象”方式低风险落地，避免再次引发大规模回归。 |
| **#63918** Cron agentTurn sends `thinking=none` to gpt-5-nano | 17 | OpenAI 新模型兼容性：cron 任务向不支持 `none` 的模型发送非法参数导致 400 错误。 |
| **#67035** Windows chat UI regression: input swallowed, replies invisible | 14 | **P1 回归**，Windows 端输入被吞、流式回复不可见，严重影响桌面端可用性。 |
| **#39604** Add `tools.web.fetch.allowPrivateNetwork` | 13 / 👍9 | 企业/自托管用户强烈需求：允许显式开启后访问内网地址，安全与功能性的边界讨论激烈。 |
| **#88788** GHCR 2026.5.28 image emits stale Discord progress commentary config | 12 | 容器镜像与源码配置不同步，反映发布流水线中 schema 版本漂移问题。 |

链接：
- https://github.com/openclaw/openclaw/issues/52875
- https://github.com/openclaw/openclaw/issues/88838
- https://github.com/openclaw/openclaw/issues/63918
- https://github.com/openclaw/openclaw/issues/67035
- https://github.com/openclaw/openclaw/issues/39604
- https://github.com/openclaw/openclaw/issues/88788

---

### 5. Bug 与稳定性

今日新增/活跃的 Bug 按严重程度排列如下。**标注状态：** 🔧 已有修复 PR / ✅ 已关闭 / 🚩 待维护者决策或复现。

**P1（严重/影响生产）**
- **#67035** Windows chat UI 严重回归：输入文本被吞、流式回复不可见、打字指示器闪烁后空白。影响 2026.4.14+ Windows 用户。🚩  
  https://github.com/openclaw/openclaw/issues/67035
- **#55334** `sessions.json` 无界增长导致 Gateway OOM：每个会话重复存储 `skillsSnapshot`，且临时会话无修剪。🚩（`clawsweeper:linked-pr-open`）  
  https://github.com/openclaw/openclaw/issues/55334
- **#88312** Codex app-server turn-completion stall 回归：2026.5.27 复现“Codex stopped before confirming the turn was complete”，系 #84076 的再次回归。🚩  
  https://github.com/openclaw/openclaw/issues/88312
- **#86519** Telegram 代理重复发送相同回复 2-10 次（2026.5.20 更新后）。🚩  
  https://github.com/openclaw/openclaw/issues/86519
- **#52249** ACP 父会话在子会话完成后卡住，需手动刷新 UI 才能恢复。🚩  
  https://github.com/openclaw/openclaw/issues/52249
- **#86047** Codex app-server / plugin approval stalls 导致 Nextcloud Talk 会话中断与工具执行超时（2026.5.22 回归）。🚩  
  https://github.com/openclaw/openclaw/issues/86047
- **#72031** Bedrock `image` 工具在 `auth mode: aws-sdk` 下因 `requireApiKey` 抛错，即使 AWS SDK 凭证已就绪。🔧（`linked-pr-open`）  
  https://github.com/openclaw/openclaw/issues/72031
- **#80715** Slack 回复被静默丢弃：transcript 中已合成，但从未调用 `chat.postMessage`（本周已两次出现，👍8）。🔧（`linked-pr-open`）  
  https://github.com/openclaw/openclaw/issues/80715
- **#86090** `runHeartbeatOnce` 在空闲代理上返回伪运行状态（78ms 内 `{status: "ran"}`），实际未执行模型轮次。🚩  
  https://github.com/openclaw/openclaw/issues/86090
- **#79552** Android 节点在 WebSocket 握手完成前发送 `node.event`，导致通知事件丢失。🔧（`queueable-fix`）  
  https://github.com/openclaw/openclaw/issues/79552
- **#85773** 重装 v2026.5.20 后代理完全忽略工作区文件与技能，仅返回通用回复。🚩  
  https://github.com/openclaw/openclaw/issues/85773
- **#89374** 超时压缩报告成功，但 Codex 通道会话仍不可恢复。🚩  
  https://github.com/openclaw/openclaw/issues/89374

**P2（中等/有变通方案）**
- **#52875** `Session_send` 找不到会话（stale 回归，21 条评论）。🚩  
  https://github.com/openclaw/openclaw/issues/52875
- **#63918** Cron 向 gpt-5-nano 发送非法 `thinking=none`。🚩  
  https://github.com/openclaw/openclaw/issues/63918
- **#88788** GHCR 2026.5.28 镜像携带过期 Discord progress commentary schema。🚩  
  https://github.com/openclaw/openclaw/issues/88788
- **#85103** 提供商级配额耗尽时模型降级链未触发，且出现 `EmbeddedAttemptSessionTakeoverError`。🚩  
  https://github.com/openclaw/open

---

## 横向生态对比

**个人 AI 助手/自主智能体开源生态横向对比分析**  
*基于 2026-06-03 社区动态数据*

---

### 1. 生态全景

当前个人 AI 助手与自主智能体开源生态呈现**“头部深潜、长尾静默”**的分化格局。OpenClaw、ZeroClaw、NanoBot 等核心项目以极高代码吞吐量推动架构升级，但共同面临从“功能可用”向“生产可靠”过渡的阵痛——MCP 协议稳定性、会话状态持久化、跨平台 UI 回归成为共性瓶颈。与此同时，安全加固（沙箱、SSRF、命令注入修复）与可观测性建设被普遍提到更高优先级，表明行业整体进入**质量巩固与工程化落地**阶段，而非早期功能堆砌。

---

### 2. 各项目活跃度对比

| 项目 | Issues (24h) | PR (24h) | 版本发布 | 健康度评估 |
|------|-------------|----------|----------|------------|
| **OpenClaw** | 425 条（271 活跃/154 关闭） | 500 条（392 待审/108 关闭） | 无 | 🔶 质量承压：多平台 P1 回归并发，架构迁移与稳定性修复并行 |
| **NanoBot** | 9 条（6 活跃/3 关闭） | 25 条（17 关闭/8 待审） | 无 | 🟢 健康：修复闭环效率高，MCP 与渠道扩展活跃 |
| **ZeroClaw** | 50 条（33 关闭） | 50 条（47 关闭/合并） | **v0.8.0-beta-2** | 🟢 健康：交付节奏强劲，安全与技能子系统深度打磨 |
| **LobsterAI** | 0 条新增 | 9 条（6 关闭/3 待处理） | 无 | 🟢 良好：模型适配与 MCP 性能治理为主，3 条 PR 长期悬置 |
| **NanoClaw** | 1 条新增 | 6 条（4 关闭/2 待审） | 无 | 🔶 技术稳健但社区静默：所有 Issue/PR 评论数为 0 |
| **Moltis** | 1 条新增 | 1 条待合并 | 无 | 🔶 低位静默：核心贡献者单点驱动，社区参与度极低 |
| **EasyClaw** | 0 条 | 0 条 | **4 个补丁** (v1.8.24→v1.8.27) | 🟡 发布窗口期：流水线高频运转，社区讨论停滞 |
| **TinyClaw / ZeptoClaw** | 0 | 0 | 无 | ⚪ 无活动 |
| **PicoClaw / IronClaw / CoPaw** | — | — | — | ⚪ 当日无公开数据 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是生态中**唯一的“操作系统级”多平台 Agent 框架**，其单日 425 Issues / 500 PR 的吞吐量在数量级上碾压其他项目（NanoBot 25 PR、ZeroClaw 50 PR）。核心优势在于**全渠道覆盖**（Telegram、Slack、Feishu、Codex、Web、Android）与**架构前瞻性**（SQLite 化迁移、accessor seam 抽象）。

然而，其技术路线呈现**“重架构、重集成”**特征，导致版本迭代伴随大规模回归风险——2026.5.27 升级后同时引爆 Windows UI、Codex、Feishu、Slack 等多通道 P1 级故障。相比之下，ZeroClaw 选择 Rust 安全沙箱与 TUI 的垂直深耕，NanoBot 聚焦 Python 易用性与 MCP 生态，OpenClaw 则更像一个**高复杂度的生产级底座**，适合需要跨平台企业部署的场景，但对稳定性容忍度要求更高。

---

### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **MCP 生态稳定性** | NanoBot、NanoClaw、LobsterAI | NanoBot 遭遇 Session 自毁（#4168）与 Notion 握手失败（#1168）；NanoClaw 修复 MCP 联合类型兼容（#2672）；LobsterAI 优化 npx MCP 启动性能（#2091） |
| **会话状态与历史管理** | OpenClaw、Moltis、NanoBot | OpenClaw 的 `sessions.json` 无界增长（#55334）与 SQLite 迁移（#88838）；Moltis 截断工具结果防上下文溢出（#1089）；NanoBot 修复历史记录越界隐藏（#4169） |
| **多平台 UI/渠道可靠性** | OpenClaw、NanoBot、NanoClaw | OpenClaw Windows 端输入被吞（#67035）、Slack 消息静默丢弃（#80715）；NanoBot 新增 QQ 渠道与 WebUI 路由重构；NanoClaw 落地 WebChat Skill |
| **安全加固** | ZeroClaw、NanoClaw、NanoBot | ZeroClaw 细化技能审计与 shell policy（#5952）；NanoClaw 修复容器 Dockerfile 命令注入（#2538）；NanoBot 增加 MCP SSRF 校验（#4123） |
| **企业/私有部署适配** | OpenClaw、NanoClaw | OpenClaw 请求允许内网访问配置（#39604）；NanoClaw 修复代理后 HTTP-only 传输（#2672） |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 跨平台企业级 Agent 操作系统 | 需集成多 IM/企业系统的团队 | 重状态机与多通道适配器，TypeScript/Node 生态，架构庞大 |
| **ZeroClaw** | 安全优先的开发者运行时 | 注重沙箱与本地执行的工程师 | Rust 构建，Bubblewrap 沙箱，自有 ACP 协议，TUI（zerocode）为核心交互 |
| **NanoBot** | 易用型个人助手与 MCP 生态 | 中文社区开发者、成本敏感用户 | Python 生态，轻量 RAG 记忆，快速适配 QQ/Email 等国内渠道 |
| **LobsterAI** | 模型适配与 Agent 基础设施 | 中文场景、MiniMax 生态用户 | 背靠网易有道，聚焦模型层（MiniMax-M3）与 MCP 启动优化 |
| **NanoClaw** | 可扩展宿主与插件化平台 | 需自定义扩展的开发者 | 宿主侧插件钩子（onStartup/onShutdown），Skill 体系扩展频道 |
| **EasyClaw** | 垂直电商场景 | 电商运营者、多店铺卖家 | 非通用框架，聚焦店铺数据同步、OAuth 多店授权、客服系统 |
| **Moltis** | 工具链精细化与 Telegram 渠道 | 小众 Telegram Bot 部署者 | 工具结果截断与 Activity log 可配置性 |

---

### 6. 社区热度与成熟度

**快速迭代期（高频 + 大变更）**
- **OpenClaw**：社区体量最大，但处于“架构迁移 vs 质量回归”的阵痛期，属于**高活跃、高风险**的深潜阶段。
- **ZeroClaw**：v0.8.0-beta-2 交付多代理运行时与全新 TUI，合并率高达 94%（47/50），属于**健康的高速演进**。
- **NanoBot**：MCP、RAG、QQ 渠道多点开花，修复闭环快，属于**功能扩张期**。

**质量巩固期（高频 + 小补丁 / 治理）**
- **LobsterAI**：无新增 Issue，PR 聚焦 MCP 性能与模型适配，属于**低调治理期**。
- **EasyClaw**：24 小时 4 个补丁版本，围绕电商数据完整性打补丁，**发布密集但社区冷**。

**低频维护 / 静默期**
- **NanoClaw、Moltis**：技术推进持续（插件系统、工具截断），但社区互动为 0，属于**核心团队单点维护**。
- **TinyClaw、ZeptoClaw、PicoClaw、IronClaw、CoPaw**：当日无活动或数据，生态位边缘化。

---

### 7. 值得关注的趋势信号

1. **MCP 成为事实标准，但“连接稳定性”成为新瓶颈**  
   NanoBot 的 Session 自毁、NanoClaw 的联合类型兼容、LobsterAI 的 npx 启动优化，共同指向 MCP 传输层与生命周期管理仍是半成品。对开发者的价值：**MCP 中间件与重连机制将是下一个基础设施竞争点**。

2. **安全左移：从“能跑”到“敢跑”**  
   ZeroClaw 的技能审计策略细化、NanoClaw 的容器注入修复、NanoBot 的 SSRF 校验，表明 Agent 执行环境的安全基线正在快速抬高。开发者需将**沙箱与输入校验**纳入首日架构，而非事后补丁。

3. **终端 UX 专业化**  
   ZeroClaw 推出 zerocode TUI、OpenClaw 修复 Windows UI 回归、NanoBot 优化 WebUI 复制回退与路由，显示 Agent 交互正从 API/命令行走向**面向终端用户的精致化体验**。

4. **成本敏感型开发崛起**  
   NanoBot 社区对 DeepSeek V4 缓存未命中成本的高度关注，预示 Agent 应用进入**精细化 API 成本运营**阶段，缓存策略与模型降级链将成为标配

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
**日期：** 2026-06-03  
**仓库：** [HKUDS/nanobot](https://github.com/HKUDS/nanobot)

---

### 1. 今日速览

过去 24 小时，NanoBot 维持极高活跃度：PR 更新 25 条（17 条已合并/关闭，8 条待审阅），Issues 更新 9 条（6 条新开或活跃，3 条关闭）。今日无新版本发布。社区焦点集中在 **MCP 生态稳定性**（连接中断、子代理权限）、**WebUI 体验打磨**（路由、排序、复制回退）以及 **Email/QQ 等新渠道能力**上。整体项目健康度良好，修复闭环效率高，但长期积压的 MCP 兼容性问题仍需关注。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日已合并/关闭的 17 个 PR 中，以下推进了核心功能或关键修复：

- **即时通讯渠道扩展**  
  - [#4146](https://github.com/HKUDS/nanobot/pull/4146) 新增 **Napcat (QQ) 渠道**，支持 OneBot v11 Forward WebSocket 的私聊与群聊，补齐了国内 IM 生态。  
- **记忆系统增强**  
  - [#4109](https://github.com/HKUDS/nanobot/pull/4109) 引入轻量级 **RAG 记忆检索**，使用本地嵌入改善长程上下文召回。  
  - [#3990](https://github.com/HKUDS/nanobot/pull/3990) 重构 `Dream` 类，将旧版两阶段流程替换为基于 `process_direct()` 的简化 cron 循环，降低维护复杂度。  
- **Email 渠道完善**  
  - [#4162](https://github.com/HKUDS/nanobot/pull/4162) 为 Email 渠道增加**文件附件支持**，支持媒体文件自动 MIME 检测与大小限制。  
- **WebUI 架构与体验**  
  - [#4115](https://github.com/HKUDS/nanobot/pull/4115) 完成 **WebUI Gateway 依赖拆分**，将 HTTP 路由从 WebSocketChannel 解耦，改善架构清晰度。  
  - [#4157](https://github.com/HKUDS/nanobot/pull/4157) 为 WebUI 启动请求增加 `fetchWithTimeout`，防止永久挂起。  
  - [#4151](https://github.com/HKUDS/nanobot/pull/4151) 修复侧边栏 "Chats" 分组始终沉底的问题，改为按最近更新时间排序。  
  - [#4150](https://github.com/HKUDS/nanobot/pull/4150) 引入 hash 路由持久化，刷新页面后可恢复当前聊天位置。  
  - [#4149](https://github.com/HKUDS/nanobot/pull/4149) 为回复复制按钮增加 `execCommand("copy")` 回退，解决非安全上下文或 WebView 内复制失败问题。  
- **关键 Bug 修复**  
  - [#4155](https://github.com/HKUDS/nanobot/pull/4155) 修复 `read_file` 在 tool-result offloading 后的恢复死循环（对应 Issue [#4153](https://github.com/HKUDS/nanobot/issues/4153)）。  
  - [#4159](https://github.com/HKUDS/nanobot/pull/4159) 自动修复 `uv tool` 环境下 pip 模块缺失导致的 CLI App 安装失败（对应 Issue [#4158](https://github.com/HKUDS/nanobot/issues/4158)）。

---

### 4. 社区热点

今日讨论最活跃的议题集中在 **MCP 与图片生成** 的兼容性上：

| 议题 | 状态 | 评论 | 核心诉求 |
|------|------|------|----------|
| [#4167](https://github.com/HKUDS/nanobot/issues/4167) Image generation fails with OpenAI-compatible APIs | OPEN | 2 | 用户希望 `generate_image` 兼容不支持 `response_format` 参数的 OpenAI 兼容 API（如 Agnes AI）。 |
| [#4158](https://github.com/HKUDS/nanobot/issues/4158) Fix WebUI CLI App pip installs under uv tool | OPEN | 1 | `uv tool` 安装环境下缺失 pip 模块，导致 WebUI 安装 CLI 应用失败，已有关键 PR 待合并。 |
| [#4142](https://github.com/HKUDS/nanobot/issues/4142) Optimization of usage costs for cache miss Input Tokens | CLOSED | 1 | 围绕 DeepSeek V4 等模型的缓存未命中成本优化讨论，反映社区对 API 成本的高度敏感。 |
| [#1168](https://github.com/HKUDS/nanobot/issues/1168) Nanobot 连接 Notion MCP 失败 | OPEN | 1 | 中文用户反馈 Notion MCP 连接问题，Claude 侧可正常登录，指向 NanoBot 的 MCP 握手或配置差异。 |

**分析：** 社区正从“功能可用”向“生态兼容”与“成本可控”迁移，对 OpenAI 兼容层和 MCP 稳定性的要求显著提升。

---

### 5. Bug 与稳定性

按严重程度排列：

**🔴 高严重：尚无 Fix PR**
- **[#4168](https://github.com/HKUDS/nanobot/issues/4168) MCP 服务器随机时间后不可达**  
  运行一段时间后出现 `McpError: Session terminated`，必须从 MCP Server 侧断连后重启 NanoBot 恢复。影响长时间会话的生产稳定性。
- **[#4167](https://github.com/HKUDS/nanobot/issues/4167) 图片生成硬编码 `response_format` 导致兼容 API 崩溃**  
  调用 Agnes AI 等 OpenAI 兼容接口时直接抛出 `UnsupportedParamsError`，阻塞非官方 OpenAI 的图片生成工作流。

**🟡 中严重：已有修复或在途**
- **[#4158](https://github.com/HKUDS/nanobot/issues/4158) / [#4153](https://github.com/HKUDS/nanobot/issues/4153) `uv tool` / `read_file` 工具链故障**  
  前者已有 [#4164](https://github.com/HKUDS/nanobot/pull/4164)（待合并）和已关闭的 [#4159](https://github.com/HKUDS/nanobot/pull/4159)；后者已通过 [#4155](https://github.com/HKUDS/nanobot/pull/4155) 修复。
- **[#4081](https://github.com/HKUDS/nanobot/issues/4081) MemoryStore 并发写入产生重复 cursor**  
  已关闭，根因是 cursor 分配与 JSONL 追加缺乏异步锁保护。

**🟢 低严重：边缘场景修复待审**
- **[#4165](https://github.com/HKUDS/nanobot/pull/4165) Email 渠道发送空邮件**  
  progress 消息被误当作普通消息投递，导致每次工具调用后发送无内容邮件。
- **[#4169](https://github.com/HKUDS/nanobot/pull/4169) `last_consolidated` 越界导致历史记录被整体隐藏**  
  会话损坏后 `get_history()` 返回空切片，使代理进入“失忆”状态。

---

### 6. 功能请求与路线图信号

以下需求与在途 PR 共同勾勒出近期可能的路线图方向：

- **自定义图片生成 Provider**  
  - Issue [#4132](https://github.com/HKUDS/nanobot/issues/4132)（good first issue）请求支持 Agnes AI 等自定义图片 API，与 [#4167](https://github.com/HKUDS/nanobot/issues/4167) 的 Bug 形成互补，预计下一版本会统一纳入。
- **Subagent MCP 权限**  
  - Issue [#4166](https://github.com/HKUDS/nanobot/issues/4166) 请求配置项允许子代理访问 MCP 工具，这是多 Agent 协作的关键缺口。
- **WebUI 会话 Fork**  
  - PR [#4163](https://github.com/HKUDS/nanobot/pull/4163) 已实现“从此处 Fork”功能，允许用户基于历史消息分支新会话，预计很快合并。
- **云平台一键部署**  
  - PR [#4139](https://github.com/HKUDS/nanobot/pull/4139) 提出 HuggingFace Spaces / ModelScope 的零依赖部署层（+851 行），若合并将大幅降低云端上手门槛，属于战略性基础设施。
- **MCP 安全加固**  
  - PR [#4123](https://github.com/HKUDS/nanobot/pull/4123) 在探测前增加 SSRF 校验，防止不安全 HTTP URL 攻击，属于安全基线补强。

---

### 7. 用户反馈摘要

从今日 Issues 中提炼的真实痛点与场景：

- **MCP 生态是最大摩擦点：** 用户不仅遇到 Notion 连不上（[#1168](https://github.com/HKUDS/nanobot/issues/1168)），还遇到长时间运行后 Session 自毁（[#4168](https://github.com/HKUDS/nanobot/issues/4168)），且子代理无法复用 MCP 工具（[#4166](https://github.com/HKUDS/nanobot/issues/4166)）。这表明 MCP 的传输层重连、生命周期管理与权限继承需要系统性加固。
- **部署环境碎片化：** `uv` 作为新兴 Python 包管理器被越来越多用户采用，但 NanoBot 的 CLI App 管理器仍假设 `pip` 始终可用（[#4158](https://github.com/HKUDS/nanobot/issues/4158)）。用户期望与 Python 现代工具链无缝兼容。
- **成本敏感型用户崛起：** [#4142](https://github.com/HKUDS/nanobot/issues/4142) 的讨论显示，DeepSeek V4 等低价

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
**日期：** 2026-06-03  
**仓库：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)

---

### 1. 今日速览

过去 24 小时，ZeroClaw 维持极高活跃度，共有 **50 条 Issue** 与 **50 条 PR** 更新，关闭/合并率表现强劲（Issue 关闭 33 条，PR 合并或关闭 47 条）。项目正式发布 **v0.8.0-beta-2**，推出全新终端 UI `zerocode` 与多代理运行时，是自 v0.7.5 以来最大规模的功能迭代。社区侧的安全加固与技能（Skills）子系统打磨仍是焦点，多个 P1 级安全与稳定性问题被集中修复，整体交付节奏健康。

---

### 2. 版本发布

**[v0.8.0-beta-2](https://github.com/zeroclaw-labs/zeroclaw/releases/tag/v0.8.0-beta-2)**  
这是 v0.8.0 线的第二个 Beta 版本，核心亮点包括：

- **zerocode**：全新的全功能终端 UI（TUI），用户无需离开终端即可运行、操作和与 Agent 交互。相关代码已从 `crates/zeroclaw-tui` 迁移并重命名为 `apps/zerocode`（见 [#6821](https://github.com/zeroclaw-labs/zeroclaw/issues/6821)）。
- **多代理运行时（Multi-Agent Runtime）**：正式随本版本交付，支持更复杂的代理协作场景。
- **ACP 协议扩展**：支持 diff 展示与文件提议（file-proposal）消息类型，为 TUI 和 Web Dashboard 的审批流程提供侧-by-侧差异对比（见 [#6820](https://github.com/zeroclaw-labs/zeroclaw/issues/6820)）。

**迁移提示：** 若从早期版本升级并使用自定义技能路径或 TUI 主题，建议核对新的 `apps/zerocode` 目录结构；使用 Bubblewrap 沙箱的 Fedora 43 用户需确认 `/lib64` 挂载参数已生效（见 [#6878](https://github.com/zeroclaw-labs/zeroclaw/issues/6878)）。

---

### 3. 项目进展

今日合并/关闭的重要 PR 推动了文档基础设施、安全策略、技能子系统和运行时稳定性的多重进展：

- **文档与交付基础设施**
  - [#7023](https://github.com/zeroclaw-labs/zeroclaw/pull/7023) 实现版本化文档部署与版本选择器，解决多版本文档浏览需求。
  - [#7124](https://github.com/zeroclaw-labs/zeroclaw/pull/7124)（待合并）修复版本化文档的 `_shared` 资源归属问题，防止旧标签覆盖主版本样式。

- **安全与沙箱策略**
  - [#5952](https://github.com/zeroclaw-labs/zeroclaw/pull/5952) 将技能审计范围严格限定为结构性与文件系统检查，命令内容安全统一交由 shell policy 执行，避免重复且不一致的静态扫描。
  - [#5981](https://github.com/zeroclaw-labs/zeroclaw/pull/5981) 修复 `ReadSkillTool` 未透传 `allow_scripts` 配置的问题，解决技能被误拦截的痛点（关联 [#5697](https://github.com/zeroclaw-labs/zeroclaw/issues/5697)）。
  - [#6071](https://github.com/zeroclaw-labs/zeroclaw/pull/6071) 停止对 Markdown 文档内容执行高风险命令模式扫描，减少误报。

- **运行时与协议**
  - [#6009](https://github.com/zeroclaw-labs/zeroclaw/pull/6009) 为 OTel 工具调用跨度补充 `gen_ai.tool.*` 语义约定属性，提升可观测性。
  - [#6026](https://github.com/zeroclaw-labs/zeroclaw/pull/6026) 修复 cron 代理运行中工具输出回显与降级投递问题，避免 Telegram 等通道的空消息。
  - [#6114](https://github.com/zeroclaw-labs/zeroclaw/pull/6114) 在辅助 LLM 调用（意图分类、上下文压缩）中剥离 `[IMAGE:...]` 等多模态标记，防止污染非多模态模型输入。
  - [#6054](https://github.com/zeroclaw-labs/zeroclaw/pull/6054) 使 `SKILL.toml` 中的 `timeout_secs` 字段真正生效。

- **平台兼容性**
  - [#5450](https://github.com/zeroclaw-labs/zeroclaw/pull/5450) 为 `http_request`、`web_fetch`、`browser_open` 等工具添加 IPv6 支持。
  - [#5254](https://github.com/zeroclaw-labs/zeroclaw/pull/5254) 清理 llama.cpp Gemma 4

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-03 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

过去24小时，NanoClaw 项目保持中等活跃度：共 **4 条 PR 成功合并/关闭**，**2 条 PR 待审**，**1 条新 Issue 开启**。无新版本发布。今日核心进展集中在 Codex 运行时稳定性加固、容器安全漏洞修复，以及主机端插件扩展机制的落地。值得注意的是，社区互动指标偏低（所有 Issues/PRs 评论数均为 0），项目健康度在技术推进上表现稳健，但社区参与度仍有提升空间。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日合并/关闭的 4 条 PR 推动了架构扩展性、安全性和多频道集成三个维度的重要更新：

- **[#2674] [codex] standardize runtime status messages**（已关闭）  
  将长时间运行的运行时状态消息标准化为机械标签，并增加内部通道防护以防止自循环，提升了 Codex 提供程序在复杂消息循环中的可靠性。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2674)

- **[#1193] feat: add host-side plugin hook system (onStartup/onShutdown)**（已关闭）  
  引入 `src/plugin-loader.ts`，支持在通道连接后、消息循环前扫描并加载 ES 模块插件。插件可通过 `onStartup(ctx)` 启动 HTTP 服务等长期任务，标志着 NanoClaw 向可扩展宿主架构迈出关键一步。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/1193)

- **[#2069] Skill/webchat v1**（已关闭）  
  新增 WebChat 频道技能（Skill），进一步丰富了 NanoClaw 的多频道集成能力，符合项目作为 AI 助手平台的定位。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2069)

- **[#2538] fix(container-runner): validate package names before Dockerfile interpolation**（已关闭）  
  在 `buildAgentGroupImage()` 中增加包名校验，修复了通过构造恶意包名引发的 OS 命令注入漏洞（CWE-78），属于关键安全加固。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2538)

---

### 4. 社区热点

今日所有 Issues/PRs 的评论数与反应数均为 0，社区表面互动处于静默状态。但从技术影响力看，以下两项待合并 PR 是实际热点：

- **[#2672] fix(codex): MCP union compatibility + HTTP-only transport behind proxies**（待合并）  
  解决 Codex 提供程序在 `providers` 分支上的 MCP 配置联合类型（`stdio | http | sse`）兼容性问题，并修复代理环境下 HTTP-only 传输的可用性。该 PR 直接影响企业级部署场景，值得高度关注。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2672)

- **[#2187] fix(platform-id): don't namespace CLI bare platform ids**（待合并）  
  针对 CLI 通道的 platform ID 命名空间逻辑进行 carve-out 修复，解决 CLI 用户在平台标识上的回归问题。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2187)

此外，**[#2673] Automated Student Grading System**（新开启 Issue）内容呈现为 AI 视频生成提示词（AI Video Prompt），而非标准的功能请求或 Bug 报告，可能属于误发或低质量内容，反映社区内容审核机制面临新挑战。  
[→ 查看 Issue](https://github.com/nanocoai/nanoclaw/issues/2673)

---

### 5. Bug 与稳定性

| 严重程度 | 问题描述 | 状态 | 修复 PR / Issue |
|---|---|---|---|
| **🔴 高危** | 容器运行器 Dockerfile 插值存在 OS 命令注入（CWE-78） | **已修复** | [#2538](https://github.com/nanocoai/nanoclaw/pull/2538) |
| **🟡 中危** | Codex 提供程序 MCP 配置联合类型不兼容，且代理后 HTTP-only 传输异常 | **待修复** | [#2672](https://github.com/nanocoai/nanoclaw/pull/2672) |
| **🟢 低危** | CLI 通道 bare platform ID 被错误添加命名空间，影响开发者体验 | **待修复** | [#2187](https://github.com/nanocoai/nanoclaw/pull/2187) |

今日安全态势显著改善，关键容器注入漏洞已被封堵；但 `providers` 分支的 Codex 兼容性问题仍在等待合并，建议优先审阅以降低分支回归风险。

---

### 6. 功能请求与路线图信号

- **可扩展宿主架构**：[#1193](https://github.com/nanocoai/nanoclaw/pull/1193) 插件钩子系统的合并释放强烈信号——NanoClaw 正从单一运行时向插件化平台演进，下一版本可能会围绕插件生命周期管理、插件市场或 SDK 进行建设。
- **企业级部署适配**：[#2672](https://github.com/nanocoai/nanoclaw/pull/2672) 对 MCP 联合类型和代理环境的修复，表明项目正在补足企业网络环境下的边缘场景。
- **多频道集成**：[#2069](https://github.com/nanocoai/nanoclaw/pull/2069) WebChat 技能的落地显示"Skill"体系仍是核心扩展路径，预计后续将有更多频道/集成类 PR 跟进。
- **教育场景兴趣**：[#2673](https://github.com/nanocoai/nanoclaw/issues/2673) 虽内容不规范，但提及"学生成绩系统"与移动端（Android）使用场景，或可作为产品化方向的弱信号。

---

### 7. 用户反馈摘要

今日 Issues/PR 评论区无新增用户声音（评论数均为 0），直接反馈有限。从 PR 内容可间接提炼开发者侧痛点：

- **代理与网络限制**：企业用户在使用 Codex 提供程序时，受限于代理后的 HTTP-only 传输环境（[#2672](https://github.com/nanocoai/nanoclaw/pull/2672)）。
- **CLI 开发者体验**：CLI 通道的 platform ID 处理存在不符合直觉的命名空间行为，影响脚本化/自动化使用（[#2187](https://github.com/nanocoai/nanoclaw/pull/2187)）。
- **安全信任**：容器构建环节的安全校验（[#2538](https://github.com/nanocoai/nanoclaw/pull/2538)）表明维护者对供应链安全有明确意识，有助于提升企业用户信任度。

---

### 8. 待处理积压

以下长期未决或需要维护者介入的事项建议优先处理：

- **[#2187] fix(platform-id): don't namespace CLI bare platform ids**（已积压 32 天）  
  创建于 2026-05-02，最后一次更新为昨日，但仍处于 Open 状态。该 PR 修复 CLI 核心路径的回归问题，且遵循贡献指南，建议尽快审阅合并以避免进一步的分支漂移。  
  [→ 查看 PR](https://github.com/nanocoai/nanoclaw/pull/2187)

- **[#2673] Automated Student Grading System**（需分类/关闭）  
  内容不符合标准 Issue 格式，疑似 AI 生成提示词误发。建议维护者进行标签分类（如 `invalid` 或 `spam`）并关闭，以保持 Issue 面板清洁。  
  [→ 查看 Issue](https://github.com/nanocoai/nanoclaw/issues/2673)

---

*日报生成基于 NanoClaw GitHub 公开数据。如需更详细的技术评审或社区情绪分析，请联系项目维护者。*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-03 | 仓库：netease-youdao/LobsterAI*

---

### 1. 今日速览

LobsterAI 在过去 24 小时内保持**中等偏上的代码活跃度**，无新增公开 Issue，核心工作集中在 PR 合并与审阅（9 条 PR 更新，其中 6 条已关闭/合并，3 条待处理）。今日主线围绕 **MiniMax M3 模型适配**、**MCP 启动性能优化**、**子代理批量删除**及 **IM 多实例重复校验**展开，显示项目正处于模型层升级与 Agent 基础设施深度治理并行的迭代周期。整体健康度良好，但存在 3 条长期悬而未决的 PR 需维护者介入。

---

### 3. 项目进展

今日合并/关闭的 6 个 PR 推动了以下关键进展：

- **MCP 启动性能与可观测性提升**（[#2091](https://github.com/netease-youdao/LobsterAI/pull/2091)）：针对 `npx -y <package>@latest` 类 stdio MCP，前置执行 npm 包解析与本地安装，将启动命令转换为稳定的 `node <absolute-bin-path>`，避免每次会话重复走 npx 慢路径；同时在 OpenClaw runtime adapter 与主进程关键路径增加**首次响应计时日志**，并支持解析失败后的自动重试恢复。
- **MiniMax-M3 图像输入修复**（[#2093](https://github.com/netease-youdao/LobsterAI/pull/2093)）：解除硬编码的 `supportsImage: false`，使 MiniMax-M3 的多模态图像输入能力得以正常使用。
- **子代理批量删除支持**（[#2095](https://github.com/netease-youdao/LobsterAI/pull/2095)）：侧边栏批量选择现覆盖子代理会话，网关 transcript 清理改为异步并限制并发与重试次数，降低批量操作时的系统压力。
- **OpenClaw 内部插件隐藏**（[#2096](https://github.com/netease-youdao/LobsterAI/pull/2096)）：过滤内部/运行时捆绑的插件 ID，避免其在插件管理界面暴露并污染用户配置。
- **Artifacts 与分享体验优化**（[#2092](https://github.com/netease-youdao/LobsterAI/pull/2092)、[#2094](https://github.com/netease-youdao/LobsterAI/pull/2094)）：调整分享成功弹窗的信息层级与视觉样式，移除冗余状态标识；同步推进跨 renderer / main / docs / artifacts 的多模块功能迭代。

---

### 4. 社区热点

今日无新增 Issue，且所有 PR 评论区数据为空（`undefined`），公开社区讨论热度较低。从代码变更方向看，当前最值得关注的技术主线为：

1. **MCP 生态性能优化**（[#2091](https://github.com/netease-youdao/LobsterAI/pull/2091)）：反映项目对 MCP（Model Context Protocol）工具链启动延迟和运行时稳定性的深度治理诉求，属于 Agent 基础设施的关键路径。
2. **MiniMax M3 模型适配**（[#2093](https://github.com/netease-youdao/LobsterAI/pull/2093)、[#388](https://github.com/netease-youdao/LobsterAI/pull/388)）：显示项目正紧跟上游模型迭代，快速补齐多模态能力，但默认模型切换的正式合入仍悬而未决。

---

### 5. Bug 与稳定性

按严重程度排列：

- **中-高：IM 多

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-03 | 数据来源：github.com/moltis-org/moltis*

---

### 1. 今日速览

今日 Moltis 项目活跃度处于低位静默期：过去 24 小时内仅产生 1 条新增 Issue 与 1 条待合并 PR 更新，无版本发布，且所有新增条目均未有社区评论或点赞互动。核心贡献者 `@s-salamatov` 持续聚焦于工具链（Tool）相关的性能优化与可配置性改进，显示出项目在技术债清理与用户体验精细化方向上的持续投入，但社区整体参与热度有待提升。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日无已合并或已关闭的 Pull Request。

唯一活跃的 PR 为 [#1089 Cap persisted tool results before rehydration](https://github.com/moltis-org/moltis/pull/1089)（状态：待合并）。该 PR 旨在对持久化的 `tool` 与 `tool_result` 内容在会话历史重新水合（rehydration）为供应商绑定的 `ChatMessage` 时进行上限截断（capping），覆盖范围包括常规聊天、流式聊天、压缩后重试、提示词检查、静默记忆轮次及 LLM 驱动的压缩提示词等全链路场景。尽管尚未合并，但该改动属于核心消息处理路径的性能与稳定性加固，一旦合入将显著降低因工具返回结果过大导致的上下文溢出与内存压力。

---

### 4. 社区热点

今日社区互动指标（评论数、反应数）均为零，讨论热度最高的条目为当日新建的 Issue：

- **[#1092 Add a config option to disable channel Activity log tool-status messages](https://github.com/moltis-org/moltis/issues/1092)**  
  作者 `@s-salamatov` 提出在 Telegram 等渠道中，Agent 调用工具后会在主回复后附加一个 `Activity log` 块（表现为可折叠 HTML 或单独的跟进消息）。该 Issue 请求增加配置项以允许完全禁用此类工具状态消息。  
  **诉求分析**：这反映了生产环境部署中对“终端用户对话纯净度”与“开发调试可观测性”之间的灵活权衡需求，尤其针对 Telegram 这类对消息排版敏感的前端渠道。

---

### 5. Bug 与稳定性

今日未收到新的 Bug、崩溃或回归报告。

- **预防性优化**：PR [#1089](https://github.com/moltis-org/moltis/pull/1089) 通过截断持久化工具结果，可间接规避因历史记录膨胀引发的上下文窗口超限或处理延迟，属于稳定性方向的防御性编程，但尚未合入主分支。

---

### 6. 功能请求与路线图信号

- **可配置化工具日志（高概率纳入）**：Issue [#1092](https://github.com/moltis-org/moltis/issues/1092) 请求的配置开关实现成本较低，且与当前工具链治理主题高度契合。结合 PR [#1089](https://github.com/moltis-org/moltis/pull/1089) 对工具结果处理的全链路重构，可以看出项目正围绕“工具调用可观测性的精细控制”进行主题式迭代。该功能请求具备明确的用户场景（Telegram 生产部署），预计较易被维护者采纳并纳入下一版本路线图。

---

### 7. 用户反馈摘要

从 Issue [#1092](https://github.com/moltis-org/moltis/issues/1092) 可提炼出以下真实痛点：

- **痛点**：在 Telegram 场景中，当 Agent 使用工具后，即使主答案已通过流式编辑（edit-in-place）交付，系统仍可能以单独跟进消息的形式推送 `Activity log`，造成对话流打断和界面冗余。
- **场景**：面向终端用户的生产环境 Bot 部署，开发者希望隐藏底层工具调用痕迹，仅保留对最终用户有价值的回复内容。
- **诉求**：在保留现有调试能力的前提下，通过配置项实现“面向用户的工具状态消息”的按需关闭，以提升渠道适配性与专业感。

---

### 8. 待处理积压

- **PR [#1089](https://github.com/moltis-org/moltis/pull/1089)**：创建于 2026-06-01，已滞留 2 天仍处于待合并状态。该 PR 触及会话历史重新水合的核心逻辑，影响面涵盖流式聊天、压缩重试等关键路径，建议维护者优先安排代码审阅，避免长期挂增加合并冲突风险。
- **Issue [#1092](https://github.com/moltis-org/moltis/issues/1092)**：当日新建，尚未获得维护者或社区的正式回应，建议标记为 `enhancement` 并评估实现排期。

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

**EasyClaw 项目动态日报**  
*日期：2026-06-03 | 分析师：AI 智能体与开源项目研究*

---

### 1. 今日速览

EasyClaw 今日代码仓库表面活跃度处于静默状态，过去 24 小时内无新增 Issues 与 Pull Requests，社区讨论暂时停滞。然而，项目发布流水线保持高频运转，24 小时内连续推送 4 个补丁版本（v1.8.24 → v1.8.27），累计交付 10 余项变更，核心围绕电商店铺数据完整性、桌面端新手体验、OAuth 多店授权可靠性及客服系统稳定性展开。整体健康度评估：开发侧进入「发布窗口期」，社区侧需关注参与度回落风险。  
🔗 [https://github.com/gaoyangz77/easyclaw](https://github.com/gaoyangz77/easyclaw)

---

### 2. 版本发布

今日项目密集发布 4 个补丁版本，均为向后兼容的稳定性与体验优化，无已知破坏性变更。

- **v1.8.27** (最新)
  - **数据完整性修复**：将 `shop-update` 接口中的 `null` 字段视为无操作（no-ops），防止现有电商店铺详情被意外清空。
  - **前后端契约对齐**：确保电商面板在后台 payload 省略可选值时仍保持状态一致。
  - **客服策略放宽**：放宽客服平台 catchup 资格限制，改善恢复路径。
  - 🔗 [https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.27](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.27)

- **v1.8.26**
  - **桌面端体验**：优化桌面欢迎流程与认证入口

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*