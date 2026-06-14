# OpenClaw 生态日报 2026-06-14

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-06-14 03:35 UTC

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
**日期：2026-06-14**

---

### 1. 今日速览

OpenClaw 在 2026-06-14 维持极高社区活跃度，24 小时内 Issues 与 PR 各更新 500 条，其中 400 条 Issues 处于新开或活跃状态，289 个 PR 待合并。项目连续发布两个 Beta 版本（v2026.6.7-beta.1 / v2026.6.8-beta.1），重点强化跨频道消息交付的可靠性。然而稳定性风险不容忽视：**一个 P0 级 Gateway 内存泄漏（#91588）仍未关闭**，且多个 P1 级子代理与会话状态问题持续积压。今日维护者通过 Clownfish 自动化机器人集中修复并关闭了多个历史 PR，同时在 Codex OAuth、Gateway 配置热重载、iOS Safari 等方向提交了新的修复补丁。

---

### 2. 版本发布

**v2026.6.8-beta.1**  
- **核心改进**：Telegram 与 WhatsApp 频道交付能力显著增强。Telegram 现支持结构化富文本（表格、列表、可展开引用块）、保留提示词的 CLI 后端交付，并退役了原生草稿迁移机制，富媒体边界处理更安全。  
- **迁移注意**：依赖旧版 Telegram 草稿迁移的自定义工作流需验证兼容性。  
- 链接：https://github.com/openclaw/openclaw/releases/tag/v2026.6.8-beta.1

**v2026.6.7-beta.1**  
- **核心改进**：全渠道消息交付 tightened。Slack 同频道最终消息将持久化保留在转录（transcript）中；顶级 `image` 消息工具可直接发送附加媒体；Telegram 支持可展开引用块与池化（spool）机制；优化了静默回复、进度草稿与分页操作结果的交付一致性。  
- **迁移注意**：Slack 转录行为变更可能影响依赖历史消息清理的外部归档逻辑。  
- 链接：https://github.com/openclaw/openclaw/releases/tag/v2026.6.7-beta.1

---

### 3. 项目进展

今日合并/关闭的重要 PR 推进了以下方向：

- **自动化修复集群（Clownfish Bot）**：今日批量修复并关闭了 4 个历史 PR，包括内存核心索引元序列化（[#92850](https://github.com/openclaw/openclaw/pull/92850)）、钩子 slug 生成器错误载荷拒绝（[#92854](https://github.com/openclaw/openclaw/pull/92854)）、ACP 服务器 MCP 协议版本兼容（[#92853](https://github.com/openclaw/openclaw/pull/92853)）以及 Tailscale JSON 解析容错（[#92849](https://github.com/openclaw/openclaw/pull/92849)），显著降低了陈旧 PR 的积压率。
- **Codex / OpenAI 生态**：提交 [#92824](https://github.com/openclaw/openclaw/pull/92824) 修复 OpenAI OAuth 媒体路由，使隐式图像模型选择具备鉴权模式感知能力；[#92839](https://github.com/openclaw/openclaw/pull/92839) 修复 `openclaw doctor --fix` 误删旧版 Codex OAuth 凭证的问题。
- **Gateway 可靠性**：[#92852](https://github.com/openclaw/openclaw/pull/92852) 在 inotify 资源耗尽时自动降级为轮询模式，保障配置热重载不中断；[#890

---

## 横向生态对比

**个人 AI 助手与自主

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报**  
*日期：2026-06-14 | 仓库：HKUDS/nanobot*

---

### 1. 今日速览

NanoBot 过去 24 小时保持高活跃度，共有 **18 个 PR** 更新（其中 5 个已合并/关闭）及 **5 个 Issue** 变动。社区焦点集中在三方面：Anthropic 新模型（opus-4-8 / Fable）的兼容性急救、WebUI 配置与部署体验优化，以及合并引入的 `session_key` 回归错误。核心层面，内存压缩逻辑与执行环境安全漏洞得到修复，项目整体向前稳步推进；但配置系统的环境变量解析链出现多处连锁缺陷，需维护者持续关注。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日合并/关闭的 5 个 PR 主要围绕稳定性、性能与工程债务：

- **内存压缩逻辑修复**：[#4326](https://github.com/HKUDS/nanobot/pull/4326) 修复了 `idleCompact` 仅对丢弃前缀做总结、遗漏最近 8 条消息后缀的 bug（[#4264](https://github.com/HKUDS/nanobot/issues/4264)），确保会话尾部的纠错与正确结果被完整归档。
- **执行环境安全与 PATH 优先级**：[#4098](https://github.com/HKUDS/nanobot/pull/4098) 合并了 exec 工具的两项修复：阻止受限命令通过相对符号链接逃逸工作区，并将 `pathAppend` 前置到 Unix PATH，使配置工具优先于系统可执行文件（[#4083](https://github.com/HKUDS/nanobot/issues/4083)）。
- **WebUI 启动性能**：[#4327](https://github.com/HKUDS/nanobot/pull/4327) 将慢速 WebUI HTTP 处理程序移出网关事件循环，避免启动时阻塞，并优化侧边栏工作区解析与会话读取策略。
- **配置系统重构**：[#4314](https://github.com/HKUDS/nanobot/pull/4314) 打破工具配置 schema 的循环导入，将共享 Pydantic Base 提取至独立模块，提升代码可维护性。
- **设置面板同步**：[#4313](https://github.com/HKUDS/nanobot/pull/4313) 缩小 WebUI 设置面板与 `config.json` 的差距，新增 temperature、工具限制、memory 等字段的写入端点与 UI 控件。

---

### 4. 社区热点

- **Ollama 本地模型支持诉求（15 条评论）**：[#193](https://github.com/HKUDS/nanobot/issues/193) 虽已于今日关闭，但自 2 月创建以来累计 15 条评论，显示社区对本地开源模型接入的强需求。目前项目主推 vLLM，Ollama 兼容层仍是用户自助集成场景的焦点。
- **Anthropic 新模型兼容性**：[#4333](https://github.com/HKUDS/nanobot/issues/4333) 报告 opus-4-8 与 Fable 因仍被发送已弃用的 `temperature` 参数而持续返回 400，社区已快速提交修复 PR [#4334](https://github.com/HKUDS/nanobot/pull/4334)。
- **交互式 TUI 大 PR**：[#4329](https://github.com/HKUDS/nanobot/pull/4329) 提出为 `nanobot agent` 新增内联交互式 T

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报**  
*日期：2026-06-14 | 分析师：AI 智能体与开源项目分析师*

---

### 1. 今日速览

PicoClaw 在 2026-06-14 保持稳健迭代节奏，过去 24 小时内合并/关闭了 **5 个 PR** 并解决 **1 个 Issue**，同时发布 `v0.2.9` 分支的 nightly 自动化构建。社区活跃度处于中等水平，代码质量修复与功能补全并行推进，但图像压缩与远程 Agent 模式两大功能 PR 仍待合入主线。Evolution 模块的 token 持续消耗问题仍是开放 Bug 中的主要用户痛点，亟需维护者介入。

---

### 2. 版本发布

**v0.2.9-nightly.20260614.cf67dd38**  
🔗 https://github.com/sipeed/picoclaw/compare/v0.2.9...main

- **发布类型**：自动化 Nightly Build（基于 `cf67dd38` 提交）。
- **稳定性提示**：官方明确标注此为自动化构建，**可能不稳定**，建议谨慎使用，生产环境请等待稳定版本。
- **变更范围**：包含自 `v0.2.9` 标签以来所有进入 `main` 分支的提交，涵盖 Agent 媒体路由修复、TTS OpenRouter 适配、资源关闭错误清理及 seahorse 引擎改进。
- **迁移注意事项**：无明确破坏性变更（Breaking Changes）；若从稳定版升级至 nightly，建议重点验证多模态管道与 TTS 语音合成路径。

---

### 3. 项目进展

今日合并/关闭的 5 个 PR 显著推进了多模态可靠性、语音合成鲁棒性与代码健康度：

- **#3117** `fix(agent): route media turns to image models`  
  🔗 https://github.com/sipeed/picoclaw/pull/3117  
  修复了 Agent 媒体路由逻辑，将媒体轮次和 `load_image` 后续请求正确导向配置的**图像模型**，而非在纯文本模型上重试。该 PR 直接解决了 Issue #3108 中 deepseek-v4-flash 等模型产生的图像描述幻觉问题，并内嵌了 `workspace/` 目录的 onboarding 机制以改善干净构建体验。

- **#3119** `fix(tts): support OpenRouter voice overrides and fallback`  
  🔗 https://github.com/sipeed/picoclaw/pull/3119  
  为 TTS 模块引入基于 `extra_body` 的 OpenRouter 语音参数（`voice`、`response_format`）覆盖能力，并实现**自动单重试回退机制**（在 `response_format` 不被支持时自动降级）。这标志着 PicoClaw 对聚合型 API 提供商生态的适配进入更精细的阶段。

- **#3065 & #3066** 系统性清理资源关闭错误  
  🔗 https://github.com/sipeed/picoclaw/pull/3065 | https://github.com/sipeed/picoclaw/pull/3066  
  在 `pkg/seahorse/short_engine.go`、`pkg/tools/normalization.go`、`pkg/channels/wecom/media.go` 等关键路径上，将静默忽略 `Close()` 返回值的行为改为显式 `_ = db.Close()` / `_ = tmpFile.Close()`，消除了 linter 警告并降低了资源泄漏与数据库 PRAGMA/migration 失败时的潜在风险。

- **#2935** `docs(i18n): add Traditional Chinese (zh-TW) locale and READMEs`  
  🔗 https://github.com/sipeed/picoclaw/pull/2935  
  虽因 **stale** 状态被关闭，但其尝试为项目引入完整的繁体中文（台湾）国际化支持（含 `zh-TW` locale、README 与贡献指南），反映了华语社区的增长需求。

---

### 4. 社区热点

今日讨论最活跃、用户诉求最集中的是以下两项：

- **#3012** `[BUG] Continuous consumption of tokens every minutes when evolution is enabled`  
  🔗 https://github.com/sipeed/picoclaw/issues/3012  
  **热度指标**：3 条评论（今日最高）。  
  **背后诉求**：用户在 FreeBSD 环境使用 MiniMax 模型并开启 Evolution（Draft 模式）时，观察到每分钟持续产生 token 消耗。这暴露了长期运行 Agent 的**成本可控性焦虑**——用户需要更细粒度的预算控制、休眠策略或 Evolution 触发频率配置。

- **#2964** `Feat/image input compression`  
  🔗 https://github.com/sipeed/picoclaw/pull/2964  
  **热度指标**：由 Issue #3108 的同一作者 @afjcjsbx 持续推动，已开放 17 天。  
  **背后诉求**：社区对多模态**成本与性能平衡**的高度关注。当前仅依赖 `max_media_size` 的单一限制无法有效阻止大图像撑爆上下文窗口，用户迫切需要可配置的多级压缩策略。

---

### 5. Bug 与稳定性

按严重程度排列：

| 严重程度 | 事项 | 状态 | 说明与链接 |
|---|---|---|---|
| 🔴 **中高风险** | Evolution 模式每分钟持续消耗 token | **OPEN** | Issue #3012，影响长期部署成本，目前**无关联 fix PR**，需维护者紧急评估 Evolution 调度逻辑。<br>🔗 https://github.com/sipeed/picoclaw/issues/3012 |
| 🟢 **已修复** | 无视觉支持模型产生图像描述幻觉 | **CLOSED** | Issue #3108，已由 #3117 修复，通过将媒体请求路由至专用图像模型解决。<br>🔗 https://github.com/sipeed/picoclaw/issues/3108 |
| 🟡 **预防性** | 多处 `Close()` 错误被静默忽略 | **CLOSED** | PR #3065、#3066 已合并，消除 linter 警告并降低资源泄漏风险。<br>🔗 https://github.com/sipeed/picoclaw/pull/3065 |

---

### 6. 功能请求与路线图信号

结合今日开放 PR 与已合并变更，以下功能极有可能被纳入下一版本（v0.3.0 或 v0.2.10）：

- **可配置图像压缩管道（#2964）**  
  该 PR 提供多级入站图像压缩策略，解决 `max_media_size` 单一阈值导致的上下文膨胀与 API 成本问题。鉴于视觉功能已被广泛使用，这是**高优先级**的功能补全。

- **远程 Pico WebSocket Agent 模式（#3118）**  
  为 `picoclaw agent` 新增 `--remote ws://` 远程模式，支持边缘部署与远程调试。这是架构从本地单节点向分布式/远程控制扩展的重要信号，建议关注其对安全模型与认证机制的影响。

- **聚合型 TTS 提供商深度适配（#3119，已合并）**  
  通过 `extra_body` 覆盖与自动回退，PicoClaw 正在从“兼容 OpenAI 接口”走向“深度适配 OpenRouter 等聚合平台”，预计后续会有更多针对提供商特性的精细化配置。

---

### 7. 用户反馈摘要

从今日 Issues 与关联 PR 中提炼的真实用户声音：

- **成本可控性痛点**：#3012 用户明确反馈 Evolution 在 Draft 状态下“每分钟都在烧钱”，暗示当前进化机制缺乏预算上限、触发频率调节或休眠策略，对商业 API（如 MiniMax）用户极不友好。
- **多模态可靠性期望**：#3108 用户在使用 `deepseek/deepseek-v4-flash` 等低成本文本模型时，期望系统**自动识别模型能力边界**并正确路由视觉请求，而非产生与图像无关的幻觉答案。
- **平台多样性**：#3012 运行在 **FreeBSD-15.0-release-p9**，表明 PicoClaw 用户群体已覆盖传统 Linux 之外的服务器环境，对跨平台稳定性与系统调用兼容性提出更高要求。

---

### 8. 待处理积压

以下 Issue/PR 长期未获最终响应或合入，提醒维护者关注：

- **#2964** `Feat/image input compression`  
  🔗 https://github.com/sipeed/picoclaw/pull/2964  
  已开放 **17 天**，是解决视觉管道成本问题的关键功能 PR，建议维护者优先审阅并给出合并或修改意见。

- **#3012** Evolution 模式 token 持续消耗  
  🔗 https://github.com/sipeed/picoclaw/issues/3012  
  已存在 **9 天**，累计 3 条评论但**无维护者响应或修复计划**。该问题直接影响用户留存与长期部署可行性，建议尽快复现并标记优先级。

- **#3118** 远程 Pico WebSocket 模式  
  🔗 https://github.com/sipeed/picoclaw/pull/3118  
  刚提交 2 天，属于架构级新功能。建议尽早评估其对现有 Agent 本地执行模型的兼容性，以及远程模式下的身份验证与安全边界设计。

---

*日报基于 GitHub 公开数据生成，仅供项目健康度参考。*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报**  
*日期：2026-06-14*

---

### 1. 今日速览

IronClaw 项目在 6 月 14 日保持极高开发强度，过去 24 小时内 **23 个 PR** 发生更新（5 条已合并/关闭，18 条待审），同时新增 **2 条 Issue**。核心贡献者正集中火力解决 Slack 集成的 re-approval 循环缺陷（#4839、#4843、#4844）、推进附件系统端到端重构（Epic #4644 系列 Tracks），并提升 Reborn 运行时的容错与可恢复能力（#4841）。社区表面讨论度偏低（评论数普遍为 0），但代码交付节奏稳健，项目整体处于**功能冲刺与稳定性修复并行**的健康状态。

---

### 2. 版本发布

**无新版本发布。**

但需注意已开放近一个月的发布 PR [#3708](https://github.com/nearai/ironclaw/pull/3708) 仍待合并。该 PR 计划将 `ironclaw_common` 升级至 0.5.0、`ironclaw_skills` 升级至 0.4.0，并包含明确的 API 破坏性变更（`ironclaw_common` 与 `ironclaw_skills` 均标记为 ⚠ breaking）。下游依赖方应提前评估迁移成本。

---

### 3. 项目进展

今日附件系统重构（Epic #4644）取得里程碑式进展，**5 条 PR 完成合并/关闭**，正式打通端到端数据流：

- **[#4654](https://github.com/nearai/ironclaw/pull/4654)**（已关闭）：建立可扩展的附件格式注册表，消除此前分散在通道白名单、MIME→扩展名映射、提取器分发和前端 `accept` 属性中的四处硬编码列表，根治“CSV 被当作文本上传”类漂移 Bug。
- **[#4655](https://github.com/nearai/ironclaw/pull/4655)**（已关闭）：Reborn transcript 合约正式支持携带附件引用（`AttachmentRef`），附件元数据不再在持久化环节静默丢失。
- **[#4668](https://github.com/nearai/ironclaw/pull/4668)**（已关闭）：引入 `MountView`-based 附件落地 crate，为字节存储提供基础能力，使模型可见附件的前提（bytes living in storage）得以满足。
- **[#4670](https://github.com/nearai/ironclaw/pull/4670)**（已关闭）：桥接入站字节流与 transcript `AttachmentRef`s，实现 `storage_key` 与消息引用的关联。
- **[#4672](https://github.com/nearai/ironclaw/pull/4672)**（已关闭）：WebChat v2 支持内联附件上传，浏览器文件可经文件系统权限落入项目存储，并完成端到端 ingress 接线。

这标志着附件从**上传 → 落地存储 → 文本提取 → transcript 持久化**的全链路已正式闭环。

---

### 4. 社区热点

尽管过去 24 小时评论数为 0，以下 PR/Issue 因涉及核心稳定性与架构演进，成为事实上的技术焦点：

- **[#4839](https://github.com/nearai/ironclaw/pull/

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报**  
*日期：2026-06-14 | 仓库：netease-youdao/LobsterAI*

---

### 1. 今日速览

过去 24 小时，项目共产生 9 条事务状态更新（Issues 4 条、PR 5 条），但**全部为 4 月初积压项的批量 stale 标记或状态变更，无当日新建 Issue/PR 及版本发布**。其中 2 个 PR 被关闭，3 个功能/修复 PR 仍待合并；4 个 Issue 均保持 Open 且已挂 stale 标签。整体活跃度偏低，社区以“存量清理”为主，维护者对长期积压事项的响应速度是当前健康度的主要瓶颈。

---

### 2. 版本发布

**无新版本发布。**  
今日未发布 Release，项目最新可用版本保持不变。

---

### 3. 项目进展

今日关闭的 2 个 PR 均为体验级修复，核心功能线尚未推进：

- **#1466** `fix(mcp): modal close button unreachable when content grows tall`  
  修复 MCP Server 表单模态框在内容过长时（如添加多组 env vars），因整体滚动导致关闭/取消按钮滑出视口的布局缺陷。将滚动区域限定在内容体，确保头部与底部操作区固定可见。  
  [→ 查看 PR](https://github.com/netease-youdao/LobsterAI/pull/1466)

- **#1467** `fix(shortcuts): display Cmd (⌘) instead of Ctrl on macOS`  
  修复快捷键设置面板在 macOS 下错误显示 `Ctrl` 的问题，改为遵循平台惯例显示 `⌘`，提升跨平台体验一致性。  
  [→ 查看 PR](https://github.com/netease-youdao/LobsterAI/pull/1467)

**待合并（3 条）：**  
- **#1440** 技能标签从底部工具栏移至输入框顶部，优化布局层级。  
- **#1441** 引入可扩展的 Artifacts 预览管道（HTML / React / Mermaid），该 PR 是 #1011 的冲突解决与 bug 修复重提版，已解决 10 个冲突文件并修复 5 个运行时缺陷。  
- **#1445** 修复技能 zip 导入目录名随机化及重复导入无校验问题。  

[→ #1440](https://github.com/netease-youdao/LobsterAI/pull/1440) | [→ #1441](https://github.com/netease-youdao/LobsterAI/pull/1441) | [→ #1445](https://github.com/netease-youdao/LobsterAI/pull/1445)

---

### 4. 社区热点

今日讨论热度集中在 **Skills（技能）系统** 的生命周期管理与 UI 反馈，3 个相关议题形成明确诉求集群：

| 事项 | 类型 | 核心诉求 |
|---|---|---|
| **#1445** | PR (待合并) | 技能导入需校验重复，zip 解压目录名需可读 |
| **#1439** | Issue (Open) | 技能“停用”状态应在对话路由中真正失效 |
| **#1442** | Issue (Open) | Agent 技能选中后在对话中消失，用户困惑触发逻辑 |

**分析：** 用户正在将 Skills 用于生产级 Agent 工作流，对“启用/停用/导入”状态的可预期性和 UI 反馈清晰度要求显著提高。当前系统存在“状态不同步、反馈缺失、校验不足”三类体验断层。

[→ #1439](https://github.com/netease-youdao/LobsterAI/issues/1439) | [→ #1442](https://github.com/netease-youdao/LobsterAI/issues/1442) | [→ #1445](https://github.com/netease-youdao/LobsterAI/pull/1445)

---

### 5. Bug 与稳定性

按严重程度排列今日活跃的 Bug 报告：

- **P1 · 高 · 状态同步缺陷**  
  **#1439** `上传技能已停用，对话中仍然可以调用`  
  技能关闭后仍可通过关键字触发，存在权限与路由稳定性风险。**暂无 fix PR。**

- **P2 · 中 · 前端交互阻塞**  
  **#1437** `创建定时任务时，计划选择不重复，清空日历，点击【创建任务】按钮没反应`  
  表单校验或状态管理异常导致按钮无响应，且页面无错误提示，用户无法自助排查。**暂无 fix PR。**

- **P2 · 中 · 前端状态丢失**  
  **#1442** `Agent添加技能，对话后引用的技能不展示`  
  技能选中状态在对话后消失，需重新切换 Agent 会话才恢复，影响多轮对话体验。**暂无 fix PR。**

- **P3 · 低-中 · 外部依赖 Breaking Change**  
  **#1443** `有计划支持新版本的 openclaw 吗？`  
  openclaw v2026.3.24 引入破坏性变更，导致本地无法拉起，阻塞用户升级。**暂无 fix PR。**

**已有修复/待合并：**  
- #1466、#1467（已关闭）  
- #1445（待合并，仅覆盖导入侧重复与目录名问题，不覆盖 #1439 的运行时停用失效）

[→ #1437](https://github.com/netease-youdao/LobsterAI/issues/1437) | [→ #1439](https://github.com/netease-youdao/LobsterAI/issues/1439) | [→ #1442](https://github.com/netease-youdao/LobsterAI/issues/1442) | [→ #1443](https://github.com/netease-youdao/LobsterAI/issues/1443)

---

### 6. 功能请求与路线图信号

- **Artifacts 预览管道扩展（高概率纳入）**  
  **#1441** 提供了 HTML、React、Mermaid 的可扩展预览能力，且明确说明是 #1011 的“冲突解决 + 5 个运行时 bug 修复”重提版。该 PR 投入成本较高、功能完整度好，是下一版本中最有可能被合入的大特性。

- **技能系统 UX 重构（中概率纳入）**  
  **#1440** 将 ActiveSkillBadge 从底部工具栏移入输入框顶部，解决“技能多选时布局拥挤”问题，与 #1442、#1445 共同构成 Skills 体验优化包，建议打包评审。

- **底层依赖升级（待路线图确认）**  
  **#1443** 反映社区对 openclaw 新版本适配的刚需，需维护者评估 breaking change 影响范围后给出时间表。

[→ #1441](https://github.com/netease-youdao/LobsterAI/pull/1441) | [→ #1440](https://github.com/netease-youdao/LobsterAI/pull/1440) | [→ #1443](https://github.com/netease-youdao/LobsterAI/issues/1443)

---

### 7. 用户反馈摘要

从 Issue 描述中提炼的真实痛点：

1. **“状态不可信”** — 用户明确关闭技能后，对话中依旧能被调用（#1439），说明技能生命周期管理存在后端/路由层与前端展示层的状态不一致。
2. **“反馈黑洞”** — 前端交互失败时无错误提示（#1437）、技能选中后视觉消失（#1442），用户无法确认系统是否接收到操作。
3. **“导入不可控”** — zip 导入后目录名为随机字符串（#1445），且同名技能静默追加 `-1` 后缀，导致 system prompt 中注入重复技能，影响大模型路由。
4. **“跨平台/升级成本”** — macOS 快捷键显示错误（已修复）与 openclaw 升级阻断（#1443）显示用户群体覆盖多平台，且希望紧跟上游依赖版本。

**使用场景画像：** 用户在通过 Agent + Skills 构建相对复杂的自动化工作流，对“技能启停、定时任务、Artifacts 渲染”的稳定性与可预期性有生产环境要求。

---

### 8. 待处理积压

以下 Issue 与 PR 均创建于 **2026-04-03/04**，已积压逾两个月，昨日被统一标记为 `stale`，存在“自动关闭”或“再次冲突”风险，建议维护者优先处理：

| 类型 | 编号 | 标题 | 风险提醒 |
|---|---|---|---|
| Issue | #1437 | 定时任务创建无响应 | 纯前端 bug，修复成本低，长期未响应影响基础功能口碑 |
| Issue | #1439 | 技能停用后仍可调用 | 涉及权限/路由，安全风险随用户量增加而放大 |
| Issue | #1442 | Agent 技能展示消失 | UX 设计疑问需产品/开发共同答复 |
| Issue | #1443 | 适配 openclaw 新版本 | 依赖越滞后，breaking change 累积越多 |
| PR | #1440 | 技能标签 UI 重构 | 待代码评审，与 #1442 可联动解决 |
| PR | #1441 | Artifacts 预览管道 | **#1011 的重提版**，若继续搁置将再度与 main 冲突，前期投入沉没成本高 |
| PR | #1445 | 修复技能重复导入 | 已提供完整修复，建议尽快合入减少用户侧脏数据 |

[→ #1437](https://github.com/netease-youdao/LobsterAI/issues/1437) | [→ #1439](https://github.com/netease-youdao/LobsterAI/issues/1439) | [→ #1442](https://github.com/netease-youdao/LobsterAI/issues/1442) | [→ #1443](https://github.com/netease-youdoudao/LobsterAI/issues/1443) | [→ #1440](https://github.com/netease-youdao/LobsterAI/pull/1440) | [→ #1441](https://github.com/netease-youdao/LobsterAI/pull/1441) | [→ #1445](https://github.com/netease-youdao/LobsterAI/pull/1445)

---

*日报结论：LobsterAI 今日无新增功能交付，社区活动以 stale 积压项的批量状态更新为主。建议维护者在近期安排一次 Skills 模块专项评审（#1439 / #1440 / #1442 / #1445），并优先合入 #1441 以避免再次冲突，从而提振项目健康度。*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报**  
*日期：2026-06-14*

---

### 1. 今日速览

过去 24 小时，Moltis 项目保持中等活跃度，社区新增 1 个 Issue 与 3 个 Pull Request，但暂无 PR 被合并或关闭，亦无新版本发布。当前工作重心集中在 MCP 协议 OAuth 兼容性的关键修复、Docker 部署路径冲突的修正，以及前端构建依赖的例行升级。整体而言，项目处于“问题修复待审阅”阶段，代码落地速度取决于维护者的合并节奏。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 项目进展

今日无已合并或已关闭的 PR，但社区提交了 3 个待审阅的 PR，推动以下方向：

- **MCP OAuth 协议兼容性修复**：PR [#1120](https://github.com/moltis-org/moltis/pull/1120) 针对 `WWW-Authenticate` 头中 `resource_metadata` 参数的处理逻辑进行修正，直接解决 Notion、Linear 等主流 MCP 服务器接入失败的问题。
- **Docker 部署稳定性修复**：PR [#1122](https://github.com/moltis-org/moltis/pull/1122) 移除 Dockerfile 中与 home 目录 bind mount 冲突的 `VOLUME` 声明，避免部署时配置与数据丢失。
- **前端构建链维护**：PR [#1121](https://github.com/moltis-org/moltis/pull/1121) 将 `esbuild` 从 `0.25.12` 升级至 `0.28.1`，跟进构建工具的安全性与性能更新。

尽管代码尚未合入主线，社区在协议兼容性、部署稳定性和依赖健康度三方面均提供了明确的修复方案，项目整体向前推进了关键的技术债务清理与生态集成能力。

---

### 4. 社区热点

今日讨论焦点集中在 **Issue [#1119](https://github.com/moltis-org/moltis/issues/1119)**（MCP OAuth `invalid_target` 错误），这是过去 24 小时内唯一产生评论的议题。

- **诉求分析**：该 Issue 揭示了用户正在尝试将 Moltis 与 Notion、Linear 等主流 SaaS 的 MCP 服务器进行集成，属于真实的生产/工作流接入场景。`WWW-Authenticate` 头中 `resource_metadata` 参数的处理失败，直接阻断了第三方 MCP 生态的扩展，社区对此有明确的“协议兼容性”诉求。
- **响应速度**：Issue 创建后不到一日，作者 @xzavrel 即提交了对应的修复 PR [#1120](https://github.com/moltis-org/moltis/pull/1120)，显示核心贡献者对 MCP 生态集成问题的高度敏感。

---

### 5. Bug 与稳定性

按严重程度排列：

| 严重程度 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| **高** | **MCP OAuth 授权失败**：使用 `resource_metadata` 的 MCP 服务器（Notion、Linear）在 OAuth 流程中返回 `invalid_target`，导致无法完成远程服务器注册。 | 开放 | [#1120](https://github.com/moltis-org/moltis/pull/1120) |
| **中** | **Docker 数据丢失风险**：Dockerfile 中的 `VOLUME` 声明与常见的 home 目录 bind mount（如 `./moltis-home:/home/moltis`）产生冲突，可能导致容器内配置与数据不可见或丢失。 | 开放 | [#1122](https://github.com/moltis-org/moltis/pull/1122) |

---

### 6. 功能请求与路线图信号

今日无新增功能请求（Feature Request）类 Issue。

从现有 PR 推断路线图信号：
- **MCP 生态集成优先**：PR [#1120](https://github.com/moltis-org/moltis/pull/1120) 表明项目正积极对齐 MCP 协议的 OAuth 实现细节，兼容 Notion、Linear 等头部 SaaS 是当前的隐性路线图目标。
- **前端基础设施维护**：PR [#1121](https://github.com/moltis-org/moltis/pull/1121) 对 `esbuild` 的大版本升级，暗示 `/crates/web/ui` 仍在活跃维护，可能为后续的 Web UI 功能迭代或性能优化铺路。

---

### 7. 用户反馈摘要

从 Issue [#1119](https://github.com/moltis-org/moltis/issues/1119) 可提炼以下真实用户信号：

- **使用场景**：用户正在将 Moltis 作为 MCP 客户端，接入 Notion、Linear 等外部知识管理与项目管理工具，属于典型的“AI 助手 + SaaS 生态”联动场景。
- **核心痛点**：Moltis 的 OAuth 2.0 实现未能正确处理 `WWW-Authenticate` 响应头中的 `resource_metadata` 字段，导致授权窗口直接报错，阻断工作流。
- **满意度/不满意度**：用户对 Moltis 支持 MCP 协议持积极尝试态度，但对协议边缘场景的兼容性（尤其是主流 SaaS 的实际实现）存在明显挫败感。

---

### 8. 待处理积压

今日所有新增 Issue 与 PR 均处于开放且未合并状态，建议维护者优先关注以下积压项：

- **Issue [#1119](https://github.com/moltis-org/moltis/issues/1119) + PR [#1120](https://github.com/moltis-org/moltis/pull/1120)**：MCP OAuth 关键修复，直接影响第三方生态扩展能力，已有一日未获审阅。
- **PR [#1122](https://github.com/moltis-org/moltis/pull/1122)**：Docker 部署隐患修复，影响自托管用户的首次部署体验与数据持久化。
- **PR [#1121](https://github.com/moltis-org/moltis/pull/1121)**：Dependabot 提交的依赖升级，建议尽快审阅以消除潜在的安全或构建风险。

---

*日报基于 GitHub 公开数据生成，所有链接均指向 `github.com/moltis-org/moltis`。*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw 项目动态日报 | 2026-06-14**

---

### 1. 今日速览

过去 24 小时，CoPaw（`agentscope-ai/QwenPaw`）社区保持高活跃度，共有 **8 条 Issues**（7 条开放/活跃、1 条关闭）与 **9 条 PRs**（7 条待合并、2 条已合并/关闭）更新。首次贡献者表现亮眼，单日提交 6 个修复/优化 PR，涵盖备份容错、上下文空值保护、Linux 浏览器检测等边缘场景。国际化需求显著上升，越南语界面支持已有人提交完整 PR。稳定性方面，Tauri 桌面端启动性能衰退与上下文压缩导致信息丢失成为用户最尖锐的反馈。

---

### 2. 版本发布

**无新版本发布。**  
今日未发布 Release，项目版本仍维持在 `v1.1.11` 附近。

---

### 3. 项目进展

今日共有 **2 条 PR 已合并/关闭**，推动项目在本地化与技能管理方面向前迈进：

- **PR #2498** — `fix(agents): use console language when creating agent and fallback unsupported langs`  
  修复了新创建 Agent 总是默认使用英语、且无论用户 UI 语言如何都复制中文人设文件的问题。现在创建 Agent 时会读取 `localStorage` 中的控制台语言，并在服务端进行校验与自动回退。  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/2498

- **PR #4969** — `feat(skill): Add skill tag batch download`  
  技能市场支持按标签批量下载到工作区，解决了此前只能全量或单一下载的痛点。  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/4969

---

### 4. 社区热点

今日讨论最活跃、反映社区核心诉求的议题如下：

| 议题 | 评论数 | 核心诉求 |
|------|--------|----------|
| **#5156** 建议支持 `kimi-for-coding` / 加入 `uv` 白名单 | 4 | 付费订阅用户希望复用已有 Kimi Coding 套餐，降低 API 调用成本，而非重复购买官方 API。 |
| **#5047** Windows Tauri 桌面端启动特别慢 | 3 | 从 Python 打包迁移到 Tauri 后，启动时间从 1–2 分钟恶化到 10 分钟以上，且频繁无响应。 |
| **#5169 / #5175** 越南语界面支持 | 2 (Issue) + PR | 东南亚用户群体扩张，要求 Console 前端增加 `vi` 语言，并已有首次贡献者提交完整实现。 |

**背后信号：** 社区正从“核心功能可用”转向“成本优化、性能体验、国际化”阶段，对桌面端技术选型的容忍度降低。

---

### 5. Bug 与稳定性

按严重程度排列的今日 Bug 与稳定性问题：

**🔴 严重（影响核心功能/数据完整性）**

- **#5171** — 上下文压缩保留缺少按条数保留或排除人设文件，导致信息完全丢失，任务中断  
  当 Agent 人设文件 token 大于保留阈值时，压缩后上下文变为 0，模型无法继续任务。**暂无 fix PR。**  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5171

- **#5172** — 聊天总出现问完问题没反应一直等待（`Error: Task has been cancelled!`）  
  会话闲置后再提问会无限等待，接入 QQ/微信时因无法点击“停止”而直接卡死。Issue 已于今日关闭，但用户情绪激烈，需确认根因是否真正修复。  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5172

- **#5047** — Windows Tauri 桌面端启动特别慢（10 分钟+ / 无响应）  
  影响 Windows 11 大量用户，属于架构迁移后的性能回归。**暂无 fix PR。**  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5047

**🟡 中等（功能受限/边缘场景崩溃）**

- **#5174** — 定时任务和心跳机制的缺陷  
  Cron Agent 能运行 Python 脚本但无法产出知识文件；心跳 Agent 理论上能做重任务但实际不执行。用户质疑这是机制固有限制。  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5174

**🟢 已有 Fix PR（首次贡献者集中提交，待合并）**

- **#5038** — 修复 `LightContextManager.pre_reply` 中空消息列表导致的 `IndexError`  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/5038

- **#5040** — 修复 `jobs.json` 中单个无效任务导致全部定时任务加载失败的问题  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/5040

- **#5041** — 修复备份时单个不可读文件导致整个备份失败的问题  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/5041

- **#5037** — 修复 Linux 浏览器检测中 `Exec=` 为空时的 `IndexError`  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/5037

- **#5035** — 修复 llama.cpp 服务端版本号解析硬编码切片导致 5 位版本号静默失败的问题  
  🔗 https://github.com/agentscope-ai/QwenPaw/pull/5035

---

### 6. 功能请求与路线图信号

- **#5156** — `kimi-for-coding` / `uv` 白名单支持  
  属于生态接入与成本优化需求，若官方希望降低用户接入门槛，可考虑允许白名单内的本地/第三方模型客户端。

- **#5168** — 官方 Zalo Bot 频道支持  
  Zalo 是越南主流 IM，与 #5169 越南语界面请求形成明确的地域市场信号。建议维护者将“越南/东南亚本地化包”纳入下一版本路线图。

- **#5175** — 越南语（`vi`）界面支持 PR  
  已实现前端 i18n 翻译并优雅回退英文，代码质量符合合并标准，**高概率可纳入下一版本**。

- **#5173** — Console 前端功能请求（具体需求待补充）  
  作者勾选仅影响 Console，需维护者进一步澄清需求范围。

---

### 7. 用户反馈摘要

**真实痛点：**
- **性能倒退：** Tauri 桌面端在 Windows 上启动速度“从一两分钟变成十几分钟”，且启动期无响应，重装无效。
- **长会话稳定性：** 聊天间隔一段时间后再次提问会无限等待，必须手动停止后重新发送；若接入 QQ/微信等无头渠道，问题会直接“卡死”整个会话。
- **上下文管理失控：** 用户发现当人设文件较大时，上下文压缩策略会“一刀切”导致保留 token 为 0，任务直接中断，且缺乏按条数或排除人设文件的细粒度控制。
- **付费权益无法复用：** 已订阅 Kimi Coding 套餐的用户被迫再购买官方 API 才能接入，产生双重成本。

**使用场景：**
- 通过 QQ、微信等渠道接入 Agent 的自动化工作流（对“停止”按钮不可用场景极度敏感）。
- 越南本地用户/企业希望将 Agent 接入 Zalo 进行日常助理工作。

**情绪倾向：** 对 Tauri 迁移后的性能表现和心跳/Cron 机制的实际效用表达失望；对项目长期维护投入表示认可，但对“严重 Bug 持续存在”容忍度降低。

---

### 8. 待处理积压

以下 PR/Issue 已长期未获最终响应，建议维护者优先审阅，避免首次贡献者流失：

- **5 条首次贡献者 PR 审核中（创建于 2026-06-09，已积压 5 天）：**  
  - #5035（llama.cpp 版本解析）、#5037（Linux 浏览器检测）、#5038（上下文空列表保护）、#5040（Cron 任务容错）、#5041（备份容错）。  
  均为边缘场景的稳定修复，风险低、合并价值高。  
  🔗 见上文 PR 链接。

- **#5047** — Windows Tauri 桌面端启动慢  
  创建于 2026-06-09，已持续 5 天无官方技术回应。该问题直接影响 Windows 用户留存，建议维护者复现并给出性能剖析计划或回滚评估。  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5047

- **#5156** — Kimi-for-coding 白名单  
  评论数已达 4 条，涉及付费用户核心利益，需产品侧明确第三方模型接入策略。  
  🔗 https://github.com/agentscope-ai/QwenPaw/issues/5156

---

*日报基于 GitHub 公开数据生成，仅供项目健康度参考。*

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