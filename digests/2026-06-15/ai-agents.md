# OpenClaw 生态日报 2026-06-15

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-15 03:46 UTC

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



---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
**日期：** 2026-06-15  
**仓库：** [HKUDS/nanobot](https://github.com/HKUDS/nanobot)

---

### 1. 今日速览

过去 24 小时，NanoBot 项目保持**极高活跃度**：PR 更新达 **46 条**（已合并/关闭 27 条，待合并 19 条），Issues 更新 5 条（3 条关闭、2 条活跃）。社区在配置系统重构、WebUI 体验对齐、多平台稳定性方面推进迅速，但待审阅 PR 积压至 19 条，合并队列压力值得关注。今日无新版本发布。

---

### 3. 项目进展

今日合并/关闭的 27 条 PR 中，以下变更显著推进了项目核心能力：

**配置与工具系统硬化**
- **#4314** [Break tool config schema import cycle](https://github.com/HKUDS/nanobot/pull/4314)：将共享 Pydantic `Base` 抽离至独立模块，打破工具配置 schema 的导入循环，提升启动稳定性。
- **#4275** [Fail fast on invalid config files](https://github.com/HKUDS/nanobot/pull/4275)：配置文件解析或校验失败时立即报错，避免带着错误配置静默运行。
- **#4138** [Add tools.file.enable to toggle built-in filesystem tools](https://github.com/HKUDS/nanobot/pull/4138)：内置文件系统工具新增 `enable` 开关，满足仅通过 MCP 服务器操作文件的安全部署场景。
- **#4273** [feat(exec): add pathPrepend config](https://github.com/HKUDS/nanobot/pull/4273)：`exec` 工具支持 `pathPrepend`，让指定工具目录优先于系统 `PATH` 解析。

**Agent 核心与调度优化**
- **#4269** [fix(agent): finalize max-iteration turns without tools](https://github.com/HKUDS/nanobot/pull/4269)：当 turn 耗尽 `max_tool_iterations` 时，新增无工具最终化流程，用户可获得明确状态摘要而非仅通用预算提示。
- **#4299** [feat(cron): bind scheduled automations to sessions](https://github.com/HKUDS/nanobot/pull/4299)：定时任务绑定至具体起源会话，解决 `unified_session` 模式下 cron 归属混乱问题。
- **#4274** [Scope prompt recent history by session](https://github.com/HKUDS/nanobot/pull/4274)：非统一模式下，按当前会话过滤 `# Recent History` 提示注入，减少会话间上下文污染。

**平台适配与体验修复**
- **#4339** [Improve WebUI mobile responsiveness](https://github.com/HKUDS/nanobot/pull/4339)：收紧移动端边距、安全区适配，优化侧边栏、Composer 控件与 Token 热力图布局。
- **#4248** [Fix token usage heatmap rendering](https://github.com/HKUDS/nanobot/pull/4248)：对齐热力图日期窗口与 Agent 时区配置，修复月份标签被截断问题。
- **#4277** [fix(feishu): lazy-load lark SDK during gateway startup](https://github.com/HKUDS/nanobot/pull/4277)：飞书通道延迟加载 `lark_oapi` SDK，避免通道发现阶段即初始化重载，提升冷启动性能。
- **#4210** [Fix desktop restart token and replay gaps](https://github.com/HKUDS/nanobot/pull/4210)：修复桌面端原生引擎重启后 WebUI bootstrap/API token 失效问题，并在无 WebSocket 客户端订阅时持久化转录事件，防止刷新后流输出丢失。

**文档与工程规范**
- **#4177** [docs: make onboarding friendlier for beginners](https://github.com/HKUDS/nanobot/pull/4177)：重构文档入口，新增无背景部署、CLI 快速设置、配置任务地图等新手导向内容。
- **#4245** [docs: remove nightly branch guidance](https://github.com/HKUDS/nanobot/pull/4245)：移除已废弃的 nightly 双分支贡献指引，并新增“禁止在功能 PR 中混入机械性格式化变更”的规范。

---

### 4. 社区热点

今日社区焦点集中在**配置系统一致性**与**安全隐私**两大主题：

- **#4345** [Image-strip fallback makes the model act as if it saw an image it never received (and leaks the file path)](https://github.com/HKUDS/nanobot/issues/4345)（今日新建）：用户报告当模型不支持图像输入触发 fallback 时，系统不仅将本地文件路径泄漏给模型，还导致模型产生“幻觉”认为已看到图片。该 Issue 引发对隐私边界的高度关注，社区响应极快，同日即提交修复 PR **#4346**。
- **#4313** [Feat(webui): config.json/webui parity](https://github.com/HKUDS/nanobot/pull/4313)（待合并）：长期呼声最高的“WebUI 与配置文件双向同步”功能进入实现阶段，新增 temperature、tool limits、dream、channels、memory 等字段的写入端点，标志着 NanoBot 从“代码优先配置”向“UI 友好配置”转型。
- **#4344** [Refactor config and agent loop boundaries](https://github.com/HKUDS/nanobot/pull/4344)（待合并）：大规模重构 PR，将工具配置模型迁移至无副作用模块，并抽取 AgentLoop 协调器，反映核心架构正在向更清晰的分层演进。

**背后诉求：** 用户希望降低配置心智负担（UI↔配置一致性），同时对数据隐私与模型幻觉的容忍度极低，要求 fallback 机制必须透明且安全。

---

### 5. Bug 与稳定性

按严重程度排列今日 Bug 与修复状态：

| 严重程度 | 问题 | 状态 |
|---|---|---|
| **🔴 高** | **#4345** 图像 fallback 泄漏本地文件路径并误导模型产生幻觉 | 已有 Fix PR **#4346**（待合并） |
| **🔴 高** | **#4333** Anthropic provider 向 `opus-4-8` / Fable 发送已弃用 `temperature` 参数，导致每次请求返回 400 | 已关闭（通过 PR 修复并合并） |
| **🟡 中** | **#4309** `nanobot serve` 的 OpenAI 兼容端点 `/v1/chat/completions` 始终硬编码返回零 token 使用量，破坏依赖 `usage` 字段的下游计费/监控逻辑 | 开放中（创建于 06-12，最新更新 06-14） |
| **🟡 中** | **#4250** Telegram `split_message` 在围栏代码块（` ``` `）中间截断，导致消息渲染为破碎 HTML | 已关闭 |
| **🟡 中** | **#4343** 内置工具参数校验未遵循 JSON Schema `additionalProperties`，导致拼写错误的未知参数被静默接受而非拒绝 | Fix PR **#4343**（待合并） |
| **🟢 低** | **#4337** Runner 将空注入负载错误追加为空白用户消息，污染对话上下文 | Fix PR **#4337**（待合并） |
| **🟢 低** | **#4293** `process_direct()`（如 cron 任务）缺少 `pending_queue`，导致子 Agent 结果无法在当前 turn 注入，只能压缩进下一轮 | Fix PR **#4293**（待合并） |

---

### 6. 功能请求与路线图信号

结合待合并 PR 与近期 Issue，以下方向极可能纳入下一版本：

- **配置体验统一化**：**#4313**（WebUI ↔ config.json 双向同步）已进入实现阶段，是解决“配置漂移”用户痛点的标志性功能。
- **自动化管理可视化**：**#4330** [feat(webui): add automation management view](https://github.com/HKUDS/nanobot/pull/4330) 提供自动化的列表、过滤、运行、暂停/恢复与删除界面，配合 **#4299** 的会话绑定能力，表明 cron/自动化正从“后台黑盒”走向“前台可管可控”。
- **Agent 执行边界细化**：**#4344** 重构配置与 Agent 循环边界，**#4269** 完善 max-iteration 收尾逻辑，显示核心 Agent 运行时正从“功能可用”向“行为可预测”演进。
- **安全加固**：**#4346** 与 **#4343** 分别堵住隐私泄漏与参数校验漏洞，安全与合规将成为近期重点。

---

### 7. 用户反馈摘要

从今日 Issues 与 PR 摘要中提炼的真实用户声音：

- **API 兼容性痛点**：OpenAI 兼容端点返回虚假零 token（#4309），直接影响基于 `usage` 做成本监控或限流的下游系统，用户呼吁尽快补齐真实用量统计。
- **隐私零容忍**：图像 fallback 机制将本地绝对路径暴露给 LLM（#4345），用户明确将此视为安全漏洞而非体验瑕疵。
- **多平台稳定性诉求**：Telegram 长消息分割、Anthropic 新模型（`opus-4-8`）参数兼容性、飞书 SDK 启动性能等问题显示用户正在将 NanoBot 部署到生产级多通道环境。
- **配置管理焦虑**：新手抱怨入门路径混乱（#4177 已响应），进阶用户则苦于 WebUI 与 `config.json` 不同步（#4313 待合并），两端体验均需提升。
- **移动端刚需**：WebUI 在移动设备上的溢出与布局问题（#4339）被主动修复，反映用户有强烈的移动场景使用需求。

---

### 8. 待处理积压

以下 Issue/PR 已开放

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目动态日报**  
**日期：** 2026-06-15  
**仓库：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)

---

### 1. 今日速览

过去 24 小时项目维持极高社区活跃度：Issues 更新 42 条（关闭 28，活跃/新开 14），PR 更新 50 条，但代码审查瓶颈显著——仅 4 条 PR 完成合并或关闭，46 条仍处于待审状态。今日无新版本发布。生态集成出现“爆发式”落地，单日关闭 14 个 Provider 与 Tool 集成 Issue，涵盖 SMS 网关、智能家居与音乐服务；与此同时，安全与核心运行时的 Bug 受到集中关注，其中邮件通道配置错误（S0 级）与 Delegate 多 Agent 权限问题（S1 级）成为稳定性焦点。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

**已合并/关闭的关键 PR：**

- **[#7664](https://github.com/zeroclaw-labs/zeroclaw/pull/7664)** — 修复网关 Web 中 `ask_user` 因通道提前关闭而立即失败的 Bug（[#7542](https://github.com/zeroclaw-labs/zeroclaw/issues/7542)），恢复了人机协作工作流的可用性。
- **[#7384](https://github.com/zeroclaw-labs/zeroclaw/pull/7384)** — 为定时任务（Cron）Dashboard 增加暂停/恢复开关，补齐了数据模型已支持但前端缺失的核心运维能力。
- **[#7594](https://github.com/zeroclaw-labs/zeroclaw/pull/7594)** — 超大体积（XL）配置系统重构“类型驱动别名选择器与自声明配置枚举”关闭，虽未最终合并，但推动了配置层去硬编码化的技术路线讨论。

**已关闭的重要 Issues（功能落地）：**

- **基础设施与文档：** 本地 CA 证书支持（[#1458](https://github.com/zeroclaw-labs/zeroclaw/issues/1458)）、邮件通道危险配置逻辑（[#5528](https://github.com/zeroclaw-labs/zeroclaw/issues/5528)）、WhatsApp QR 码不显示（[#6847](https://github.com/zeroclaw-labs/zeroclaw/issues/6847)）、Docker 文档更新（[#6760](https://github.com/zeroclaw-labs/zeroclaw/issues/6760)）。
- **模型提供商生态：** 新增 Arcee AI（[#6456](https://github.com/zeroclaw-labs/zeroclaw/issues/6456)）、Inception Labs Mercury（[#6458](https://github.com/zeroclaw-labs/zeroclaw/issues/6458)）、Lambda AI（[#6457](https://github.com/zeroclaw-labs/zeroclaw/issues/6457)）、Featherless AI（[#6455](https://github.com/zeroclaw-labs/zeroclaw/issues/6455)）、Upstage Solar（[#6454](https://github.com/zeroclaw-labs/zeroclaw/issues/6454)）。
- **通道与工具生态：** Vonage（[#6494](https://github.com/zeroclaw-labs/zeroclaw/issues/6494)）、Sinch（[#6452](https://github.com/zeroclaw-labs/zeroclaw/issues/6452)）、Plivo（[#6453](https://github.com/zeroclaw-labs/zeroclaw/issues/6453)）、Telnyx（[#6451](https://github.com/zeroclaw-labs/zeroclaw/issues/6451)）四大 SMS 网关；Sonos（[#6477](https://github.com/zeroclaw-labs/zeroclaw/issues/6477)）、Spotify（[#6475](https://github.com/zeroclaw-labs/zeroclaw/issues/6475)）、Shazam（[#6476](https://github.com/zeroclaw-labs/zeroclaw/issues/6476)）、8Sleep（[#6450](https://github.com/zeroclaw-labs/zeroclaw/issues/6450)）、Philips Hue（[#6449](https://github.com/zeroclaw-labs/zeroclaw/issues/6449)）等智能家居与音乐工具。

---

### 4. 社区热点

| 议题 | 状态 | 评论 | 核心诉求 |
|------|------|------|----------|
| **[#3642](https://github.com/zeroclaw-labs/zeroclaw/issues/3642)** Provide a "full" docker image | 已关闭 | 13 | 非技术用户入门门槛：默认编译关闭 WhatsApp 等功能以降低内存，但导致新手难以获得开箱即用体验。 |
| **[#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)** RFC: Work Lanes, Board Automation, and Label Cleanup | 开放 | 11 | 治理层减负：维护者不愿再维护手动路由系统，寻求轻量级 PR 泳道与自动化标签机制。 |
| **[#7470](https://github.com/zeroclaw-labs/zeroclaw/issues/7470)** delegate agentic mode rejects empty risk_profile | 开放 | 7 | 多 Agent 协作受阻：reviewer/research 类多 Agent 场景因空 `allowed_tools` 和同 profile 门控而无法实际运行。 |
| **[#6293](https://github.com/zeroclaw-labs/zeroclaw/issues/6293)** RFC: Air-gapped execution mode | 开放 | 5 | 高安全/企业场景：要求将 ZeroClaw 拆分为离线 Agent 容器与在线 Companion Daemon，通过 Unix Socket 通信，实现气隙与 enclave 支持。 |

---

### 5. Bug 与稳定性

按严重程度排序：

- **S0 — 数据丢失/安全风险**
  - **[#5528](https://github.com/zeroclaw-labs/zeroclaw/issues/5528)** `[CLOSED]` 邮件通道 IMAP/SMTP 配置逻辑错误，可能导致错误 TLS 配置或数据风险。已修复关闭。
- **S1 — 工作流阻塞**
  - **[#7470](https://github.com/zeroclaw-labs/zeroclaw/issues/7470)** `[OPEN]` Delegate 工具在目标 Agent 为 agentic 模式且 `risk_profile.allowed_tools` 为空时拒绝委托，同时同 profile 门控阻止更严格的委托目标。多 Agent 审查场景被完全阻塞。**尚无明确 fix PR。**
  - **[#7664](https://github.com/zeroclaw-labs/zeroclaw/pull/7664)** `[CLOSED]` 网关 Web 中 `ask_user` 因通道关闭立即失败。已合并修复。
  - **[#5527](https://github.com/zeroclaw-labs/zeroclaw/issues/5527)** `[CLOSED]` Gemini OAuth 加载项目上下文解析失败。已关闭。
- **S2 — 行为降级**
  - **[#6856](https://github.com/zeroclaw-labs/zeroclaw/issues/6856)** `[OPEN]` Schema v3 中 Channel 缺失 `show_tool_calls` 选项，导致工具调用详情无法展示。
  - **[#5662](https://github.com/zeroclaw-labs/zeroclaw/issues/5662)** `[OPEN]` QQ 频道语音消息被重复处理 20+ 次，导致 `brain.db` 出现大量重复条目。
- **高安全/高严重待审 PR**
  - **[#7424](https://github.com/zeroclaw-labs/zeroclaw/pull/7424)** `[OPEN]` `web_fetch.allowed_private_hosts = ["*"]` 未正确覆盖 DNS 解析后的私有主机，存在 SSRF 绕过风险。
  - **[#5892](https://github.com/zeroclaw-labs/zeroclaw/pull/5892)** `[OPEN]` 生产阻塞：空 `tool_choice` 与孤立 `tool

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-15 | 数据来源：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

过去 24 小时 NanoClaw 核心仓库活跃度极高，共更新 **7 条 Issues** 与 **10 条 PRs**，无新版本发布。当日最大焦点是安全研究员集中披露的 **3 个高危漏洞**（审批绕过、本地文件外泄、隐藏参数持久化），对 agent self-modification 与本地网关的信任边界构成严峻挑战。与此同时，项目架构取得关键进展：操作员驱动的 Provider 选择与记忆迁移、Codex Payload V2、容器 CLI 数据驱动安装均成功合入主干，标志着 NanoClaw 正从单一模型托管向多 Provider Agent 平台加速演进。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

以下 PR 已合并/关闭，推动核心架构与文档向前迈进：

- **#2756** `feat(providers): operator-driven provider selection, switching, and memory migration` [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2756)  
  将 agent provider 转变为显式操作员选择属性，合入 provider 注册表、安装向导、vault 认证流程及记忆迁移能力，为多云/多模型架构奠定基础设施。

- **#2757** `feat(codex): Codex agent-provider payload v2 — app-server on capability seams, vault-only auth` [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2757)  
  Codex 升级为完整的 agent provider，基于主机 capability seams 运行，并通过 OneCLI vault 独占认证，重构了远程 agent 托管与授权模型。

- **#2758** `feat(container): data-drive global CLI installs from cli-tools.json` [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2758)  
  全局 Node CLI（`claude-code`、`agent-browser`、`vercel` 等）的安装逻辑从 Dockerfile 硬编码迁移至 `cli-tools.json` 数据清单，容器构建的可维护性与技能扩展性显著提升。

- **#2764 / #2769** 文档修复 [→ #2764 链接](https://github.com/nanocoai/nanoclaw/pull/2764) | [→ #2769 链接](https://github.com/nanocoai/nanoclaw/pull/2769)  
  修复 `CLAUDE.md` 中已迁移文件的路径引用，并补充 `/add-codex` 交互式认证与 host-restart 步骤说明，改善 AI 辅助开发与 onboarding 体验。

---

### 4. 社区热点

今日所有 Issues/PRs 的评论数与反应数均为 0，但提交密度与主题严重性表明社区注意力高度集中在以下方向：

- **安全披露三连发（#2762 / #2761 / #2760）** [→ #2762](https://github.com/nanocoai/nanoclaw/issues/2762) | [→ #2761](https://github.com/nanocoai/nanoclaw/issues/2761) | [→ #2760](https://github.com/nanocoai/nanoclaw/issues/2760)  
  安全研究员 `@YLChen-007` 于同日提交三份安全报告，直指审批流、本地网关和文件传输的严重缺陷。这反映出外部安全社区对 NanoClaw 作为“可自我修改的 AI Agent 平台”的高度关注，也暴露出现有沙箱与审批透明度的不足。

- **Provider 架构重构（#2756）** [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2756)  
  该架构级合并标志着项目从“Claude-centric”向可插拔 Provider 生态转型，记忆迁移与统一 vault 认证将成为后续版本的核心叙事。

- **Codex 深度集成（#2757 / #2770）** [→ #2757](https://github.com/nanocoai/nanoclaw/pull/2757) | [→ #2770](https://github.com/nanocoai/nanoclaw/pull/2770)  
  Codex Payload V2 合入后，配套的文件事件传递修复（#2770）迅速跟进，显示核心贡献者正全力保障多 Provider 并行的功能完整性。

---

### 5. Bug 与稳定性

按严重程度排列：

| 严重程度 | 事项 | 状态 |
|---|---|---|
| 🔴 **Critical** | **#2762** [Security] `add_mcp_server` 审批流允许隐藏的 `args` 与 `env` 在未经展示的情况下被持久化 [→ 链接](https://github.com/nanocoai/nanoclaw/issues/2762) | 尚无 fix PR |
| 🔴 **Critical** | **#2761** [Security] 本地网关通过未认证的 loopback webhook 绕过审批 [→ 链接](https://github.com/nanocoai/nanoclaw/issues/2761) | 尚无 fix PR |
| 🔴 **Critical** | **#2760** [Security] `send_file` 通过绝对路径处理导致任意本地文件外泄 [→ 链接](https://github.com/nanocoai/nanoclaw/issues/2760) | 尚无 fix PR |
| 🟡 **High** | **#2751** LLM 预算耗尽时 turn 被静默丢弃，用户无感知 [→ 链接](https://github.com/nanocoai/nanoclaw/issues/2751) | **Fix PR #2759** 已提交待审 [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2759) |
| 🟡 **Medium** | **#2770** Codex 图像生成的 `file` 事件未被消费，导致文件丢失且破坏 TypeScript 编译 [→ 链接](https://github.com/nanocoai/nanoclaw/pull/2770

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI 项目动态日报 | 2026-06-15

## 1. 今日速览
过去 24 小时，LobsterAI 项目活跃度偏低，**无新增 Issue/PR，无版本发布**。社区活动主要表现为对历史积压项的“唤醒”——共计 6 条创建于 4 月初的 `[stale]` 条目（2 Issue + 4 PR）在沉寂两个月后于昨日被同步更新，暗示维护者可能正在启动一轮存量清理。代码层面仅 **1 个修复型 PR 完成关闭**，3 个功能增强型 PR 仍滞留待合并。整体健康度评估：**维护节奏缓慢，社区贡献存在明显积压，但核心模块的稳定性缺陷今日得到一处关键修复**。

---

## 2. 版本发布
（无新版本发布）

---

## 3. 项目进展

**已关闭 / 已合并**
- **#1465** `fix(scheduled-tasks): 已删除的定时任务重启后作为幽灵会话重新出现` [→ 查看](https://github.com/netease-youdao/LobsterAI/pull/1465)
  - 作者 @linlihua 定位并修复了定时任务删除流程中的数据清理缺口：此前仅移除了网关侧 `cron` 记录，但未清理本地 SQLite `cowork_sessions` 表，导致重启后幽灵会话反复出现。该 PR 的关闭消除了任务调度模块的持久化层数据不一致隐患，提升了长周期任务管理的可靠性。

**待合并（3 个功能增强）**
- **#1429** `feat(cowork): add in-session message search with mark.js highlighting` [→ 查看](https://github.com/netease-youdao/LobsterAI/pull/1429)
- **#1430** `feat(cowork): 会话运行期间自动阻止系统休眠` [→ 查看](https://github.com/netease-youdao/LobsterAI/pull/1430)
- **#1431** `feat(cowork): StreamingActivityBar 右侧显示会话运行计时器` [→ 查看](https://github.com/netease-youdao/LobsterAI/pull/1431)

> 上述三个 Cowork 会话体验增强 PR 均处于 Open 状态，尚未进入主分支，但已形成“可检索 → 可观测 → 防中断”的完整体验闭环。

---

## 4. 社区热点

今日社区焦点集中在 **2 个重新激活的 UI/UX Issue** 与 **3 个 Cowork 功能 PR** 上：

- **#1434** `龙虾的语言为中文时，在我的agent里，选择一个agent，在技能tab页，搜索没数据时，展示了英文提示，按钮也是英文的` [→ 查看](https://github.com/netease-youdao/LobsterAI/issues/1434)
  - **核心诉求**：中文环境下的国际化（i18n）覆盖存在断层，空状态提示存在英文硬编码，直接破坏中文用户的沉浸感。该 Issue 今日新增评论并被重新激活。

- **#1435** `新建自定义agent时，名称过长直接超出弹框，展示不友好` [→ 查看](https://github.com/netease-youdao/LobsterAI/issues/1435)
  - **核心诉求**：表单输入缺乏边界校验与自适应布局，长文本直接破坏弹窗排版，属于基础体验瑕疵。

- **Cowork 体验三连 PR（#1429 / #1430 / #1431）**
  - **背后信号**：社区贡献者对长时间运行 Agent 任务的**可观测性**（实时计时器、会话内搜索）和**可靠性**（系统防休眠）存在强烈且系统性的需求。三个 PR 由不同开发者提交但目标高度一致，反映出该场景是当前用户痛点最集中的领域。

---

## 5. Bug 与稳定性

| 严重程度 | 问题描述 | 状态 | Fix PR |
|---------|---------|------|--------|
| 🔴 中-高 | **幽灵会话回归**：定时任务删除后，本地 SQLite 记录残留，重启后反复出现空会话 | ✅ 已关闭 | [#1465](https://github.com/netease-youdao/LobsterAI/pull/1465) |
| 🟡 中 | **国际化缺失**：中文环境下 Agent 技能 Tab 搜索无结果时，提示文案与按钮为英文 | ⏳ Open | 无 |
| 🟡 中 | **UI 溢出**：新建自定义 Agent 时名称过长，文本直接超出弹框边界 | ⏳ Open | 无 |

- **#1465** 的关闭消除了定时任务模块的一个关键数据一致性隐患，避免了用户因“删不掉的任务”而对调度系统产生不信任。
- **#1434 / #1435** 虽非崩溃级缺陷，但均属于高频交互路径上的体验债务，且修复成本较低，建议优先纳入补丁迭代。

---

## 6. 功能请求与路线图信号

基于今日活跃的 PR 与 Issue，下一版本（或下一迭代主题）可能优先纳入以下方向：

1. **Cowork 长时间任务体验套件**（高置信度）
   - **#1430**（防休眠）+ **#1431**（计时器）+ **#1429**（会话内搜索）三者共同补齐了长会话的**可靠性、可观测性与可检索性**。这三个 PR 代码目标聚焦、相互独立但场景互补，极可能以“Cowork 体验增强”主题被批量 review 并合入。
   
2. **国际化与 UI 边界治理**（中置信度）
   - **#1434** 和 **#1435** 暴露了前端基础体验的债务。若维护者计划进行一轮体验打磨，这两个 Issue 的修复成本低、用户感知度高，适合作为补丁版本内容或标记为 `good-first-issue` 吸引社区贡献。

---

## 7. 用户反馈摘要

从 Issues 与 PR 背景中提炼的真实用户痛点与场景：

- **本地化断层**：中文用户在使用核心功能（Agent 技能搜索）时遭遇英文空状态提示，造成明显的语言

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-15 | 项目：github.com/moltis-org/moltis*

---

### 1. 今日速览

Moltis 在过去 24 小时内整体活跃度处于低位。社区仅新增 **1 条 Enhancement 类 Issue**，无 Pull Request 创建、合并或审查活动，亦无新版本发布。代码层面处于静止状态，项目进入典型的维护平静期。尽管如此，新提交的功能请求表明社区仍在关注极端边缘场景下的性能与架构优化方向。

---

### 2. 版本发布

今日无新版本发布，本节略。

---

### 3. 项目进展

今日无已合并或关闭的 Pull Request，代码库未发生实质性功能推进或缺陷修复。主分支处于稳定挂起状态，核心模块暂无新增提交。

---

### 4. 社区热点

今日唯一社区动态来自新创建的功能请求：

- **Issue #1123** — [Feature]: Add pure-Rust turbovec as an alternative memory backend for extreme edge compression  
  链接：https://github.com/moltis-org/moltis/issues/1123  
  作者：@joeblew999 | 状态：Open | 评论：0 | 👍：0

**诉求分析：**  
该 Issue 提出为“极端边缘压缩”场景引入纯 Rust 实现的 `turbovec` 作为替代内存后端。提出者已完成预检清单（Preflight Checklist）并附带了会话上下文，说明需求来源于实际使用场景。当前 0 评论、0 反应，表明该想法尚处于早期播种阶段。其背后核心诉求可能是：用户对现有内存后端在资源受限边缘设备上的压缩效率、FFI 依赖或二进制体积存在顾虑，希望通过纯 Rust 方案提升可移植性与内存安全性。

---

### 5. Bug 与稳定性

过去 24 小时内 **未报告新的 Bug、崩溃或回归问题**。Issues 列表中无 `bug`、`crash`、`regression` 标签的新增条目，项目稳定性层面无新增风险信号。

---

### 6. 功能请求与路线图信号

今日唯一的功能信号来自 **Issue #1123**（https://github.com/moltis-org/moltis/issues/1123）。这是一个**架构扩展级别**的提案，涉及内存管理抽象层的改造，目标场景为极端边缘计算（embedded / IoT / 边缘 AI 推理）。

**纳入评估：**  
- 目前**无关联 PR**，且处于开放讨论初期，短期内直接进入主线的可能性较低。  
- 若项目当前已具备内存后端插件化或 trait 抽象设计，该功能的实现成本将显著降低，具备纳入后续次要版本（minor release）的技术可行性。  
- 建议维护者评估其与现有压缩管线的兼容性，以及对“纯 Rust 生态”这一差异化卖点的战略价值。

---

### 7. 用户反馈摘要

基于今日有限的 Issue 数据，可提炼以下真实信号：

| 维度 | 内容 |
|------|------|
| **痛点** | 用户关注极端边缘环境下的压缩性能与内存占用，暗示当前后端在该场景下可能存在瓶颈、依赖过重（如 C/C++ FFI）或二进制体积问题。 |
| **使用场景** | 提出者明确指向 *"extreme edge compression"*，表明 Moltis 可能被用于资源高度受限的嵌入式设备或边缘 AI 智能体场景。 |
| **社区情绪** | 评论数为 0，尚无法判断更广泛社区的共鸣程度；但提出者遵循了 Preflight Checklist 并声明包含会话上下文，说明需求具备一定真实性，非重复噪音。 |

---

### 8. 待处理积压

- **Issue #1123**（https://github.com/moltis-org/moltis/issues/1123）于 2026-06-14 创建，目前**尚未获得维护者或社区任何回复**。作为过去 24 小时内唯一的活跃 Issue，建议维护者在近期给予初步技术反馈（如询问接口设计思路或指出与现有后端的差异），避免新功能请求在提出初期即陷入零回复沉默，从而降低贡献者流失风险。

---

*日报生成依据：过去 24 小时 GitHub Issues/PRs/Release 公开数据。*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw 项目动态日报**  
**日期：** 2026-06-15  
**仓库：** agentscope-ai/QwenPaw  

---

### 1. 今日速览

过去 24 小时，CoPaw 社区保持高活跃度，共产生 **21 条 Issue 更新**（17 条新开/活跃，4 条关闭）与 **16 条 PR 更新**（11 条待合并，5 条已合并/关闭），无新版本发布。当前社区焦点集中在 **v1.1.11.post2 版本的回归问题**（本地模型显示异常、Gemini tool calling 失效、插件安装弹窗死循环）、**桌面端 Tauri 迁移后的稳定性**以及**多语言/多渠道生态扩展**（越南语、Zalo、Kimi 接入）。首次贡献者持续涌入，国际化与插件系统成为近期主要增长极，但 post2 版本引入的多项回归对生产环境用户造成了明显困扰。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日共有 **5 条 PR 已合并或关闭**，核心修复与调整如下：

- **[#5051](https://github.com/agentscope-ai/QwenPaw/pull/5051)** `fix(desktop): persist backend port across restarts to preserve localStorage`  
  修复了 Windows 桌面端每次重启后智能体选择重置为默认（CloudPaw-Master）的问题。根因在于 Tauri 桌面端每次启动随机分配后端端口，导致 `localStorage` 因同源策略隔离而失效。该合并直接关闭了用户长期反馈的 [#4733](https://github.com/agentscope-ai/QwenPaw/issues/4733)。

- **[#5035](https://github.com/agentscope-ai/QwenPaw/pull/5035)** `fix(local_models): parse llama.cpp server version without fixed-width slice`  
  修复了 llama.cpp 后端版本号解析硬编码 `line[9:13]` 的问题。随着 llama.cpp 构建号突破 4 位（当前约 8514），固定宽度切片会导致版本检测静默失败，该修复保障了本地模型后端的长期兼容性。

- **[#5038](https://github.com/agentscope-ai/QwenPaw/pull/5038)** `fix(context): guard empty msg list in LightContextManager.pre_reply`  
  修复了 `LightContextManager.pre_reply()` 在处理空消息列表时触发 `IndexError` 的边界情况，提升了上下文管理的健壮性。

- **[#5188](https://github.com/agentscope-ai/QwenPaw/pull/5188)** `Request payload transforms`（已关闭）  
  为前端插件暴露了请求负载转换钩子，允许通过 SDK 注册转换函数，虽已关闭但体现了控制台插件化架构的持续推进。

- **[#5092](https://github.com/agentscope-ai/QwenPaw/pull/5092)** `Revert "fix(pack): compile-check discord after conda-unpack"`（已关闭）  
  回滚了引发问题的 conda-unpack 后 discord 编译检查，避免打包流程回归。

---

### 4. 社区热点

今日讨论最活跃、评论数最高的议题反映了用户对**桌面端性能**与**第三方生态接入**的强烈关注：

- **[#5156](https://github.com/agentscope-ai/QwenPaw/issues/5156)** `[Feature]: 建议支持 kimi-for-coding / 加入 uv 白名单`（5 条评论，OPEN）  
  用户诉求：已订阅 Kimi Coding 套餐的用户无法将套餐能力接入 CoPaw，只能走官方 API。该 Issue 揭示了社区对**订阅制第三方模型灵活接入**的迫切需求，涉及 uv 白名单机制与商业模型授权模式的兼容性设计。

- **[#5047](https://github.com/agentscope-ai/QwenPaw/issues/5047)** `[Question]: Windows Tauri 桌面端启动特别慢`（5 条评论，CLOSED）  
  用户反馈从 Python 打包迁移至 Tauri 后，启动时间从 1–2 分钟恶化至十几分钟，且频繁无响应。该 Issue 已被关闭，但反映出桌面端架构迁移带来的性能阵痛仍在持续影响用户体验。

- **[#5009](https://github.com/agentscope-ai/QwenPaw/issues/5009)** `[Question]: 是否有路线图集成 Langfuse / OpenTelemetry`（3 条评论，CLOSED）  
  企业级用户关注 LLM 可观测性（token 用量、分布式追踪、延迟拆解、成本归因）。该 Issue 被关闭，暗示当前官方对可观测性平台的原生集成尚无明确时间表，可能成为企业采纳的阻碍。

---

### 5. Bug 与稳定性

今日报告的 Bug 按严重程度排列如下，**v1.1.11.post2 成为回归重灾区**：

| 严重程度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| **🔴 高** | [#5181](https://github.com/agentscope-ai/QwenPaw/issues/5181) | **插件依赖安装死循环弹窗**：v1.1.11.post2 启动插件时自动 `pip install` 依赖，网络异常时失败重试并持续弹出可见 cmd 窗口，严重影响桌面使用。 | 无 |
| **🔴 高** | [#5163](https://github.com/agentscope-ai/QwenPaw/issues/5163) | **Gemini tool calling 回归**：v1.1.10 正常，v1.1.11.post2 中 Gemini 模型无法正常调用内置工具。 | 无 |
| **🔴 高** | [#5184](https://github.com/agentscope-ai/QwenPaw/issues/5184) | **本地模型提供商不显示**：v1.1.11.post2 中创建的本地模型提供商在设置中无法正确显示。 | 无 |
| **🟡 中** | [#5190](https://github.com/agentscope-ai/QwenPaw/issues/5190) | **企业微信审批入口缺失**：开启私聊访问控制后，用户触发审批但 Web 控制台与企业微信端均找不到审批界面。 | 无 |
| **🟡 中** | [#5166](https://github.com/agentscope-ai/QwenPaw/issues/5166) | **Python 3.13 兼容性**：安装 TeamChat 插件失败，因 `imghdr` 模块在 Python 3.13 中已被移除。 | 无 |
| **🟡 中** | [#5161](https://github.com/agentscope-ai/QwenPaw/issues/5161) | **长对话无响应**：单会话轮数过多或上下文过长后，CoPaw 卡住不再回复。

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