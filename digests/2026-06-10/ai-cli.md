# AI CLI 工具社区动态日报 2026-06-10

> 生成时间: 2026-06-10 02:57 UTC | 覆盖工具: 7 个

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

**AI CLI 工具生态横向对比分析报告**  
*基于 2026-06-10 社区动态*

---

### 1. 生态全景

当前 AI CLI 工具已从功能验证期全面进入生产可靠性攻坚阶段。头部产品（OpenAI Codex、Claude Code、GitHub Copilot CLI）保持高频版本迭代，社区议题迅速从“功能有无”转向“会话持久化、跨平台一致性、MCP 生态可靠性”等工程深水区。与此同时，开放生态工具（OpenCode、Kimi CLI）在自定义模型接入与安全沙箱机制上加速追赶，但整体成熟度分化明显，部分工具长期悬而未决的基础稳定性问题开始阻碍用户留存。

---

### 2. 各工具活跃度对比

| 工具 | 今日活跃/热点 Issues | 今日 PR | 版本发布 |
|---|---|---|---|
| **Claude Code** | 未披露具体数量 | 修复 PR 审查中 | **v2.1.170**（引入 Claude Fable 5） |
| **OpenAI Codex** | 10+（Top 10 列出） | 10（工程密集型） | **rust-v0.139.0** 稳定版 + 2 个 alpha 预发布 |
| **GitHub Copilot CLI** | 10 | 1（无效/测试提交） | **v1.0.61** |
| **Kimi Code CLI** | 2 | 1 | 无 |
| **OpenCode** | 10 | 3+ | 无 |
| **Gemini CLI / Qwen Code** | 无动态 | 无动态 | 无动态 |

---

### 3. 共同关注的功能方向

- **会话历史持久化与“假丢失”**  
  **OpenAI Codex**（#20741、#23979 等 5+ 条 Issues）、**GitHub Copilot CLI**（恢复后屏幕空白）、**OpenCode**（Windows 路径分隔符导致会话不显示）均遭遇历史记录数据在本地但 UI 不可见的索引/渲染链路断裂问题，成为最高频共性痛点。

- **Windows / 跨平台稳定性**  
  **Claude Code**（Windows 平台稳定性反馈）、**OpenAI Codex**（#24391 Windows sandbox 初始化失败）、**OpenCode**（#31597 Windows 路径分隔符混用）集中暴露跨平台路径处理与进程管理缺陷。

- **MCP 与插件生态可靠性**  
  **OpenAI Codex**（MCP 启动容错、锁竞争优化）、**GitHub Copilot CLI**（MCP 注册表 URL 修复、插件钩子回归 #3727）、**OpenCode**（MCP 容错）、**Kimi CLI**（Hook 错误暴露 PR）共同指向扩展机制从“功能支持”进入“生产级容错”阶段。

- **安全沙箱与 Agent 权限约束**  
  **OpenCode**（#2242 seatbelt 沙箱需求，64 评论/53 👍）、**OpenAI Codex**（sandbox spawn 失败）反映用户对 Agent 终端命令权限管控的迫切需求。

---

### 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|---|---|---|---|
| **OpenAI Codex** | 企业级复杂编排：多智能体追踪、实时语音交接、流式文件 API、MCP 可靠性 | 大型工程团队 / 多 Agent 场景 | Rust 重构，强调性能与协议层抽象（PathUri、analytics） |
| **Claude Code** | 深度推理与安全优先：首发 Mythos-class 模型（Fable 5）、安全分类器 | 高复杂度分析 / 安全敏感场景 | 官方模型能力首发阵地，闭环优化模型-工具链协同 |
| **GitHub Copilot CLI** | 消费级易用性：UI 打磨（/agents、/settings 交互）、GitHub 生态集成 | GitHub 生态开发者 | 封闭开发，外部 PR 贡献停滞，微软内部主导 |
| **OpenCode** | 可扩展与自托管：ACP 协议、API Key 轮询、多 Provider、PWA 支持 | 追求开放生态 / 私有部署的开发者 | 开放架构，

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-10*

---

### 1. 热门 Skills 排行（Top 7）

基于 PR 技术影响力与社区痛点匹配度综合排序：

| 排名 | Skill | 功能简述 | 社区讨论热点 | 状态 |
|---|---|---|---|---|
| 1 | **document-typography** | AI 生成文档的排版质量控制：防止孤字换行（orphan）、寡段标题（widow）、编号错位等。 | 被视为所有 Claude 文档输出的通用痛点，技术方案具体且跨场景适用。 | Open<br>[#514](https://github.com/anthropics/skills/pull/514) |
| 2 | **ODT skill** | OpenDocument（.odt/.ods）创建、模板填充、解析及转 HTML，覆盖 LibreOffice 生态。 | 填补开源/ISO 标准文档格式空白，与现有 PDF/DOCX skills 形成互补。 | Open<br>[#486](https://github.com/anthropics/skills/pull/486) |
| 3 | **SAP-RPT-1-OSS predictor** | 基于 SAP 开源表格基础模型（Apache 2.0）对 SAP 业务数据进行预测分析。 | 企业 ERP + AI 集成热点，直接对接 TechEd 2025 发布的新模型。 | Open<br>[#181](https://github.com/anthropics/skills/pull/181) |
| 4 | **ServiceNow platform** | 全平台助手，覆盖 ITSM、ITOM、SecOps、ITAM、FSM、SPM、CSDM、IntegrationHub。 | 企业级 SaaS 深度集成，广度远超一般脚本助手，

---

# Claude Code 社区动态日报 | 2026-06-10

## 1. 今日速览

Anthropic 发布 v2.1.170，正式将 Mythos 级模型 **Claude Fable 5** 推向通用场景；社区同期集中反馈 Windows 平台稳定性与 Fable 5 安全分类器误报问题，相关修复 PR 已提交审查。

---

## 2. 版本发布

**v2.1.170**  
- **核心更新**：引入 **Claude Fable 5**（Mythos-class 模型），官方

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-06-10*

---

### 1. 今日速览

今日 `rust-v0.139.0` 稳定版发布，Code mode 新增直接调用独立网页搜索能力，工具 Schema 的 `oneOf`/`allOf` 兼容性也得到保留。社区侧，**会话历史“假丢失”**仍是最高频痛点，过去 24 小时内多个高互动 Issue 持续发酵；工程侧则密集推进文件系统抽象向 `PathUri` 迁移、实时语音交接优化及 MCP 启动可靠性改进。

---

### 2. 版本发布

- **[rust-v0.139.0](https://github.com/openai/codex/releases/tag/rust-v0.139.0)**  
  - **Code mode 网页搜索**：支持直接调用独立网页搜索，包括在嵌套 JavaScript 工具调用中触发，并返回纯文本搜索结果。  
  - **Schema 兼容性提升**：工具与连接器的输入 Schema 现保留 `oneOf` 与 `allOf`；大型 Schema 在压缩时保留更多浅层结构，减少信息丢失。  
- **[rust-v0.140.0-alpha.2](https://github.com/openai/codex/releases/tag/rust-v0.140.0-alpha.2)**、**[rust-v0.139.0-alpha.3](https://github.com/openai/codex/releases/tag/rust-v0.139.0-alpha.3)** 等预发布版本同步迭代。

---

### 3. 社区热点 Issues（Top 10）

| # | 主题 | 评论/反应 | 关键看点 |
|---|------|-----------|----------|
| [#24391](https://github.com/openai/codex/issues/24391) | Windows sandbox: spawn setup refresh fails on CLI 0.133.0 | 44 评论 / 25 👍 | **Windows CLI 严重回归**，sandbox 初始化刷新失败，影响命令执行。 |
| [#20741](https://github.com/openai/codex/issues/20741) | Codex Desktop 项目聊天历史在更新后消失 | 33 评论 / 14 👍 | 桌面端更新后项目级历史记录不可见，用户担忧数据丢失。 |
| [#19585](https://github.com/openai/codex/issues/19585) | Pro 周度额度在 5.5 模型下异常快速耗尽 | 29 评论 / 26 👍 | **付费用户核心痛点**，上下文压缩不稳定导致额度消耗远超预期。 |
| [#21128](https://github.com/openai/codex/issues/21128) | Desktop 静默隐藏全局最近 50 条窗口外的项目对话 | 23 评论 / 16 👍 | 产品设计缺陷：旧对话未归档却从 UI 消失，仅因全局窗口限制。 |
| [#23979](https://github.com/openai/codex/issues/23979) | 更新后本地项目历史在 UI 丢失，但 `state_5.sqlite` 仍存在 | 20 评论 / 4 👍 | **典型“假丢失”**，数据完好但索引/渲染链路断裂。 |
| [#17540](https://github.com/openai/codex/issues/17540) | Windows 应用：旧本地线程在重启后从侧边栏消失 | 19 评论 / 6 👍 | Windows 平台历史可见性问题，磁盘文件仍在但侧边栏与搜索均不显示。 |
| [#25500](https://github.com/openai/codex/issues/25500) | 项目侧边栏对旧对话显示“No chats” | 17 评论 / 2 👍 | 非归档旧对话被错误归类为空项目，影响工作流连续性。 |
| [#26493](https://github.com/openai/codex/issues/26493) | `context_compaction` 因 `invalid_enum_value` 失败 | 16 评论 / 4 👍 | 上下文压缩触发枚举校验错误，导致长会话无法继续。 |
| [#2909](https://github.com/openai/codex/issues/2909) | VS Code 扩展支持多根工作区 (Multi-root Workspaces) | 9 评论 / 125 👍 | **长期高赞需求**，企业级/大型仓库开发者的 IDE 集成瓶颈。 |
| [#25084](https://github.com/openai/codex/issues/25084) | Desktop 隐藏活跃项目聊天历史，本地线程仍在磁盘 | 15 评论 / 2 👍 | 活跃项目会话被隐藏，解档、置顶、搜索均无法恢复，阻断日常开发。 |

---

### 4. 重要 PR 进展（Top 10）

| # | 主题 | 说明 |
|---|------|------|
| [#27190](https://github.com/openai/codex/pull/27190) | Add streaming file APIs | 为 app-server v2 与 exec-server 引入基于拉取的流式文件读写 API（`fs/readFile/open`、`fs/writeFile/open` 等），降低大文件传输内存占用。 |
| [#27107](https://github.com/openai/codex/pull/27107) | Add spans to `run_turn` | 在 turn 编排、采样请求准备及工具加载阶段增加细粒度追踪 span，帮助区分本地协调开销与模型流式/工具执行耗时。 |
| [#27127](https://github.com/openai/codex/pull/27127) | Forward assistant output to realtime through handoffs | 实时语音场景下，将 Codex 的 preamble 与 final 消息透传至前端模型，使语音助手体验更像单一连贯智能体。 |
| [#27261](https://github.com/openai/codex/pull/27261) | Make MCP connection startup fallible | 将 MCP 服务器启动失败从 `Session::new` 的强制断言改为可错误处理，避免单个 MCP 故障阻塞整个会话初始化。 |
| [#27259](https://github.com/openai/codex/pull/27259) | Replace MCP manager lock with explicit retirement | 以显式生命周期管理替换 `RwLock<McpConnectionManager>`，消除启动预热时读锁持有导致的工具列表阻塞。 |
| [#27282](https://github.com/openai/codex/pull/27282) | Migrate `ExecutorFileSystem` to `PathUri` | 将执行文件系统抽象迁移至 `PathUri`，统一跨平台路径表示，为后续协议层无感改造铺路。 |
| [#27276](https://github.com/openai/codex/pull/27276) | Reduce archive rollout lookup CPU | 优化归档线程时的回退查找逻辑：在 state DB 缺少 rollout 路径时，直接通过 UUID 定位文件，避免全局扫描带来的 CPU 峰值。 |
| [#27055](https://github.com/openai/codex/pull/27055) | Add parent turn id to Codex turn analytics | 在分析事件中携带可空的 `parent_turn_id`，覆盖多智能体 spawn、CSV agent-job、委托审查等场景，完善调用链路审计。 |
| [#27247](https://github.com/openai/codex/pull/27247) | Resize all history images behind a feature flag | 在功能开关后统一对历史图片进行尺寸压缩，减少上下文窗口与带宽占用。 |
| [#17931](https://github.com/openai/codex/pull/17931) | Support encrypted local secrets for keyring auth | 解决 Windows Credential Manager 2,560 字节限制问题，对超大 ChatGPT/MCP OAuth 载荷进行分块加密存储。 |

---

### 5. 功能需求趋势

从过去 24 小时社区反馈中，可提炼出以下四大需求方向：

1. **会话历史持久化

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*2026-06-10*

---

### 1. 今日速览
Copilot CLI 发布 **v1.0.61**，重点优化了 `/agents` 选择器与 `/settings` 交互体验，并修复会话恢复后屏幕空白的 bug。社区对长达 6 个月未决的“CLI 命令回归”议题（#53）持续施压，同时 **v1.0.60 引入的插件钩子回归**（#3727）开始影响生产环境。过去 24 小时官方 Issue 处理活跃，但社区外部 PR 贡献几乎停滞。

---

### 2. 版本发布
**v1.0.61**（2026-06-09）
- **UI 打磨**：统一 `/agents` 选择器与“Create New Agent”向导的视觉风格（边框、标题、输入框样式）。
- **稳定性修复**：解决恢复会话后屏幕空白的 bug；改进本地会话恢复体验。
- **交互增强**：新增 `/settings` 交互式对话框，支持一站式浏览和编辑所有用户设置。

---

### 3. 社区热点 Issues（10 条）

| # | 状态 | 标题 | 社区反应 | 链接 |
|---|------|------|----------|------|
| **#53** | 🔴 OPEN | Bring back the GitHub Copilot in the CLI commands to not break workflows | **75👍 31💬**。长达 6 个月无官方回应，社区已自发孵化 `shell-ai` 等替代方案，是目前呼声最高的破坏性变更回退请求。 | [链接](https://github.com/github/copilot-cli/issues/53) |
| **#1703** | 🔴 OPEN | Copilot CLI does not list all org-enabled models (e.g. Gemini 3.1 Pro) while VS Code Copilot does | **54👍 29💬**。企业组织已启用的模型在 CLI 与 VS Code 间列表不同步，直接影响统一 AI 策略落地。 | [链接](https://github.com/github/copilot-cli/issues/1703) |
| **#1613** | 🔴 OPEN | Feature request: Built-in git worktree lifecycle management | **31👍**。高赞功能请求，希望 CLI 内置 git worktree 的自动创建与清理，以安全隔离多任务会话。 | [链接](https://github.com/github/copilot-cli/issues/1613) |
| **#2082** | 🔴 OPEN | ctrl+shift+c no longer copies to clipboard on Linux | **8👍 20💬**。Linux 终端默认复制快捷键失效，虽提供替代方案，但打破既有肌肉记忆，讨论热烈。 | [链接](https://github.com/github/copilot-cli/issues/2082) |
| **#3596** | 🔴 OPEN | Error loading model list: Error: Not authenticated | **10👍**。恢复特定会话后丢失认证状态，导致 `/model` 命令失败，新会话则正常，指向会话持久化缺陷。 | [链接](https://github.com/github/copilot-cli/issues/3596) |
| **#2050** | 🔴 OPEN | Claude Sonnet 4.6 - Execution failed: 503 HTTP/2 GOAWAY | **4👍 8💬**。读取大文件时 Claude Sonnet 4.6 反复出现 503 连接中断，同一任务 Gemini 3 Pro 正常，暴露模型后端稳定性差异。 | [链接](https://github.com/github/copilot-cli/issues/2050) |
| **#3436** | 🟢 CLOSED | /mcp search constructs wrong URL for custom MCP registries | **7💬**。企业级 MCP 注册表 URL 构造缺少 `/v0.1/` 段导致 404，已修复，反映企业 MCP 集成进入实用阶段。 | [链接](https://github.com/github/copilot-cli/issues/3436) |
| **#2540** | 🔴 OPEN | Plugin-defined preToolUse hooks (hooks.json) do not fire | **3👍 7💬**。插件通过 `hooks.json` 定义的 preToolUse 钩子完全不执行，影响插件生态扩展能力。 | [链接](https://github.com/github/copilot-cli/issues/2540) |
| **#3727** | 🔴 OPEN | Regression in v1.0.60: userPromptSubmitted hook additionalContext no longer injected into planner | **新提交**。v1.0.60 严重回归：插件 `userPromptSubmitted` 钩子附加上下文无法注入 planner，v1.0.59 正常，插件开发者需紧急关注。 | [链接](https://github.com/github/copilot-cli/issues/3727) |
| **#3736** | 🔴 OPEN | Thinking Tokens/Text never appears with BYOK models regardless of endpoint type | **新提交**。自带密钥（BYOK）模型无法显示思考过程/Thinking Tokens，影响可解释性与调试。 | [链接](https://github.com/github/copilot-cli/issues/3736) |

---

### 4. 重要 PR 进展
过去 24 小时内仅更新 **1 条** Pull Request，且为无效/测试提交，无实质性功能合并，社区外部代码贡献处于停滞状态。

- **#3737 Jigg empire ai** [OPEN] — 非正式测试提交，无实际代码变更价值。  
  [链接](https://github.com/github/copilot-cli/pull/3737)

---

### 5. 功能需求趋势
从 30 条活跃 Issue 中提炼出四大趋势：

1. **企业级集成与治理**：组织模型同步（#1703、#3730）、企业 MCP 注册表（#3436）、私有网络访问（#3731）成为企业用户核心诉求。
2. **插件与扩展性**：插件

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI 社区动态日报 | 2026-06-10**

---

### 1. 今日速览

过去24小时，Kimi Code CLI 仓库无新版本发布，但社区焦点集中在稳定性议题上：一个存续近五个月的文件读取死循环 Bug 于今日再次更新，持续引发用户讨论；同时，一条关于编辑工具频繁失败的 Issue 和一条旨在提升 Hook 错误输出可见性的 PR 构成了今日主要动态。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 社区热点 Issues

> 过去24小时内仓库共更新 **2** 条 Issue，以下按社区影响度列出：

**1. 文件读取陷入死循环 [#640](https://github.com/MoonshotAI/kimi-cli/issues/640)**
- **状态**: Open | **作者**: @isbafatima90-arch | **👍**: 1 | **评论**: 7
- **核心问题**: 在 Linux 环境下使用自定义 Anthropic Endpoint（mimo-v2-flash）时，CLI 反复读取同一文件导致死循环。该 Issue 创建于 2026-01-19，今日再次更新，已持续近 5 个月未解决。
- **社区反应**: 7 条评论表明用户对此高度关注，问题可能涉及与第三方模型/端点兼容时的上下文管理缺陷。

**2. 编辑工具频繁执行失败 [#2443](https://github.com/MoonshotAI/kimi-cli/issues/2443)**
- **状态**: Open | **作者**: @iaindooley | **👍**: 0 | **评论**: 0
- **核心问题**: Kimi Code v0.12.0 在 Debian 环境下通过 `/login` 使用 k2.6 模型时，Edit tool 频繁报错失败，直接影响代码编辑这一核心工作流。
- **社区反应**: 昨日刚创建，尚未形成讨论，但属于高频使用的核心功能故障，预计将持续获得关注。

---

### 4. 重要 PR 进展

> 过去24小时内仓库共更新 **1** 条 Pull Request：

**1. 将 PostToolUse Hook 的 stderr 暴露至 LLM 上下文 [#2445](https://github.com/MoonshotAI/kimi-cli/pull/2445)**
- **状态**: Open | **作者**: @zwpdbh
- **功能概述**: 将 PostToolUse Hook 从“即发即弃”（fire-and-forget）模式改为 `awaited` 模式，收集 Hook 的标准错误输出并追加到工具结果消息中。这使 LLM 能在工具调用后立即感知 Hook 的执行错误，提升调试与错误恢复能力。
- **影响评估**: 增强了 CLI 扩展机制的可观测性，对依赖自定义 Hook 的企业用户和高级开发者具有实用价值。

---

### 5. 功能需求趋势

基于今日更新的 Issues 与 PR，社区当前最关注的技术方向集中在：

- **工具调用稳定性**：编辑工具（Edit tool）和文件读取工具的执行可靠性是首要痛点，用户期望核心工作流零失败。
- **可观测性与调试**：开发者希望系统内部状态（如 Hook 错误、循环读取行为）能被 LLM 或用户及时感知，而非静默失败或陷入死循环。
- **多平台/多模型兼容**：自定义端点（如 Anthropic Endpoint）与非标准模型配置下的行为一致性仍需加强。

---

### 6. 开发者关注点

- **死循环与资源占用**：文件读取循环问题长期悬而未决，严重影响长会话下的使用体验和系统资源消耗。
- **核心编辑功能健壮性**：v0.12.0 中编辑工具的高频失败直接阻断开发流程，是阻碍日常使用的关键障碍。
- **自定义集成兼容性**：使用第三方模型端点时，上下文管理和工具行为易出现异常，表明开放生态的适配层仍需打磨。
- **错误信息透明度**：开发者希望工具链各环节的 stderr、调试信息能完整传递至上下文，减少“黑盒”故障排查成本。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-06-10*

---

### 1. 今日速览
过去 24 小时社区持续聚焦 **Agent 安全沙箱** 与 **自定义 OpenAI 兼容提供商** 的稳定性缺陷，相关 Issue 讨论热度居高不下。代码层面则以 **CLI/TUI 体验修复** 和 **核心架构优化** 为主线，MCP 容错、文件搜索服务统一及 PWA 支持等多项改进已进入评审阶段。

---

### 2. 版本发布
过去 24 小时内无新 Release。

---

### 3. 社区热点 Issues

| # | 标题 | 状态 | 核心看点 |
|---|------|------|----------|
| [#2242](https://github.com/anomalyco/opencode/issues/2242) | Is there a way to sandbox the agent ? | OPEN | **安全架构焦点**。用户呼吁引入类似 gemini-cli / codex-cli 的 seatbelt 沙箱机制，限制 Agent 终端命令仅能访问当前目录。64 条评论、53 👍，是社区长期高票需求。 |
| [#13984](https://github.com/anomalyco/opencode/issues/13984) | can not copy and paste in opencode CLI | OPEN | **基础体验阻塞**。CLI 内复制提示成功但无法粘贴，影响高频交互。45 条评论，用户反馈集中。 |
| [#5674](https://github.com/anomalyco/opencode/issues/5674) | Custom OpenAI-compatible provider options not being passed to API calls | OPEN | **生态兼容**。`opencode.json` 中配置的 `baseURL` 与 `apiKey` 未实际传入请求，导致本地/私有模型无法连通。23 条评论。 |
| [#20802](https://github.com/anomalyco/opencode/issues/20802) | Custom OpenAI-compatible providers: image file attachments do not reach vision-capable models correctly | OPEN | **多模态链路断裂**。自定义提供商下图片附件无法被模型正确识别为 vision 输入，影响视觉 Agent 场景。 |
| [#31498](https://github.com/anomalyco/opencode/issues/31498) | Extremely bad developer prompt | OPEN | **产品质量**。开发者吐槽系统 prompt 过度犹豫，简单文件操作产生冗长无效思考，直接影响 Agent 执行效率。 |
| [#31525](https://github.com/anomalyco/opencode/issues/31525) | Prompt loop reloads all messages from DB every iteration, breaking prompt cache byte-identity | OPEN | **性能/成本**。每次 prompt 循环全量重载消息，破坏 Anthropic prompt cache 的字节一致性，导致 token 成本上升。 |
| [#18757](https://github.com/anomalyco/opencode/issues/18757) | Tool execution frequently fails with 'Tool execution aborted' error | OPEN | **稳定性**。bash / edit / read 等工具频繁返回执行中止，需重启会话恢复，严重影响工作流连续性。 |
| [#31579](https://github.com/anomalyco/opencode/issues/31579) | `@ai-sdk/anthropic` 3.0.71 rejects `usage.iterations[].type: "fallback_message"` | OPEN | **SDK 兼容性**。Anthropic 新增 fallback 模型响应类型，但 bundled SDK 校验失败导致整轮对话报错，需紧急适配。 |
| [#22235](https://github.com/anomalyco/opencode/issues/22235) | IDE (VSCode): `Context Awareness` function didn’t take effect. | OPEN | **IDE 集成**。VSCode 扩展宣称的上下文感知（自动附加选中代码）未实际生效，开发者质疑配置门槛或功能回归。 |
| [#31597](https://github.com/anomalyco/opencode/issues/31597) | Windows: Sessions not showing in opencode desktop UI due to inconsistent path separator | OPEN | **跨平台一致性**。SQLite 中目录路径混用 `/` 与 `\`，导致 Windows 桌面端会话列表异常，属于典型的路径处理缺陷。 |

---

### 4. 重要 PR 进展

| # | 标题 | 类型 | 内容摘要 |
|---|------|------|----------|
| [#31596](https://github.com/anomalyco/opencode/pull/31596) | feat: support apiKey arrays with round-robin rotation per provider | 新功能 | 支持在 provider 配置中传入 API Key 数组并按轮询策略切换，提升高并发或限流场景下的可用性。 |
| [#31392](https://github.com/anomalyco/opencode/pull/31392) | feat(acp): stage edits for native review in ACP clients | 新功能 | 让 OpenCode 支持 ACP 客户端（如 Zed、Devin）的原生文件审查流程，实现编辑 staged review。 |
| [#31595](

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*