# AI CLI 工具社区动态日报 2026-06-15

> 生成时间: 2026-06-15 03:46 UTC | 覆盖工具: 7 个

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
*2026-06-15 | 基于社区动态与工程进展*

---

### 1. 生态全景

当前 AI CLI 生态已从“功能演示期”全面进入“生产可靠性攻坚期”。头部工具不再局限于代码补全，而是围绕 **Agent 架构治理**（子代理递归控制、权限合约）、**跨平台一致性**（Windows 原生体验补齐）和**商业化透明度**（配额、定价、免费策略调整）展开深度博弈。与此同时，MCP 协议集成、上下文内存安全、TUI 精细化交互成为共性技术高地，反映出开发者正将这些工具从实验环境推向核心工作流，对稳定性、安全性和成本可控性的要求显著提升。

---

### 2. 各工具活跃度对比

| 工具 | 今日 Release | Issues 更新/热点 | PR 更新 | 核心焦点 |
| :--- | :--- | :--- | :--- | :--- |
| **Claude Code** | 无 | 2+（子代理失控、INR 定价） | 未披露 | 架构安全、区域定价公平性 |
| **OpenAI Codex** | 无 | 10+ | 10+ | Windows 稳定性危机、网络安全误报、TUI 配额兑换 |
| **Gemini CLI** | — | 数据未提供 | 数据未提供 | — |
| **GitHub Copilot CLI** | 无 | 8 | 0 | Agent 路径偏差、上下文重复、附件污染会话 |
| **Kimi Code CLI** | 无 | 3 | 4 | 限速/限额透明度、系统提示冲突、Windows 修复 |
| **OpenCode** | **v1.17.7** | 10+ | 7+ | 订阅限流调整、TUI 终端体验、MCP 安全隔离 |
| **Qwen Code** | 无 | 10+ | 7+ | 免费额度政策剧变、杀毒误报、权限合约绕过 |

---

### 3. 共同关注的功能方向

- **Windows 平台原生体验补齐**  
  **涉及工具**：Kimi Code CLI（3 个 Windows PR：粘贴快捷键、日志锁、可配置 Shell）、OpenAI Codex（WSL 断裂、MSIX 包缺失、启动崩溃）、Qwen Code（VSCode 扩展被杀毒软件误报）。  
  **诉求**：开发者要求 Windows 终端获得与 macOS/Linux 对等的原生集成，而非依赖 WSL 折中方案。

- **安全与权限治理**  
  **涉及工具**：Claude Code（子代理无限递归导致灾难性 Token 消耗）、OpenAI Codex（网络安全误报阻断付费会话）、Copilot CLI（附件解析失败永久污染会话）、Qwen Code（权限合约探测被绕过执行副作用命令）。  
  **诉求**：沙盒隔离、输入预检、副作用熔断、会话级故障隔离成为 Agent 落地的信任基石。

- **上下文与内存管理**  
  **涉及工具**：Copilot CLI（上下文重复项触发 CAPI 400 错误）、Qwen Code（大体积工具结果重复携带致上下文膨胀）、OpenCode（递归语言模型上下文管理 RLM 提案）。  
  **诉求**：从简单的滑动窗口转向智能去重、外部化记忆与长会话稳定性保障。

- **服务透明度与配额可控性**  
  **涉及工具**：Kimi Code（5 小时 60 次 vs 宣传 300–1200 次）、OpenAI Codex（TUI 盲盒式配额）、OpenCode（DeepSeek 降价后呼吁上调限流）、Qwen Code（免费额度从 1,000 骤降至 100）。  
  **诉求**：实时数字配额、清晰 SLA、与市场行情联动的定价策略。

- **MCP 生态集成与安全边界**  
  **涉及工具**：OpenCode（MCP 客户端能力滞后、API Key 经 `process.env` 泄露）、Qwen Code（MCP Server 连接但工具不可见）、OpenAI Codex（MCP 超时治理）。  
  **诉求**：完整协议支持、子进程环境变量隔离、长耗时工具超时配置。

---

### 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线特征 |
| :--- | :--- | :--- | :--- |
| **Claude Code** | 深度 Agent 编排与自主任务执行 | 追求极致自动化的高级开发者 | **子代理架构**先驱，探索多 Agent 递归协作，但正面临生产级控制考验；生态封闭，区域定价争议大。 |
| **OpenAI Codex** | 全栈企业级工作流与跨平台覆盖 | 付费企业开发者、Teams 用户 | **Electron + TUI 双端**重投入，异步 Hook 运行时、配额兑换系统精细化；当前受困于 Windows 稳定性与网络安全策略过度敏感。 |
| **GitHub Copilot CLI** | GitHub/Azure DevOps 原生 Agent 工作流 | GitHub 生态重度用户 | **CAPI + Agent Skills** 路线，强调脚本化技能与仓库上下文；迭代节奏放缓，聚焦上下文稳定性与执行路径确定性。 |
| **Kimi Code CLI** | 高性价比专业编码与跨平台补齐 | 国内开发者、价格敏感型团队 | **代码编辑可靠性**优先（如 `StrReplaceFile` 精确修复），正系统性补齐 Windows 短板；信任危机集中于配额透明度。 |
| **OpenCode** | 开放模型聚合与前沿 TUI 体验 | 多模型极客、自托管/成本敏感用户 | **多 Provider 聚合**（DeepSeek、GLM、Z.AI 等），提示缓存优化与双向游标分页架构；激进迭代，但需警惕新版本回归（如 v1.17.7 EditBuffer 报错）。 |
| **Qwen Code** | 国内全链路开发平台与阿里云生态 | 国内开发者、阿里云用户 | **Web Shell + 工作流元数据 + Computer Use** 全栈覆盖；免费策略收缩与安全误报（木马标记）成为当前最大阻力。 |

---

### 5. 社区热度与成熟度

- **高活跃 · 快速迭代期**：**OpenAI Codex**（同日 10+ Issues 与 10+ PR，异步 Hook 三部曲、配额系统持续演进）、**OpenCode**（发布 v1.17.7，PR 密集覆盖 TUI 与协议层）、**Qwen Code**（#3203 单日激增 135 条评论，PR 覆盖工作流与扩展管理）。三者社区声

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills 社区热点报告（截至 2026-06-15）

## 1. 热门 Skills 排行（按社区讨论热度）

1. **document-typography** ([#514](https://github.com/anthropics/skills/pull/514))
   - **功能**：AI 生成文档的排版质量控制，自动修复孤字换行（orphan）、寡段（widow）、编号错位等排版问题。
   - **热点**：被视为所有 Claude 文档输出的通用痛点，社区关注其能否成为默认文档后处理标准。
   - **状态**：OPEN

2. **ODT Skill — OpenDocument 支持** ([#486](https://github.com/anthropics/skills/pull/486))
   - **功能**：创建、填充、读取及将 ODT/ODS 转换为 HTML，面向 LibreOffice 和开源办公生态。
   - **热点**：企业用户和开源社区对 ISO 标准文档格式的强需求，填补官方 Skill 在开放文档格式的空白。
   - **状态**：OPEN

3. **frontend-design 改进** ([#210](https://github.com/anthropics/skills/pull/210))
   - **功能**：重写前端设计 Skill，提升指令清晰度与可执行性，确保单次对话内可完成操作。
   - **热点**：社区对现有前端 Skill“过于笼统”的反馈集中体现，关注 Prompt 工程的可操作性边界。
   - **状态**：OPEN

4. **skill-quality-analyzer & skill-security-analyzer** ([#83](https://github.com/anthropics/skills/pull/83))
   - **功能**：两个元技能（Meta Skill），分别从结构文档、安全合规等五维度评估 Skill 质量。
   - **热点**：随着 Skill 数量爆发，社区开始关注 Skill 本身的可维护性与安全边界

---

**Claude Code 社区动态日报**  
*2026-06-15*

---

### 1. 今日速览
今日无新版本发布。社区焦点集中在 **子代理（Subagent）架构失控** 风险上，过去24小时新增多个 Critical/High 优先级 Issue，揭露无限递归与灾难性 Token 消耗问题；同时，**印度区 INR 定价** 请求（#17432）仍以 194 条评论、442 赞的热度稳居功能诉求榜首。

---

### 2. 版本发布
*过去24

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-06-15*

---

### 1. 今日速览

今日社区焦点集中在 **Windows 端稳定性危机** 与 **网络安全误报** 两大主题。桌面端出现多起更新后无法启动、WSL 集成断裂及沙盒 ACL 损坏案例；同时，CLI 与 App 的 cybersecurity false positive 成为付费用户工作流的主要阻断点。开发侧则持续推进异步 Hook 运行时、MCP 超时治理及 TUI 配额兑换体验。

---

### 2. 版本发布

今日无新 Release。

---

### 3. 社区热点 Issues

| Issue | 状态 | 说明与社区反应 |
|-------|------|----------------|
| **#12564** 支持重命名任务/线程标题以改善历史导航 | CLOSED | 高票（111 👍）用户体验改进已落地，80 条评论反映了开发者对会话管理强需求的长期呼声。[链接](https://github.com/openai/codex/issues/12564) |
| **#27979** Windows Codex App 26.609.4994.0 更新后无法打开 | OPEN | 21 评论，影响面大。Windows 桌面端在最新更新后出现启动崩溃，用户无法通过常规方式恢复或查看 About 对话框。[链接](https://github.com/openai/codex/issues/27979) |
| **#27817** 授权财务/税务工作被误标网络安全风险 | OPEN | 16 评论。典型的安全策略 false positive，正常个人理财对话被阻断，社区呼吁优化关键词/语义判定。[链接](https://github.com/openai/codex/issues/27817) |
| **#28015** CLI 本地仓库维护任务反复触发网络安全检查 | OPEN | 16 评论。与 #27817 同源，DevOps 日常操作（查看日志、清理分支）被误判为安全威胁，严重中断付费会话。[链接](https://github.com/openai/codex/issues/28015) |
| **#25500** Desktop Projects 侧边栏对旧对话显示 "No chats" | OPEN | 18 评论。非归档历史对话在最新版中不可见，引发用户对数据持久性的担忧。[链接](https://github.com/openai/codex/issues/25500) |
| **#27353** 最新更新后项目聊天历史消失 | OPEN | 7 评论，3 👍。macOS 用户在更新后遭遇历史记录丢失，与 #25500 共同指向版本升级中的数据迁移风险。[链接](https://github.com/openai/codex/issues/27353) |
| **#28103** Windows MSIX 包缺少 Linux `codex` 二进制，破坏 WSL 模式 | OPEN | 5 评论，9 👍。"Run agent in WSL" 功能因打包遗漏而完全失效，Windows 跨平台工作流受阻。[链接](https://github.com/openai/codex/issues/28103) |
| **#15281** CLI `/status` 命令暴露完整用量与限额数据 | OPEN | 6 评论，15 👍。Plus 用户希望像网页端一样在 TUI 中查看精确限额与重置时间，避免“盲盒式”使用。[链接](https://github.com/openai/codex/issues/15281) |
| **#27536** macOS `code_sign_clone` 目录无限增长至 62 GB+ | OPEN | 2 评论。Electron 自动更新后的临时签名克隆文件未清理，导致磁盘空间静默泄漏。[链接](https://github.com/openai/codex/issues/27536) |
| **#23840** Computer Use MCP 在 Desktop 中初始化超时 | OPEN | 9 评论。同一 MCP 客户端在 Terminal 可握手，但在 Codex Desktop 内超时，影响 Computer Use 插件稳定性。[链接](https://github.com/openai/codex/issues/23840) |

---

### 4. 重要 PR 进展

| PR | 说明 |
|----|------|
| **#28235** [链接](https://github.com/openai/codex/pull/28235) | 为 `request_user_input` 提示增加自动解决计时器：60 秒静默宽限期 + 60 秒可见倒计时，无交互则自动提交空响应，减少 TUI 挂起。 |
| **#28154** [链接](https://github.com/openai/codex/pull/28154) | 在 TUI `/usage` 命令中增加速率限制重置积分（reset credits）的查看与兑换入口，配合后端 #28143 提升配额透明度。 |
| **#28143** [链接](https://github.com/openai/codex/pull/28143) | App-server 后端新增 `account/rateLimits/read` 接口，暴露个人速率限制重置积分，为 CLI 兑换功能提供协议基础。 |
| **#28234** [链接](https://github.com/openai/codex/pull/28234) | 将 MCP 工具默认调用超时从 120 秒提升至 300 秒，缓解复杂工具（如数据库迁移、长耗时构建）频繁超时的问题。 |
| **#27771** [链接](https://github.com/openai/codex/pull/27771) | 为异步 Hook 引入有界运行时（Bounded Runtime），提供会话级资源限制与确定性交付门控，是异步 Hook 三部曲之首。 |
| **#27452** [链接](https://github.com/openai/codex/pull/27452) | 激活异步 Hook 执行，并在模型请求被接受后交付 Hook 输出，实现后台任务与主会话的解耦。 |
| **#27772** [链接](https://github.com/openai/codex/pull/27772) | 在 App-server 与 TUI 中展示 Hook 执行模式（同步/异步），提升可观测性，完成异步 Hook 堆栈。 |
| **#28008** [链接](https://github.com/openai/codex/pull/28008) | 增加外部 Agent 导入结果统计，为同步或后台导入的插件/会话提供稳定的导入 ID 与制品类型对账。 |
| **#27640** [链接](https://github.com/openai/codex/pull/27640) | 扩展 `request_plugin_install` 支持多工具批量安装（`entries` 或 `categories` 列表），简化复杂工具链初始化。 |
| **#28232** [链接](https://github.com/openai/codex/pull/28232) | 新增 TUI `workspace-headline` 状态栏项，

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报 | 2026-06-15**

### 1. 今日速览
过去24小时，Copilot CLI 仓库无新 Release 与 PR 更新，但 Issues 区保持活跃，共 8 条 Issue 发生状态变更或新增评论。社区焦点集中在 **Agent 技能执行路径偏差**、**上下文重复项导致的 CAPI 400 错误**、**BYOK 模型自动发现** 及 **Azure DevOps 集成** 等方向，同时出现一个可导致会话完全瘫痪的附件污染严重 Bug。

---

### 2. 版本发布
今日无新 Release。

---

### 3. 社区热点 Issues
过去24小时共有 8 条 Issue 更新，以下按技术影响与社区关注度排序：

| # | 标题 | 状态 | 重要性说明 |
|---|---|---|---|
| **#3558** | [Duplicate Item Errors](https://github.com/github/copilot-cli/issues/3558) | OPEN | **高稳定性风险**。上下文内存中出现重复项触发 CAPI 400 错误（`bad_request` / `websocket_error`），直接阻断模型调用流程，获 7 个 👍，社区持续复现中。 |
| **#3791** | [Malformed attachment poisons session; all subsequent turns fail with 400](https://github.com/github/copilot-cli/issues/3791) | OPEN | **严重 Bug**。加密/受密码保护的 `.xlsx` 附件触发 400 错误后，会**永久污染当前会话**，导致后续所有对话（即使不带附件）均失败，急需容错与会话隔离修复。 |
| **#956** | [Agent skills scripts executed in wrong folder](https://github.com/github/copilot-cli/issues/956) | OPEN | **Agent 核心体验**。Agent 技能引用 `scripts/myscript.sh` 时未按官方规范在工作目录执行，影响自定义技能脚本的可预测性，已有 6 条讨论，长期未决。 |
| **#3795** | [Feature request: opt-in model discovery for BYOK / custom providers](https://github.com/github/copilot-cli/issues/3795) | OPEN | **企业级需求**。请求在 BYOK/自定义 Provider 模式下支持模型自动发现，避免手动硬编码 `COPILOT_MODEL`，降低私有化与多模型切换门槛。 |
| **#3794** | [Add Azure DevOps work items to Up next](https://github.com/github/copilot-cli/issues/3794) | OPEN | **生态集成**。要求跨会话的 "Up next" 面板支持 Azure DevOps 工作项，与现有 ADO 仓库支持形成闭环，满足混合托管场景需求。 |
| **#3797** | [Different prompt input box layout in two different cmd tabs in the same window](https://github.com/github/copilot-cli/issues/3797) | OPEN | **UI 一致性**。同一窗口内不同 cmd 标签页的提示输入框渲染布局不一致，影响终端多开场景下的用户体验，刚于今日提交。 |
| **#3796** | [hhhhhhh](https://github.com/github/copilot-cli/issues/3796) | CLOSED | 无效 Issue，无实质内容，已被维护者快速关闭，反映社区噪音仍需过滤。 |
| **#3793** | [十六进制字符串标题](https://github.com/github/copilot-cli/issues/3793) | OPEN | 无描述的低质量 Bug 报告（标题为十六进制串），目前处于 triage 状态，缺乏可复现信息，属于待清理的社区噪音。 |

---

### 4. 重要 PR 进展
今日无 Pull Request 更新。

---

### 5. 功能需求趋势
从近期 Issues 可提炼出以下社区最关注的功能方向：

- **Agent 技能生态完善**：脚本执行路径解析、工作目录上下文管理是 Agent 能力落地的关键瓶颈（#956）。
- **上下文与模型稳定性**：上下文去重、内存管理及 CAPI 错误处理成为高频痛点（#3558、#3791）。
- **企业级自定义模型支持**：BYOK 场景下的模型发现、配置简化需求显著上升（#3795）。
- **跨平台 DevOps 集成**：社区希望 Copilot CLI 不仅支持 GitHub，还能深度整合 Azure DevOps 工作流（#3794）。
- **终端 UI 一致性**：多标签页、多会话下的界面渲染稳定性仍需打磨（#3797）。

---

### 6. 开发者关注点
- **会话健壮性**：开发者对"单次错误永久污染会话"的容忍度极低（#3791），要求更强的输入校验、附件预检与会话隔离机制。
- **Agent 确定性**：自定义技能脚本在何处、以何种上下文执行必须可预测（#956），否则 Agent 工作流难以在生产环境落地。
- **错误信息透明度**：CAPI 400 错误中的 "Duplicate item"（#3558）及附件解析失败缺乏足够上下文，增加排查成本。
- **配置体验**：BYOK 用户厌倦了手动维护模型 ID，期望 CLI 能像主流工具一样自动探测可用模型（#3795）。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI 社区动态日报**  
*2026-06-15 | 数据来源: MoonshotAI/kimi-cli*

---

### 1. 今日速览

过去 24 小时无新版本发布，社区活跃度平稳。Issue 侧聚焦于**服务透明度**与**系统提示可控性**两大敏感话题，其中一则关于限速争议的反馈引发付费用户强烈关注；代码侧则集中合入了 3 个 Windows 平台体验修复，显示开发团队正在补齐跨平台兼容性短板。

---

### 2. 版本发布

今日无新 Release。

---

### 3. 社区热点 Issues

> 注：过去 24 小时内共有 3 条 Issue 更新，以下为其完整梳理与优先级解读。

| # | 状态 | 标题 | 重要性分析 | 社区反应 |
|---|------|------|------------|----------|
| **#2123** | 🔴 OPEN | [enhancement] 限速，限额严重 | **高**。付费用户指控实际调用额度（5 小时 60+ 次）与官方宣传的 300–1200 次存在巨大落差，且缺乏明确的额度计量方式，已涉及退款纠纷与服务透明度信任危机。 | 作者情绪强烈，引用《消费者权益保护法》维权；目前 👍 虽为 0，但属于典型的沉默大多数痛点，极易引发连锁讨论。 |
| **#2451** | 🔴 OPEN | [bug] System prompt conflicting with my desired workflow | **中高**。用户在使用 `k2.7-coding` 模型时，内置系统提示与其自定义的严格开发规范产生冲突，直接影响了 AI 编码助手的输出可控性。 | 刚创建尚无评论，但触及“AI 工具应服从用户意志还是平台预设”的核心设计哲学，预计会吸引提示工程开发者参与。 |
| **#850** | 🟢 CLOSED | [enhancement] Auto-load project context/rules at session start | **中**。请求仿照 Claude Code 的 `CLAUDE.md` 机制，在会话启动时自动加载 `AGENTS.md`、`.cursorrules` 等项目级规则文件。 | 历时 4 个月于昨日关闭，评论区有 3 条讨论；对于从其他 AI 编码工具迁移的用户群体，上下文自动感知是降低上手成本的关键需求。 |

---

### 4. 重要 PR 进展

> 注：过去 24 小时内共有 4 条 PR 更新，以下为其完整技术解读。

| # | 状态 | 标题 | 功能/修复内容 |
|---|------|------|---------------|
| **#2452** | 🔵 OPEN | fix(tools): fail StrReplaceFile when a multi-edit hunk is unmatched | 修复 `StrReplaceFile` 工具的静默失败缺陷：此前多段编辑中若某 hunk 未匹配，工具仅在**全部内容**未变化时才报错；修复后，单段 hunk 未匹配即可触发 `ToolError`，提升代码编辑的可靠性。 |
| **#2018** | 🟣 CLOSED | feat: add Alt+V paste support for Windows Terminal | 为 Windows Terminal 增加 `Alt+V` 粘贴回退快捷键。因 Windows Terminal 默认拦截 `Ctrl+V` 用于自身文本粘贴，导致 `prompt_toolkit` 无法接收媒体粘贴事件，此 PR 补齐了 Windows 下的交互一致性。 |
| **#2020** | 🟣 CLOSED | fix: use per-process log filenames to prevent rotation lock on Windows | 解决 Windows 下多进程并发运行 Kimi CLI 时的日志锁竞争问题。将日志文件名从固定的 `kimi.log` 改为 `kimi.{pid}.log`，消除 `loguru` 因 `PermissionError [WinError 32]` 导致的日志轮转失败。 |
| **#839** | 🟣 CLOSED | feat(shell): add configurable shell support for Windows | 增加 Windows 平台可配置 Shell 支持，允许用户自定义底层 Shell 路径，改善在 Windows 环境下的命令执行兼容性与开发者体验。 |

---

### 5. 功能需求趋势

基于今日 Issues 与近期社区讨论，可提炼出以下三个明确的需求方向：

1. **项目级上下文自动感知**  
   开发者强烈期望 Kimi Code 能原生识别项目根目录下的 `AGENTS.md`、`.cursorrules` 或 `CLAUDE.md` 等规则文件，实现“开箱即用”的项目记忆，减少每次会话重复交代技术栈与编码规范的成本。

2. **Windows 平台体验补齐**  
   今日 4 个 PR 中有 3 个针对 Windows（粘贴快捷键、多进程日志锁、可配置 Shell），表明该平台的边缘场景正被系统性修复，但社区仍期待更原生的 Windows 终端集成体验。

3. **服务透明度与配额可控性**  
   限速与额度计算方式的不透明已成为付费用户最大焦虑点。社区不仅需要更清晰的“剩余额度/速率”实时显示，也期望官方提供与“Code Plan”专业定位相符的 SLA 承诺。

---

### 6. 开发者关注点

- **付费性价比与知情权（🔥 高频痛点）**  
  开发者对“5 小时 60 次 vs 宣传 300–1200 次”的落差极为敏感，认为百分比进度条无法替代明确的数字配额，存在信息不对称。

- **系统提示的侵入性边界**  
  高级用户（尤其是通过 API Key 使用 `k2.7-coding` 的群体）开始反馈平台预设系统提示过度干预其自定义工作流，需求“用户提示优先”或“系统提示可覆盖”的开关。

- **跨工具迁移的上下文成本**  
  从 Claude Code、Cursor 等竞品迁移的用户将“自动加载项目规则”视为基础功能，其缺失显著抬高了多项目切换时的认知负担。

- **Windows 下的并发稳定性**  
  多进程日志锁等底层问题虽已被修复，但反映出 Windows 环境在过去可能是测试覆盖的薄弱环节，企业级用户会关注此类修复是否能进入长期 LTS 策略。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-06-15*

---

### 1. 今日速览

OpenCode 今日发布 **v1.17.7** 补丁版本，重点修复插件客户端端口复用、ACP Shell 输出及 PTY 环境变量传递问题。社区方面，关于 **DeepSeek V4 Pro 永久降价 75% 后调整 Go 订阅限制** 的讨论以 77 条评论、79 个 👍 的高热度关闭；同时，TUI 终端体验成为今日 PR 焦点，涉及终端模式重置、Linux 剪贴板支持及会话分页等多项改进进入评审阶段。

---

### 2. 版本发布

**v1.17.7** 已发布，核心变更如下：

- **Bugfixes**
  - 插件客户端请求现在复用活动服务器，不再固定假设默认本地端口。
  - ACP shell 工具调用现在从执行起始即展示命令与工作目录。
  - 插件提供的 shell 环境变量现已正确应用到 PTY 会话。
- **Improvements**
  - MCP 相关改进（详情见 Release Note）。

---

### 3. 社区热点 Issues

| # | 标题 | 状态 | 互动 | 关键看点 |
|---|------|------|------|----------|
| [#28846](https://github.com/anomalyco/opencode/issues/28846) | Adjust Go usage limits after DeepSeek V4 Pro permanent 75% price reduction | CLOSED | 77 评论 / 79 👍 | 社区最热议题。DeepSeek V4 Pro 大幅降价后，用户强烈呼吁上调 Go 订阅用量上限，官方已响应关闭。 |
| [#13984](https://github.com/anomalyco/opencode/issues/13984) | can not copy and paste in opencode CLI | OPEN | 48 评论 / 20 👍 | 长期存在的终端体验痛点，用户反馈剪贴板复制后无法粘贴，影响日常效率。 |
| [#15585](https://github.com/anomalyco/opencode/issues/15585) | When use a free model "free usage exceed" appeared | CLOSED | 48 评论 / 13 👍 | 免费模型触发“用量超出”引发大量质疑，反映免费层策略与用户体验之间的摩擦。 |
| [#28567](https://github.com/anomalyco/opencode/issues/28567) | [FEATURE]: Full MCP client capabilities | OPEN | 11 评论 / 21 👍 | 用户指出 OpenCode 的 MCP 客户端能力滞后于最新标准，要求补齐完整协议支持。 |
| [#32348](https://github.com/anomalyco/opencode/issues/32348) | EditBuffer Destroyed consistently popping after upgrading to 1.17.7 | OPEN | 3 评论 | **新版本回归**。macOS + Ghostty 环境下升级 1.17.7 后持续报错，需优先关注。 |
| [#31778](https://github.com/anomalyco/opencode/issues/31778) | [BUG] MCP server subprocess receives full process.env (API keys leaked) | OPEN | 2 评论 | **安全风险**。本地 MCP 子进程被传入完整 `process.env`，存在 API Key 与密码泄露隐患。 |
| [#26412](https://github.com/anomalyco/opencode/issues/26412) | Custom OpenAI-compatible provider: "Expected 'function.name' to be a string" on streaming tool call chunks | OPEN | 6 评论 | 自托管/企业场景阻塞。使用 vLLM 等自定义 OpenAI 兼容后端时，流式工具调用直接失败。 |
| [#11829](https://github.com/anomalyco/opencode/issues/11829) | [FEATURE] Recursive Language Model (RLM) Context Management | OPEN | 6 评论 / 11 👍 | 前沿架构提案。借鉴 MIT 论文，将上下文视为外部可查询环境，而非简单压缩/滑动窗口。 |
| [#32366](https://github.com/anomalyco/opencode/issues/32366) | bug: UI stuck on 'thinking' indefinitely after stream error | OPEN | 2 评论 | 稳定性缺陷。流式请求异常后 UI 无限卡死，无错误提示且无法自动恢复，必须重启应用。 |
| [#32172](https://github.com/anomalyco/opencode/issues/32172) | [FEATURE]: Add GLM-5.2 model support for Z.AI provider | OPEN | 7 评论 | 新模型接入需求。Z.AI 发布 GLM-5.2 推理模型，用户希望尽快在 OpenCode 中启用。 |

---

### 4. 重要 PR 进展

| # | 标题 | 类型 | 内容摘要 |
|---|------|------|----------|
| [#30977](https://github.com/anomalyco/opencode/pull/30977) | feat(tui): attach to configured server by default | Feature | TUI 新增 `server.attach` 配置，默认直接连接已配置服务器，而非仅本地模式。 |
| [#32364](https://github.com/anomalyco/opencode/pull/32364) | fix: reset terminal modes on tui shutdown | Bug fix | TUI 退出时重置终端模式，解决关闭后终端标题异常或状态残留问题。 |
| [#32373](https://github.com/anomalyco/opencode/pull/32373) | feat(opencode): support models.dev reasoning options | Feature | 为 models.dev 提供方增加 `reasoning_options` 支持，可按 effort 值生成精确模型变体。 |
| [#8535](https://github.com/anomalyco/opencode/pull/8535) | feat(session): bi-directional cursor-based pagination | Feature | 为会话消息引入双向游标分页，覆盖 Server、App、TUI 及 HttpApi，提升长会话加载性能。 |
| [#31867](https://github.com/anomalyco/opencode/pull/31867) | feat: improve deepseek prompt cache reuse | Feature / Refactor | 移除系统提示中动态注入的当前日期，提升 DeepSeek 提示缓存命中率，降低 API 成本。 |
| [#32302](https://github.com/anomalyco/opencode/pull/32302) | fix(opencode): forward parent attachments to subagents | Bug fix | 修复 `@mention` 子代理在 `task` 路径下丢失父会话附件的问题，确保上下文连贯。 |
| [#32241](https://github

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-06-15*

---

### 1. 今日速览
今日社区最激烈的讨论围绕 **Qwen OAuth 免费额度政策调整** 展开（#3203），该 Issue 单日激增 135 条评论，开发者对每日免费请求从 1,000 骤降至 100 并即将关闭免费入口表示强烈关切。与此同时，安全与权限类问题集中爆发，包括 VSCode 扩展被杀毒软件误报为木马、权限合约探测被绕过执行副作用命令等，成为开发者新的信任焦虑点。核心工程方面，工作流元数据提取、会话中断恢复、交互式扩展管理等重要 PR 仍在密集迭代。

---

### 2. 版本发布
**无**（过去 24 小时未发布新版本）。

---

### 3. 社区热点 Issues

| # | 标题 | 状态 | 重要性说明 |
|---|------|------|------------|
| **#3203** | [Qwen OAuth Free Tier Policy Adjustment](https://github.com/QwenLM/qwen-code/issues/3203) | OPEN | **社区头号焦点**。官方计划将每日免费额度从 1,000 降至 100 并关闭免费入口，引发 135 条评论的激烈反馈，开发者普遍担忧开发测试成本骤增与 Pro 计划长期售罄的困境。 |
| **#5055** | [Trojan:JS/ShaiWorm.DBA!MTB](https://github.com/QwenLM/qwen-code/issues/5055) | OPEN | **安全信任危机**。Windows 版 VSCode 扩展（`qwen-code-vscode-ide-companion`）被多款杀毒软件标记为木马，直接影响 IDE 分发与用户安装意愿，需官方尽快澄清并修复签名/打包流程。 |
| **#5102** | [Qwen Code executes a provider-requested side effect despite the permission-contract probe](https://github.com/QwenLM/qwen-code/issues/5102) | OPEN | **潜在安全漏洞**。在非交互式 CLI 配置下，权限合约探测阶段本应被拒绝的 shell 命令仍被执行并写入文件，暴露了权限控制机制的绕过风险。 |
| **#5080** | [阿里云 Standard API Key 与 Token Plan 接入点混用导致 401](https://github.com/QwenLM/qwen-code/issues/5080) | OPEN | **国内开发者高频痛点**。使用 `qwen config` 配置阿里云百炼后，切换模型时因 API Key 类型与 Token Plan 接入点不匹配导致认证失败，反映多认证体系并存时的配置复杂性。 |
| **#4218** | [MCP Server "filesystem" shows connected on UI, but tools are not available to the model](https://github.com/QwenLM/qwen-code/issues/4218) | OPEN | **MCP 生态阻塞**。UI 显示 MCP Server 已连接，但模型侧无法获取工具定义，影响基于 MCP 的扩展生态落地，Windows 平台尤为突出。 |
| **#5101** | [Qwen Code carries repeated large tool results through provider history](https://github.com/QwenLM/qwen-code/issues/5101) | OPEN | **上下文性能陷阱**。确定性本地验证显示，大体积工具输出被重复携带进历史记录，导致请求上下文膨胀直至超限，直接影响长会话稳定性与 Token 成本。 |
| **#4727** | [Dual Output 模式运行 TUI 无响应](https://github.com/QwenLM/qwen-code/issues/4727) | CLOSED | **CLI 稳定性**。通过 FIFO 管道进行 JSONL 双路输出时 TUI 完全无响应，影响自动化集成与 headless 场景下的交互可靠性。 |
| **#5119** | [when the agent wants to run a sudo command there is no way to allow it](https://github.com/QwenLM/qwen-code/issues/5119) | OPEN | **交互体验缺口**。Agent 尝试执行 `sudo` 命令时缺乏优雅的权限提升通道，只能让用户手动复制粘贴，打断自动化流程。 |
| **#4369** | [Stop using AI issue / PR and fix RAM leak manually](https://github.com/QwenLM/qwen-code/issues/4369) | CLOSED | **技术债与可维护性**。社区贡献者指出代码库中大量 AI 生成代码导致 GC 难以正常工作，呼吁团队手动修复内存泄漏而非依赖自动化补丁。 |
| **#3979** | [plan mode 下，qwen code 完成回复后在 ghostty 终端会出现不停闪屏](https://github.com/QwenLM/qwen-code/issues/3979) | OPEN | **终端兼容性**。在 ghostty 终端的 plan mode 下出现持续闪屏，反映新兴终端模拟器的渲染兼容问题。 |

---

### 4. 重要 PR 进展

| # | 标题 | 说明 |
|---|------|------|
| **#5123** | [fix(web-shell): remove redundant sanitizeSvg, fix mermaid render failure](https://github.com/QwenLM/qwen-code/pull/5123) | 移除 web-shell 中冗余的 SVG 消毒逻辑，直接复用 Mermaid 内置的 DOMPurify 严格模式，修复图表渲染失败问题。 |
| **#5094** | [feat(core): Workflow P4a — extractAndStripMeta + meta on RunOutcome](https://github.com/QwenLM/qwen-code/pull/5094) | 动态工作流第四阶段（P4a）落地，实现元数据提取与剥离，为后续工作流编排提供结构化运行时信息。 |
| **#5030** | [feat(core,cli,sdk): resume an interrupted turn without a synthetic "continue" message](https://github.com/QwenLM/qwen-code/pull/5030) | 允许会话在崩溃或流中断后恢复未完成的助手回合，无需向对话历史注入虚假的 `"continue"` 用户消息，保持上下文纯净。 |
| **#4850** | [feat(extensions): interactive multi-tab /extensions manager](https://github.com/QwenLM/qwen-code/pull/4850) | 将 `/extensions` 从只读列表升级为交互式多标签页管理器，覆盖已安装、发现、源管理全生命周期，并支持独立 MCP 服务器配置。 |
| **#5122** | [feat(computer-use): configurable screenshot max dimension](https://github.com/QwenLM/qwen-code/pull/5122) | 为 computer-use 驱动引入截图长边上限的用户级配置（设置项 + 环境变量），解决不同场景下截图尺寸与 Token 消耗的权衡问题。 |
| **#5073** | [fix: warn on oversized context instructions](https://github.com/QwenLM/qwen-code/pull/5073) | 当 `QWEN.md` 或上下文指令块预估占用超过当前模型上下文窗口 15% 时，在启动阶段发出警告，帮助用户及时发现隐性的 Token 浪费。 |
| **#5118** | [feat(web-shell): per-task token & time detail on completed todos](https://github.com/QwenLM/qwen-code/pull/5118) | 在 web-shell 的待办列表中，点击已完成任务可展开查看起止时间、耗时、输入/输出/缓存 Token 及 API 耗时等资源明细。 |
| **#5120**

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*