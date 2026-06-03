# AI CLI 工具社区动态日报 2026-06-03

> 生成时间: 2026-06-03 03:40 UTC | 覆盖工具: 7 个

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

以下是基于 2026-06-03 社区动态生成的横向对比分析报告：

---

## 1. 生态全景

当前 AI CLI 工具市场呈现显著的分化态势：Claude Code、GitHub Copilot CLI 与 Qwen Code 形成第一梯队，围绕 MCP 生态集成、上下文工程化与终端体验进行高频迭代；而 OpenAI Codex、Gemini CLI、Kimi Code CLI 及 OpenCode 则处于沉寂或数据空白期。社区焦点已从“模型能力演示”转向“生产级可靠性”，MCP 规模化架构、跨端配置同步、Windows 平台补齐及成本可控性成为共性攻坚方向。头部工具在 Agent 编排、语音交互等差异化特性上各辟蹊径，但均面临长会话稳定性与计费信任的双重考验。

---

## 2. 各工具活跃度对比

| 工具 | 今日活跃 Issues | 今日活跃 PRs | 版本发布 | 社区状态 |
|------|----------------|-------------|----------|----------|
| **Claude Code** | 10+ 热点（#38335 单 Issue 达 761 评论 / 461 👍） | 3 | v2.1.161 | 高活跃，争议密集 |
| **GitHub Copilot CLI** | 10 个热点 | 0 | v1.0.59 / v1.0.58 | 稳定发布，PR 停滞 |
| **Qwen Code** | 10 个（24h 内共 34 条活跃 Issue） | 10（24h 内） | v0.17.0-preview.0 | 极高频迭代 |
| **Kimi Code CLI** | 0 | 0 | 无 | 24h 无活动 |
| **OpenAI Codex** | 无数据 | 无数据 | 无 | 数据缺失 |
| **Gemini CLI** | 无数据 | 无数据 | 无 | 数据缺失 |
| **OpenCode** | 无数据 | 无数据 | 无 | 数据缺失 |

---

## 3. 共同关注的功能方向

**MCP 生态与企业级安全**  
Claude Code 面临子代理 MCP 注册表为空（#64909）及过多 MCP 导致提示超长崩溃（#37793）；Copilot CLI 存在项目级配置被静默忽略（#3642）与自托管注册表 URL 构造错误（#3436）；Qwen Code 则正推动项目级 `.mcp.json` 与显式审批门控（#4615 / #4713）。三者共同暴露 MCP 从个人玩具向团队基础设施演进时的架构与安全瓶颈。

**上下文与会话生命周期管理**  
Claude Code 用户强烈呼吁 Skills / Memory 跨端同步（#20697）及压缩策略透明化；Copilot CLI 社区需求自动命名会话与持久化记忆；Qwen Code 则修复 `/clear` 误换 Session ID（#4593）并探索长会话压缩式回放（#4694）。长周期任务的可追溯与可恢复成为共性刚需。

**Windows 平台与终端工程化**  
Claude Code 将 Windows 能力补齐列为高频诉求；Copilot CLI 遭遇 CJK 字符重叠（#3536）、PowerShell 路径解析失败（#2355）及滚动行为异常（#2205）；Qwen Code 密集修复 IME 光标对齐（#4652）与 Vim 模式键位泄漏（#4677）。终端仿真质量正成为 AI CLI 的“最后一公里”。

**成本与模型可控性**  
Claude Code 爆发 Max 订阅配额异常速耗（#38335）与 1M 上下文强制计费（#63896）信任危机；Copilot CLI 存在企业模型目录不可见（#1703）与本地端点支持不足（#3624）；Qwen Code 针对本地模型流超时（#4604 / #4711）推出可配置 `bodyTimeout`。开发者对“云端订阅 + 本地端点”的混合可控性诉求显著上升。

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线特征 |
|------|---------|---------|-------------|
|

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-03 | 来源：anthropics/skills*

---

### 1. 热门 Skills 排行（Top PRs）

基于功能影响力、企业场景覆盖及创新性综合评估，当前社区最受关注的 Skills 如下：

- **#1140 agent-creator + 多工具评估修复** [OPEN]  
  元技能，支持为特定任务创建专属 Agent 组合；同时修复 `evaluation.py` 多并行工具调用评估错误及 Windows 路径兼容性问题。被视为 Skill 生态的“基础设施级”贡献。  
  🔗 https://github.com/anthropics/skills/pull/1140

- **#568 ServiceNow 平台 Skill** [OPEN]  
  覆盖 ITSM、ITOM、SecOps、FSM、SPM、CSDM、IntegrationHub 等企业全模块，旨在将 Claude Code 从代码助手扩展为企业 IT 工作流核心入口。  
  🔗 https://github.com/anthropics/skills/pull/568

- **#723 testing-patterns** [OPEN]  
  全栈测试指南，涵盖 Testing Trophy 模型、AAA 模式、React 组件测试及边缘用例处理，直接回应开发者对代码质量保障的强需求。  
  🔗 https://github.com/anthropics/skills/pull/723

- **#360 AppDeploy** [OPEN]  
  支持从 Claude 直接部署并管理全栈 Web 应用至公网，打通“生成代码→部署上线”的最后一公里，实用价值极高。  
  🔗 https://github.com/anthropics/skills/pull/360

- **#514 document-typography** [OPEN]  
  针对 AI 生成文档的排版质量控制，解决孤儿词（orphan）、寡居标题（widow）、编号错位等常见排版问题，提升输出专业度。  
  🔗 https://github.com/anthropics/skills/pull/514

- **#181 SAP-RPT-1-OSS predictor** [OPEN]  
  集成 SAP 开源表格基础模型，针对 SAP 业务数据进行预测分析，填补 ERP 生态与 Claude Code 集成的空白。  
  🔗 https://github.com/anthropics/skills/pull/181

- **#806 sensory（macOS AppleScript 自动化）** [OPEN]  
  通过 `osascript` 实现原生 macOS 自动化，替代基于截图的 Computer Use，提供更低成本、更高精度的本地系统交互方案。  
  🔗 https://github.com/anthropics/skills/pull/806

- **#154 shodh-memory** [OPEN]  
  为 AI Agent 提供跨会话的持久化记忆系统，通过 `proactive_context` 主动召回历史上下文，解决长周期任务中的记忆中断痛点。  
  🔗 https://github.com/anthropics/skills/pull/154

---

### 2. 社区需求趋势（Issues 提炼）

从高热度 Issue 中可提炼出四大明确方向：

- **组织级 Skill 治理与共享**  
  企业用户强烈需求组织内直接共享 Skill 库（#228，13 评论 / 7 👍），而非手动导出/上传；同时 #492 警示社区 Skill 冒用 `anthropic/` 命名空间的安全风险，反映治理与信任边界机制亟待完善。  
  🔗 #228: https://github.com/anthropics/skills/issues/228  
  🔗 #492: https://github.com/anthropics/skills/issues/492

- **开发者工具链稳定性（skill-creator 与评估体系）**  
  `run_eval.py` 0% 触发率（#556，9 评论 / 6 👍）、skill-creator 不符合最佳实践（#202）及大量 Windows 兼容性 PR 表明，Skill 创作与自测工具本身存在跨平台缺陷，社区急需更健壮的 creator 工具链。  
  🔗 #556: https://github.com/anthropics/skills/issues/556  
  🔗 #202: https://github.com

---

**Claude Code 社区动态日报**  
*2026-06-03*

---

### 1. 今日速览
Claude Code 发布 v2.1.161，增强可观测性指标维度与 Agent 并行任务可视化；社区持续聚焦 **Max 订阅会话配额异常消耗**（#38335）及 **1M 上下文计费争议**，同时 Windows 平台能力补齐与跨端 Skills 同步成为高频功能诉求。

---

### 2. 版本发布
**v2.1.161** 已发布，主要更新包括：
- **可观测性增强**：`OTEL_RESOURCE_ATTRIBUTES` 环境变量值现在会作为标签附加到指标数据点，支持按团队、仓库等自定义维度切分用量指标。
- **Agent 并行任务优化**：`claude agents` 列表在任务分发（fan-out）时优先展示 `done/total` 进度；peek 视图直接高亮耗时最长的子项，提升并行任务可读性。

---

### 3. 社区热点 Issues（Top 10）

1. **[#38335] Max 订阅会话配额异常速耗（CLI）**  
   761 评论 · 461 👍 | [链接](https://github.com/anthropics/claude-code/issues/38335)  
   自 3 月 23 日起，大量 Max 计划用户反馈 CLI 端会话限制异常快速耗尽，是社区声量最高的计费信任危机。

2. **[#62123] 模型工具调用解析失败（opus 4.7）**  
   40 评论 · 65 👍 | [链接](https://github.com/anthropics/claude-code/issues/62123)  
   macOS/VS Code 环境下，opus 4.7 频繁抛出 *"The model's tool call could not be parsed (retry also failed)"*，重试无效，直接中断开发流。

3. **[#20697] Desktop 与 CLI Skills 双向同步**  
   28 评论 · 99 👍 | [链接](https://github.com/anthropics/claude-code/issues/20697)  
   高赞功能请求。用户要求 Claude Desktop 与 Claude Code CLI 之间的 Skills 互通，避免重复配置与技能碎片化。

4. **[#63875] 工具调用解析失败反复打断会话（Windows）**  
   26 评论 · 27 👍 | [链接](https://github.com/anthropics/claude-code/issues/63875)  
   Windows 平台同样遭遇模型 tool call 解析失败，且错误无法自愈，严重影响长会话稳定性。

5. **[#63896] 1M 上下文强制要求 Usage credits**  
   22 评论 · 11 👍 | [链接](https://github.com/anthropics/claude-code/issues/63896)  
   压缩阶段触发 1M 上下文时直接报错阻断，要求用户开启积分付费或切换模型，引发成本可控性质疑。

6. **[#37793] MCP 过多导致子代理提示超长（>200K）**  
   21 评论 · 23 👍 | [链接](https://github.com/anthropics/claude-code/issues/37793)  
   用户级 MCP 服务器配置过多时，子代理因 tool definitions 超过 200K token 上限直接失败，暴露 MCP 规模化架构瓶颈。

7. **[#63015] 自动压缩在 100% 上下文时不触发（回归）**  
   16 评论 · 12 👍 | [链接](https://github.com/anthropics/claude-code/issues/63015)  
   v2.1.153 回归问题：状态栏已显示 *"100% context used"*，但 auto-compact 始终不触发，存在上下文泄漏风险。

8. **[#64919] VS Code 扩展强制启用 1M 上下文（Pro 计划）**  
   2 评论 | [链接](https://github.com/anthropics/claude-code/issues/64919)  
   v2.1.161 VS Code 扩展被曝在 Pro 计划下未经请求强制使用 1M 上下文，导致所有用法被计费拦截，完全无法工作。

9. **[#64909] 子代理 MCP 工具注册表为空**  
   2 评论 | [链接](https://github.com/anthropics/claude-code/issues/64909)  
   通过 `Task` 工具派生的子代理未继承父进程的 MCP 服务器连接，子代理工具注册表为空，复杂工作流编排能力受限。

10. **[#63197] 低上下文时压缩报错（已关闭）**  
    4 评论 | [链接](https://github.com/anthropics/claude-code/issues/63197)  
    v2.1.153 回归：上下文仅 20% 即触发 *"context window limit"* 压缩失败。今日被官方关闭，表明该回归已修复。

---

### 4. 重要 PR 进展

1. **[#64857] 修复 extensibility.py 在项目受控 GUI 中跟随符号链接的安全问题**  
   [链接](https://github.com/anthropics/claude-code/pull/64857)  
   解决 `extensibility.py` 在处理项目受控 GUI 时未正确处理符号链接的安全隐患。

2. **[#64728] 从 devcontainer 防火墙白名单移除失效域名**  
   [链接](https://github.com/anthropics/claude-code/pull/64728)  
   清理已失效的 `statsig.anthropic.com`，解决该域名解析失败导致 devcontainer 启动即退出的问题。

3. **[#62821] 文档：plugin-MCP 会话标识的 env-bridge 变通方案（已合并）**  
   [链接](https://github.com/anthropics/claude-code/pull/62821)  
   补充官方文档，说明在 plugin stdio MCP 服务器尚未接收 `CLAUDE_CODE_SESSION_ID` 时的 env-bridge 临时方案。

---

### 5. 功能需求趋势

- **跨端生态统一**：Skills、Memory 与配置在 Claude Desktop 与 CLI 之间无缝同步的呼声极高，用户拒绝“两端两套系统”。
- **Windows 平台补齐**：Computer Use CLI 支持、COWork 连接器工具暴露、IntelliJ 平台稳定性等 Windows 体验缺口正在被密集填补。
- **会话生命周期管理**：导出/备份、归档、手动完成 Agent 会话等需求涌现，反映用户将 Claude Code 用于长周期生产项目。
- **成本与上下文可控性**：社区强烈需要 1M 上下文的显式开关、更透明的压缩策略，以及订阅配额异常消耗的官方解释。
- **MCP 规模化架构**：随着 MCP 生态膨胀，子代理继承父级工具、注册表隔离、提示长度控制已成为复杂工作流的核心瓶颈。

---

### 6. 开发者关注点

- **计费与配额焦虑**：Max 计划异常消耗、Pro 用户被强制升级 1M 上下文导致积分扣费，信任危机持续发酵，官方尚未给出明确根因说明。
- **上下文管理可靠性**：自动压缩失效、压缩误判、长会话记忆漂移等问题直接影响长程开发体验，开发者对“200K/1M 上下文”的实际可用性存疑。
- **模型稳定性**：opus 4.7 tool call 解析失败在 macOS/Windows/VS Code 多平台高频复现，且重试机制无效，严重打断流式编程节奏。
- **MCP 扩展瓶颈**：过多 MCP 服务器导致子代理崩溃、Task 子进程工具注册表为空，制约基于 Agent 的复杂自动化编排落地。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报 | 2026-06-03**

---

### 1. 今日速览
今日社区聚焦 **v1.0.59** 带来的本地语音输入能力（`/voice`），但企业场景下模型目录可达性与组织级模型同步问题持续发酵。Windows 平台终端渲染、国际化支持及 MCP 生态配置成为开发者反馈的高频痛点。

---

### 2. 版本发布

**v1.0.59**（2026-06-02）
- 新增 **`/voice` 命令**：支持调用本地语音转文本模型口述提示词，实现终端内的免提交互。

**v1.0.58**（2026-06-02）
- **Rubber Duck** 与**远程 JSON RPC** 默认启用；
- 实验性指令增强：支持 `/every` 与 `/after` 定时调度提示词；
- 新增 GitHub `/theme` 主题与可快捷访问 Issues、Pull Requests、Gists 的实验性 UI。

---

### 3. 社区热点 Issues（10 个最值得关注的）

| # | 标题 | 状态 | 互动 | 核心看点 |
|---|------|------|------|----------|
| **#1703** | Copilot CLI 未列出所有组织启用的模型（如 Gemini 3.1 Pro） | 🔴 Open | 👍54 / 💬28 | 同一账户与组织下，CLI 模型列表远少于 VS Code Copilot，企业用户选型严重受阻。<br>🔗 https://github.com/github/copilot-cli/issues/1703 |
| **#2101** | 瞬态 API 错误导致频繁触发速率限制 | 🔴 Open | 👍17 / 💬26 | 大量 `transient API error` 最终触发限流，工作流连续性被严重打断。<br>🔗 https://github.com/github/copilot-cli/issues/2101 |
| **#2205** | Terminator 终端滚动行为异常 | 🔴 Open | 👍12 / 💬12 | 鼠标滚轮不再浏览历史输出，而是跳转输入历史，交互逻辑反转。<br>🔗 https://github.com/github/copilot-cli/issues/2205 |
| **#2355** | Windows 内部 PowerShell 工具无法生成 `pwsh.exe` | 🔴 Open | 👍6 / 💬6 | 交互式提示正常，但内部命令执行时报 `ENOENT`，PowerShell 7 路径解析失败。<br>🔗 https://github.com/github/copilot-cli/issues/2355 |
| **#3436** | `/mcp search` 构造自定义注册表 URL 时缺失 `/v0.1/` 段 | 🔴 Open | 👍1 / 💬5 | 导致自托管 MCP 注册表返回 404，破坏企业级 MCP Registry URL 配置。<br>🔗 https://github.com/github/copilot-cli/issues/3436 |
| **#3624** | 为通用本地推理端点（非 Anthropic）提供 BYOM 注册 | 🟢 Closed | 👍0 / 💬3 | 社区呼吁支持 LM Studio、Ollama 等 OpenAI 兼容的本地端点，突破现有 Anthropic 配置限制。<br>🔗 https://github.com/github/copilot-cli/issues/3624 |
| **#3642** | 1.0.58 未自动加载项目级 `.copilot/mcp-config.json` | 🟢 Closed | 👍0 / 💬2 | 仅读取全局配置，项目级 MCP 服务器被静默忽略，影响团队协作与可复现性。<br>🔗 https://github.com/github/copilot-cli/issues/3642 |
| **#3536** | Windows 终端 CJK 字符视觉重叠/丢失 | 🔴 Open | 👍2 / 💬1 | 中英文混合输入时，已提交提示气泡中的 CJK 字符显示异常（缓冲区数据正确）。<br>🔗 https://github.com/github/copilot-cli/issues/3536 |
| **#3636** | 企业 VPN 环境下语音模式无法获取模型目录 | 🔴 Open | 👍0 / 💬1 | 与 v1.0.59 `/voice` 直接相关，企业网络隔离导致 STT 模型目录不可达。<br>🔗 https://github.com/github/copilot-cli/issues/3636 |
| **#3572** | 无 GitHub 仓库工作目录时组织级自定义代理不可见 | 🔴 Open | 👍1 / 💬1 | 组织级 agent 依赖当前目录的 git remote 判定，非仓库场景下无法加载。<br>🔗 https://github.com/github/copilot-cli/issues/3572 |

---

### 4. 重要 PR 进展

过去 24 小时内，仓库 **无更新的 Pull Requests**。

---

### 5. 功能需求趋势

- **多模型生态与 BYOM**：开发者迫切要求 CLI 与 VS Code 的模型列表保持严格一致，并支持 Ollama / LM Studio 等通用本地推理端点（OpenAI 兼容 API）。
- **MCP 与企业集成**：项目级 MCP 配置自动加载、自托管注册表 URL 路径规范、配置错误暴露机制成为企业落地的三大焦点。
- **Windows 终端体验**：CJK 渲染、IME 闪烁、剪贴板失效、PowerShell 集成等问题集中爆发，平台适配质量明显滞后于 macOS/Linux。
- **语音与交互创新**：伴随 `/voice` 发布，企业网络环境下的语音目录可达性、低延迟本地 STT 以及“推送即说”交互细节受关注。
- **会话与上下文管理**：自动命名会话、持久化记忆、禁用自动压缩等需求上升，反映开发者对长周期任务与审计追溯的期待。

---

### 6. 开发者关注点

- **模型可见性落差**：CLI 与 VS Code / 组织后台的模型策略不同步，造成“同一账户、不同客户端、不同能力”的困惑。
- **Windows 平台稳定性**：从终端渲染（CJK、IME、滚动）到系统工具

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-06-03*

---

### 1. 今日速览
Qwen Code 今日推送了 `v0.17.0-preview.0` 及对应 nightly 版本，重点修复了 rewind 功能中的 "compressed turn" 误判问题。社区讨论高度集中在 **MCP 安全审批机制**、**本地模型流超时配置** 与 **终端 UI 稳定性** 三大方向，相关核心 PR 已进入活跃评审阶段。

---

### 2. 版本发布
- **[v0.17.0-preview.0](https://github.com/QwenLM/qwen-code/releases/tag/v0.17.0-preview.0)** / **[v0.17.0-nightly.20260603.68408c30c](https://github.com/QwenLM/qwen-code/releases/tag/v0.17.0-nightly.20260603.68408c30c)**  
  - **修复 rewind 逻辑**：解决当对话中存在 mid-turn 消息时，系统误报 "compressed turn" 错误的问题。  
  - 常规版本发布流程更新。

---

### 3. 社区热点 Issues（过去 24 小时）

| # | 状态 | 标题 | 核心看点 |
|---|------|------|----------|
| [#4615](https://github.com/QwenLM/qwen-code/issues/4615) | OPEN | 项目级 `.mcp.json` 支持 + 待审批语义 | **安全架构级需求**。要求引入项目级 MCP 配置并强制“先审批后启动”，与 Claude Code 对齐，获 4 条深度讨论。 |
| [#4604](https://github.com/QwenLM/qwen-code/issues/4604) | CLOSED | API Error: terminated (cause: Body Timeout Error) | 本地/慢速模型高频痛点，5 条评论。社区正通过可配置超时参数系统性解决。 |
| [#4095](https://github.com/QwenLM/qwen-code/issues/4095) | OPEN | 原子文件写入 & 事务回滚 | 数据可靠性核心议题。第一阶段实现后暴露 Docker 与共享工作场景下的 inode 权限丢失问题，持续迭代中。 |
| [#4676](https://github.com/QwenLM/qwen-code/issues/4676) | CLOSED | Auto-mode 分类器超时过于严格 | 自动审批模式下，LLM 分类器因超时直接阻断操作。已调整阶段超时并关闭 thinking 以降低误判。 |
| [#4663](https://github.com/QwenLM/qwen-code/issues/4663) | CLOSED | 新增 MiniMax-M3 及复选框模型选择 | 多模型生态扩展，8 条评论。将原本手输 Model ID 的交互改为多选 UI，降低配置门槛。 |
| [#4711](https://github.com/QwenLM/qwen-code/issues/4711) | OPEN | 自托管慢模型 Body Timeout Error | 与 #4604 同源，强调 5 分钟默认超时对本地大模型的限制，需暴露自定义配置。 |
| [#4714](https://github.com/QwenLM/qwen-code/issues/4714) | OPEN | 请求禁用自动创建的 skills | **可控性争议**。开发者反馈自动生成的 skills 存在幻觉错误且优先级过高，导致不可预测行为。 |
| [#4672](https://github.com/QwenLM/qwen-code/issues/4672) | OPEN | 自动接受/YOLO 模式下读取错误导致文件不更新 | 影响效率的稳定性 Bug：读取失败时不会重试，需再次下指令才更新。 |
| [#2950](https://github.com/QwenLM/qwen-code/issues/2950) | CLOSED | 长上下文时屏幕无限上下滚动 | 经典 UI 稳定性问题，在上下文过长时终端自动滚屏异常，视觉体验极差。 |
| [#4593](https://github.com/QwenLM/qwen-code/issues/4593) | CLOSED | `/clear` 不应切换新 Session ID | 会话管理体验优化。原实现会丢弃 Session ID，导致基于会话的调试与日志追踪断裂。 |

---

### 4. 重要 PR 进展（过去 24 小时）

| # | 状态 | 标题 | 功能/修复摘要 |
|---|------|------|---------------|
| [#4713](https://github.com/QwenLM/qwen-code/pull/4713) | OPEN | MCP 项目 `.mcp.json` + 工作空间审批门控 | 实现与 #4615 配套的审批机制：项目级 `.mcp.json` 默认不可信，需显式批准后才启动，并建立跨源优先级模型。 |
| [#4677](https://github.com/QwenLM/qwen-code/pull/4677) | OPEN | 修复 Vim 模式 Esc 泄漏、Enter 提交及渲染延迟 | 系统性修复终端 Vim 模式：阻止 Esc 误触全局处理器、补全缺失的 NORMAL 命令、优化输入渲染。 |
| [#4694](https://github.com/QwenLM/qwen-code/pull/4694) | OPEN | 长会话恢复的压缩式回放 | 替代无界 JSONL 原始事件存储，按 turn 边界压缩合并流式分片与工具调用，将加载复杂度降至 O(turns)。 |
| [#4667](https://github.com/QwenLM/qwen-code/pull/4667) | CLOSED | 新增可配置 `bodyTimeout` 防止本地模型流超时 | 为 Node.js 无代理路径引入可自定义的 undici `bodyTimeout`（默认 0 禁用），根治 300 秒默认超时导致本地模型断连。 |
| [#4533](https://github.com/QwenLM/qwen-code/pull/4533) | OPEN | `/skills` 选择器对话框 | 裸 `/skills` 命令现可打开浏览/搜索/切换/选择的一体化对话框，并支持工作区级 `skills.disabled` 配置。 |
| [#4710](https://github.com/QwenLM/qwen-code/pull/4710) | OPEN | Web-shell 内联终端命令 UI | 将 `/agents`、`/memory`、`/mcp` 等命令从弹窗改为消息流内联面板；新增 `/insight` 流式进度与 `/btw` 支持。 |
| [#4652](https://github.com/QwenLM/qwen-code/pull/4652) | CLOSED | IME 输入时光标物理位置对齐 | 解决 CJK 输入法候选框出现在错误位置的问题，通过 yoga layout 计算绝对坐标，实现光标同步。 |
| [#4708](https://github.com/QwenLM/qwen-code/pull/4708) | OPEN | 允许有意的前台 sleep 用于退避 | 为 shell sleep 拦截增加显式逃生舱：命令尾部注释 `# intentional-sleep: <reason>` 可在 10 分钟内豁免拦截，满足速率限制退避。 |
| [#4719](https://github.com/QwenLM/qwen-code/pull/4719) | OPEN | 修复 CLI 包缺少扩展示例模板 | 解决 `qwen extensions new` 因打包遗漏 `dist/examples/` 而失败的问题，补充构建脚本与测试。 |
| [#4577](https://github.com/QwenLM/qwen-code/pull/4577) | OPEN | 新增 `/triage` skill 用于 Issue/PR 分类 | 项目级 skill，支持自动化 GitHub 问题分类与 PR 准入审查，附带双语评论模板，面向 CI/GitHub Actions 场景。 |

---

### 5. 功能需求趋势

从过去 24 小时的 34 条活跃 Issue 中，可提炼出社区当前最关注的四大方向：

1. **MCP 安全与项目级配置**  
   开发者强烈呼吁引入 `.mcp.json` 的项目级作用域及显式审批门控，避免仓库级 MCP 服务器自动启动带来的安全隐患。

2. **本地/自托管模型体验**  
   `Body Timeout Error` 成为高频关键词。社区不仅需要可配置的超时参数，还期望针对慢速本地模型（LM Studio、Ollama 等）优化流式连接稳定性。

3. **文件操作与自动模式的可靠性**  
   原子写入、事务回滚、YOLO/Auto-edit 模式下的读取失败重试，反映出开发者在“无人值守”场景下对数据一致性的担忧。

4. **终端 UI 与交互稳定性**  
   长上下文无限滚屏、IME 候选框错位、界面闪烁、Vim 模式输入泄漏等问题持续被提及，终端渲染引擎的健壮性是当前体验瓶颈。

---

### 6. 开发者关注点

- **超时配置自主权**：使用本地或私有部署模型的开发者反复遭遇 300 秒默认 `bodyTimeout` 中断，急需在 `generationConfig` 中显式控制或彻底禁用。  
- **自动模式的可预测性**：Auto-mode 分类器超时即阻断、自动 skills 生成错误内容且难以关闭，导致“无人值守”反而增加人工介入成本。  
- **终端渲染质量**：CJK 输入、长会话滚屏、Vim 模式键位冲突等 UI 问题在中文开发者群体中反馈密集，终端交互的精细度直接影响日常编码效率。  
- **MCP 供应链安全**：随着 MCP 生态扩展，开发者要求区分“全局可信源”与“项目级待审源”，避免任意代码通过 MCP 在本地执行。  
- **Skills 系统的可控性**：自动生成的 skills 与用户自定义技能之间的优先级冲突，以及缺乏便捷的禁用/管理入口，成为新的配置痛点。

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*