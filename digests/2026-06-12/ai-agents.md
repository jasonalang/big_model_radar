# OpenClaw 生态日报 2026-06-12

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-12 03:32 UTC

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
**日期：2026-06-12**

---

### 1. 今日速览

过去 24 小时，OpenClaw 仓库保持极高频运转，Issues 与 PR 各更新 **500 条**，其中 Issues 关闭 28 条、PR 合并/关闭 120 条，无新版本发布。社区火力集中在 **Cron 可靠性修复**、**消息投递边界情况**、**会话状态一致性**三大战场，同时长期呼声最高的 Linux/Windows 桌面客户端与预构建 Android APK 仍是未解的结构性缺口。整体健康度活跃，但 P1 级稳定性问题数量提示核心运行时仍面临压力。

---

### 2. 版本发布

**无。**  
今日未发布新版本（v0 releases）。近期变更以主干（main）迭代为主，建议生产环境用户关注 Cron 与消息投递相关 PR 的合并进度。

---

### 3. 项目进展

今日推进的关键 PR 集中在调度可靠性、通道投递与运行时修复：

- **Cron 配置可靠性**：[#92295](https://github.com/openclaw/openclaw/pull/92295) 与 [#92304](https://github.com/openclaw/openclaw/pull/92304) 修复 `openclaw cron edit --cron` 时静默

---

## 横向生态对比

**个人 AI 助手/自主智能体开源生态横向对比分析**  
*报告日期：2026-06-12*

---

### 1. 生态全景

当前个人 AI 助手与自主智能体开源生态呈现**“头部狂飙、长尾停滞”**的鲜明分化。以 OpenClaw、IronClaw 为代表的头部项目日处理 Issues/PR 达数百量级，社区正集体从“功能构建”转向**质量加固与生产就绪**；MCP 协议集成、多 Agent 协作、企业级消息网关可靠性成为共同的主战场。与此同时，TinyClaw、ZeptoClaw、EasyClaw 等多个项目已陷入停滞，资源正加速向具备持续工程能力的核心仓库聚集。

---

### 2. 各项目活跃度对比

| 项目 | Issues 更新 | PR 更新 | 已合并/关闭 PR | 待审 PR | 版本发布 | 健康度评估 |
|------|-------------|---------|----------------|---------|----------|------------|
| **OpenClaw** | ~500 条更新（关闭 28） | ~500 条更新（合并/关闭 120） | 120 | — | 无 | 🔥 极高活跃，核心运行时承压，P1 稳定性问题集中 |
| **IronClaw** | 30（17 活跃/新开，13 关闭） | 47（24 合并/关闭，23 待审） | 24 | 23 | 无（release PR #3708 待合入） | 🔥 极高活跃，Reborn 生产底座就绪，向发布过渡 |
| **PicoClaw** | 7（4 活跃/新开，3 关闭） | 31（18 合并/关闭，13 待审） | 18 | 13 | v0.2.9-nightly | 🚀 高活跃，功能激进，协议层创新显著 |
| **NanoBot** | 3（2 新开，1 关闭） | 18（6 合并/关闭，12 待审） | 6 | 12 | 无 | ⚡ 中高活跃，稳定性加固为主，积压 PR 待审 |
| **LobsterAI** | 2 活跃 | 15（14 合并/关闭，1 待审） | 14 | 1 | 无 | ⚡ 中高活跃，清理 7 条 stale PR，协作功能冲刺 |
| **NanoClaw** | — | 14（9 合并/关闭，5 待审） | 9 | 5 | 无 | ✅ 中等活跃，架构扩展与稳定性并重 |
| **Moltis** | 1 新开 | 1（待审） | 0 | 1 | 无 | ⚠️ 低活跃，维护模式，核心网关修修补补 |
| **TinyClaw** | 0 | 0 | 0 | 0 | 无 | ❌ 停滞 |
| **ZeptoClaw** | 0 | 0 | 0 | 0 | 无 | ❌ 停滞 |
| **EasyClaw** | 0 | 0 | 0 | 0 | 无 | ❌ 停滞 |
| **Zeroclaw / CoPaw** | — | — | — | — | — | 无数据 |

---

### 3. OpenClaw 在生态中的定位

**优势**：OpenClaw 是无可争议的**流量与工程吞吐量核心**，单日 Issues/PR 更新量达 500 条级别，远超其他项目，表明其作为“默认参照”的社区引力极强。其在 Cron 调度、消息投递、会话状态管理等底层运行时上积累了最深的工程厚度。

**技术路线差异**：与 IronClaw（押注 WebUI v2 + Reborn 重构）、NanoBot（押注企业 IM 与多提供商路由）不同，OpenClaw 更偏向**“无头运行时（headless runtime）”**，强调后端调度与通道抽象，但**结构性缺口**同样明显——Linux/Windows 桌面客户端与预构建 Android APK 长期缺位，使其在个人终端覆盖上弱于更完整的发行版。

**社区规模对比**：OpenClaw 的绝对事件量是 NanoBot 的约 28 倍、PicoClaw 的 16 倍，但高吞吐量伴随高 P1 缺陷密度（Cron 可靠性、消息边界、会话一致性），说明其正处于“大规模生产验证”阶段，而非 polished 产品阶段。

---

### 4. 共同关注的技术方向

以下需求在**多项目同时涌现**，反映行业共性瓶颈：

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **MCP 协议稳定性与集成** | NanoBot、PicoClaw、Moltis、IronClaw | NanoBot 出现 P0 级 MCP 网关重连崩溃；PicoClaw 合入 MCP 动态头部支持；Moltis 遭遇 Fastmail MCP 授权失败；IronClaw 推进 MCP 自动启用。 |
| **多 Agent 协作与路由** | PicoClaw、LobsterAI、NanoClaw、NanoBot | PicoClaw 的 Agent Collaboration Bus（#2937）待审；LobsterAI 上线 Cowork 实时语音协作；NanoClaw 引入 channel-instance 支持多 bot；NanoBot 社区强烈诉求多自定义 OpenAI 兼容提供商并存。 |
| **消息网关可靠性** | OpenClaw、NanoBot、PicoClaw、Moltis、LobsterAI | OpenClaw 修复投递边界；NanoBot 优化 Slack 频道策略与消息分割；PicoClaw 修复 WhatsApp 原生模式检测与 tool_calls 过滤；Moltis 修复 WhatsApp @lid 隐私聊天丢消息；LobsterAI 解决网关启动竞态与慢网关超时。 |
| **会话与记忆架构** | NanoClaw、NanoBot、OpenClaw | NanoClaw 的 Agent 内存系统在 ~83 KB/54 文件规模触及天花板（#1356）；NanoBot 清理会话历史孤儿 tool 消息；OpenClaw 攻坚会话状态一致性。 |
| **本地/私有部署体验** | IronClaw、NanoBot、LobsterAI | IronClaw Reborn 本地 SSO 与配置管理债务突出；NanoBot 将本地 LLM 流超时下沉为按提供商配置；LobsterAI 提升 OpenClaw 网关堆内存限制并做模型 Failover。 |

---

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 核心调度引擎、Cron、消息总线 | 需要自建 AI 助手后端的开发者 | 无头运行时优先，缺官方桌面/移动端发行版 |
| **NanoBot** | 企业 IM（Slack/Discord）、多提供商、Python SDK | 企业 IT 与多模型路由需求用户 | 模块化架构演进（core + WebUI，桌面端将外迁） |
| **PicoClaw** | 协议层创新、多 Agent 协作总线、嵌入式 | 协议集成方与硬件/边缘开发者 | Sipeed 背景，强调 MCP 动态头部与 Pico Protocol 可观测性 |
| **NanoClaw** | 高吞吐多 bot 部署、Agent 驱动 DevOps | 规模化部署与平台型开发者 | 引入 channel-instance 维度，探索 PR Factory 自动化工作流 |
| **IronClaw** | WebUI v2、Reborn 重构、NEAR AI 生态 | 追求开箱即用本地体验的用户 | 强绑定 NEAR AI 凭证与模型生态，配置管理债务显著 |
| **LobsterAI** | 实时语音 Cowork、分享矩阵、Failover | 团队协作与知识共享场景 | 网易有道背景，重视 V8 内存管理与长时工作负载稳定性 |
| **Moltis** | WhatsApp 等 IM 网关桥接 | 轻量级消息自动化用户 | 低维护带宽，聚焦隐私聊天（@lid）等边缘合规场景 |

---

### 6. 社区热度与成熟度

**🔥

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
*日期：2026-06-12 | 仓库：HKUDS/nanobot*

---

### 1. 今日速览

过去 24 小时，NanoBot 项目保持**高活跃度**：PR 侧共有 18 条更新，其中 6 条已合并/关闭、12 条待审；Issues 侧 3 条更新，2 条新开、1 条关闭，无新版本发布。今日主线集中在**稳定性加固**（MCP 网关重连崩溃、会话历史孤儿工具结果、cron 子代理生命周期）与**开发者体验提升**（Python SDK 扩展、多自定义提供商支持）。社区明确提出了对多自定义 OpenAI 兼容端点的配置诉求，相关长期 PR 再次回到审查视野。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日共有 **6 个 PR 合并/关闭**，推动项目在 AI 基础设施集成、企业 IM 适配与本地部署体验上稳步前进：

- **SiliconFlow 转录能力上线** —— [#4281](https://github.com/HKUDS/nanobot/pull/4281) 接入 SiliconFlow 作为新的语音转录提供商（默认模型 `FunAudioLLM/SenseVoiceSmall`），复用现有 Whisper 兼容适配器，丰富了多厂商语音 pipeline。
- **Slack 频道策略精细化** —— [#4289](https://github.com/HKUDS/nanobot/pull/4289) 在 `allowlist` 模式下新增 `groupRequireMention` 选项，允许在指定频道内仅当 bot 被 @提及时才响应，解决了企业 Slack 场景中“全量响应干扰”与“完全静默”的二选一难题。
- **本地 LLM 流超时可配置** —— [#4020](https://github.com/HKUDS/nanobot/pull/4020) 将原本全局的 `NANOBOT_STREAM_IDLE_TIMEOUT_S`（90s）下沉为**按提供商配置**，显著改善 LM Studio / Ollama 等本地重载模型的超时中断问题。
- **消息分割代码块感知** —— [#4257](https://github.com/HKUDS/nanobot/pull/4257) 修复 `split_message` 在长消息切分时可能撕裂 fenced code block 的 bug，避免渲染出破损的 HTML/ Markdown。
- **仓库架构瘦身** —— [#4294](https://github.com/HKUDS/nanobot/pull/4294)（待合并）计划将 Electron 桌面应用从核心仓库移除，聚焦 core + WebUI 公共面；[#4298](https://github.com/HKUDS/nanobot/pull/4298)、[#4297](https://github.com/HKUDS/nanobot/pull/4297) 已关闭，疑似重复或撤回的工作树文档 PR。

---

### 4. 社区热点

今日社区讨论围绕**架构调整**与**核心稳定性**展开，虽评论数绝对值不高，但技术影响面较大：

- **MCP 网关级崩溃与紧急修复** —— Issue [#4302](https://github.com/HKUDS/nanobot/issues/4302) 报告 `streamableHttp` MCP 会话终止后网关重连崩溃，PR [#4303](https://github.com/HKUDS/nanobot/pull/4303) 已快速跟进，定位到跨 task 的 cancel scope 退出问题。该组合是今日最高优先级热点。
- **多自定义提供商诉求升温** —— Issue [#4305](https://github.com/HKUDS/nanobot/issues/4305) 明确提出需要同时配置多个 `custom` / `openai` 提供商，与 4 月积压的 PR [#3239](https://github.com/HKUDS/nanobot/pull/3239) 形成呼应，反映出多模型路由、多云/多内部 API 接入已成为企业用户的刚需。
- **核心仓库去桌面化** —— PR [#4294](https://github.com/HKUDS/nanobot/pull/4294) 引发对项目边界与维护策略的关注，标志着 NanoBot 正从“all-in-one 单体”向“core 为核、桌面外迁”的模块化架构演进。

---

### 5. Bug 与稳定性

按严重程度排列，今日 Bug 态势如下：

| 严重度 | 问题 | 状态 | 链接 |
|---|---|---|---|
| **P0 / 崩溃** | MCP 网关重连时因 cancel scope 跨 task 退出导致进程崩溃 | **Fix PR 已提交** | [#4302](https://github.com/HKUDS/nanobot/issues/4302) / [#4303](https://github.com/HKUDS/nanobot/pull/4303) |
| **P1 / 数据污染** | 会话历史残留孤儿 `role:"tool"` 消息，导致严格兼容的 OpenAI/Anthropic API 拒绝请求 | **Fix PR 待审** | [#4306](https://github.com/HKUDS/nanobot/pull/4306) |
| **P1 / 生命周期** | Cron 任务在子代理（subagent）仍在后台运行时即被标记为完成，造成状态不一致 | **Fix PR 待审** | [#4304](https://github.com/HKUDS/nanobot/pull/4304) |
| **P2 / API 错误** | OpenAI Codex provider 重复发送已接受的 reasoning item，触发 `400 Duplicate item` | **Fix PR 待审** | [#4021](https://github.com/HKUDS/nanobot/pull/4021) |
| **已修复** | Ubuntu 24.04 默认限制非特权用户命名空间导致 bwrap 沙箱失效 | **已关闭** | [#4236](https://github.com/HKUDS/nanobot/issues/4236) |
| **已修复** | 长消息切分破坏 fenced code block | **已合并** | [#4257](https://github.com/HKUDS/nanobot/pull/4257) |

---

### 6. 功能请求与路线图信号

结合今日 Issues 与长期 PR，以下需求极可能纳入下一版本或近期里程碑：

- **多自定义 OpenAI 兼容提供商**（[#4305](https://github.com/HKUDS/nanobot/issues/4305) + [#3239](https://github.com/HKUDS/nanobot/pull/3239)）：用户需要连接多个内部/云端 OpenAI 兼容端点，现有单 `custom` 限制已成为瓶颈。该 PR 已积压约 2 个月，社区新 Issue 再次催审。
- **Python SDK 完整化**（[#4296](https://github.com/HKUDS/nanobot/pull/4296)）：从简单的 `bot.run(...)` 门面升级为具备会话、记忆、运行时控制的完整开发者 API，且保持向后兼容，利好 Agent 开发者生态。
- **网关生命周期 CLI**（[#3538](https://github.com/HKUDS/nanobot/pull/3538)）：提供 `start/stop/restart/status` 命令及本地 runtime metadata，对运维部署友好，已积压 1.5 个月。
- **Cron 与会话绑定**（[#4299](https://github.com/HKUDS/nanobot/pull/4299)）：避免定时自动化注入到正在进行的用户会话中，提升多租户/长会话场景体验。
- **技能依赖与类型检查**（[#4300](https://github.com/HKUDS/nanobot/pull/4300)）：允许技能声明前置依赖（如股票数据技能依赖新闻技能），支撑更复杂的组合式 Agent 工作流。

---

### 7. 用户反馈摘要

从今日 Issues 与 PR 描述中提炼的真实声音：

- **企业 Linux 部署痛点**：Ubuntu 24.04 等现代发行版对非特权用户命名空间的默认限制，使 Bubblewrap 沙箱开箱即失败（[#4236](https://github.com/HKUDS/nanobot/issues/4236)），反映出安全沙箱与操作系统默认策略的兼容性仍需文档或自动降级机制。
- **多云/多模型接入刚需**：“I need more than one custom (and openai) provider”（[#4305](https://github.com/HKUDS/nanobot/issues/4305)）—— 用户不再满足于单一自定义端点，期望通过配置化模板实现多提供商并存。
- **稳定性优先于新功能**：MCP 重连崩溃（[#4302](https://github.com/HKUDS/nanobot/issues/4302)）、会话历史严格性（[#4306](https://github.com/HKUDS/nanobot/pull/4306)）、cron 子代理生命周期（[#4304](https://github.com/H

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
**日期：2026-06-12**  
**仓库：** [github.com/sipeed/picoclaw](https://github.com/sipeed/picoclaw)

---

### 1. 今日速览

过去 24 小时，PicoClaw 维持高活跃度开发节奏：共发生 **31 个 PR 更新**（其中 18 个已合并/关闭，13 个待合并）与 **7 个 Issue 更新**（4 个活跃/新开，3 个关闭）。项目发布了基于 main 分支的自动化夜间构建 `v0.2.9-nightly.20260612.413d3749`。功能层面，Agent 协作总线（#2937）进入待审阅状态，MCP 协议动态头部支持（#2696）正式合入主线；安全方面，启动器 `allowed_cidrs` 绕过漏洞（#3080）已被关闭。整体健康度良好，但仍有 2 个新增 Bug（#3108、#3094）与 1 个存在逾 2 个月的 Windows 兼容性缺陷（#2472）等待修复。

---

### 2. 版本发布

**Nightly Build: [v0.2.9-nightly.20260612.413d3749](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)**  
- **类型：** 自动化夜间构建  
- **更新内容：** 包含自 `v0.2.9` 以来所有已合并提交，涵盖 MCP 动态头部、通道消息过滤修复、配置持久化修正及多项依赖升级。  
- **风险提示：** 官方明确标注 *"This is an automated build and may be unstable. Use with caution."* 不建议用于生产环境。  
- **迁移注意：** 若从稳定版切换至本 nightly 版本，建议备份 `.security.yml` 与 `config.json`，并留意 Agent 子代理消息行为变更（涉及 #3094 相关逻辑）。

---

### 3. 项目进展

今日合并/关闭的关键 PR 推动了协议稳定性、配置持久化与代码质量三方面进展：

- **消息通道与协议层修复**
  - [#2957](https://github.com/sipeed/picoclaw/pull/2957) 修复了 streaming 过程中 `tool_calls` 被错误过滤为辅助消息的问题，直接关闭了关联 Issue [#2958](https://github.com/sipeed/picoclaw/issues/2958)。
  - [#2696](https://github.com/sipeed/picoclaw/pull/2696) 引入 MCP 每请求动态头部能力：通道上下文可通过 `mcp:` 前缀向 MCP 服务器透传 HTTP Header（如 `Authorization`），增强企业级集成。
  - [#2934](https://github.com/sipeed/picoclaw/pull/2934) 修正 WhatsApp 通道配置检测，使 `use_native: true` 原生模式（whatsmeow）不再被错误判定为未配置。

- **配置与运行时稳定性**
  - [#3067](https://github.com/sipeed/picoclaw/pull/3067) 向 `SessionConfig` 补充缺失的 `DmScope` 字段，解决了前端“运行时会话隔离范围”设置无法持久化的回归问题。
  - [#2955](https://github.com/sipeed/picoclaw/pull/2955) 强化单例检查：在验证 PID 文件时增加进程身份校验，避免 PID 复用（如被 `systemd-resolved` 占用）导致启动失败。
  - [#3060](https://github.com/sipeed/picoclaw/pull/3060) 统一使用 `%w` 进行错误包装，恢复 `errors.Is`/`errors.As` 调用链；同时补全 `json.MarshalIndent` 的错误处理。

- **模型与工具修正**
  - [#2947](https://github.com/sipeed/picoclaw/pull/2947) 修正 Anthropic 默认模型 ID 格式，将 `claude-sonnet-4.6` 改为规范的 `claude-sonnet-4-6`，消除首次调用时的 HTTP 404。

- **依赖维护**
  - 已合并：AWS SDK Go v2 / Config（#3102、#3106）、MCP Go SDK 1.6.1（#3098）、`golang.org/x/sync` 0.21.0（#3099）。
  - 待合并：GitHub Copilot SDK Go 1.0.1（#3107）、前端 Vite / ESLint / shadcn / typescript-eslint 等（#3100–#3105）。

---

### 4. 社区热点

| 条目 | 热度指标 | 核心诉求 |
|------|----------|----------|
| [#2472](https://github.com/sipeed/picoclaw/issues/2472) `list_dir` Windows 路径分隔符 Bug | 5 评论, 1 👍 | **跨平台工具稳定性**：Windows 反斜杠被直接传入 Go 的 `fs.FS`/`os.Root`，导致基础文件操作失败。 |
| [#2984](https://github.com/sipeed/picoclaw/issues/2984) WebSocket 显式回合完成信号 | 2 评论, 2 👍 | **协议确定性**：外部 Pico Protocol 客户端需要明确知道 Agent 何时真正结束处理，而非仅靠 `typing.stop` 推断。 |
| [#3094](https://github.com/sipeed/picoclaw/issues/3094) 异步子代理重复消息 | 1 评论 | **消息体验**：`spawn` 任务完成后，飞书/Telegram 等通道同时收到原始结果与主代理汇总两条重复消息。 |
| [#2937](https://github.com/sipeed/picoclaw/pull/2937) Agent Collaboration Bus | 大 PR, 待合并 | **架构升级**：社区对多 Agent 协作需求强烈，该 PR 引入持久化邮箱、协作线程、权限感知等一阶能力。 |

**分析**：今日社区焦点集中在“协议可观测性”（#2984）与“多 Agent 协作”（#2937）两大主题，反映出 PicoClaw 正从单 Agent 工具调用向复杂多 Agent 系统演进，外部集成方对协议边界的确定性要求同步提高。

---

### 5. Bug 与稳定性

按严重程度排序：

1. **[高] [#3080](https://github.com

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报**  
*日期：2026-06-12 | 仓库：github.com/qwibitai/nanoclaw*

---

### 1. 今日速览

NanoClaw 今日展现极高开发吞吐量，24 小时内处理 **14 个 PR**（合并/关闭 9 个，待审 5 个），无新版本发布。核心修复集中在 Signal 适配器、CLI wiring 副作用及 session-manager 数据库只读模式等稳定性问题。功能层面，"PR Factory" 自动化工作流与多 bot 通道实例支持显示项目正向企业级部署演进。唯一活跃 Issue 为长期开放的 Agent 内存架构重设计，社区对当前 ~83 KB 规模上限的扩展性焦虑持续。

---

### 3. 项目进展

今日合并/关闭的 9 个 PR 推动项目在稳定性、架构扩展与开发者体验三方面同步前进：

- **核心 Bug 修复闭环**：[#2738](https://github.com/nanocoai/nanoclaw/pull/2738) 修复 `session-manager` 以只读模式打开 outbound.db 导致 command-gate 拒绝响应被静默丢弃的问题，并关联关闭 [#2495](https://github.com/nanocoai/nanoclaw/issues/2495)。
- **基础设施加固**：[#2736](https://github.com/nanocoai/nanoclaw/pull/2736) 为刚唤醒容器添加宽限期，避免 host-sweep 误清理陈旧处理声明；[#2740](https://github.com/nanocoai/nanoclaw/pull/2740) 引入按组空闲超时，实现临时会话优雅退出。
- **架构扩展**：[#2733](https://github.com/nanocoai/nanoclaw/pull/2733) 引入原生 `channel-instance` 维度，为同一通道部署多 bot 提供底层支持；[#2737](https://github.com/nanocoai/nanoclaw/pull/2737) 增加审批解决回调注册表，实现模块间可观测性解耦；[#2734](https://github.com/nanocoai/nanoclaw/pull/2734) 补齐 delivery action 注册表的读取侧。
- **开发者体验**：[#2741](https://github.com/nanocoai/nanoclaw/pull/2741) 修复 setup 流程向 Claude 交接时因缺少 user message 导致的交互挂起；[#2739](https://github.com/nanocoai/nanoclaw/pull/2739) 将非 Chat-SDK webhook 改为追加式 raw-route 注册，降低集成门槛。

---

### 4. 社区热点

- **[#1356](https://github.com/nanocoai/nanoclaw/issues/1356) Agent memory system redesign**（👍 6，评论 2，开放中）  
  这是目前社区反应最集中的议题。作者 @Ordinath 指出当前基于 `MEMORY.md` 索引 + 卫星 markdown 的内存系统在 ~54 文件 / ~83 KB 规模已触及天花板。诉求核心：Agent 长期记忆与上下文压缩的架构升级，反映了生产环境用户从 PoC 向规模化部署的跃迁痛点。

- **[#2742](https://github.com/nanocoai/nanoclaw/pull/2742) The PR Factory**（新开，待合并）  
  虽暂无评论/点赞，但其将每个 PR 转化为由独立 Worker Agent 驱动的 Slack 线程工作流（自动分类、审查 diff、生成测试计划），代表了社区对 Agent 驱动软件工程（Agentic SE）的高度兴趣，预计将成为高关注 PR。

---

### 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | 说明 |
|---|---|---|---|
| **高** | [#2495](https://github.com/nanocoai/nanoclaw/issues/2495) `writeOutboundDirect` 只读打开 DB，command-gate 拒绝响应静默丢失 | **已修复** via [#2738](https://github.com/nanocoai/nanoclaw/pull/2738) | `SQLITE_READONLY` 错误被 `finally` 块吞掉，导致安全策略响应永不投递。 |
| **高** | [#2743](https://github.com/nanocoai/nanoclaw/pull/2743) `ncl wirings create` 跳过 `agent_destinations` 副作用 | **待合并** | 通用 CRUD 仅插入 `messaging_group_agents`，Companion 行缺失导致 Agent 向新会话发送的消息被静默丢弃。 |
| **高** | [#2744](https://github.com/nanocoai/nanoclaw/pull/2744) Signal 适配器缺失 `operation: 'reaction'` 处理 | **待合并** | Agent 的 `add_reaction` 工具输出与入站反应信封均被静默丢弃，影响 Signal 通道交互完整性。 |
| **中** | [#2732](https://github.com/nanocoai/nanoclaw/pull/2732) Host + agent-runner 健康审计缺陷 | **待合并** | Docker Desktop drvfs staging 崩溃循环、容器唤醒后陈旧处理声明竞争、`MAX_CONCURRENT_CONTAINERS` 未强制执行。 |
| **低** | [#2741](https://github.com/nanocoai/nanoclaw/pull/2741) Setup handoff 上下文无 user message | **已修复** | 仅通过 `--append-system-prompt` 传递上下文，交互式 Claude 挂起等待输入。 |

---

### 6. 功能请求与路线图信号

- **规模化记忆架构**：[#1356](https://github.com/nanocoai/nanoclaw/issues/1356) 明确要求替代当前 markdown 索引方案，预计将成为 vNext 的核心路线图项目。信号强烈，需维护者给出 RFC 时间表。
- **多 bot 部署**：[#2733](https://github.com/nanocoai/nanoclaw/pull/2733)（已合并）的原生 channel-instance 维度表明官方已认可"同一通道多 Agent"场景，预计后续将配套路由与隔离策略。
- **自动化 DevOps**：[#2742](https://github.com/nanocoai/nanoclaw/pull/2742) PR Factory 配方将 Agent 能力从"对话"扩展到"软件工程工作流"，若合并，可能催生官方

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
**日期：** 2026-06-12  
**仓库：** nearai/ironclaw

---

### 1. 今日速览

过去 24 小时 IronClaw 维持极高活跃度，共有 **30 条 Issues**（17 条新开/活跃，13 条关闭）和 **47 条 PR**（23 条待合并，24 条已合并/关闭）更新。社区正集中火力打磨 **IronClaw Reborn** 的本地开发体验与 WebUI v2 稳定性，同时生产环境切换（production cutover）相关的基础设施 Issues 被批量关闭，表明项目正从“功能构建”向“质量加固与发布准备”阶段过渡。无新版本发布，但一条包含多项 API 破坏性变更的 release PR 仍在等待合入。

---

### 2. 版本发布

**今日无新版本发布。**

> 注：PR [#3708](https://github.com/nearai/ironclaw/pull/3708) `chore: release` 仍在开放中，计划将 `ironclaw` 从 `0.24.0` 升级至 `0.29.1`，并包含 `ironclaw_common` 与 `ironclaw_skills` 的 API 破坏性变更，需关注迁移影响。

---

### 3. 项目进展

今日合并/关闭的重要 PR 与 Issues 推动了以下关键进展：

**已合并/关闭的 Pull Requests：**

- **[#4757](https://github.com/nearai/ironclaw/pull/4757)** — 修复 Automations 页面点击触发运行后跳转 `/chat/<thread_id>` 白屏/404 的问题，使触发器线程的查看、监控与审批流程在 WebUI 中完全打通。
- **[#4784](https://github.com/nearai/ironclaw/pull/4784)** — 将 Capability 运行时不可用从“中止整个 Agent 循环”降级为“正常 Tool Failure 处理”，显著提升复杂工作流的容错性。
- **[#4782](https://github.com/nearai/ironclaw/pull/4782)** — 统一 Outbound 状态存储实例，修复 WebUI 中设置的 Slack DM 交付默认值无法生效、导致触发运行结果为 `NoDefaultConfigured` 的问题。
- **[#4744](https://github.com/nearai/ironclaw/pull/4744)** — 引入扩展激活门控并加固 GSuite OAuth 运行时，解决 GitHub/Gmail/Google Drive 等 bundled extension 的端到端安装与授权复用问题。
- **[#4781](https://github.com/nearai/ironclaw/pull/4781)** — 为 Reborn binary 引入 `build` / `deslop` / `review` 自主循环命令文档，规范 AI 辅助开发工作流。

**批量关闭的生产与集成 Issues（13 条）：**

- 生产 Postgres 存储配置、生产切换门控（cutover gate）及运行时启动就绪检查相关 Issues（[#4551](https://github.com/nearai/ironclaw/issues/4551), [#4619](https://github.com/nearai/ironclaw/issues/4619), [#4620](https://github.com/nearai/ironclaw/issues/4620), [#4615](https://github.com/nearai/ironclaw/issues/4615)）全部关闭，标志 Reborn 生产底座基本就绪。
- NEAR AI 集成链路大量修复：凭证重启保留（[#4766](https://github.com/nearai/ironclaw/issues/4766)）、本地 SSO（[#4705](https://github.com/nearai/ironclaw/issues/4705)）、自动启用 MCP（[#4700](https://github.com/nearai/ironclaw/issues/4700)）、搜索 Tool 名称回退（[#4699](https://github.com/nearai/ironclaw/issues/4699)）。
- 运行时状态与配置 API（[#4595](https://github.com/nearai/ironclaw/issues/4595), [#4593](https://github.com/nearai/ironclaw/issues/4593)）完成交付。

---

### 4. 社区热点

今日讨论最活跃的议题集中在 **Reborn 本地体验**与**配置管理**：

| 议题 | 评论数 | 核心诉求 |
|------|--------|----------|
| **[#3036](https://github.com/nearai/ironclaw/issues/3036)** [EPIC] Configuration-as-Code for IronClaw Reborn | 7 条 | 用户强烈希望以声明式方式（tenant blueprints / use-case harnesses）统一管理 `.env`、workspace docs、settings JSON 与 runtime flags，替代当前无 schema、无 diff、无审计追踪的手工配置。 |
| **[#4766](https://github.com/nearai/ironclaw/issues/4766)** Chat runtime does not use UI-saved NEAR AI credentials after restart | 2 条 | 本地重启后丢失 UI 已保存的凭证，严重影响首次使用体验。 |
| **[#4703](https://github.com/nearai/ironclaw/issues/4703)** NEAR AI model picker saves display name instead of model ID | 2 条 | 模型选择器保存的是展示名（如 "DeepSeek V4 Flash"）而非模型 ID，导致后续调用失败。已有 PR [#4772](https://github.com/nearai/ironclaw/pull/4772) 批量修复。 |
| **[#4705](https://github.com/nearai/ironclaw/issues/4705)** NEAR AI SSO setup fails in local environment | 1 条 | 本地 Reborn 的 GitHub/Google SSO 因 `Invalid frontend_callback` 失败，阻断新用户 onboarding。 |

**信号：** 社区对“可重复、可审计的本地部署体验”的诉求极为强烈，配置管理（#3036）已成为长期架构债务。

---

### 5. Bug 与稳定性

今日报告的新 Bug 按严重程度排列如下：

**🔴 高优先级（影响核心工作流）**

- **[#4761](https://github.com/nearai/ironclaw/issues/4761)** — Agent 在重复 Tool Failure 后停止运行，无法自我恢复，导致长任务中断。**暂无 fix PR。**
- **[#4762](https://github.com/nearai/ironclaw/issues/4762)** — Tool Workflow 失败后，后续消息与活动顺序不一致，疑似 SSE/前端状态同步 bug。**暂无 fix PR。**

**🟡 中优先级（功能受损）**

- **[#4783](https://github.com/nearai/ironclaw/issues/4783)** — 本地开发中，无 `runtime_credentials` 的纯计算 WASM Extension Capability 在调度阶段即报 `network` obligation 错误，无法执行。**暂无 fix PR。**
- **[#4751](https://github.com/nearai/ironclaw/issues/4751)** — 大文本生成请求（如 3000 字指南）因 provider tool arguments 超过 16384 bytes 而失败。**暂无 fix PR。**
- **[#4770](https://github.com/nearai/ironclaw/issues/4770)** — 刷新页面后 Tool Activity 可能停止更新，疑似 SSE 重连问题。**暂无 fix PR。**
- **[#4703](https://github.com/nearai/ironclaw/issues/4703)** — NEAR AI 模型选择器保存展示名而非模型 ID。**→ 已由 PR [#4772](https://github.com/nearai/ironclaw/pull/4772) 修复。**
- **[#4759](https://github.com/nearai/ironclaw/issues/4759)** — 使用 `workspace/` 相对路径时发生路径重复（`workspace/workspace/...`）。**暂无 fix PR。**
- **[#4764](https://github.com/nearai/ironclaw/issues/4764)** — 拒绝 Shell 审批后，Tool Invocation 处于挂起状态且无用户反馈。**暂无 fix PR。**

**🟢 低优先级（UI/UX 瑕疵）**

- **[#4748](https://github.com/nearai/ironclaw/issues/4748)** — Code blocks 的 Wrap / No Wrap 切换无视觉效果。**暂无

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-12 | 数据来源：github.com/netease-youdao/LobsterAI*

---

### 1. 今日速览

过去 24 小时，LobsterAI 展现出极高的工程活跃度：**15 条 PR 更新（14 条已合并/关闭，1 条待合并），同时清理了 7 条积压近两个月的 stale PR**，仓库健康度显著提升。Issue 侧相对平稳，2 条 Issue 保持活跃但无关闭。开发主线明确聚焦于 **Cowork 协作体验（实时语音、网关稳定性）、分享功能矩阵（文件/HTML 访问控制）以及系统稳定性（OOM、内存泄漏、模型 Failover）**。社区层面，用户正从“单助手工具”向“多 Agent 协作系统”提出明确的架构级诉求。

---

### 2. 版本发布

**今日无新版本发布。**

---

### 3. 项目进展

今日合并/关闭的 14 条 PR 覆盖核心功能、稳定性修复与积压清理，项目在多维度同步推进：

**Cowork 协作与语音交互**
- **实时 ASR 语音输入上线**（[#2148](https://github.com/netease-youdao/LobsterAI/pull/2148)）：为 Cowork 引入基于 WebSocket 的流式实时语音识别，支持首帧 WAV header 与音频帧分片，并可在“实时识别”与“一次性录入”模式间切换。
- **修复启动-停止竞态条件**（[#2147](https://github.com/netease-youdao/LobsterAI/pull/2147)）：解决用户在网关运行激活前停止会话，仍导致消息发送的问题。
- **慢网关超时兜底**（[#2152](https://github.com/netease-youdao/LobsterAI/pull/2152)）：将预发送模型同步超时从 30s 提升至 90s，避免冷启动或进程卡顿（现场观测 35–107s）导致消息丢失。

**分享与对外协作**
- **文件分享功能**（[#2151](https://github.com/netease-youdao/LobsterAI/pull/2151)）：新增文件分享能力，覆盖 renderer、docs、main 及 artifacts 链路。
- **HTML 分享访问方式切换**（[#2146](https://github.com/netease-youdao/LobsterAI/pull/2146)）：创建 HTML 分享时支持选择“分享码”或“公开访问”，已有分享支持动态切换访问方式。

**稳定性与性能**
- **提升 OpenClaw 网关堆内存限制**（[#2149](https://github.com/netease-youdao/LobsterAI/pull/2149)）：显式设置 V8 old-space limit，显著降低长时多通道工作负载下的 OOM 崩溃率。
- **主模型故障自动 Failover**（[#1483](https://github.com/netease-youdao/LobsterAI/pull/1483)）：当主模型

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-12 | 数据来源：github.com/moltis-org/moltis*

---

### 1. 今日速览
Moltis 项目在 2026-06-12 活跃度处于低位，过去 24 小时内仅产生 1 条新增 Issue 与 1 条待合并 PR，无版本发布。开发活动集中在即时通讯网关稳定性修复（WhatsApp @lid 隐私聊天场景）与第三方服务集成故障排查（Fastmail MCP 授权）两个方向。社区整体节奏平稳，但待审 PR 与待解 Bug 各一，需维护者介入以推进代码合并与问题定位。

---

### 2. 版本发布
今日无新版本发布。

---

### 3. 项目进展
今日无已合并或关闭的 PR。唯一活跃的代码贡献为 PR #1116，该修复针对 WhatsApp 网关在隐私发送者（@lid）场景下的消息静默丢失问题，目前仍处于待合并状态。由于未产生合并提交，项目主分支今日未发生功能性前进，代码库处于等待维护者审核的状态。

---

### 4. 社区热点
- **Issue #1115: [Bug]: Fastmail MCP Authorisation**  
  链接：https://github.com/moltis-org/moltis/issues/1115  
  由 @kmath313 于昨日创建，是今日唯一活跃的 Issue。反映用户在使用 Fastmail 作为 MCP（Model Context Protocol）服务端时遭遇授权失败，表明 Moltis 与第三方邮件生态的集成边界存在兼容性摩擦。

- **PR #1116: fix(whatsapp): deliver replies to @lid chats via PN JID rewrite**  
  链接：https://github.com/moltis-org/moltis/pull/1116  
  由 @juanlotito 今日提交，针对 WhatsApp 隐私聊天场景的消息投递缺陷。诉求明确：修复网关在处理隐私启用发送者时的 JID 重写逻辑，确保回复消息能正确送达并获取送达回执。

---

### 5. Bug 与稳定性
1. **中高严重度**：WhatsApp 网关消息静默丢失（隐私发送者 @lid 场景）  
   - 影响：回复消息在 Web UI 可见但用户实际未收到，无 Delivered 回执。  
   - 状态：**已有修复 PR #1116 待合并**（https://github.com/moltis-org/moltis/pull/1116）。

2. **中等严重度**：Fastmail MCP 授权失败  
   - 影响：特定邮件服务（Fastmail）的 MCP 授权流程异常，阻碍邮件相关 Agent 工作流。  
   - 状态：已确认使用最新版本，**尚无修复 PR**，需维护者复现并定位根因。  
   - 链接：https://github.com/moltis-org/moltis/issues/1115

---

### 6. 功能请求与路线图信号
今日未出现显式的功能请求（Feature Request）类 Issue。但从 PR #1116 可提取路线图信号：开发团队正持续投入于 WhatsApp 企业级/隐私合规场景的网关可靠性，特别是 JID（Jabber ID）解析与 PN（Phone Number）重写机制。此类修复通常属于“消息通道稳定性”主线，预计将持续纳入后续补丁版本。暂无证据表明有全新功能模块即将进入主分支。

---

### 7. 用户反馈摘要
- **痛点**：WhatsApp 隐私保护用户（@lid 聊天）无法收到 Agent 回复，且系统无错误提示，属于“静默失败”，严重影响生产环境可靠性。  
- **痛点**：Fastmail MCP 授权链路存在阻塞，用户已按规范提交预检清单并使用最新版本，说明问题出在 Moltis 与 Fastmail OAuth/授权协议的交互层。  
- **场景**：用户期望 Moltis 作为 AI 助手中枢，能无缝桥接 WhatsApp 商业沟通与邮件 MCP 工具，但目前两端均存在最后一公里故障。

---

### 8. 待处理积压
基于今日数据，#1115 与 #1116 均为近 24 小时内新增，尚未形成长期积压。但鉴于两者分别涉及：
- 核心消息网关（WhatsApp）的送达可靠性；
- 主流邮件服务（Fastmail）的 MCP 集成可用性；

建议维护者优先审核 **PR #1116** 以修复生产环境消息丢失问题，并尽快在 **Issue #1115** 中提供复现指引或日志要求，防止问题滞留。

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