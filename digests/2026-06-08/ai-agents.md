# OpenClaw 生态日报 2026-06-08

> Issues: 295 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-08 03:34 UTC

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
*报告日期：2026-06-08*

---

### 1. 生态全景

当前生态呈现显著的**“头部高速迭代、腰部维护巩固、长尾大量沉寂”**的分化格局。Zeroclaw 与 IronClaw 以日均 50 级 Issues/PRs 的吞吐量推动全渠道网关、企业级工作流架构和终端体验升级，而 LobsterAI、Moltis 等项目已进入低代码动量的维护期，另有超过半数追踪项目（TinyClaw、ZeptoClaw、EasyClaw 等）24 小时内零活动。技术焦点正从“基础对话能力”转向**多实例路由、协议互操作、Token 成本优化和可视化运维**。

---

### 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Releases | 健康度评估 |
|---|---|---|---|---|
| **Zeroclaw** | 50 条（18 关闭/合并） | 50 条（12 已合并） | 0（v0.8.0 发布准备中） | 🔥 极高活跃，迭代健康，关闭率 36% |
| **IronClaw** | 50 条（43 活跃/新开，7 关闭） | 38 条（16 已合并/关闭，22 待合并） | 0（版本积压 #3708） | 🔥 极高活跃，Reborn 架构迁移期，合并流速健康 |
| **LobsterAI** | 15 条（1 新增，14 条历史标记 stale） | 2 条（均已合并） | 0 | 🟡 低活跃，修复收尾，中长期积压浮现 |
| **Moltis** | 1 条（活跃） | 1 条（待审阅） | 0 | 🟡 停滞，热修复未合并，审阅吞吐量为零 |
| **TinyClaw** | 0 | 0 | 0 | ⚪ 沉寂 |
| **ZeptoClaw** | 0 | 0 | 0 | ⚪ 沉寂 |
| **EasyClaw** | 0 | 0 | 0 | ⚪ 沉寂 |
| **OpenClaw** | —（核心参照，当日未披露） | — | — | 🎯 生态协议/架构基准 |
| **NanoBot / PicoClaw / NanoClaw / CoPaw** | 未披露 | 未披露 | 未披露 | ⚪ 无数据 |

---

### 3. OpenClaw 在生态中的定位

OpenClaw 是当前生态的**事实标准与架构参照系**，而非单纯的竞品。

- **协议与接口层优势**：LobsterAI 在网关层针对“OpenClaw image payloads”做溢出保护（#2110），表明 OpenClaw 的传输协议或 API 规范已被下游实现广泛兼容。
- **多工作区管理标杆**：Zeroclaw 社区在讨论 Multi-Agent Routing（#2767）时，明确以“类似 OpenClaw 的多工作区管理”作为需求对标，说明其在多租户隔离、网关路由方面处于领先定位。
- **技术路线差异**：相较于 Zeroclaw 的“极客 CLI/TUI 全渠道网关”和 IronClaw 的“企业 Reborn 工作流平台”，OpenClaw 更偏向**平台化底座与生态连接器**，被其他项目作为互操作兼容目标而非直接替代对象。
- **社区规模**：尽管当日未披露具体数据，但其被 LobsterAI、Zeroclaw 等多个独立项目引用的频率，表明其具备最大的生态影响力和第三方集成渗透率。

---

### 4. 共同关注的技术方向

以下需求在多个项目中同步涌现，构成当前生态的集体技术议程：

| 技术方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **多实例路由与网关管理** | Zeroclaw、IronClaw、OpenClaw（参照） | Zeroclaw 推进多实例 Webhook 路由（PR #7367）和按频道账号隔离（#2767）；IronClaw 通过 `ProductWorkflow` 统一 `submit/read/subscribe` 三大入口（#4488） |
| **Web 管理界面与可视化运维** | Zeroclaw、IronClaw、LobsterAI | Zeroclaw 新增 MCP/Skills/Plugins/Providers 四大管理标签页（PR #7229）；IronClaw 推进 WebUI v2 Beta；LobsterAI 用户呼吁会话标签分类（#1541）与本地统计（#1532） |
| **跨平台 IM 协议与互操作** | Zeroclaw、IronClaw、Moltis、LobsterAI | Zeroclaw 呼吁 A2A 协议（#3566）与 Napcat/QQ（#2503）；IronClaw 生产化 Slack 渠道；Moltis 修复 Telegram 流式传输；LobsterAI 维护 Popo/飞书集成 |
| **Token 成本与上下文优化** | Zeroclaw、LobsterAI | Zeroclaw 提出 Skill 编译/缓存机制以减少重复 Markdown 传输（#5146）；LobsterAI 修复重复输出导致的 Token 浪费（#2121） |
| **终端 UX 升级** | Zeroclaw、IronClaw、Moltis | Zeroclaw 重构 TUI 异步输入队列（PR #7190）与主题系统（PR #7249）；IronClaw 完善 WebChat 线程删除与偏好设置；Moltis 支持移动端多行输入（#1107） |

---

### 5. 差异化

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**Zeroclaw 项目动态日报**  
**日期：** 2026-06-08  
**分析范围：** 过去 24 小时（Issues: 50 条 | PRs: 50 条 | Releases: 0 个）

---

### 1. 今日速览

Zeroclaw 社区今日保持极高活跃度，24 小时内同步处理 50 个 Issues 与 50 个 PR，关闭/合并率达 36%（Issues 18 条，PRs 12 条）。项目核心工作围绕 **v0.8.0 发布准备**（PR #7364）、**多实例 Webhook 路由**（PR #7367）及 **TUI/CLI 体验升级**（PR #7190、#7209 已合并）展开。安全与稳定性方面，多个 S1/S2 级 Bug 被关闭，但仍有 S0 级数据丢失风险（#4627）待修复。整体健康度良好，代码迭代与社区讨论同步加速。

---

### 2. 版本发布

今日无新版本发布。  
**注：** 维护者已提交发布准备分支 [PR #7364](https://github.com/zeroclaw-labs/zeroclaw/pull/7364)（`chore(release): release v0.8.0`），主要修复了 `--no-default-features` 构建下的 `unused_imports` 警告，预示 v0.8.0 即将进入最终发布流程。

---

### 3. 项目进展

今日合并/关闭的关键 PR 与 Issues 显著推进了运行时稳定性、安全模型与终端用户体验：

**已合并/关闭的核心 PR：**
- **出站消息队列与实时输入（[PR #7190](https://github.com/zeroclaw-labs/zeroclaw/pull/7190)）：** 已合并。将 zerocode TUI 的“硬阻塞输入”改为异步出站队列，允许用户在模型生成回复期间继续编辑、附加文件并提交消息，属于 XL 级 UX 重构。
- **会话内模型切换（[PR #7209](https://github.com/zeroclaw-labs/zeroclaw/pull/7209)）：** 已合并。新增 `/model` 与 `/model-provider` 实时切换命令，无需重启会话即可变更底层模型。
- **按别名模型回退链（[PR #7178](https://github.com/zeroclaw-labs/zeroclaw/pull/7178)）：** 已合并。重新引入基于 schema-v3 的显式逐别名模型回退机制，替代此前被移除的隐式 V2/V3 实现。
- **主题系统增强（[PR #7249](https://github.com/zeroclaw-labs/zeroclaw/pull/7249)）：** 已合并。解决旧版终端（如 macOS Terminal.app、tmux）对 24-bit 真彩色的兼容性问题，新增注册表预设与按代理覆盖能力。
- **Quickstart 模态框高度修复（[PR #7360](https://github.com/zeroclaw-labs/zeroclaw/pull/7360)）：** 已关闭。修复文本换行导致的模态框尺寸与滚动追踪错误。

**已关闭的高影响 Bug：**
- **Web Dashboard 不可用（[Issue #4866](https://github.com/zeroclaw-labs/zeroclaw/issues/4866)）：** 关闭。该 Issue 累计 28 条评论，影响面广泛，现已解决构建路径与 Tauri 桌面端加载问题。
- **context_compression 在 Daemon/频道模式未触发（[Issue #4880](https://github.com/zeroclaw-labs/zeroclaw/issues/4880)）：** 关闭。修复了仅 CLI 交互循环调用压缩逻辑，而频道模式（QQ、Telegram 等）遗漏导致的内存膨胀问题。
- **web_fetch 私有主机绕过漏洞（[Issue #5122](https://github.com/zeroclaw-labs/zeroclaw/issues/5122)）：** 关闭。修复了 `allowed_private_hosts` 对解析到私有 IP 的域名无效的安全问题。
- **Fallback Provider 配置被忽略（[Issue #5803](https://github.com/zeroclaw-labs/zeroclaw/issues/5803)）：** 关闭。修复了回退链仅从环境变量读取凭证与 `base_url`，而忽略 `[providers.X]` 配置的 S1 级阻塞问题。
- **Delegate Agents 强制全量 Skill 注入（[Issue #5155](https://github.com/zeroclaw-labs/zeroclaw/issues/5155)）：** 关闭。修复了委托代理无视 `prompt_injection_mode = "compact"` 配置、始终全量注入 Skill 的 Bug。

---

### 4. 社区热点

今日讨论最激烈的议题集中在**可用性、部署门槛与协议扩展**上：

| 议题 | 状态 | 评论 | 反应 | 核心诉求 |
|------|------|------|------|----------|
| **[Bug] Web dashboard is still not available** ([#4866](https://github.com/zeroclaw-labs/zeroclaw/issues/4866)) | 已关闭 | 28 | 0 | 新用户首次安装后无法访问 Web UI 与 Tauri 桌面端，构建指引缺失或失效，属于 onboarding 阻塞。 |
| **[Feature] A better LOGO** ([#4710](https://github.com/zeroclaw-labs/zeroclaw/issues/4710)) | 开放 | 11 | 2 | 社区希望品牌视觉更专业，已有用户提交设计方案，目前因作者未跟进被标记 `needs-author-action`。 |
| **[Feature] Token consumption minimization via skill compilation** ([#5146](https://github.com/zeroclaw-labs/zeroclaw/issues/5146)) | 开放 | 9 | 1 | 用户指出每次调用天气等 Skill 都重复发送 400+ 行 Markdown，导致 Token 浪费与延迟，呼吁引入 Skill 编译/缓存机制。 |
| **[Feature] Provide a "full" docker image** ([#3642](https://github.com/zeroclaw-labs/zeroclaw/issues/3642)) | 开放 | 9 | 3 | 默认镜像为降低内存剔除了 WhatsApp 等功能，非技术用户难以自行编译，要求提供全功能开箱即用镜像。 |
| **[Feature] Where is napcat channel** ([#2503](https://github.com/zeroclaw-labs/zeroclaw/issues/2503)) | 开放 | 9 | 0 | 中国区用户需要 OneBot 11 / Napcat 协议支持以接入 QQ，目前配置界面无此选项。 |
| **[Feature][interop] A2A Protocol Support** ([#3566](https://github.com/zeroclaw-labs/zeroclaw/issues/3566)) | 开放 | 6 | 7 | 跨生态互操作诉求强烈，用户希望 Zeroclaw 原生支持 Linux Foundation 的 Agent2Agent 协议，与外部智能体通信。 |
| **[Feature] Multi-Agent Routing** ([#2767](https://github.com/zeroclaw-labs/zeroclaw/issues/2767)) | 开放 | 6 | 9 | 高赞需求。用户要求单 Gateway 实例内运行多个隔离代理，并按频道账号绑定路由，类似 OpenClaw 的多工作区管理。 |

---

### 5. Bug 与稳定性

按严重程度排序的今日活跃/已关闭 Bug：

- **S0 — 数据丢失 / 安全风险**
  - **[#4627](https://github.com/zeroclaw-labs/zeroclaw/issues/4627)** `[OPEN]` `file_write` 工具在 Docker 环境下静默失败，文件写入后无法在宿主机文件系统可见。目前状态 `in-progress`，尚无明确 fix PR 合并。**（高风险，需优先关注）**

- **S1 — 工作流阻塞**
  - **[#4879](https://github.com/zeroclaw-labs/zeroclaw/issues/4879)** `[OPEN]` Gemini CLI OAuth 认证完成后仍报 `rate_limited` 错误，完全无法使用 Gemini 系列模型。状态 `in-progress`。
  - **[#4866](https://github.com/zeroclaw-labs/zeroclaw/issues/4866)** `[CLOSED]` Web Dashboard 与桌面端无法加载。**（已修复）**
  - **[#5803](https://github.com/zeroclaw-labs/zeroclaw/issues/5803)** `[CLOSED]` Fallback provider 链忽略配置文件，仅读取环境变量。**（已修复）**
  - **[#5155](https://github.com/zeroclaw-labs/zeroclaw/issues/5155)** `[CLOSED]` Delegate agents 无视 Skill 注入模式配置。**（已修复）**
  - **[#4827](https://github.com/zeroclaw-labs/zeroclaw/issues/4827)** `[CLOSED]` 频道模式下 `auto_compact_history` 未启用，导致工具调用上下文丢失。**（已修复）**

- **S2 — 体验降级**
  - **[#4880](https://github.com/zeroclaw-labs/zeroclaw/issues/4880)** `[CLOSED]` Daemon/频道模式下 `context_compression` 未触发。**（已修复）**
  - **[#5122](https://github.com/zeroclaw-labs/zeroclaw/issues/5122)** `[CLOSED]` `web_fetch` 的 `allowed_private_hosts` 对解析到私有 IP 的域名无效。**（已修复）**
  - **[#4848](https://github.com/zeroclaw-labs/zeroclaw/issues/4848)** `[CLOSED]` MCP 服务器无法被 Zeroclaw 检测。**（已修复）**
  - **[#4721](https://github.com/zeroclaw-labs/zeroclaw/issues/4721)** `[OPEN]` 日志输出到 stdout 而非 stderr，导致管道命令（如 `zeroclaw config schema`）被日志污染。

- **S3 — 轻微问题**
  - **[#4873](https://github.com/zeroclaw-labs/zeroclaw/issues/4873)** `[OPEN]` 接入飞书（Feishu/Lark）后默认仅调用 LLM 而非完整 Agent，行为不符合预期。

---

### 6. 功能请求与路线图信号

结合已开放 Issue 与今日 PR，以下功能极可能进入 v0.8.0 或后续版本：

- **网关多实例与 Webhook 路由（高优先级）：** Issue [#6312](https://github.com/zeroclaw-labs/zeroclaw/issues/6312) 已有对应实现 [PR #7367](https://github.com/zeroclaw-labs/zeroclaw/pull/7367)，支持按 `channels.<type>.<alias>` 路径级路由，解决多 WhatsApp/Telegram 实例冲突。
- **Web 仪表板管理界面（高优先级）：** [PR #7229](https://github.com/zeroclaw-labs/zeroclaw/pull/7229)（XL 级）新增 MCP、Skills、Plugins、Providers 四大管理标签页，标志着 Zeroclaw 从纯配置文件向 GUI 运维转型。
- **Provider 生态扩展（中优先级）：** [PR #7260](https://github.com/zeroclaw-labs/zeroclaw/pull/7260) 一次性新增 morph、github_models、upstage、featherless、arcee、lambda_ai、inception 7 个 OpenAI 兼容家族。
- **安全与沙箱（长期路线）：** Issue [#6293](https://github.com/zeroclaw-labs/zeroclaw/issues/6293) 提出气隙执行模式（Air-gapped execution）与 Unix socket 伴生守护进程，目前处于 RFC 阶段，标记 `needs-maintainer-review`。
- **Token 与 Skill 优化（长期路线）：** Issue [#5146](https://github.com/zeroc

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-06-08 | 仓库：nearai/ironclaw*

---

### 1. 今日速览

IronClaw 过去 24 小时展现出极高活跃度，共有 **50 条 Issues 更新**（43 条活跃/新开，7 条关闭）与 **38 条 PR 更新**（22 条待合并，16 条已合并/关闭），无新版本发布。社区工作重心继续围绕 **"Reborn" 架构迁移**展开，核心贡献者 `@serrrfirat`、`@zmanian` 等密集推进 WebUI v2 Beta、Slack/CLI 渠道能力、安全加固及技能系统（Skills）建设。项目处于功能快速迭代与生产就绪准备并行的关键阶段，PR 合并流速健康，但多个 P0 级 Reborn 切换阻断项仍在积压。

---

### 2. 版本发布

今日无新版本发布。  
值得注意的是，发布自动化 PR [#3708](https://github.com/nearai/ironclaw/pull/3708) 已长期排队待合并，计划将 `ironclaw` 从 `0.24.0` 升级至 `0.29.1`，并包含 `ironclaw_common` 与 `ironclaw_skills` 的破坏性 API 变更，维护者需关注其合并窗口。

---

### 3. 项目进展

今日关闭/合并的 16 个 PR/Issue 中，以下进展标志着项目在多维度向前推进：

- **Slack 渠道生产化**：PR [#4463](https://github.com/nearai/ironclaw/pull/4463)（已关闭）完成 Slack host-beta 持久化存储接入与对话状态落盘；PR [#4532](https://github.com/nearai/ironclaw/pull/4532)（已关闭）添加运营侧允许频道选择器，Slack 渠道从 demo 级进入可托管状态。
- **WebChat v2 产品面扩展**：PR [#4516](https://github.com/nearai/ironclaw/pull/4516)（已关闭）实现线程删除能力；PR [#4511](https://github.com/nearai/ironclaw/pull/4511)（已关闭）落地外发偏好 facade 合约；PR [#4519](https://github.com/nearai/ironclaw/pull/4519) 新增会话能力端点，WebUI 权限模型趋于完整。
- **Reborn 核心架构定型**：Issue [#4488](https://github.com/nearai/ironclaw/issues/4488)（已关闭）明确 `ProductWorkflow` 三大入口门（`submit/read/subscribe`），为 OpenAI 兼容 API 接线奠定边界；Issue [#4116](https://github.com/nearai/ironclaw/issues/4116)（已关闭）完成 v1 Google/GitHub/NEAR SSO 向 WebChat v2 的迁移。
- **开发者体验与质量门禁**：PR [#3298](https://github.com/nearai/ironclaw/pull/3298)（已关闭）引入 hermetic 本地门禁，统一 fmt/safety/clippy 与分层测试；PR [#4517](https://github.com/nearai/ironclaw/pull/4517) 首次运行时自动 seed `config.toml`，显著降低本地启动门槛。
- **运行时数据完整性**：PR [#4534](https://github.com/nearai/ironclaw/pull/4534) 优化 compaction 策略以保留活跃任务；PR [#4530](https://github.com/nearai/ironclaw/pull/4530)（已关闭）规范模型可见的工具观察（Tool Observation）结构，提升错误恢复上下文的可预测性。

---

### 4. 社区热点

今日讨论最活跃、评论最多的议题反映了社区对架构门面、配置工程与本地开发体验的集中关注：

1. **[#3280] [Reborn] Add ProductWorkflow and InboundTurnService facade**（7 条评论，P0）  
   作为 Reborn 产品工作流的核心门面设计，讨论聚焦于如何统一 `ProductAdapter` 与宿主层服务边界。该 Issue 是后续 OpenAI

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-08 | 仓库：netease-youdao/LobsterAI*

---

### 1. 今日速览

过去24小时，项目代码侧以**质量修复收尾**为主，2个PR完成合并/关闭，分别解决了OpenClaw图片传输溢出和配置迁移时用户删除模型被意外恢复的问题。Issues侧呈现**“低新增、高积压浮现”**特征：仅新增1条用户主动发起的活跃讨论（#2121），但另有14条历史Issue于昨日被批量标记为 `stale`，暴露出4月初以来在稳定性、IM集成和会话管理方面的中长期积压。无新版本发布，整体活跃度中等偏低，维护者需关注积压Issue的消化节奏。

---

### 2. 版本发布

无。

---

### 3. 项目进展

今日共有 **2 条 PR 已合并/关闭**，均聚焦于稳定性与数据一致性：

- **#2110** `fix(cowork): guard oversized OpenClaw image payloads`  
  [→ 查看 PR](https://github.com/netease-youdao/LobsterAI/pull/2110)  
  在网关层前增加 OpenClaw `chat.send` 超大 Payload 检测，将 `1009` / max-payload 错误明确归类为消息尺寸错误，并补充了针对 Payload 估算与错误分类的专项测试。该修复降低了协作场景下因图片过大导致的消息发送失败率。

- **#2117** `fix(config): preserve deleted provider models after migration`  
  [→ 查看 PR](https://github.com/netease-youdao/LobsterAI/pull/2117)  
  通过追踪 Provider 模型迁移版本号，确保默认模型仅在首次迁移时注入；用户主动删除的 Provider 模型在应用重启后不再被静默恢复。同时补充了针对所有受影响 Provider 的回归测试覆盖，提升了配置系统的可预测性。

---

### 4. 社区热点

今日讨论最活跃、值得维护者优先关注的条目如下：

- **#2121 对一个现象的疑问（怀疑是bug）**  
  [→ 查看 Issue](https://github.com/netease-youdao/LobsterAI/issues/2121)  
  用户质疑AI在对话中出现重复输出，怀疑该现象在大量消耗Token并造成浪费。此Issue为昨日新建，直接触及用户成本敏感点，尚无修复PR，需尽快确认是模型行为还是前端渲染/去重逻辑缺陷。

- **#1509 skills文件长时间生成阻塞无法感知，中间态过程无展示**  
  [→ 查看 Issue](https://github.com/netease-youdao/LobsterAI/issues/1509)  
  该Issue有 **2 条评论**，是评论数最多的开放Issue。核心矛盾在于 `skill-creator` 生成过程缺乏进度与状态反馈，且同模型在OpenClaw与LobsterAI中的理解表现不一致，反映出技能编排链路的状态透明度与模型对齐问题。

- **#1541 会话列表缺少标签分类和筛选功能，大量会话难以高效组织管理**  
  [→ 查看 Issue](https://github.com/netease-youdao/LobsterAI/issues/1541)  
  高价值功能请求，获得社区隐性关注。用户将会话管理痛点从“线性列表”提升到“多维分类体系”，与 #1525（颜色标注）、#1528（批量导出）形成强关联需求集群。

---

### 5. Bug 与稳定性

今日报告或重新浮出水面的Bug与稳定性问题，按严重程度排列如下：

| 严重程度 | Issue | 说明 | Fix PR |
|---|---|---|---|
| 🔴 高 | **#2121** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/2121) | 用户侧观察到AI重复输出，担心造成Token经济成本浪费；需确认根因（模型/前端/去重） | 无 |
| 🟠 中 | **#1516** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1516) | 关闭Settings面板后，GitHub Copilot OAuth轮询未取消，导致认证成功后的Token静默丢失 | 无 |
| 🟠 中 | **#1500** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1500) | 禁用技能后，Redux状态 `activeSkillIds` 未同步清理，已禁用技能仍被注入对话提示词 | 无 |
| 🟠 中 | **#1502** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1502) | Agent设置面板保存技能列表后，当前会话的 `activeSkillIds` 未热更新，需切换Agent才能生效 | 无 |
| 🟠 中 | **#1506** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1506) | 定时任务表单在IM通知频道未选择具体会话时仍可提交，运行时通知静默失败，用户无感知 | 无 |
| 🟡 低 | **#1504** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1504) | IM机器人（Popo）的AES Key配置项缺少前端必填校验，空值可保存成功 | 无 |
| 🟡 低 | **#1513** [→ 链接](https://github.com/netease-youdao/LobsterAI/issues/1513) | 「声明条款」页面存在序号重复、括号不完整等文案规范问题 | 无 |

---

### 6. 功能请求与路线图信号

用户提出的新功能需求呈现明显的**“会话管理与信息组织”**主题，结合已有PR判断，以下方向可能被纳入下一版本规划：

- **会话多维组织体系**（高优先级信号）：  
  - **#1541** 标签分类与筛选  
  - **#1525** 会话颜色标注  
  - **#1528** 批量导出（当前仅支持批量删除）  
  三项需求相互补强，构成从“分类 → 视觉区分 → 数据导出”的完整闭环，适合作为会话管理模块的统一迭代。

- **消息层级管理**：  
  - **#1537** 长会话中AI回复消息的书签/收藏功能，解决长对话中关键信息回溯效率问题。

- **本地数据洞察**：  
  - **#1532** 设置页增加本地使用统计（总会话数、总消息数、Agent分布等），提升用户对本地SQLite数据的认知。

- **工程基础设施**：  
  - **#1518** 修复CI Labeler权限错误并明确 `lint --max-warnings 0` 策略，属于开发者体验优化，修复成本明确。

---

### 7. 用户反馈摘要

从Issues中提炼的真实用户痛点与场景：

- **状态不透明焦虑**：用户在 skills 生成（#1509）和定时任务IM通知（#1506）场景中，均遭遇“系统正在做什么/为何失败”的黑盒体验，缺乏中间态与错误提示。
- **状态同步断裂**：Agent与技能的配置变更无法实时反映到当前会话（#1500、#1502），用户被迫通过“切换Agent”这类 workaround 刷新

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-08 | 数据来源：github.com/moltis-org/moltis*

---

### 1. 今日速览

过去24小时内，Moltis 项目维持轻量级维护节奏：无新版本发布，无 Issue/PR 关闭，仅有 1 个 Issue 保持活跃、1 个 Hotfix PR 等待合并。社区贡献集中在**移动端 Web 交互体验**与 **Telegram 集成稳定性**两个维度。整体健康度平稳，但代码审阅与合并吞吐量为零，主分支今日未产生实质性推进，处于“修复待审阅”状态。

---

### 2. 版本发布

（今日无新版本发布，该部分省略）

---

### 3. 项目进展

今日**无已合并或已关闭的 PR**。唯一待处理的代码变更 [PR #1113](https://github.com/moltis-org/moltis/pull/1113) 针对 Telegram 流式传输的回归问题提交热修复，目前等待维护者审阅。由于该修复尚未合入主干，项目在主分支层面未产生功能增量或稳定性更新，整体处于维护停滞状态，建议尽快恢复审阅流程以推动代码落地。

---

### 4. 社区热点

- **[#1107] [Feature]: Multiline text input in the mobile web UI**（[链接](https://github.com/moltis-org/moltis/issues/1107)）  
  由 @IlyaBizyaev 提出的移动端增强需求，过去24小时内仍有活跃更新，反映了用户在移动场景下进行长文本交互的痛点。
  
- **[#1113] hotfix(telegram): stream final replies without completion notify**（[链接](https://github.com/moltis-org/moltis/pull/1113)）  
  @s-salamatov 提交的 Telegram 热修复，针对 [#1099](https://github.com/moltis-org/moltis/pull/1099) 引入的流式传输回归。

**诉求分析**：社区当前最强烈的信号是**跨平台体验一致性**。移动端 Web 需要更自然的输入方式以支撑复杂对话，而 Telegram 作为重要接入渠道，其流式渲染的稳定性直接影响用户感知。两者共同指向项目在多端交互细节上的打磨需求。

---

### 5. Bug 与稳定性

| 问题描述 | 来源 | 严重程度 | 状态 |
|---|---|---|---|
| Telegram 流式传输在**禁用完成通知**时，最终答案未被正确识别为流式最终回复，导致消息渲染异常或丢失 | 回归自 [#1099](https://github.com/moltis-org/moltis/pull/1099)，修复见 [#1113](https://github.com/moltis-org/moltis/pull/1113) | 中 | **Fix PR 已提交**（[#1113](https://github.com/moltis-org/moltis/pull/1113) 待合并） |

该问题属于配置组合边缘场景（`streaming enabled + completion notifications disabled`）下的行为退化，影响 Telegram 用户的端到端流式体验。建议维护者优先审阅合并，以防止问题在特定用户群中持续扩散。

---

### 6. 功能请求与路线图信号

- **移动端多行输入支持**（[#1107](https://github.com/moltis-org/moltis/issues/1107)）：用户明确请求在移动 Web UI 中支持多行文本输入。该需求属于前端/UX 层改进，实现成本相对可控，且能直接提升移动端可用性。结合当前项目对多平台支持的重视，该功能有较大概率被纳入下一版本的体验优化批次。

目前暂无其他 competing 功能请求，此 Issue 可作为移动端体验专项的优先候选。

---

### 7. 用户反馈摘要

- **痛点**：移动端 Web 用户受限于单行输入框，在进行复杂提示词（prompt）输入或多轮对话时体验受阻（[#1107](https://github.com/moltis-org/moltis/issues/1107)）。
- **场景**：Telegram 用户在开启流式传输但关闭完成通知的特殊配置下，遭遇最终消息无法正确回显的问题（[#1113](https://github.com/moltis-org/moltis/pull/1113)）。
- **稳定性预期**：社区对 Telegram 集成的稳定性预期较高，[#1099](https://github.com/moltis-org/moltis/pull/1099) 引入的回归表明**配置组合测试覆盖**仍需加强，以避免边缘场景下的行为退化。

---

### 8. 待处理积压

- **[#1107](https://github.com/moltis-org/moltis/issues/1107)**：创建于 2026-06-05，距今已 3 天，有 1 条评论，尚未分配里程碑或负责人。作为移动端体验的重要补充，建议维护者评估优先级并给出社区反馈。
- **[#1113](https://github.com/moltis-org/moltis/pull/1113)**：作为热修复 PR 已等待审阅，建议维护者优先处理，避免 Telegram 相关回归问题持续影响终端用户。

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