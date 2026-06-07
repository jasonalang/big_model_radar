# OpenClaw 生态日报 2026-06-07

> Issues: 296 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-07 03:28 UTC

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

**个人 AI 助手 / 自主智能体开源生态横向对比报告**  
*监测周期：2026-06-07*

---

### 1. 生态全景

当前生态呈现**“高工程吞吐与质量债务并存”**的特征：头部项目单日 PR 量可达 30–50 条，密集推进多 Agent 编排、MCP 工具治理与企业级认证；但普遍面临审阅队列积压（Zeroclaw 45 条待合并、NanoClaw 核心 PR 积压 4–6 周）、E2E 门禁失效（IronClaw）及容器化摩擦（NanoClaw Signal 路径问题）。技术重心正从“单 Agent 功能堆砌”转向**长会话治理、边缘二进制控制与合规审计**，社区诉求明显分化：一端是 ZeptoClaw 代表的亚 MB 级嵌入式部署，另一端是 IronClaw/EasyClaw 指向的企业 SaaS 化与桌面端管理。

---

### 2. 各项目活跃度对比

| 项目 | 新增/活跃 Issues | PR 动态 | Release | 健康度评估 |
|---|---|---|---|---|
| **Zeroclaw** | 38 条更新（24 新开/活跃，14 关闭） | 50 条更新（5 已合并/关闭，45 待合并） | 无 | 🔶 高活跃，审阅队列承压 |
| **PicoClaw** | 10 条新开 | 18 条合并/关闭 | v0.2.9-nightly | 🟢 高吞吐量，防御性修复密集 |
| **IronClaw** | 社区互动为 0 | 30 条更新（10 已合并/关闭，20 待审） | 无（发布 PR 滞留 3 周+） | 🔶 架构重构期，E2E 持续失败 |
| **NanoClaw** | 2 条新开 | 14 条更新（3 已合并，11 待审） | 无 | 🔶 中等活跃，核心 PR 积压 |
| **LobsterAI** | 6 条动态（1 新开，5 历史激活） | 2 条历史 PR 关闭 | 无 | 🔶 中等偏谨慎，Bug 长期积压 |
| **CoPaw** | 11 条更新（9 新开/活跃） | 0 条更新 | 无 | 🔴 问题收集期，v1.1.10 回归缺陷 |
| **Moltis** | 3 条新开 | 2 条更新（待合并） | 无 | 🟢 平稳，待响应 Docker 安全类 Bug |
| **ZeptoClaw** | 2 条更新（1 关闭，1 新开） | 1 条待合并 | 无 | 🟢 精益维护，目标聚焦 |
| **EasyClaw** | 0 | 0 | **v1.8.33** | 🟢 低互动，版本节奏连续 |
| **TinyClaw** | 0 | 0 | 无 | ⚪ 24h 无活动 |
| **NanoBot** | — | — | — | ⚪ 数据未提供 |
| **OpenClaw** | — | — | — | ⚪ 数据未提供（核心参照） |

---

### 3. OpenClaw 在生态中的定位

**本次监测周期内未提供 OpenClaw 当日动态数据，无法量化其当日活跃度与技术进展。** 作为生态“核心参照”，其历史定位大概率占据**通用型个人 AI 助手**的主流生态位。从周边项目的差异化矩阵可反推其潜在竞争边界：

- **vs. Zeroclaw**：Zeroclaw 以 WASM 插件生态、Web 管理后台及 OIDC/OAuth 企业认证为矛，偏向“可扩展平台”；OpenClaw 若保持核心参照地位，可能在开箱即用性与默认体验上占优。
- **vs. ZeptoClaw / PicoClaw**：后两者分别通过二进制体积控制（<7 MB）与 ARM 嵌入式预编译包切入边缘/量化金融硬件场景，与 OpenClaw 的通用云端/桌面定位形成垂直切割。
- **vs. IronClaw**：IronClaw 正以“Reborn”架构推进 OpenAI 兼容层与多租户 SaaS 化，若 OpenClaw 未同步推进企业级租户隔离与审计合规，可能在 B 端集成上落后。

---

### 4. 共同关注的技术方向

以下需求在 **3 个及以上项目**中同步涌现，构成行业级共识：

| 技术方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **MCP 工具生态与治理** | Zeroclaw、IronClaw、NanoClaw、PicoClaw、LobsterAI | Zeroclaw 扩建 MCP Dashboard；IronClaw 落地 Notion MCP 工具包；NanoClaw 推进 HTTP/SSE 传输（#2208）；PicoClaw 实现 Frontmatter 工具策略（allow/deny/glob） |
| **多 Agent 协作与路由** | PicoClaw、IronClaw、LobsterAI、NanoClaw | PicoClaw 探索 Blackboard 共享上下文与 Agent Handoff；IronClaw 设计子代理（subagent）与上下文压缩；LobsterAI 新增多 Agent 任务归属选择器；NanoClaw 讨论 peer-to-peer 通信 |
| **企业级认证与 SSO** | Zeroclaw、IronClaw、Moltis、EasyClaw | Zeroclaw 跟踪 OIDC Provider（#7141）与订阅制 OAuth；IronClaw 修复 TenantId/UserId 反序列化；Moltis 处理 Docker 禁用认证失效；EasyClaw 加固桌面端订阅认证生命周期 |
| **通信通道“零公网”化** | NanoClaw、PicoClaw、Zeroclaw | NanoClaw 将 Slack 全面迁移至 Socket Mode；PicoClaw 升级 Slack 频道级路由过滤器；Zeroclaw 修复 Telegram 流式更新洪水 |
| **长会话与上下文治理** | CoPaw、Moltis、IronClaw、

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
**日期：2026-06-07**

---

### 1. 今日速览

过去 24 小时项目活跃度极高：**50 条 PR 更新**（其中 45 条仍待合并，5 条已合并/关闭），**38 条 Issue 更新**（新开/活跃 24 条，关闭 14 条），无新版本发布。今日核心动能集中在 **WASM 插件生态爆发**（6 个新插件提交 + 3 条插件基础设施 PR）与 **Web 管理后台扩建**（MCP/Skills/Plugins/Providers Dashboard）。同时，维护者关闭了多个高严重级 Bug（含 2 项 S0 级安全/数据风险）。值得注意的是，待合并 PR 积压达 45 条，审阅队列压力显著。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日合并/关闭的关键 PR 主要围绕**安全加固**与**稳定性修复**，推动 v0.8.x 里程碑向稳定态迈进：

- **fix(channels/telegram): clamp zero draft update interval**  
  PR [#7334](https://github.com/zeroclaw-labs/zeroclaw/pull/7334) | 已关闭  
  修复 Telegram 流式更新间隔为 `0` 时导致的编辑洪水问题，回退至默认节流间隔并补充回归测试。

- **fix(policy): stop path guard false-positives on heredoc bodies and non-path tildes**  
  PR [#7281](https://github.com/zeroclaw-labs/zeroclaw/pull/7281) | 已关闭  
  修复安全策略对 heredoc 正文及 `~` 符号的路径误报，避免合法 shell 命令被错误拦截。

- **feat(gateway): per-request agent dispatch for POST /webhook via ?agent=**  
  PR [#7297](https://github.com/zeroclaw-labs/zeroclaw/pull/7297) | 已关闭  
  Webhook 端点现支持通过 `?agent=` 按请求级动态路由至指定 Agent，提升多租户集成灵活性。

此外，以下重要 Issue 已关闭，消除多项生产风险：session/kill 复活已终止会话 [#7252](https://github.com/zeroclaw-labs/zeroclaw/issues/7252)、嵌套 secret 脱敏失败 [#6978](https://github.com/zeroclaw-labs/zeroclaw/issues/6978)、Web UI “Clear all” 仅清前端 [#7126](https://github.com/zeroclaw-labs/zeroclaw/issues/7126)、可观测性 telemetry 泄漏至聊天 WebSocket [#7151](https://github.com/zeroclaw-labs/zeroclaw/issues/7151)、Windows 工具栏加载缓慢与 cmd 弹窗 [#7197](https://github.com/zeroclaw-labs/zeroclaw/issues/7197)、`<tool_calls>` 复数标签解析失败 [#6875](https://github.com/zeroclaw-labs/zeroclaw/issues/6875)。

---

### 4. 社区热点

今日讨论最活跃的议题反映社区对**企业级认证**、**仓库治理**与**国际化工程化**的强烈诉求：

| Issue | 评论 | 核心诉求 |
|-------|------|----------|
| [#5601](https://github.com/zeroclaw-labs/zeroclaw/issues/5601) Add subscription-native OAuth support for Ollama Cloud, z.ai, Kimi, MiniMax | 7 | 用户希望免除静态 API Key 管理，直接通过订阅制 OAuth 登录主流国内与国际模型厂商。该 Issue 已被接受但处于 `blocked` 状态，说明依赖项尚未就绪。 |
| [#7184](https://github.com/zeroclaw-labs/zeroclaw/issues/7184) RFC: Move translated .ftl and .po files into a git submodule | 4 | 翻译文件历史与主仓库解耦，减少翻译更新对核心代码树历史的噪音。 |
| [#6715](https://github.com/zeroclaw-labs/zeroclaw/issues/6715) Delete unneeded branches from main repository | 4 | 仓库已累积 200+ 分支，社区呼吁清理已合并的无用分支以降低维护负担。 |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) OIDC Authentication Provider support | 4 | v0.9.0 跟踪项，要求可插拔 OIDC 认证，是企业 SSO 集成的关键前置。 |
| [#6915](https://github.com/zeroclaw-labs/zeroclaw/issues/6915) skill-scoped tool activation | 3 | 已关闭。社区关注最小权限原则：技能执行期间临时提升工具权限，执行后自动回收。 |

---

### 5. Bug 与稳定性

按严重程度排序的今日 Bug 动态：

**S0 — 数据丢失 / 安全风险**
- **session/kill can rehydrate killed ACP sessions from durable history**  
  Issue [#7252](https://github.com/zeroclaw-labs/zeroclaw/issues/7252) | **已关闭**  
  `session/kill` 仅移除内存中的 ACP 会话， durable history 仍可导致已终止会话被重新水合，存在权限逃逸风险。
- **redact nested secrets in object-array property displays**  
  Issue [#6978](https://github.com/zeroclaw-labs/zeroclaw/issues/6978) | **已关闭**  
  对象数组内的嵌套 `#[secret]` 字段在序列化时未脱敏，导致敏感配置泄露。

**S1 — 工作流阻断**
- **bedrock qwen integration not working on second prompt**  
  Issue [#7312](https://github.com/zeroclaw-labs/zeroclaw/issues/7312) | **Open，暂无 fix PR**  
  使用 Bedrock `qwen.qwen3-coder-next` 时，第二次提示必现“unsupported model”错误，影响连续对话。
- **Tool call parser does not handle `<tool_calls>` (plural) tag**  
  Issue [#6875](https://github.com/zeroclaw-labs/zeroclaw/issues/6875) | **已关闭**  
  Llama 4 Scout 等模型输出复数标签导致工具调用静默失败。

**S2 — 行为降级**
- **Telegram partial streaming accepts zero draft update interval and floods edits**  
  Issue [#7332](https://github.com/zeroclaw-labs/zeroclaw/issues/7332) | **已修复**（PR [#7334](https://github.com/zeroclaw-labs/zeroclaw/pull/7334)）
- **path-policy false-positive on ~ tokens in quoted/heredoc command data**  
  Issue [#7133](https://github.com/zeroclaw-labs/zeroclaw/issues/7133) | **已修复**（PR [#7281](https://github.com/zeroclaw-labs/zeroclaw/pull/7281)）
- **Web UI "Clear all" only wipes rendered messages, not the backend session history**  
  Issue [#7126](https://github.com/zeroclaw-labs/zeroclaw/issues/7126) | **已关闭**
- **Observability tool_call telemetry leaks onto chat WebSocket**

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
**日期：** 2026-06-07  
**仓库：** [sipeed/picoclaw](https://github.com/sipeed/picoclaw)

---

### 1. 今日速览

PicoClaw 在过去 24 小时展现出极高的工程吞吐量：**18 个 PR** 完成合并或关闭，**10 个新 Issue** 开启，并推送了 1 个 Nightly 构建。社区核心贡献者 `@chengzhichao-xydt` 集中提交了大量防御性修复，显著提升了运行时稳定性与资源安全。与此同时，以 `@jcafeitosa` 为代表的社区成员一次性抛出了 9 个围绕 Binance 连接器、Risk Manager 和交易 CLI 的功能 Issue，强烈暗示项目路线图正快速向**量化金融 / 交易 Agent** 场景演进。整体健康度良好，代码合并节奏紧凑，但待处理的国际化 PR 和 Windows 平台 Bug 需要维护者尽快响应。

---

### 2. 版本发布

**Nightly Build: `v0.2.9-nightly.20260607.7d2b0c2a`**  
🔗 [Release 页面](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)

- **性质：** 自动化构建，基于 `main` 分支最新提交 `7d2b0c2a`。
- **稳定性：** 官方明确标注为不稳定版本（*may be unstable*），建议仅用于测试环境。
- **迁移注意：** 无正式 Release Note，若从 `v0.2.9` 升级至该 nightly，需自行查阅 [Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.2.9...main) 确认兼容性。生产环境建议继续停留在 `v0.2.9`。

---

### 3. 项目进展

今日合并/关闭的 16 个 PR 可归纳为三大主线，推动项目在**稳定性、渠道生态和多 Agent 基础设施**上同步前进：

**A. 稳定性与防御性编程（核心进展）**  
- **修复 Goroutine 泄漏：** [#3016](https://github.com/sipeed/picoclaw/pull/3016) 在 `Manager.Reload()` 中确保旧 `dispatchTask` 的 `cancel()` 被调用，防止配置热重载后旧调度协程无限期运行。
- **消除 Panic 风险：** [#3021](https://github.com/sipeed/picoclaw/pull/3021) 对 `GetStartupInfo()` 返回的空 map 增加 `ok` 检查；[#3022](https://github.com/sipeed/picoclaw/pull/3022) 为多处 `sync.Map` 的 `LoadAndDelete` / `Load` 增加类型断言保护；[#3019](https://github.com/sipeed/picoclaw/pull/3019) 修正 WhatsApp 通道的类型切换捕获模式并增加 `nil` guard。
- **资源与 I/O 安全：** [#3017](https://github.com/sipeed/picoclaw/pull/3017) 确保 `io.Copy` 失败时 `base64.Encoder` 仍被关闭；[#3023](https://github.com/sipeed/picoclaw/pull/3023) 在自更新解压路径中显式检查 `Close()` 错误，防止磁盘满或 I/O 错误导致文件静默损坏。

**B. 渠道与模型生态扩展**  
- **新增 Google Chat 支持：** [#830](https://github.com/sipeed/picoclaw/pull/830) 合并，企业协作场景覆盖进一步扩展。
- **DeepSeek 协议修复：** [#1112](https://github.com/sipeed/picoclaw/pull/1112) 为 `modelscope.cn` 上 `deepseek-ai/*` 模型前缀增加协议识别，解决 `unknown protocol` 错误。
- **Slack 体验升级：** [#3020](https://github.com/sipeed/picoclaw/pull/3020) 改进 Slack 工具反馈追踪、消息格式化，并新增频道级 allow/ignore 路由过滤器。

**C. 多 Agent 与工具策略**  
- **多 Agent 协作框架（WIP 关闭）：** [#423](https://github.com/sipeed/picoclaw/pull/423) 虽然以 WIP 状态关闭，但其提出的 Blackboard 共享上下文池、Agent Handoff 和发现工具为后续原生 Agent 间通信奠定了架构参考。
- **Frontmatter 工具策略：** [#2838](https://github.com/sipeed/picoclaw/pull/2838) 让 `AGENT.md` 的 `tools` / `mcpServers` 支持 `allow` / `deny` 策略对象与 glob 模式，实现更细粒度的工具权限管控。

---

### 4. 社区热点

| 条目 | 互动数据 | 链接 | 诉求分析 |
|---|---|---|---|
| **#2625** [CLOSED] WhatsApp 预编译构建支持 | 8 评论, 👍 1 | [Issue](https://github.com/sipeed/picoclaw/issues/2625) | **嵌入式场景痛点**：用户在 Raspberry Pi Zero 2 上使用 PicoClaw，官方 arm64 构建未包含 WhatsApp 支持，导致快速更新困难。社区诉求是**开箱即用的 IoT/ARM 预编译包**。 |
| **#2929** [CLOSED] Agent 对等通信 | 3 评论, 👍 2 | [Issue](https://github.com/sipeed/picoclaw/issues/2929) | **多 Agent 编排诉求**：现有 `spawn` / `delegate` 是主从模式，用户需要真正的 first-class peer-to-peer 通信层来支持协作式工作流。该 Issue 关闭可能意味着需求被 #423 的 WIP PR 覆盖或回炉重造。 |
| **#2935** [OPEN] 繁体中文 (zh-TW) 国际化 | stale, 待合并 | [PR](https://github.com/sipeed/picoclaw/pull/2935) | **华语社区扩张**：包含完整 README、贡献指南与前端 i18n locale，是近期待合并中影响力最大的国际化贡献，但已标记 stale，需维护者 review。 |

---

### 5. Bug 与稳定性

按严重程度排序：

| 严重程度 | 条目 | 状态 | 说明 |
|---|---|---|---|
| **🔴 高** | **#3015** QQ 频道 Windows 构建连接失败 | **无 Fix PR** | Windows 下运行 `picoclaw gateway` 时，QQ 频道在获取 `bots.qq.com` access token 阶段超时，Pico 频道正常。影响 Windows 生产部署。🔗 [Issue](https://github.com/sipeed/picoclaw/issues/3015) |
| **🟡 中** | **#3016** / **#3014** Goroutine 泄漏 (Reload) | ✅ 已修复 | 配置重载导致旧 dispatch goroutine 泄漏，长期运行可能引发内存与连接耗尽。🔗 [#3016](https://github.com/sipeed/picoclaw/pull/3016) |
| **🟡 中** | **#3021** nil agent 引发启动信息 Panic | ✅ 已修复 | `GetStartupInfo()` 返回空 map 时， unchecked 类型断言导致崩溃。🔗 [#3021](https://github.com/sipeed/picoclaw/pull/

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-07*  
*仓库：github.com/nanocoai/nanoclaw*

---

### 1. 今日速览

过去 24 小时，NanoClaw 保持**中等活跃度**：Issues 新增 2 条（均处于开放状态），PR 更新 14 条（3 条已关闭/合并，11 条待审）。社区贡献者在**通信通道稳定性**（Slack、Signal）与**技能库可维护性**方面投入显著，但无新版本发布。值得注意的是，5 月初提交的多个核心运行时修复 PR 至今仍在队列中，合并吞吐量与提交速率之间存在一定落差，可能对长期稳定性构成积压风险。

---

### 3. 项目进展

今日共有 **3 条 PR 关闭/合并**，推动项目在技能工程规范与运行时可靠性上迈出关键一步：

- **#2698** — Skills conformance: exemplars + fleet retrofit  
  作者 @gavrielc 完成了技能库的**可升级维护改造**，确立了技能合规标准（最小化侵入、集成测试、幂等删除 `REMOVE.md`、移除 `VERIFY.md`），为后续核心变更时的技能兼容性奠定基础。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2698

- **#2696** — feat(add-dashboard): make the skill conformant (drift fix + shipped test)  
  作为上述标准的**首个范例**，`/add-dashboard` 技能修复了因核心代码重组导致的静默导入漂移（`src/modules/` 路径变更），并补充了进程内集成测试。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2696

- **#2697** — feat(host): single-instance lock to prevent duplicate messages  
  作者 @simonstudios 通过文件锁机制解决了**双 host 进程并行导致的重复消息投递**问题（如 `pnpm run dev` 与系统服务同时运行），消除了 60 秒扫描周期内的重复容器派生。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2697

---

### 4. 社区热点

今日讨论焦点集中在**通信通道架构迁移**与**容器化边缘场景**：

- **Slack Socket Mode 迁移（#2702 / #2700）**  
  贡献者 @mperraillon 连发两 PR，将 Slack 适配器与 `/add-slack` 技能从**需要公网 URL 的 HTTP Webhook 模式**全面切换至 **Socket Mode**。这显著降低了本地/内网部署的门槛，反映出社区对“开箱即用”通道配置的强烈诉求。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2702  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2700

- **Signal 容器化适配（#2695 / #2694）**  
  @cfis 针对 Signal 通道提交了两项紧密关联的修复：入站图片附件在容器内不可读（主机路径未挂载）、以及入站 DM 因缺少 `isMention`/`isGroup` 标记被静默丢弃。这表明 Signal 作为隐私敏感场景通道，正被用户用于生产环境。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2695  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2694

- **CLI ID 生成规范（#2699）**  
  `ncl groups create` 使用 `crypto.randomUUID()` 生成纯数字开头的 ID，导致 OneCLI 标识符不合法。@mperraillon 的修复要求生成**字母开头**的 ID，反映出 CLI 与容器运行时的接口契约仍需对齐。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2699

---

### 5. Bug 与稳定性

按严重程度排序：

| 严重程度 | Issue/PR | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高（新手阻断） | **#2703** | 推荐安装路径完成后，`cli/local` 实际未连接，但引导界面仍提示用户运行 `pnpm run chat hi`，导致命令挂起 120 秒后超时退出，且无错误提示。 | 无 |
| 🟡 中（边缘崩溃） | **#2701** | `ncl groups restart --rebuild` 在 `packages_apt` 与 `packages_npm` 均为空时抛出 `"No packages to install"` 错误；正常重启可绕过。 | 无 |
| 🟡 中（数据丢失） | **#2694** | Signal 入站 DM 因 `isMention`/`isGroup` 未设置被路由层静默丢弃，用户无感知。 | **#2694**（待合并） |
| 🟡 中（附件失效） | **#2695** | Signal 入站图片附件使用主机绝对路径，容器内无法读取，导致图片消息处理失败。 | **#2695**（待合并） |
| 🟢 低（已修复） | **#2697** | 双 host 进程并发导致消息重复投递。 | 已合并 |

🔗 #2703: https://github.com/nanocoai/nanoclaw/issues/2703  
🔗 #2701: https://github.com/nanocoai/nanoclaw/issues/2701

---

### 6. 功能请求与路线图信号

- **Google Contacts 工具技能（#2693）**  
  @cfis 提交 `/add-google-contacts-tool`，与现有的 `/add-gmail-tool`、`/add-gcal-tool` 形成 Google 办公三件套闭环。该技能采用 bundled stdio MCP 服务器模式，预计将在下一版本中被纳入官方技能库。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2693

- **MCP 传输层扩展（#2208）**  
  支持 HTTP 与 SSE 两种 MCP 服务器传输协议，突破当前仅支持 stdio 的限制。随着 MCP 生态的扩展，该 PR 对集成远程/云端工具链具有战略意义，但自 5 月初提交以来尚未合并。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2208

- **技能可维护性标准化（#2698）**  
  项目正从“快速堆砌技能”转向“可升级维护”的工程化阶段，未来新技能提交可能需要满足测试覆盖与幂等卸载的硬性要求。

---

### 7. 用户反馈摘要

从今日 Issues 中可提炼以下真实痛点：

- **新手体验断裂**：用户严格遵循官方推荐路径安装后，却遭遇“命令挂起 + 无提示”的冷启动失败（#2703），说明安装向导的最终状态检测与后续提示存在脱节。
- **容器化环境摩擦**：Signal 图片路径（#2695）、rootless Podman 用户映射（#2230）等问题显示，用户在非 Docker 标准环境下运行时频繁遇到权限与路径隔离问题。
- **边缘配置脆弱性**：空包配置下的重建命令（#2701）、过期会话的错误投递（#2184）暴露了防御式编程的不足，用户在非理想配置下容易触发硬失败。
- **对通道可靠性的期待**：Slack Socket Mode 与 Signal DM 修复的集中出现，表明用户正将 NanoClaw 部署到需要**稳定双向通信**的生产场景。

---

### 8. 待处理积压

以下 **5 条核心 PR 已提交 4–6 周**，涉及运行时稳定性与扩展性，建议维护者优先审阅：

- **#2184**（2026-05-02）— 会话过期时立即重试，避免向用户投递原始错误消息。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2184

- **#2230**（2026-05-03）— rootless Podman 环境下通过 `keep-id` 正确映射主机用户，解决权限类容器启动失败。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2230

- **#2208**（2026-05-03）— MCP 服务器支持 HTTP/SSE 传输，扩展远程工具链集成能力。  
  🔗 https://github.com/nanocoai/nanoclaw/pull/2208

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
**日期：2026-06-07**  
**仓库：** `nearai/ironclaw`

---

### 1. 今日速览

IronClaw 在过去 24 小时展现出极高的工程活跃度，共有 **30 条 PR 更新**（10 条已合并/关闭，20 条待审阅），核心团队正密集推进代号 **"Reborn"** 的下一代架构落地，涵盖 OpenAI 兼容层、WebUI v2、Slack 频道路由及 Codex 安全门控。然而，社区互动指标处于静默状态（Issues/PR 评论与反应均为 0），且 **Nightly E2E 测试持续失败**，质量门禁与社区参与是当前两大健康度信号。

---

### 2. 版本发布

**无新版本发布。**

但需注意，发布 PR [#3708](https://github.com/nearai/ironclaw/pull/3708) 已滞留逾三周未合并，该 PR 包含 `ironclaw_common` 0.5.0 与 `ironclaw_skills` 0.4.0 等**破坏性 API 变更**，一旦合并将触发主版本跃迁至 **0.29.1**。

---

### 3. 项目进展

今日合并/关闭的关键 PR 推动以下战略方向：

- **Reborn 架构设计定型**  
  PR [#4485](https://github.com/nearai/ironclaw/pull/4485) 与 [#4486](https://github.com/nearai/ironclaw/pull/4486) 合并了子代理（subagent）与上下文压缩（compaction）统一设计文档，引入 `PostCapabilityStage` 作为能力编排与提示词注入之间的单一边界，并伴随**数据库迁移**。

- **CI 治理优化**  
  PR [#4520](https://github.com/nearai/ironclaw/pull/4520) 关闭，实现 Reborn 专属 PR 与遗留测试管道的隔离，通过动态发现 `reborn_*.rs` 测试目标并基于 `pull_request.head.sha` 计算作用域，显著降低遗留 CI 噪音。

- **Codex 安全门控升级**  
  PR [#4508](https://github.com/nearai/ironclaw/pull/4508) 将重复能力调用从"立即终止"改为**两阶段警告门控**，允许模型在触发停止前看到循环控制警告，改善多步推理体验。

- **Slack 集成深化**  
  PR [#4509](https://github.com/nearai/ironclaw/pull/4509) 完成 Slack 频道主题路由（subject routing），支持共享产品路由按频道 ID 解析目标用户，区分 DM 与安装级回退。

- **MCP 生态里程碑**  
  Issue [#3805](https://github.com/nearai/ironclaw/issues/3805) 关闭，**Notion 作为首个具体 MCP 工具包**的能力目录路径已实现。

---

### 4. 社区热点

今日数据集中所有 Issues 与 PR 的**评论数与反应数均为 0**，显示社区互动处于静默期。工程活动高度集中于核心团队（`@serrrfirat`、`@henrypark133`、`@hanakannzashi`），外部贡献者参与度低。

从代码变更规模看，当前最热的工程主题是：
- **Reborn 运行时实现**：PR [#4489](https://github.com/nearai/ironclaw/pull/4489)（OpenAI 兼容层）与 [#4495](https://github.com/nearai/ironclaw/pull/4495)（Chat Completions 路由）
- **WebUI v2 基础设施**：PR [#4519](https://github.com/nearai/ironclaw/pull/4519)（会话能力端点）、[#4516](https://github.com/nearai/ironclaw/pull/4516)（线程删除）

> **诉求分析**：项目正处于"深度重构与架构迁移"阶段，核心团队优先保障 Reborn 架构的端到端闭环，社区尚未在新平台形成规模性反馈。建议维护者通过 GitHub Discussions 或 RFC 流程开启设计评审，激活外部参与。

---

### 5. Bug 与稳定性

| 严重程度 | 事项 | 状态 | 备注 / 修复链接 |
|---|---|---|---|
| 🔴 **高** | Nightly E2E 测试失败 | **开放**，无修复 PR | 扩展 E2E 任务失败，影响扩展功能回归验证。[#4108](https://github.com/nearai/ironclaw/issues/4108) |
| 🟡 **中** | `TenantId`/`UserId` 反序列化拒绝 system sentinel | **待合并** | 导致 LLM 设置端点返回 `service_unavailable`。[#4523](https://github.com/nearai/ironclaw/pull/4523) |
| 🟢 **低** | Reborn PR 污染遗留 CI | **已修复** | 通过作用域分类与动态测试发现解决。[#4520](https://github.com/nearai/ironclaw/pull/4520) |

---

### 6. 功能请求与路线图信号

基于今日 PR 判断，下一版本核心方向已高度明确：

1. **Reborn 运行时成熟化**  
   OpenAI 兼容 API（[#4489](https://github.com/nearai/ironclaw/pull/4489)、[#4495](https://github.com/nearai/ironclaw/pull/4495)）、首次启动配置种子（[#4517](https://github.com/nearai/ironclaw/pull/4517)）、扩展生命周期 E2E 覆盖（[#4518](https://github.com/nearai/ironclaw/pull/4518)）表明 Reborn 正从设计文档进入可运行阶段。

2. **企业集成与多租户 SaaS 化**  
   Slack 频道管理（[#4510](https://github.com/nearai/ironclaw/pull/4510)）、出站投递偏好合约（[#4511](https://github.com/nearai/ironclaw/pull/4511)）、WebUI v2 管理端点（[#4519](https://github.com/nearai/ironclaw/pull/4519)、[#4516](https://github.com/nearai/ironclaw/pull/4516)）指向企业级部署需求。

3. **LLM 基础设施与审计合规**  
   共享工具参数解析原语（[#4522](https://github.com/nearai/ironclaw/pull/4522)，RC3/M9 Phase A）为统一提供商审计（RC1）铺路。

4. **安全与合规基线**  
   运行时 HTTP 敏感头脱敏标记测试（[#3981](https://github.com/nearai/ironclaw/pull/3981)）、本地开发审批门控（[#4186](https://github.com/nearai/ironclaw/pull/4186)）强化安全边界。

---

### 7. 用户反馈摘要

今日数据**未包含终端用户评论或外部 Issue 反馈**。所有更新均为核心团队自驱的工程实现与内部设计文档

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-07 | 数据来源：github.com/netease-youdao/LobsterAI*

---

### 1. 今日速览

过去 24 小时，LobsterAI 社区保持中等活跃度，共产生 6 条 Issue 动态与 2 条 PR 处理记录，无新版本发布。其中，1 条为新开功能建议（[#2120](https://github.com/netease-youdao/LobsterAI/issues/2120)），5 条为历史积压 Issue（含 3 个数据丢失类 Bug、2 个任务执行异常）被重新激活；2 个历史 PR（[#1529](https://github.com/netease-youdao/LobsterAI/pull/1529)、[#1530](https://github.com/netease-youdao/LobsterAI/pull/1530)）于今日关闭，协作与任务调度模块的功能迭代有所推进。整体而言，项目今日未合并新的 Bugfix，核心稳定性问题仍存在长期积压，健康度评估为**中等偏谨慎**。

---

### 3. 项目进展

今日共有 2 个历史 PR 完成处理并关闭，功能方向明确：

- **PR [#1529](https://github.com/netease-youdao/LobsterAI/pull/1529) feat(cowork): 批量模式新增导出功能**  
  在批量操作模式下新增导出按钮，支持将多选会话序列化为结构化 JSON（含会话元数据、消息列表、时间戳等），并通过系统对话框选择保存路径。该功能补全了 cowork 模块的数据可移植性，便于用户离线备份或迁移会话记录。

- **PR [#1530](https://github.com/netease-youdao/LobsterAI/pull/1530) feat(scheduledTask): 多Agent状态下支持新建任务选择归属 Agent**  
  解决了定时任务在多 Agent 场景下“隐式归属 main Agent”导致的感知混乱问题。当已启用 Agent 数量大于 1 时，新建任务界面将显式展示 Agent 选择器，默认选中 main Agent 并允许用户切换，提升了多 Agent 工作流的可控性。

两项 PR 均创建于 2026-04-07，历经约两个月评审周期后于今日关闭，说明项目维护者对协作与任务管理模块的优先级进行了集中清理。

---

### 4. 社区热点

今日讨论焦点集中在**工作流连续性与交互安全性**两大主题：

- **[#2120](https://github.com/netease-youdao/LobsterAI/issues/2120) 建议**（新开，1 条评论）  
  用户 @nbjoe 一次性提出 3 条改进建议：借鉴 WorkBuddy 实现任务预输入（提升连续性）、延长单次任务运行时长（解决数据获取脚本被中断）、以及优化 2560×1600 高分屏下的技能界面布局（双列改三列）。该 Issue 是今日唯一新开议题，直接反映了重度用户在**长时脚本监控**与**高分辨率适配**场景下的痛点。

- **[#1468](https://github.com/netease-youdao/LobsterAI/issues/1468)、[#1469](https://github.com/netease-youdao/LobsterAI/issues/1469)、[#1470](https://github.com/netease-youdao/LobsterAI/issues/1470) 未保存确认系列**（今日同步更新）  
  三个分别针对 Agent 创建弹窗、Agent 设置面板、MCP 服务器配置弹窗的 Bug 报告于今日同时被重新激活。社区对“关闭弹窗即静默丢失内容”这一交互缺陷的关注度持续上升，已形成明确的用户体验债务。

- **[#1495](https://github.com/netease-youdao/LobsterAI/issues/1495) 无缘无故中断进程**（1 👍）  
  是今日唯一获得社区投票（👍）的 Issue，说明任务无故终止问题具有代表性，影响面不仅限于报告者。

---

### 5. Bug 与稳定性

今日无新增 Bugfix PR 合并，以下问题按严重程度排列：

| 严重程度 | Issue | 描述 | 状态 |
|---|---|---|---|
| **严重** | [#1468](https://github.com/netease-youdao/LobsterAI/issues/1468) | Agent 创建弹窗关闭时无未保存确认，系统提示词等内容静默丢失 | OPEN，无 fix PR |
| **严重** | [#1469](https://github.com/netease-youdao/LobsterAI/issues/1469) | Agent 设置面板关闭时无未保存确认，修改后的配置静默丢失 | OPEN，无 fix PR |
| **严重** | [#1470](https://github.com/netease-youdao/LobsterAI/issues/1470) | MCP 服务器配置弹窗关闭或按 Escape 时无未保存确认，环境变量等配置静默丢失 | OPEN，无 fix PR |
| **高** | [#1495](https://github.com/netease-youdao/LobsterAI/issues/1495) | 长时任务（如数据获取脚本监控）无缘无故中断，提示 terminated | OPEN，无 fix PR |
| **中** | [#1496](https://github.com/netease-youdao/LobsterAI/issues/1496) | 任务显示完成，但没有任何返回结果 | OPEN，无 fix PR |

**风险警示**：三个“未保存确认”Bug 均涉及前端 Modal 组件的关闭逻辑，属于低修复成本但高用户伤害的问题，已积压两个月仍未解决；任务中断类问题（#1495、#1496）则直接影响核心执行引擎的可靠性。

---

### 6. 功能请求与路线图信号

结合今日新开 Issue 与近期关闭的 PR，可捕捉到以下产品演进信号：

- **连续型 Multi-Agent 工作流**：[#2120](https://github.com/netease-youdao/LobsterAI/issues/2120) 提出的“任务预输入”与已关闭的 [#1530](https://github.com/netease-youdao/LobsterAI/pull/1530)（多 Agent 任务归属选择）方向一致，说明社区与维护者均在推动**从单任务执行向多任务队列/多 Agent 协作**演进。该需求极有可能被纳入下一版本规划。
- **长时任务与后台监控**：[#2120](https://github.com/netease-youdao/LobsterAI/issues/2120) 建议延长单次任务运行时长，与 [#1495](https://github.com/netease-youdao/LobsterAI/issues/1495) 的任务中断投诉形成共振，暗示当前任务执行存在硬性的超时或保活机制缺陷，亟需引擎层优化。
- **数据可移植性**：[#1529](https://github.com/netease-youdao/LobsterAI/pull/1529) 的批量 JSON

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-07*

---

### 1. 今日速览
Moltis 在过去 24 小时内保持开发活跃度，但无代码合并或版本发布。社区新增 3 条 Issue（含 2 个 Bug、1 个功能请求），2 个进行中的 PR 于今日获得更新但仍在待合并状态。整体项目健康度平稳，不过 Docker 部署安全类 Bug 与 Cron 会话管理问题呈上升趋势，需维护者关注以避免体验恶化。

---

### 2. 版本发布
无。

---

### 3. 项目进展
今日无 PR 合并或关闭记录，代码库未产生实质性主干推进。不过，两个功能 PR 于今日有最新更新，显示开发仍在持续：
- **#1089** – 限制持久化 `tool` / `tool_result` 在会话重新水合（rehydration）时的体积，覆盖常规聊天、流式传输、压缩重试及静默记忆轮次等场景，旨在优化长会话下的上下文窗口管理与 Token 消耗。  
  链接：https://github.com/moltis-org/moltis/pull/1089
- **#1093** – 引入频道活动日志的多级可见性设置（账户级 / 频道级 / 用户级），支持 `all` / `errors_only` / `off` 三档控制，用户级覆盖优先级最高。  
  链接：https://github.com/moltis-org/moltis/pull/1093

---

### 4. 社区热点
过去 24 小时内讨论度最高的是 **Issue #1112**「Docker 环境下禁用认证不生效」，获得 1 条评论，为今日唯一产生互动的条目。该 Issue 反映了部署场景下配置预期与实际行为不一致的安全类问题，表明社区对容器化部署的可靠性关注度较高。其余 Issue 与 PR 暂无新增评论互动。  
链接：https://github.com/moltis-org/moltis/issues/1112

---

### 5. Bug 与稳定性
按严重程度排列，今日待处理的 Bug 如下：

| 严重程度 | Issue | 说明 | Fix PR |
|---|---|---|---|
| **高** | #1112 | Docker 环境中禁用认证（auth）后，系统仍要求身份验证，属于部署安全/配置失效问题。 | 无 |
| **中** | #1111 | 归档（Archive）Cron 会话后前端无可见状态变更，用户无法确认操作是否生效，影响数据管理信心。 | 无 |

- #1112 链接：https://github.com/moltis-org/moltis/issues/1112
- #1111 链接：https://github.com/moltis-org/moltis/issues/1111

---

### 6. 功能请求与路线图信号
1. **Cron 通知抑制关键词（#1110）**  
   用户提议引入类似 `NO_REPLY` 的关键词以静默 Cron 作业通知。该需求与 #1111（归档无反馈）共同指向 Cron 交互体验需要整体优化，目前尚无关联 PR。  
   链接：https://github.com/moltis-org/moltis/issues/1110

2. **频道活动日志可见性控制（#1093）**  
   PR 已提交，支持多粒度权限设置，预计将成为下一版本在合规与通知降噪方面的重要功能。  
   链接：https://github.com/moltis-org/moltis/pull/1093

3. **工具结果持久化上限（#1089）**  
   PR 已提交，通过限制重新水合时的工具内容长度，直接改善长会话性能与成本，具备高优先级合并价值。  
   链接：https://github.com/moltis-org/moltis/pull/1089

---

### 7. 用户反馈摘要
从最新 Issue 可提炼出以下真实痛点与场景：
- **Docker 部署配置黑洞**：用户明确配置禁用认证后仍被拦截，表明容器环境下的配置解析或文档存在缺口，部署体验与预期严重不符。
- **Cron 可观测性不足**：用户既无法直观确认归档操作是否成功（#1111），又希望减少高频 Cron 通知的干扰（#1110），反映出后台任务的状态反馈与通知策略亟需重新设计。
- **通知系统灵活性欠缺**：用户主动提出需要类似 `NO_REPLY` 的约定机制，说明当前“一刀切”的通知模式对自动化场景不够友好。

---

### 8. 待处理积压
目前暂无超长期（数周以上）未响应的 Issue，但以下近期条目已开放数日，建议维护者优先审阅，防止积压影响发布节奏：
- **PR #1089**（创建于 2026-06-01，已开放 7 天）：工具结果限制逻辑涉及核心聊天与流式传输流程，建议尽快 Review 以释放性能优化。  
  链接：https://github.com/moltis-org/moltis/pull/1089
- **PR #1093**（创建于 2026-06-03，已开放 5 天）：频道日志可见性设置涉及权限模型，需确认与现有账户体系的兼容性。  
  链接：https://github.com/moltis-org/moltis/pull/1093
- **Issue #1112**（安全/部署类 Bug）：建议 24 小时内响应并确认复现路径，避免影响 Docker 用户的生产部署。  
  链接：https://github.com/moltis-org/moltis/issues/1112

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw 项目动态日报**  
*日期：2026-06-07 | 数据来源：agentscope-ai/QwenPaw*

---

### 1. 今日速览

今日 CoPaw 社区处于**高活跃、低代码交付**状态：过去 24 小时内共有 11 条 Issue 更新（9 条新开/活跃，2 条关闭），但 Pull Request 零更新，项目处于典型的问题收集期而非代码推进期。需要警惕的是，v1.1.10 版本出现多起回归缺陷，涵盖 Coding Mode 会话切换失效、本地 vLLM 模型无响应及 Windows 路径超限，稳定性面临明显压力；同时，上下文压缩配置不生效的问题仍在持续发酵。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日 **无 PR 合并或关闭**，代码层面零进展。仅有 2 条 Issue 被关闭，均属于用户侧澄清而非代码修复：
- [#4661](https://github.com/agentscope-ai/QwenPaw/issues/4661) 关于 v1.1.8post1 上下文压缩配置未生效的问题，经讨论后关闭；
- [#4984](https://github.com/agentscope-ai/QwenPaw/issues/4984) 用户误以为缺少审批命令，经确认 `/approval approve` 已存在并关闭。

项目整体在功能交付与缺陷修复方面今日未向前推进。

---

### 4. 社区热点

| Issue | 评论数 | 核心诉求 |
|-------|--------|----------|
| [#4937](https://github.com/agentscope-ai/QwenPaw/issues/4937) `/compact` 命令忽略模型 `max_input_length`，仍使用 128K 默认值 | 5 | 要求上下文压缩阈值真正按模型配置生效，而非硬编码 |
| [#466

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

**ZeptoClaw 项目动态日报**  
*日期：2026-06-07 | 数据来源：github.com/qhkm/zeptoclaw*

---

### 1. 今日速览

ZeptoClaw 过去 24 小时保持低频次但高聚焦的维护节奏，围绕「二进制体积控制」这一核心工程目标产生 2 条 Issue 更新与 1 条 PR 更新，整体活跃度平稳。所有更新均来自核心维护者 @qhkm，社区互动指标（评论、Reaction）仍处于低位，显示当前以核心团队内部质量加固为主，外部社区参与有待提升。战略重心明确：通过 CI 门禁将 aarch64 发行体积锁定在 7 MB 以内，巩固「可部署至机器人/边缘设备」的产品护城河。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

- **Issue #612 关闭**：完成了对二进制体积漂移的审计与收敛决策。该 Issue 追溯了自 6.2 MB 低点以来约 800 KB 的体积漂移，并决定将 PR 门禁从 7.5 MB 收紧至 7 MB 战略目标，为后续 CI 策略提供了明确的数值基准。  
  [https://github.com/qhkm/zeptoclaw/issues/612](https://github.com/qhkm/zeptoclaw/issues/612)

- **PR #611 待合并**：该 PR 将 `binary-size` 任务从仅 `push-to-main` 的后置检查提升为「每次 PR 必跑」的门禁，并设定上限阈值。虽然相关审计 Issue #612 已关闭并提出了更严格的 7 MB 目标，但实现基础门禁框架的代码变更仍在等待合并，是今日唯一处于开放状态的关键工程变更。  
  [https://github.com/qhkm/zeptoclaw/pull/611](https://github.com/qhkm/zeptoclaw/pull/611)

---

### 4. 社区热点

今日讨论完全聚焦于 **二进制体积预算与 CI 门禁策略**（#612 / #629 / #611），形成唯一主线。

- **核心诉求**：维护者明确提出「6 MB fits on a robot」的战略定位，强调 aarch64（Pi / Jetson / Apple Silicon）才是真实的机器人部署目标架构；而 x86_64（实际约 10.5 MB）受编码器与链接器客观限制，不能混用同一标准。社区信号表明项目正从功能迭代转向「边缘部署就绪」的硬约束治理。  
  [https://github.com/qhkm/zeptoclaw/issues/629](https://github.com/qhkm/zeptoclaw/issues/629)

---

### 5. Bug 与稳定性

今日无传统崩溃或逻辑 Bug 报告，但存在一项已识别的 **P2-high** 资源回归：

- **二进制体积漂移（约 +800 KB）**  
  **Issue #612** 记录自 6.2 MB 低点以来的体积增长；当前 darwin-arm64 剥离后体积已达 6.98 MB，距离 7 MB 战略红线仅余 21 KB。该审计 Issue 已关闭，但根本性的体积控制需等待 PR #611 合并，并追加 aarch64 专属门禁（见 Issue #629）后方可完全闭环。  
  [https://github.com/qhkm/zeptoclaw/issues/612](https://github.com/qhkm/zeptoclaw/issues/612)

---

### 6. 功能请求与路线图信号

- **架构专属门禁需求（Issue #629）**：新开启的 Issue 明确要求为 aarch64 单独设立 7 MB 的 PR 门禁，将 x86_64 的 ~10.5 MB 现实与 aarch64 的「机器人护城河」解耦。结合已有的 PR #611，预计下一步将先合并通用门禁框架，再追加架构矩阵（aarch64 vs x86_64）的差异化阈值配置。该信号强烈暗示下一版本的发布标准将包含「ARM 边缘设备可部署」的硬门槛。  
  [https://github.com/qhkm/zeptoclaw/issues/629](https://github.com/qhkm/zeptoclaw/issues/629)

---

### 7. 用户反馈摘要

- **痛点**：核心维护者在 Issue 中指出，当前 x86_64 的 release 二进制体积（约 10.5 MB）受工具链客观限制，若强行用同一标准衡量会导致误判；而 aarch64 才是资源受限场景的真实瓶颈。
- **场景**：「Pi / Jetson / Apple Silicon」等机器人/边缘计算平台被反复提及，说明项目的核心使用场景是嵌入式 AI Agent 部署，而非云端服务器。
- **情绪**：对 800 KB 漂移保持高度警觉，对「7 MB 战略红线」有清晰共识，整体工程文化偏向保守与精益。

---

### 8. 待处理积压

- **PR #611**（创建于 2026-06-01，已开放 6 天）：作为二进制体积门禁的基础设施 PR，目前仍处于开放待合并状态。它是后续所有体积治理工作的前置依赖，建议优先审阅合并，以避免 Issue #629 的 aarch64 专属策略落地时产生框架返工。  
  [https://github.com/qhkm/zeptoclaw/pull/611](https://github.com/qhkm/zeptoclaw/pull/611)

- **Issue #629**（创建于 2026-06-06）：刚刚提出，要求补充 aarch64 专属 7 MB 门禁。若维护者认同该战略，建议在 PR #611 合并后尽快跟进，完善多架构 CI 矩阵阈值。  
  [https://github.com/qhkm/zeptoclaw/issues/629](https://github.com/qhkm/zeptoclaw/issues/629)

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

**EasyClaw 项目动态日报**  
**日期：** 2026-06-07  
**仓库：** [gaoyangz77/easyclaw](https://github.com/gaoyangz77/easyclaw)

---

### 1. 今日速览

EasyClaw 在 2026-06-07 呈现“低互动、稳维护”的态势。过去 24 小时内，Issues 与 Pull Requests 均无新增、活跃或关闭记录，社区代码贡献与问题反馈渠道处于静默期。然而，项目发布了 **v1.8.33** 维护版本，聚焦桌面端管理功能加固、认证生命周期修复与验证码登录流稳定，表明核心团队仍在持续推进产品迭代。整体健康度尚可，版本节奏保持连续，但社区活跃度指标偏低，需关注外部贡献者与用户的参与度。

---

### 2. 版本发布

**[v1.8.33 — RivonClaw](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.33)** 已发布。

- **更新内容**
  - **桌面端 Admin 设备控制接入并完成生产清理**：正式接入桌面端管理员设备控制功能，同时移除了调试通道（debug channel）订阅，降低生产环境噪声与潜在安全风险。
  - **修复桌面端订阅认证生命周期**：解决订阅认证生命周期管理缺陷，确保实时更新（live updates）在断连、认证过期或状态切换后能够干净恢复，显著提升长连接稳定性。
  - **稳定验证码登录流与 GraphQL Admin 类型**：对确定性验证码登录流程（deterministic captcha login flows）进行稳定性加固，并刷新自动生成的 GraphQL Admin 类型定义，保证后台 API 契约一致性。

- **破坏性变更**  
  无明显破坏性变更。但需注意：**调试通道订阅已被移除**。若下游集成方或内部工具仍依赖该 debug channel 获取设备状态，升级前需迁移至正式的 Admin 设备控制接口。

- **迁移注意事项**  
  使用了 GraphQL Admin 类型的客户端、SDK 或后台管理工具，建议在升级后重新生成类型定义文件，以匹配最新 Schema；若此前为排查问题启用了 debug channel，请验证生产配置是否已完全切换至正式接口。

---

### 3. 项目进展

今日无合并或关闭的 Pull Requests（[PR 列表](https://github.com/gaoyangz77/easyclaw/pulls)）。v1.8.33 的发布构成了今日的主要进展，该版本将近期完成的桌面端管理功能、认证修复与 GraphQL 类型更新集成至主线并交付。整体而言，项目今日以“质量加固”而非“功能扩张”为主，在桌面端可靠性与企业级认证体验上向前迈进了维护性的一步。

---

### 4. 社区热点

今日 Issues 与 PRs 均无新增评论或互动记录，社区讨论处于静默状态，无热点议题可追踪（[Issues 页面](https://github.com/gaoyangz77/easyclaw/issues) | [PRs 页面](https://github.com/gaoyangz77/easyclaw/pulls)）。建议维护者通过 GitHub Discussions 或外部社区渠道主动发起版本更新解读，以激活用户反馈循环。

---

### 5. Bug 与稳定性

今日无新报告的 Bug、崩溃或回归问题（[Issues 页面](https://github.com/gaoyangz77/easyclaw/issues)）。

值得注意的是，v1.8.33 已修复以下稳定性缺陷：
- **桌面端订阅认证生命周期异常**：此前实时更新在认证状态变化后可能无法干净恢复，导致长连接场景下数据推送中断，该问题已在当前版本修复（[Release v1.8.33](https://github.com/gaoyangz77/easyclaw/releases/tag/v1.8.33)）。
- **验证码登录流非确定性行为**：验证码流程存在偶发性不稳定，影响自动化或高频登录场景，已在当前版本得到加固。

当前仓库无已知严重漏洞或待合并的 fix PR。

---

### 6. 功能请求与路线图信号

今日无新增功能请求 Issue（[Issues 页面](https://github.com/gaoyangz77/easyclaw/issues)）。

从 v1.8.33 的更新方向可提取以下路线图信号：
- **企业级桌面端管理深化**：Admin 设备控制功能的正式接入表明项目正强化 B 端/企业级桌面管理能力，后续可能扩展更多设备策略与远程控制指令。
- **GraphQL 管理后台生态演进**：刷新 GraphQL Admin 类型暗示管理后台 API 层仍在积极迭代，下一版本可能继续围绕 Admin Schema 扩展查询与变更能力。
- **认证体验与安全性平衡**：对 deterministic captcha 登录流的打磨显示核心团队关注无障碍登录与安全的平衡，未来可能在多因素认证（MFA）或会话管理上持续投入。

---

### 7. 用户反馈摘要

今日无新增用户评论或 Issue 反馈（[Issues 页面](https://github.com/gaoyangz77/easyclaw/issues)）。

基于 v1.8.33 的修复内容反推，此前用户或内部测试可能遭遇以下痛点：
- **桌面端实时连接可靠性**：长连接场景下订阅更新偶发中断，且认证恢复过程不够干净，影响实时协作或远程管理体验。
- **验证码登录不稳定**：确定性不足的验证码流程可能导致重复登录失败或自动化测试 flaky。
- **生产环境配置污染**：调试通道与正式功能并存，存在配置管理风险。

建议维护者随版本发布补充简明的迁移指南，帮助用户理解 debug channel 移除的影响及 GraphQL 类型刷新后的客户端适配步骤。

---

### 8. 待处理积压

今日 24 小时数据窗口内无长期未响应的 Issue 或 PR（[Issues](https://github.com/gaoyangz77/easyclaw/issues) | [PRs](https://github.com/gaoyangz77/easyclaw/pull

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*