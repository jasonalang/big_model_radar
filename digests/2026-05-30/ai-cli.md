# AI CLI 工具社区动态日报 2026-05-30

> 生成时间: 2026-05-30 14:44 UTC | 覆盖工具: 7 个

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## 横向对比



---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**（数据截止 2026-05-30）

---

### 1. 热门 Skills 排行（按社区关注度）

| 排名 | Skill (PR) | 核心功能 | 社区讨论热点 | 状态 |
|---|---|---|---|---|
| 1 | **document-typography**<br>[#514](https://github.com/anthropics/skills/pull/514) | AI 生成文档的排版质量控制：修复孤字、寡行、编号错位等通用排版缺陷。 | 被视为所有 Claude 文档输出的底层刚需；讨论集中在如何零侵入地集成到现有 docx/ODT/PDF 工作流。 | Open |
| 2 | **odt**<br>[#486](https://github.com/anthropics/skills/pull/486) | OpenDocument（.odt/.ods）创建、模板填充及 ODT→HTML 解析。 | 企业开源合规场景需求强烈，社区关注与 LibreOffice 生态的互操作性和 ISO 标准兼容性。 | Open |
| 3 | **frontend-design**<br>[#210](https://github.com/anthropics/skills/pull/210) | 重写前端设计 Skill，提升指令清晰度与单轮对话可执行性。 | 讨论聚焦于"如何让设计约束真正落地为代码"，避免空泛指导导致反复修正。 | Open |
| 4 | **skill-quality-analyzer /<br>skill-security-analyzer**<br>[#83](https://github.com/anthropics/skills/pull/83) | 元 Skill：从结构、文档、安全等五维度评估 Skill 质量与风险。 | 社区呼吁建立官方 Skill 审核标准，此类元工具被视为生态治理的基础设施。 | Open |
| 5 | **SAP-RPT-1-OSS**<br>[#181](https://github.com/anthropics/skills/pull/181) | 基于 SAP 开源表格基础模型的业务数据预测分析。 | 企业 ERP 用户关注与 SAP 数据的对接方式及 Apache 2.0 模型许可合规性。 | Open |
| 6 | **testing-patterns**<br>[#723](https://github.com/anthropics/skills/pull/723) | 全栈测试指南：Testing Trophy、AAA 模式、React 组件测试、Mock 策略等。 | 开发者希望统一 Claude 生成测试代码的风格与覆盖率标准，减少"测什么、怎么测"的歧义。 | Open |
| 7 | **AURELION**<br>[#444](https://github.com/anthropics/skills/pull/444) | 四件套认知框架（kernel / advisor / agent / memory），用于专业知识管理与 AI 协作。 | AI 长期记忆与结构化认知是前沿热点，讨论涉及与现有 MCP 记忆机制的边界划分。 | Open |
| 8 | **ServiceNow**<br>[#568](https://github.com/anthropics/skills/pull/568) | 覆盖 ITSM、ITOM、SecOps、ITAM、FSM、SPM 等企业平台的综合助手。 | 企业 IT 管理员关注权限模型与生产实例的安全连接方案。 | Open |

---

### 2. 社区需求趋势（基于 Issues 高赞与高评论议题）

- **组织级 Skill 共享与治理**（[#228](https://github.com/anthropics/skills/issues/228), [#492](https://github.com/anthropics/skills/issues/492), [#412](https://github.com/anthropics/skills/issues/412)）  
  企业用户强烈需要 org-wide 的 Skill 库共享机制，同时担忧社区 Skill 冒用 `anthropic/` 命名空间带来的信任边界问题，呼吁官方治理框架与签名验证。

- **企业平台与云生态集成**（[#29](https://github.com/anthropics/skills/issues/29), [#568](https://github.com/anthropics/skills/pull/568), [#1175](https://github.com/anthropics/skills/issues/1175), [#16](https://github.com/anthropics/skills/issues/16)）  
  AWS Bedrock、ServiceNow、SharePoint Online 等集成需求密集，社区希望 Skill 能作为桥梁连接内部企业系统，同时解决上下文窗口膨胀与数据安全顾虑。

- **开发者工具链与质量工程**（[#556](https://github.com/anthropics/skills/issues/556), [#202](https://github.com/anthropics/skills/issues/202), [#723](https://github.com/anth

---

**Claude Code 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览
今日 Anthropic 连发 v2.1.157 与 v2.1.158，将 Auto mode 扩展至 Bedrock、Vertex 和 Foundry，并正式支持本地 `.claude/skills` 插件自动加载，无需 Marketplace。社区方面，多账户支持（#27302）持续高热，而 Opus 4.8 的 thinking blocks 崩溃（#63147、#63364）与 1M 上下文默认策略（#62063、#63896）成为开发者集中反馈的痛点。

---

### 2. 版本发布

**v2.1.158**  
- Auto mode 现已支持 Bedrock、Vertex 和 Foundry 平台上的 Opus 4.7 与 Opus 4.8，可通过环境变量 `CLAUDE_CODE_ENABLE_AUTO_MODE=1` 开启。  
[查看 Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.158)

**v2.1.157**  
- `.claude/skills` 目录下的插件现在会自动加载，无需经过 Marketplace。  
- 新增 `claude plugin init <name>` 命令，用于在 `.claude/skills` 中快速脚手架新插件。  
- 为 `/plugin` 命令参数增加自动补全（子命令、已安装插件名、已知插件）。  
[查看 Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.157)

---

### 3. 社区热点 Issues

| # | 标题 | 核心看点 |
|---|------|----------|
| [#27302](https://github.com/anthropics/claude-code/issues/27302) | Support multiple Connector accounts | **高票需求**（252👍，190 评论）。企业用户强烈希望在同一 Connector 下配置多账户，以便区分个人与组织资源。 |
| [#63147](https://github.com/anthropics/claude-code/issues/63147) | Resuming extended-thinking session fails permanently | **严重 Bug**（50 评论）。使用 extended thinking + tool calls 后恢复会话会触发 400 错误，导致会话永久损坏，影响长任务连续性。 |
| [#22264](https://github.com/anthropics/claude-code/issues/22264) | Sibling tool call errored: parallel tool calls cascade-fail | **架构级缺陷**（44👍，23 评论）。单次消息中的并行工具调用一旦有一个失败，其余兄弟调用会被自动取消，造成不必要的重试与 Token 浪费。 |
| [#41179](https://github.com/anthropics/claude-code/issues/41179) | Enable Auto mode support for Amazon Bedrock | **已兑现需求**（143👍）。社区长期呼吁的 Bedrock Auto mode 终于在 v2.1.158 落地，Issue 仍被大量用户用作反馈入口。 |
| [#47166](https://github.com/anthropics/claude-code/issues/47166) | JetBrains need some love - a real Claude AI Assist interface plugin | **IDE 生态缺口**（21 评论）。JetBrains 用户呼吁官方提供与 VS Code 体验对等的原生插件，而非仅依赖终端。 |
| [#61993](https://github.com/anthropics/claude-code/issues/61993) | Sub-agents cannot spawn other sub-agents | **Agent 架构限制**（17 评论）。`Task`/`Agent` 原语未在嵌套上下文中暴露，阻碍了复杂多层级工作流的实现。 |
| [#62063](https://github.com/anthropics/claude-code/issues/62063) | Claude Code defaults to 1M context on fresh session with no workaround | **成本痛点**（13 评论，9👍）。Pro 计划用户发现新会话默认使用 1M 上下文且无显式降级开关，导致额度快速消耗。 |
| [#63364](https://github.com/anthropics/claude-code/issues/63364) | Opus 4.8 Fails to use tools and softbricks context | **新模型回归**（7👍）。Opus 4.8 在特定场景下因 `Cannot modify thinking blocks` 错误陷入软锁，与 #63147 症状同源。 |
| [#63797](https://github.com/anthropics/claude-code/issues/63797) | Bash/Read tool results intermittently return empty on Linux | **Linux 稳定性**（6 评论）。高并发长会话中，Bash 与 Read 工具间歇性向模型返回空内容，但命令实际已成功执行。 |
| [#63903](https://github.com/anthropics/claude-code/issues/63903) | autoMemoryEnabled=false does not suppress memory preamble | **配置失效**（3 评论）。关闭自动记忆后，系统提示词中仍硬编码约 11–16k 的 memory preamble，造成隐式上下文占用。 |

---

### 4. 重要 PR 进展

| # | 标题 | 说明 |
|---|------|------|
| [#63686](https://github.com/anthropics/claude-code/pull/63686) | Bump stale and autoclose timeouts from 14 to 90 days | 社区治理调整：Issue 的 stale 与自动关闭周期从 14 天延长至 90 天，减少活跃讨论被误关。 |
| [#63467](https://github.com/anthropics/claude-code/pull/63467) | docs: add Windows gh CLI install instruction | 补充 Windows 平台 `winget install --id GitHub.cli` 的安装指引，完善跨平台文档。 |
| [#45150](https://github.com/anthropics/claude-code/pull/45150) | docs: expand CLAUDE_CODE_ACCESSIBILITY docs | 扩展无障碍文档，说明 `CLAUDE_CODE_ACCESSIBILITY=1` 如何同步终端光标与对话框焦点，以支持读屏软件。 |
| [#45151](https://github.com/anthropics/claude-code/pull/45151) | docs: add FORCE_HYPERLINK environment variable | 新增 `FORCE_HYPERLINK` 环境变量文档，覆盖 tmux/screen 等终端下的超链接强制开关行为。 |
| [#39043](https://github.com/anthropics/claude-code/pull/39043) | Remove "retro-futuristic" recommendation from Frontend Design Skill | 移除前端设计 Skill 中“复古未来主义”的默认推荐，避免风格偏见。 |
| [#63872](https://github.com/anthropics/claude-code/pull/63872) | docs: fix README capitalization and wording | 标准化 README 中 `GitHub`、`macOS` 等产品大小写，并优化可读性。 |
| [#45156](https://github.com/anthropics/claude-code/pull/45156) | docs: fix accidental strikethrough in Korean Tool Search docs | 修复韩语文档中因误用 `~~` 导致的意外删除线格式。 |
| [#1](https://github.com/anthropics/cl

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览
过去24小时 Codex 无新版本发布，但 Issues 区活跃度极高，**Windows 桌面端成为绝对重灾区**，集中爆发 UI 渲染异常、通知路径错误、Browser Bridge 沙盒崩溃及 WSL2 集成失败等阻塞性问题。与此同时，开发团队正密集推进 **Multi-Agent v2** 架构迭代与 **App-Server 队列调度**能力，多项核心重构 PR 同日进入评审。

---

### 2. 版本发布
今日无新 Release。

---

### 3. 社区热点 Issues（Top 10）

| # | 标题 | 状态 | 互动 | 关键看点 |
|---|------|------|------|----------|
| [#14860](https://github.com/openai/codex/issues/14860) | Error running remote compact task | OPEN | 87 评论 / 68 👍 | **CLI 核心故障**。自 3 月中旬持续至今，Linux 用户在上下文自动压缩阶段遭遇远程任务报错，导致长会话无法继续，社区仍在等待根本修复。 |
| [#12564](https://github.com/openai/codex/issues/12564) | Allow renaming task/thread titles | CLOSED | 71 评论 / 110 👍 | **高赞体验需求**。IDE 扩展中历史线程标题不可编辑，严重阻碍多任务导航。Issue 已关闭，预计相关改进已合入或确认排期。 |
| [#2880](https://github.com/openai/codex/issues/2880) | Copy/Export Message as Markdown | OPEN | 20 评论 / 66 👍 | **近 10 个月的老需求**。TUI/CLI 用户希望将对话导出为 Markdown 以便写入外部文档，目前只能手动复制纯文本或解析内部 JSON 日志。 |
| [#21700](https://github.com/openai/codex/issues/21700) | Computer Use Chrome extension unavailable in Web Store | OPEN | 12 评论 / 17 👍 | **核心功能阻断**。Windows 桌面端依赖的 Chrome 扩展在应用商店下架，用户无法安装离线包，Computer Use 几乎不可用。 |
| [#18553](https://github.com/openai/codex/issues/18553) | Codex Desktop terminal font rendering broken | OPEN | 11 评论 / 25 👍 | **桌面端体验痛点**。终端输出字符间距异常、呈现伪斜体，影响代码阅读，且跨版本未修复。 |
| [#19504](https://github.com/openai/codex/issues/19504) | Add full RTL text direction support | OPEN | 13 评论 / 10 👍 | **国际化诉求**。阿拉伯语与希伯来语用户要求 Codex 与 Chat 面板原生支持 RTL，目前文本、标点与对齐方式均存在渲染错误。 |
| [#25236](https://github.com/openai/codex/issues/25236) | Windows: Codex App UI renders as transparent/blank | OPEN | 9 评论 / 1 👍 | **今日新报严重缺陷**。Windows 下应用主内容区直接透明或白屏，导致完全无法操作。 |
| [#13729](https://github.com/openai/codex/issues/13729) | Windows: Ctrl+V multiline paste executes immediately | OPEN | 5 评论 / 7 👍 | **CLI 交互陷阱**。Windows PowerShell 下 Ctrl+V 粘贴多行文本会直接执行，而 Shift+Insert 表现正常，存在误操作风险。 |
| [#23122](https://github.com/openai/codex/issues/23122) | Codex Mobile setup QR on Android resolves to unhandled link | OPEN | 11 评论 / 7 👍 | **跨平台生态断裂**。Android 扫码后打开 `https://com.openai.chat` 未被正确路由到 ChatGPT App，导致移动端初始化死循环。 |
| [#13906](https://github.com/openai/codex/issues/13906) | Error running remote compact task: stream disconnected | CLOSED | 20 评论 / 10 👍 | **App 端同类故障**。与 #14860 呼应，但发生在 macOS App，表现为压缩流提前断开；已关闭说明该路径可能已修复或降级处理。 |

---

### 4. 重要 PR 进展（Top 10）

| # | 标题 | 状态 | 功能/修复摘要 |
|---|

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览
今日社区发布 `v0.45.0-nightly.20260530` 版本，重点修复了 PTY resize 原生崩溃及编辑器配置无效导致的循环问题。Issues 侧持续聚焦 Agent 稳定性（generalist agent 挂起、subagent 状态误导）与 Auto Memory 安全合规改进。PR 侧迎来多项高优先级合并与提交，涵盖正则回溯栈溢出防护、命令注入安全加固及会话恢复健壮性提升。

---

### 2. 版本发布
**v0.45.0-nightly.20260530.g013914071**  
- **fix(cli)**：修复当 `preferredEditor` 配置无效时可能触发的 spam 循环问题。  
- **fix(core)**：强化 PTY resize 的健壮性，避免原生层崩溃。  
- 其他：补充 changelog 与引用支持。  
*链接：https://github.com/google-gemini/gemini-cli/releases*

---

### 3. 社区热点 Issues（按关注度与优先级精选）

| # | 标题 | 核心看点 |
|---|------|----------|
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | **P1 Bug**，generalist agent 在简单任务（如创建文件夹）上无限挂起，获 8 个 👍，是近期最严重的可用性阻塞。 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Robust component level evaluations | **P1**，行为评估（behavioral evals）基础设施的后续建设，已生成 76 条测试用例，关乎 Agent 质量度量体系。 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | Assess the impact of AST-aware file reads, search, and mapping | **P2 EPIC**，探索基于 AST 的精确代码读取与搜索，以减少 token 噪声并降低误读概率，评论活跃。 |
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS is reported as GOAL success | **P1 Bug**，subagent 达到最大轮次后仍返回 `status: "success"`，导致中断被隐藏，严重影响调试与可靠性。 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | **P2 Bug**，开发者反馈模型几乎不会主动调用自定义 skill/sub-agent，即便任务高度相关，制约扩展生态。 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command execution gets stuck with "Waiting input" | **P1 Bug**，简单 shell 命令执行完毕后仍显示“等待输入”，导致会话挂起，获较多共鸣。 |
| [#22186](https://github.com/google-gemini/gemini-cli/issues/22186) | get-shit-done output hook causes crash | **P1 Bug**，输出钩子（output hook）在总结阶段反复触发崩溃，影响工作流闭环。 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | **P2 Security**，Auto Memory 在模型侧脱敏前已将内容送入上下文，需确定性脱敏并降低日志风险。 |
| [#24246](https://github.com/google-gemini/gemini-cli/issues/24246) | Gemini CLI encounters 400 error with > 128 tools | **P2 Bug**，工具数量超过 128 时触发 400 错误，暴露工具作用域智能裁剪的缺失。 |
| [#22672](https://github.com/google-gemini/gemini-cli/issues/22672) | Agent should stop/discourage destructive behavior | **P2**，模型在 git 操作等场景下倾向使用 `git reset --force` 等危险命令，需增加安全护栏。 |

---

### 4. 重要 PR 进展

| # | 标题 | 功能/修复摘要 |
|---|------|---------------|
| [#27580](https://github.com/google-gemini/gemini-cli/pull/27580) | fix(at-command): prevent stack overflow from regex backtracking | **P1 / Core**：将 `@` 命令解析器从正则改为迭代扫描，彻底消除大输入下的灾难性回溯与栈溢出风险。 |
| [#27575](https://github.com/google-gemini/gemini-cli/pull/27575) | fix(security): prevent command injection in findCommand | **P2 / Security**：将 `execSync` 替换为安全的 `spawnSync`，防止 `findCommand` 与 `commandExists` 中的 shell 元字符注入。 |
| [#27568](https://github.com/google-gemini/gemini-cli/pull/27568) | fix(core): fall back when ripgrep execution fails | **P1 / Agent**：当 `rg` 缺失或返回 exit 64 时，保守回退至 legacy `GrepTool`，保障搜索链可用性。 |
| [#27412](https://github.com/google-gemini/gemini-cli/pull/27412) | fix(core): prevent model fabrication when read_file returns binary content | **P2 / Agent**：读取 PDF 等二进制文件时，阻止模型基于合成提示产生幻觉内容，确保输出真实。 |
| [#27371](https://github.com/google-gemini/gemini-cli/pull/27371) | fix(core): "gemini --resume crash" handle EBADF error | **P1**：会话恢复时若 PTY fd 已失效，通过捕获 `EBADF` 避免 `ioctl failed` 崩溃。 |
| [#27383](https://github.com/google-gemini/gemini-cli/pull/27383) | fix(mcp-client): prevent eager tool wipe on network timeout | MCP 工具发现因网络超时失败时，采用原子更新保留旧工具列表，解决“tool not found”误报。 |
| [#27365](https://github.com/google-gemini/gemini-cli/pull/27365) | Add ephemeral session mode (--ephemeral) | 新增 `--ephemeral` 标志，用于 headless/批处理场景，避免会话日志膨胀。 |
| [#27179](https://github.com/google-gemini/gemini-cli/pull/27179) | Feat/add local gemma 4 support | 扩展本地模型支持，增加 Gemma 4 兼容并调整超时策略。 |
| [#27347](https://github.com/google-gemini/gemini-cli/pull/27347) | fix: add command

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览
过去 24 小时，Copilot CLI 密集推送了 v1.0.57 系列补丁，重点改进了 Diff 默认行为、认证错误提示与启动体验；社区侧围绕 MCP 生态稳定性、企业级权限治理以及终端输入回归问题的讨论持续升温，多个高互动 Issue 反映出开发者对生产环境可靠性的迫切需求。

---

### 2. 版本发布
今日共发布 5 个版本（v1.0.56 → v1.0.57-2），核心变更如下：

- **v1.0.57-2**  
  常规修复与变更。

- **v1.0.57-1**  
  **新增** `showTipsOnStartup` 设置，可控制启动时是否显示 Tips。  
  [查看 Release](https://github.com/github/copilot-cli/releases/tag/v1.0.57-1)

- **v1.0.57-0**  
  **体验优化**：当没有未暂存更改时，`/diff` 默认执行分支对比。  
  **修复**：SDK auth-token 验证失败时，不再显示误导性的 "Session was not created with authentication info..."，而是透传真实原因（如 GitHub API rate limit）。  
  [查看 Release](https://github.com/github/copilot-cli/releases/tag/v1.0.57-0)

- **v1.0.56**  
  免费与学生用户现可在模型选择器中指定非 Auto 模型；ThemePicker 支持在 120 列终端内并排显示不折行；模型选择器按定价层级展示准确的上下文窗口总大小；新增 `builtInAgents.rubberDuck` 设置。  
  [查看 Release](https://github.com/github/copilot-cli/releases/tag/v1.0.56)

- **v1.0.56-2**  
  **体验优化**：Diff 视图升级为连续滚动布局，支持粘性文件/Hunk 标题栏、全终端宽度渲染及主题感知配色；`web_fetch` 工具通过 HTTP 内容协商优先获取 Markdown，提升文档站点抓取质量。  
  **修复**：BYOK Provider 相关问题。  
  [查看 Release](https://github.com/github/copilot-cli/releases/tag/v1.0.56-2)

---

### 3. 社区热点 Issues（Top 10）

| # | 状态 | 标题 | 核心看点与社区反应 |
|---|------|------|-------------------|
| **#223** | 🔵 OPEN | [企业权限] 组织拥有的 Fine-grained Token 应显示 "Copilot Requests" 权限 | **高赞（74👍，28 评论）**。企业用户强烈反对在自动化场景中使用个人 PAT，要求组织级 Token 也能申请 Copilot 权限，是企业治理的核心阻塞。 [链接](https://github.com/github/copilot-cli/issues/223) |
| **#700** | 🔵 OPEN | [模型] 提供命令行方式列出 CLI 支持的所有模型 | **功能诉求（13 评论）**。开发者希望像 `copilot --list-models` 一样透明地查看模型列表及费用倍率，便于脚本化与成本控制。 [链接](https://github.com/github/copilot-cli/issues/700) |
| **#172** | 🟣 CLOSED | [MCP] CLI 未尊重 MCP Timeout 配置 | **已关闭（10 评论）**。MCP Server 长耗时任务被强制中断，配置 `timeout` 字段无效，直接影响自定义 MCP 工具可用性。 [链接](https://github.com/github/copilot-cli/issues/172) |
| **#1999** | 🔵 OPEN | [输入] 德式键盘无法输入 `@` (Alt-Gr + q) | **严重体验缺陷（7 评论）**。自 v1.0.2 起出现的国际化输入回归，导致大量欧洲用户无法使用 `@` 提及功能，基本不可用。 [链接](https://github.com/github/copilot-cli/issues/1999) |
| **#98** | 🔵 OPEN | 与 `prompts/*.md` 提示词文件生态集成 | **高赞（28👍，6 评论）**。开发者希望复用 VS Code Copilot 的自定义 Prompt 文件，统一跨端 AI 工作流。 [链接](https://github.com/github/copilot-cli/issues/98) |
| **#1869** | 🔵 OPEN | [模型] `gpt-5-mini` 模型选择无法持久化 | **配置持久化缺陷（5 评论）**。每次重启 CLI 后模型回退到 `claude-sonnet-4.6`，破坏用户习惯与脚本一致性。 [链接](https://github.com/github/copilot-cli/issues/1869) |
| **#3395** | 🟣 CLOSED | [Linux/输入] v1.0.49 起复制功能失效 | **回归 Bug（4 评论）**。Linux 平台复制快捷键在 1.0.49 后异常，已确认修复。 [链接](https://github.com/github/copilot-cli/issues/3395) |
| **#3545** | 🟣 CLOSED | [安装] 启动时更新提示干扰工作流 | **体验优化（3 评论）**。用户反馈每次启动都提示更新并要求退出重进，建议静默自动更新。 [链接](https://github.com/github/copilot-cli/issues/3545) |
| **#2203** | 🔵 OPEN | [Agent] 允许在任务中途切换到 Autopilot 模式 | **高赞（9👍）**。老版本支持的 `Shift+Tab` 切换能力被移除，严重影响先审阅后自动化的混合工作流。 [链接](https://github.com/github/copilot-cli/issues/2203) |
| **#3456** | 🔵 OPEN | [认证/MCP] 并发刷新 Token 导致 OAuth 链断裂 | **企业集成风险（1 评论）**。对启用严格 Token 复用检测的 MCP Server，并发刷新会直接导致认证失效。 [链接](https://github.com/github/copilot-cli/issues/3456) |

---

### 4. 重要 PR 进展
今日仓库 **无新增或更新的 Pull Requests**（共 0 条）。功能迭代与修复主要由官方团队直接推送 Release 完成，社区代码贡献活跃度较低。

---

### 5. 功能需求趋势
从 32 条近期 Issue 中，可提炼出社区最关注的五大方向：

1. **MCP 生态与企业级认证**  
   Token 刷新策略（v1 vs v2 scope）、并发 OAuth、Timeout 治理、禁用 Server 仍被加载等议题密集出现，表明 MCP 正从“尝鲜”走向“生产级”诉求。

2. **模型管理与透明度**  
   模型列表查询、上下文窗口准确展示、`gpt-5-mini` / `gpt-5.5` 等新模型持久化与稳定性，是开发者控制成本与效果的核心诉求。

3. **Agent 编排与插件系统**  
   Sub-agent 并行执行、后台任务挂起（`total_turns=0`）、主 Agent 收不到子任务通知、Hooks 作用域（Monorepo 支持）等，反映出复杂自动化工作流对编排可靠性的高要求。

4. **终端体验与国际化输入**  
   德式键盘 `@` 输入、复制/粘贴、Bell 提示、`cmd+click` 链接重复打开、Keybinding 回归等，说明 CLI 作为终端原生应用，对输入稳定性极度敏感。

5. **开发工作流集成**  
   与 `prompts/*.md` 生态打通、本地 Session 日志、启动时自动更新、Session 崩溃恢复等，体现了开发者希望 Copilot CLI 与现有工具链（VS Code、Tmux、Ghostty 等）无缝衔接的期望。

---

### 6. 开发者关注点（痛点与高频需求）

- **终端输入回归成“可用性杀手”**  
  德式键盘无法输入 `@`、复制失效、快捷键（`ctrl+c`、`ctrl+shift+j`）失灵，这类 Bug 直接阻断非英语区用户与重度终端用户的工作流。

- **MCP 稳定性决定生产落地**  
  开发者反复遭遇 Token 静默刷新失败、并发刷新撞毁 OAuth 链、Timeout 被忽略、已禁用 Server 仍被加载等问题，表明 MCP 客户端的鲁棒性是当前最大短板。

- **Agent 编排“最后一公里”未打通**  
  Sub-agent 在后台挂起、主 Agent 收不到完成通知、无法中途切换 Autopilot 模式，导致多 Agent 协作从 Demo 走向生产时频繁掉链子。

- **企业/团队场景支持不足**  
  Org 级 Token 权限缺失、Monorepo 下 Hooks 无法按子项目隔离、Session 缺乏可观测日志，阻碍了团队在大型代码库与合规环境中的采用。

- **模型配置需更透明、更持久**  
  模型选择回退、上下文窗口信息不准、缺乏命令行查询接口，让开发者在成本与效果之间难以做出稳定预期。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI 社区动态日报 | 2026-05-30

## 1. 今日速览
今日无新版本发布，但 ACP（Agent Connection Protocol）相关改进持续活跃，开发者 @huntharo 连续推进会话历史回放与权限模式切换的协议级优化。与此同时，社区对产品路线（kimi-cli 与 kimi-code 的关系）的质疑升温，同时出现了对 Claude Code 兼容性及 superpowers 扩展体系的新需求。

## 2. 版本发布
今日无新版本发布。

## 3. 社区热点 Issues（今日活跃共 4 条）

| # | 标题 | 重要性 | 社区反应 |
|---|------|--------|----------|
| **#2381** | [为什么抛弃 kimi-cli 重做 kimi code? 老的没做好还要分裂社区？](https://github.com/MoonshotAI/kimi-cli/issues/2381) | 🔴 **高**。直接挑战产品路线与社区信任，反映生产力工具用户对长期维护稳定性的核心诉求。 | 情绪激烈，4 条评论，用户明确表达退订意愿，尚未获官方回应。 |
| **#2402** | [[bug] compaction.failed: 400 The request was rejected because it was considered high risk](https://github.com/MoonshotAI/kimi-cli/issues/2402) | 🔴 **高**。Windows 平台下会话压缩阶段触发后端风控，导致工作流直接中断。 | 新提交，0 评论，属紧急运行时故障，影响 0.6.0 版本生产可用性。 |
| **#2401** | [Feature Request: Support loading CLAUDE.md alongside AGENTS.md for Claude Code compatibility](https://github.com/MoonshotAI/kimi-cli/issues/2401) | 🟡 **中高**。请求兼容 Claude Code 的项目级配置文件，降低多 AI 工具混用成本。 | 新提交，0 评论，代表开发者对跨工具生态互操作的明确需求。 |
| **#2400** | [[enhancement] Kimi cli should integrate superpowers](https://github.com/MoonshotAI/kimi-cli/issues/2400) | 🟡 **中**。参考 OpenCode 实现，请求引入可插拔的 superpowers 扩展体系。 | 新提交，0 评论，显示社区希望 CLI 从封闭功能集向可扩展 Agent 平台演进。 |

## 4. 重要 PR 进展（今日更新共 5 条）

| # | 标题 | 状态 | 功能/修复内容 |
|---|------|------|---------------|
| **#2364** | [feat(acp): support permission mode switching](https://github.com/MoonshotAI/kimi-cli/pull/2364) | OPEN | 为 ACP 协议增加会话级权限模式切换能力，支持 `default` 等模式通告。依赖 #2363，属于协议层基础设施改进。 |
| **#2363** | [fix(acp): replay loaded session history](https://github.com/MoonshotAI/kimi-cli/pull/2363) | OPEN | 修复 `session/load` 后历史记录未正确回放的问题，基于 #2359 扩展，提升长会话恢复的一致性。 |
| **#2359** | [fix(acp): assign message ids to streamed content](https://github.com/MoonshotAI/kimi-cli/pull/2359) | OPEN | 为流式内容分配 `messageId`，解决外部 Agent 平台（如 PwrAgent）通过 ACP 对接时的消息追踪与关联问题。 |
| **#776** | [fix(shell): enhance shell completion navigation and tab handling](https://github.com/MoonshotAI/kimi-cli/pull/776) | **CLOSED** | 增强 Shell 补全的 Tab 键导航与处理逻辑，今日关闭，交互体验优化落地。 |
| **#777** | [feat(ui): append space automatically after file completion](https://github.com/MoonshotAI/kimi-cli/pull/777) | **CLOSED** | 文件补全后自动追加空格，减少用户额外按键，今日关闭，细节体验改进。 |

## 5. 功能需求趋势

基于今日 Issues 与近期 PR 方向，社区最关注的功能演进集中在：

1. **跨工具生态互操作**  
   开发者明确请求兼容 `CLAUDE.md`，反映出当前工作流中 Claude Code 与 Kimi Code CLI 混用的现状，项目级配置互通成为刚需。

2. **ACP 协议深度与稳定性**  
   连续多条 PR 聚焦消息 ID 分配、会话历史回放、权限切换，表明社区正推动 Kimi CLI 从“聊天工具”向“标准化 Agent 基础设施”转型，协议级工程细节是集成关键。

3. **可扩展架构（Superpowers / Plugins）**  
   用户希望引入类似 OpenCode 的 superpowers 机制，意味着社区对官方内置功能集的满意度有限，期待开放扩展接口以满足垂直场景。

## 6. 开发者关注点

- **产品生命周期与社区信任**（高频痛点）  
  老用户对 kimi-cli 被“重做”而非“演进”感到不安，认为生产力工具的信任基础在于长期维护连续性，而非功能推倒重来。

- **API 风控误杀导致会话中断**  
  #2402 的 `400 high risk` 错误暴露了后端安全策略与编码场景的冲突，compaction 阶段被拦截直接影响长会话可靠性，需紧急调优。

- **多工具配置冗余**  
  同时使用多款 AI Coding CLI 的开发者不愿维护多份项目配置文件（`AGENTS.md` + `CLAUDE.md`），对配置标准化或自动兼容诉求强烈。

- **协议集成精度要求**  
  外部开发者（如 PwrAgent）在对接 ACP 时，对流式消息的 `messageId`、session 状态一致性有严格的工程级要求，任何协议细节缺失都会阻断集成。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览

今日社区焦点集中在**性能与稳定性**两大主题：GPT 模型响应延迟问题（#29079）以 110 条评论持续霸榜，成为开发者最关注的阻塞性痛点；同时，分享功能修复、Windows 子进程挂起、TUI 粘性提示头等 10+ 个 PR 集中更新，显示工程团队正在密集修补平台体验短板。

---

### 2. 版本发布

今日无正式版本发布。仓库仅更新了 `pr-29948-screenshots` 标签资源，用于相关 PR 的截图展示。

---

### 3. 社区热点 Issues

| Issue | 说明与社区反应 |
|-------|---------------|
| **#29079** [GPT Models takes too long to respond](https://github.com/anomalyco/opencode/issues/29079) | **性能阻塞性痛点**。GPT 5.4 (xhigh) 等模型在简单指令下仍频繁出现分钟级延迟，110 条评论、48 👍 表明该问题已严重影响日常编码流。 |
| **#13984** [can not copy and paste in opencode CLI](https://github.com/anomalyco/opencode/issues/13984) | **基础交互缺陷**。CLI 中复制粘贴失效（提示已复制但实际无法粘贴），40 条评论、20 👍，开发者普遍反映影响终端操作效率。 |
| **#27167** [[FEATURE]: Add native session goals with /goal](https://github.com/anomalyco/opencode/issues/27167) | **高赞功能请求**（45 👍）。社区希望引入原生持久化会话目标/生命周期管理，以解决长会话上下文漂移问题，评论数达 30 条。 |
| **#6680** [[FEATURE]: view archived sessions on desktop](https://github.com/anomalyco/opencode/issues/6680

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-05-30*

---

### 1. 今日速览
今日社区发布 `v0.17.0-nightly.20260530` 版本，重点修复了 rewind 场景下的压缩回合误判问题。Issues 侧出现 P1 级认证死锁故障，JetBrains IDE 用户因已下线的 `qwen-oauth` 仍被返回而陷入无法登录的困境，官方已迅速提交修复 PR。此外，可观测性（Telemetry）与 CLI 交互体验成为今日代码提交的主线。

---

### 2. 版本发布
**v0.17.0-nightly.20260530.c699738f9**  
- 修复 `rewind` 功能中错误的 "compressed turn" 判定问题，避免中途消息被误判为压缩回合。  
[查看 Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.17.0-nightly.20260530.c699738f9)

---

### 3. 社区热点 Issues（过去 24 小时）

| # | 标题 | 重要性 & 社区反应 |
|---|------|------------------|
| [#4637](https://github.com/QwenLM/qwen-code/issues/4637) | **fix(acp): 已停止的 qwen-oauth 仍返回在 authMethods 中，导致 JetBrains IDE 用户陷入认证死锁** | **P1 优先级**。用户一旦配置过 `qwen-oauth` 或留空，即进入无法切换的认证死胡同。创建当日即引发密集讨论，影响面大。 |
| [#4624](https://github.com/QwenLM/qwen-code/issues/4624) | `qwen --resume` 子进程内存持续增长，最终 OOM | 稳定性隐患。resume 后会话记录与工具调用结果持续堆积在内存且无法释放，长时间运行必崩溃，获 1 个 👍。 |
| [#4642](https://github.com/QwenLM/qwen-code/issues/4642) | loading 提示语能关掉吗？恶心透了！ | 情绪反馈强烈。CLI 随机 loading 文案（如"正在努力搬砖中"）无法关闭，影响专业场景使用体验。 |
| [#4641](https://github.com/QwenLM/qwen-code/issues/4641) | MCP 稳定性：Windows 下 session 间可用 Server 数量不定 | 配置了 8 个 MCP Server，每次启动仅 3~5 个随机可用，严重阻碍 Windows 用户工作流。 |
| [#4493](https://github.com/QwenLM/qwen-code/issues/4493) | Rider 无法登录 Qwen Code，网页登录状态导致无限重定向 | 8 条评论，持续 5 天未解决。Rider 中 OAuth 跳转与阿里云 Token Plan 调用冲突。 |
| [#2724](https://github.com/QwenLM/qwen-code/issues/2724) | IntelliJ IDEA 2026.1 无法使用本地 Ollama，始终尝试登录云服务 | 3 个 👍，跨版本兼容问题。同配置在 Rider/WebStorm 2025.3 正常，疑似 IDEA 2026.1 专属故障。 |
| [#4640](https://github.com/QwenLM/qwen-code/issues/4640) | Умный роутинг（智能路由）：本地模型处理简单任务，API 处理复杂任务 | 国际化社区需求。用户希望根据任务难度自动在本地模型与云端 API 间路由，降低 Token 成本。 |
| [#4631](https://github.com/QwenLM/qwen-code/issues/4631) | 任务完成后仍不消失（Sticky Tasks） | UI 干扰问题。已完成 task 仍占据面板，影响视觉焦点，已有对应修复 PR。 |
| [#3757](https://github.com/QwenLM/qwen-code/issues/3757) | JetBrains AI 中提示 401，是体验额度用完还是配置错误？ | 认证/计费边界模糊。用户难以区分是配置错误还是额度耗尽，调试成本高。 |
| [#3511](https://github.com/QwenLM/qwen-code/issues/3511) | JetBrains AI 集成：仅通过 API Key 如何接入 ACP Registry | 4 条评论。用户希望在仅提供 API Key 的场景下绕过 OAuth 强制要求，直接集成至 JetBrains 生态。 |

---

### 4. 重要 PR 进展（过去 24 小时）

| # | 标题 | 功能或修复内容 |
|---|------|----------------|
| [#4639](https://github.com/QwenLM/qwen-code/pull/4639) | fix(acp): drop discontinued Qwen OAuth method | **紧急修复 P1 Issue #4637**。停止在 ACP 认证方法中返回已下线的 `qwen-oauth`，解除 JetBrains IDE 用户认证死锁。 |
| [#4635](https://github.com/QwenLM/qwen-code/pull/4635) | fix(cli): hide completed sticky todos | 修复 #4631。已完成 todo 从 `Current tasks` 粘性面板中隐藏，并在全部完成时自动收起面板。 |
| [#4634](https://github.com/QwenLM/qwen-code/pull/4634) | fix(cli): stabilize statusline preset ordering | 修复 #4633。`/statusline` 预设项改为按固定内置优先级渲染，不再依赖多选插入顺序，切换显示更稳定。 |
| [#4636](https://github.com/QwenLM/qwen-code/pull/4636) | fix(core): apply output language to side queries | 修复 #4494。将用户配置的 `output-language.md` 偏好同步至 side query（标题、摘要、工具总结等），保证多语言一致性。 |
| [#4622](https://github.com/QwenLM/qwen-code/pull/4622) | fix(core): enforce adjacent tool results | 修复 #4619。`cleanOrphanedToolCalls()` 仅保留与 assistant message 紧邻的 tool block，避免被其他用户回合打断后违反 Anthropic API 邻接性约束。 |
| [#4610](https://github.com/QwenLM/qwen-code/pull/4610) | feat(daemon): add POST /session/:id/btw endpoint for side questions | 为 Daemon HTTP 模式新增 `/btw` 旁路提问端点，并抽取共享 prompt 构建逻辑至 `packages/core`。 |
| [#4630](https://github.com/QwenLM/qwen-code/pull/4630) | feat(telemetry): add tool spans and session.id to daemon/ACP path | 可观测性增强。在 daemon 及 ACP 链路中为 LLM、tool、tool.execution 等 span 注入 `session.id`，支持 ARMS 按会话聚合查询。 |
| [#4613](https://github.com/QwenLM/qwen-code/pull/4613) | feat(daemon): keep model & approval-mode state consistent across clients | 解决多客户端（聊天视图、终端、IDE）共享 session 时，当前模型与审批模式状态不同步的问题，优化广播机制。 |
| [#4629](https://github.com/QwenLM/qwen-code/pull/4629) | feat(cli): add standalone auto-update support | 为独立安装包（非 npm 安装）提供自更新能力：下载 release、校验 SHA256、原子替换安装目录。 |
| [#4564](https://github.com/QwenLM/qwen-code/pull/4564) | feat(stats): expose token usage for cost visibility | 新增持久化 Token 用量统计，支持 `/stats` 查看日/月用量、模型与认证类型 breakdown，并支持 CSV/JSON 导出。 |

---

### 5. 功能需求趋势

从今日 Issues 与 PR 可提炼出以下社区最关注的功能方向：

1. **IDE 集成与认证体系重构**  
   JetBrains 全系列（IntelliJ、Rider、WebStorm）的 OAuth/ACP 认证问题集中爆发，社区迫切需要在 API Key、阿里云 Token Plan、本地模型之间拥有更灵活、无死锁的认证切换机制。

2. **可观测性与运维能力**  
   OpenTelemetry 覆盖从交互式 CLI 到 `qwen serve` daemon 的全链路成为持续投入点，包括 session 级追踪、tool span、client_id 归因及权限路由监控。

3. **性能与稳定性治理**  
   内存管理（resume OOM）、MCP Server 跨 session 稳定性、本地 LLM 无代理场景下的 300s 超时等底层问题，已成为阻碍生产化使用的关键瓶颈。

4. **CLI 交互体验精细化**  
   状态栏预设排序、历史折叠持久化、loading 文案开关、设置损坏恢复等"微体验"需求密集出现，表明用户基数扩大后对产品 polish 度要求显著提升。

5. **智能模型路由与混合部署**  
   社区开始明确提出"本地轻量模型处理简单任务 + 云端大模型处理复杂任务"的智能路由需求，预示着多模型协同工作流将成为下一阶段竞争焦点。

---

### 6. 开发者关注点

- **认证死锁是今日最大痛点**：已下线的 `qwen-oauth` 仍在 ACP authMethods 列表中返回，导致大量 JetBrains 用户无法切换至其他认证方式，形成死胡同。该问题已被标记 P1，修复 PR 已提交待合并。
- **内存泄漏威胁长会话场景**：`qwen --resume` 后子进程内存只增不减，工具调用结果与会话记录缺乏压缩/清理机制，长时间运行必触发 OOM，严重影响自动化/服务端部署。
- **JetBrains 版本兼容性分化**：同一份本地 Ollama 配置在 IDEA 2026.1 失效，却在 Rider/WebStorm 2025.3 正常，开发者需关注 IDE 版本差异带来的 ACP 桥接行为不一致。
- **MCP 稳定性在 Windows 上存疑**：跨 session 启动时 MCP Server 可用数量随机波动（8 个配置仅 3~5 个成功），且每次失败的 Server 组合不固定，调试与复现成本高。
- **"小体验"影响专业采纳**：无法关闭的 loading 文案、无法自动清理的已完成 task、401 错误信息不明确等问题，虽非核心功能，但直接决定了开发者是否愿意在日常工作流中持续使用。

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*