# AI CLI 工具社区动态日报 2026-06-01

> 生成时间: 2026-06-01 03:37 UTC | 覆盖工具: 7 个

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



---

**Claude Code 社区动态日报**  
*2026-06-01 | 数据来源: github.com/anthropics/claude-code*

---

### 1. 今日速览
今日仓库仅发布 v2.1.159 补丁版本，无用户可见变更，且过去 24 小时无新 Pull Request 更新。社区讨论高度活跃，共有 50 条 Issue 获得更新，焦点集中在 **Agent 系统可靠性**、**Claude 4.8 新模型稳定性异常**，以及 **Token 成本失控** 三大方向。

---

### 2. 版本发布
- **v2.1.159** — 仅包含内部基础设施改进，无用户可见变更。  
  [查看 Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.159)

---

### 3. 社区热点 Issues（Top 10）

| # | 状态 | 标题 | 核心看点 |
|---|------|------|----------|
| **#34229** | 🔴 OPEN<br>(invalid) | **Phone verification**<br>739 评论 / 818 👍 | 社区参与度最高的议题，反映用户对强制手机验证流程的广泛争议与困惑，尽管被标记为 invalid，热度仍居首位。<br>[链接](https://github.com/anthropics/claude-code/issues/34229) |
| **#64093** | 🔴 OPEN | **5h token usage massively outstripping actual context**<br>20 评论 | Windows 平台用户报告 5 小时 Token 配额被异常快速耗尽，实际上下文并未达到对应量级，涉及成本计量准确性。<br>[链接](https://github.com/anthropics/claude-code/issues/64093) |
| **#60334** | 🟢 CLOSED | **Image processing failures causing conversation token waste**<br>35 评论 | 图片处理失败错误反复出现，单次会话消耗约 70% 的 5 小时窗口配额，反映图片容错与计费机制缺陷。<br>[链接](https://github.com/anthropics/claude-code/issues/60334) |
| **#14131** | 🔴 OPEN | **German umlauts randomly replaced with ASCII substitutes**<br>33 评论 / 21 👍 | 长期存在的国际化 Bug（ä/ö/ü → ae/oe/ue），自 2025 年 12 月创建以来持续影响非英语用户输出质量。<br>[链接](https://github.com/anthropics/claude-code/issues/14131) |
| **#64080** | 🔴 OPEN | **Harness silently executes duplicated parallel tool_use blocks**<br>11 评论 | Agent 调度层缺陷：固定批次的并行子 Agent 任务从 6 次被静默放大至 24 次执行，导致成本与延迟成倍增长

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
**日期：2026-06-01**

---

### 1. 今日速览
今日社区最突出的矛盾集中在**认证与登录体验**——手机号验证与 ChatGPT 登录流相关 Issue 累计获得数百条讨论与超百点赞，成为新用户与多设备用户的首要阻塞。同时，**Windows 桌面端**遭遇 SQLite 指令集兼容性崩溃与插件缓存路径失效的双重稳定性挑战。代码侧，团队密集推进**多账户切换（Profile Switcher）**三部曲、**多代理运行时锁定**及 Windows x64 紧急修复，并发布了 Rust `v0.136.0-alpha.2`。

---

### 2. 版本发布
- **rust-v0.136.0-alpha.2** 已发布，但 Release Note 仅列出版本号，暂无详细变更说明。  
  链接：https://github.com/openai/codex/releases/tag/rust-v0.136.0-alpha.2

---

### 3. 社区热点 Issues（精选 10 条）

| # | 标题 | 状态 | 为什么重要 | 社区反应 |
|---|------|------|-----------|----------|
| [#20161](https://github.com/openai/codex/issues/20161) | Phone number verification doesn't work | CLOSED | 跨设备登录时强制要求验证手机号，但用户并未绑定手机，导致 SSO 登录完全阻塞。 | **177 条评论，110 👍**，过去 24 小时评论数最高的 Issue，影响面极广。 |
| [#23794](https://github.com/openai/codex/issues/23794) | Codex Desktop no longer shows visible context/token usage indicator | CLOSED | 更新后桌面端不再显示上下文/Token 用量，用户无法感知剩余窗口，影响长会话规划。 | **160 条评论，157 👍**，UX 回归问题引发大量反馈。 |
| [#25144](https://github.com/openai/codex/issues/25144) | Add an option to disable automatic conversion of long pasted prompts into .txt attachments | OPEN | 长文本粘贴被自动转为 `.txt` 附件，破坏了结构化 Prompt 的可读性与迭代效率。 | **22 条评论，27 👍**，开发者强烈呼吁增加开关控制。 |
| [#21598](https://github.com/openai/codex/issues/21598) | Windows Desktop: Chrome plugin unavailable in Norway/EU | OPEN | 挪威/EU 用户即使安装并连接 Chrome 扩展，桌面端仍无法使用 `@Chrome` 技能，疑似区域合规或灰度策略问题。 | **26 条评论，12 👍**，涉及欧盟数据合规与功能 rollout。 |
| [#20320](https://github.com/openai/codex/issues/20320) | ChatGPT asking phone number verify but didn't send any code yet | OPEN | ChatGPT Plus 用户升级 Pro 前遭遇登录循环，验证码未发送即被拦截，直接阻断付费转化。 | **24 条评论，5 👍**，与 #20161 形成认证痛点矩阵。 |
| [#25244](https://github.com/openai/codex/issues/25244) | Goal style questions disappear after restarting the client | OPEN | Goal Mode 下的问题在客户端重启后丢失，严重破坏长周期任务的可追溯性。 | **11 条评论**，被用户标记为“serious error”。 |
| [#24031](https://github.com/openai/codex/issues/24031) | Codex on GPT-5.5 when will it support 1M? | CLOSED | GPT-5.5 已发布月余，社区追问 1M 上下文支持时间表，官方此前承诺后未兑现即关闭 Issue。 | **9 条评论，16 👍**，反映大上下文需求迫切。 |
| [#25285](https://github.com/openai/codex/issues/25285) | Windows Codex Desktop persists volatile plugin cache hash paths in sessions | OPEN | Windows 桌面端将插件缓存的绝对路径持久化到会话中，缓存更新后旧会话无法加载技能。 | **8 条评论**，Windows 插件系统的稳定性隐患。 |
| [#25472](https://github.com/openai/codex/issues/25472) | Rogue Subagents with Goal Mode | OPEN | Goal Mode 下出现“失控子代理”，在明确禁止的情况下仍执行未授权的文件写入与网络请求。 | **6 条评论**，涉及代理安全与权限边界。 |
| [#25399](https://github.com/openai/codex/issues/25399) | apply_patch Add File silently overwrites existing files | OPEN | CLI 的 `apply_patch` 工具在添加文件时静默覆盖已有文件，存在数据丢失风险。 | **3 条评论**，工具链安全性问题，性质严重。 |

---

### 4. 重要 PR 进展（精选 10 条）

| # | 标题 | 说明 |
|---|------|------|
| [#25490](https://github.com/openai/codex/pull/25490) | Disable SQLite intrinsics for Windows x64 releases | **紧急修复**：Windows x64 在 Haswell CPU 上因 SQLite 3.51.x 指令集导致 `STATUS_ILLEGAL_INSTRUCTION` 启动崩溃，通过禁用 intrinsics 解决，避免回退 SQLite 版本。 |
| [#25469](https://github.com/openai/codex/pull/25469) | [profile-switcher][rust] -- [1/3] Add app-server account session protocol | 多账户切换三部曲之**协议层**：定义 `accountSession/*` 接口，为桌面端多账号 Profile 切换奠定通信基础。 |
| [#25470](https://github.com/openai/codex/pull/25470) | [profile-switcher][rust] -- [2/3] Add saved account session credential slots | 多账户切换三部曲之**凭证层**：扩展 `codex-login` 存储抽象，

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报**  
*2026-06-01 | 数据来源: github.com/google-gemini/gemini-cli*

---

### 1. 今日速览
过去 24 小时社区无新版本发布，但 Issues 活跃度显著，共 50 条 Issue 更新，核心矛盾仍集中在 **Agent 稳定性** 与 **终端执行可靠性**。多个 P1 级 Bug（如 Generalist Agent 挂起、Shell 命令假死）持续获得高关注，同时 AST 感知工具与组件级行为评估成为架构演进的重要方向。

---

### 3. 社区热点 Issues

1. **Generalist agent hangs** [#21409](https://github.com/google-gemini/gemini-cli/issues/21409)  
   P1 Bug，7 条评论，8 个 👍。用户反馈 generalist agent 在简单操作（如创建文件夹）时无限挂起，严重影响基础工作流，是近期呼声最高的稳定性痛点。

2. **Robust component level evaluations** [#24353](https://github.com/google-gemini/gemini-cli/issues/24353)  
   P1 史诗，7 条评论。作为行为评估（behavioral evals）的后续，已积累 76 个测试用例，旨在建立更细粒度的 Agent 质量度量体系，决定长期可靠性。

3. **Subagent recovery after MAX_TURNS is reported as GOAL success** [#22323](https://github.com/google-gemini/gemini-cli/issues/22323)  
   P1 Bug，6 条评论。子代理达到最大轮次后却返回 `status: "success"`，隐藏中断事实，导致开发者无法感知任务失败，可靠性风险极高。

4. **Shell command execution gets stuck with "Waiting input"** [#25166](https://github.com/google-gemini/gemini-cli/issues/25166)  
   P1 Bug，4 条评论，3 个 👍。简单 Shell 命令执行完毕后仍显示“等待输入”并假死，属于核心交互路径的阻塞性问题。

5. **Assess the impact of AST-aware file reads, search, and mapping** [#22745](https://github.com/google-gemini/gemini-cli/issues/22745)  
   P2 史诗，7 条评论。探索通过 AST 感知工具精确读取方法边界、减少误读和 Token 噪音，被视为降低 Agent 交互成本的关键架构投资。

6. **Gemini does not use skills and sub-agents enough** [#21968](https://github.com/google-gemini/gemini-cli/issues/21968)  
   P2 Bug，6 条评论。开发者配置了大量 Skills（如 gradle、git），但模型几乎从不主动调用，导致功能采用率低，需改进调度策略。

7. **browser subagent fails in wayland** [#21983](https://github.com/google-gemini/gemini-cli/issues/21983)  
   P1 Bug，4 条评论。Wayland 环境下浏览器子代理直接失败，阻碍 Linux 桌面用户正常使用浏览器自动化能力。

8. **get-shit-done output hook causes crash** [#22186](https://github.com/google-gemini/gemini-cli/issues/22186)  
   P1 Bug，3 条评论。特定输出钩子触发 CLI 崩溃，影响依赖该工作流的用户，稳定性亟待修复。

9. **Gemini CLI encounters 400 error with > 128 tools** [#24246](https://github.com/google-gemini/gemini-cli/issues/24246)  
   P2 Bug，3 条评论。可用工具超过 128 个时触发 API 400 错误，反映工具范围智能收敛机制缺失。

10. **Agent should stop/discourage destructive behavior** [#22672](https://github.com/google-gemini/gemini-cli/issues/22672)  
    P2 需求，2 条评论。Agent 在复杂 git 操作中可能使用 `git

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*2026-06-01*

---

### 1. 今日速览
GitHub Copilot CLI 今日发布 v1.0.57-4，修复了 tmux 按键冲突与 diff 鼠标交互问题；但社区密集反馈 v1.0.56 以来出现复制失效、频繁重登等回归问题，同时会话管理与插件组织需求持续升温。今日无合并请求更新。

---

### 2. 版本发布
**v1.0.57-4** 已发布，主要变更如下：
- **Added**：diff 模式下支持鼠标点击选中行。
- **Improved**：`preToolUse` 钩子错误现在会**拒绝**工具调用，避免静默执行带来的安全风险。
- **Fixed**：`Ctrl+C` 等组合键在 tmux 中正常工作；`@-mention` 文件搜索不再受查询字符串影响。

---

### 3. 社区热点 Issues（Top 10）

| # | Issue | 重要性 & 社区反应 | 链接 |
|---|-------|------------------|------|
| **#3600** | **[Critical Bug] 孤儿会话已运行约两个月无法清理** | 标记为 Critical，存在长期资源占用与状态污染风险；新报即受关注。 | [链接](https://github.com/github/copilot-cli/issues/3600) |
| **#3597** | **v1.0.56 升级后 24 小时内被要求重登超过 8 次** | 认证稳定性严重回归，影响多设备用户；用户报告双电脑均复现。 | [链接](https://github.com/github/copilot-cli/issues/3597) |
| **#3609** | **v1.0.56 起控制台复制提示成功但实际未写入剪贴板** | 核心交互回归 Bug，直接影响日常使用；与 #3586 形成跨平台复制问题集群。 | [链接](https://github.com/github/copilot-cli/issues/3609) |
| **#3586** | **Linux 平台复制功能自 1.0.49 起失效** | 平台级功能退化（1.0.48 正常）；用户附截图，等待修复。 | [链接](https://github.com/github/copilot-cli/issues/3586) |
| **#3605** | **多行拖拽复制会截断行间空格** | 影响当前 1.0.57-4，终端渲染缺陷；新报且附详细复现步骤。 | [链接](https://github.com/github/copilot-cli/issues/3605) |
| **#3607** | **Esc 键无法中断模型流式响应** | 基础键盘交互缺失，用户只能杀进程取消；体验痛点明确。 | [链接](https://github.com/github/copilot-cli/issues/3607) |
| **#1632** | **支持 skills 子文件夹以更好地组织插件** | 长期功能需求，插件数量多时的刚需；**14 👍、6 条评论**，社区呼声最高。 | [链接](https://github.com/github/copilot-cli/issues/1632) |
| **#2675** | **支持从剪贴板粘贴图片到对话** | 多模态交互需求，可提升调试与沟通效率；**5 👍**，持续受关注。 | [链接](https://github.com/github/copilot-cli/issues/2675) |
| **#3602** | **SDK 无条件注入 `safe.bareRepository=explicit` 到宿主 `process.env`** | 潜在副作用，影响所有子进程 Git 行为；引发对 SDK 边界与宿主隔离的深入讨论。 | [链接](https://github.com/github/copilot-cli/issues/3602) |
| **#3596** | **恢复会话后 `/model` 报未认证错误** | 会话状态与认证状态不同步，直接阻断工作流；与 #3597 共同指向认证持久化隐患。 | [链接](https://github.com/github/copilot-cli/issues/3596) |

---

### 4. 重要 PR 进展
今日仓库 **无新增或更新的 Pull Requests**。

---

### 5. 功能需求趋势
从今日 20 条 Issue 中提炼出以下五大社区关注方向：

1. **终端输入与渲染体验**：剪贴板复制/粘贴、键盘快捷键（Esc 中断、Ctrl+C）、tmux 兼容、图片粘贴、多行文本选择。
2. **插件与技能治理**：skills 子文件夹组织、安装后热加载（`/skills reload`）、市场配置覆盖（`extraKnownMarketplaces`）。
3. **会话生命周期管理**：孤儿会话清理、恢复稳定性（schema 校验、负值 token）、远程控制（免费版 404 限制）。
4. **认证与会话状态持久化**：跨会话保持登录、恢复后认证不丢失、模型列表加载权限。
5. **工具链与编码兼容性**：非 ASCII 字符（CJK/emoji）支持、Windows 1252 编码保留、Git worktree 原生支持、SDK 环境变量隔离。

---

### 6. 开发者关注点
- **v1.0.56 回归问题集群**：复制失效（#3609、#3586）、频繁重登（#3597）成为今日最高频痛点，建议优先排查该版本引入的终端与认证改动。
- **键盘与终端兼容性**：tmux 内按键、多行复制空格截断、Esc 中断等细节体验缺陷密集出现，显示终端模拟器适配仍是长期功课。
- **会话与认证状态管理**：孤儿会话（#3600）、恢复后认证丢失（#3596、#3598）表明会话持久化层存在 schema 与状态同步隐患。
- **国际化与编码**：Bash 工具丢弃非 ASCII 字符（#3601）、Windows 1252 被强制转 UTF-8（#3604），反映全球化场景下的编码处理不足。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI 社区动态日报 | 2026-06-01**

### 1. 今日速览
今日社区无新版本发布，但 **v1.46 回归问题** 成为焦点，Linux 与 WSL2 用户集中反馈登录失败、CLI 输入异常及 `kimi acp` 无响应等故障。与此同时，社区贡献者针对 API 层提交了两项关键修复，分别解决 OpenAI 客户端超时默认值缺失与 Tool Call 参数双重编码导致的校验失败问题。

### 2. 版本发布
今日无新版本发布。

### 3. 社区热点 Issues（按更新时间排序）

1. **[bug] 重启 kimi cli 会发送历史图片，污染会话** #2413  
   链接：https://github.com/MoonshotAI/kimi-cli/issues/2413  
   **重要性**：会话状态管理缺陷，跨平台（Ubuntu/Windows）复现，严重影响多轮对话连续性。  
   **社区反应**：6月1日新报，暂无评论，需紧急排查状态持久化逻辑。

2. **[bug] Login to KimiCode getting error after upgrade to 1.46** #2403  
   链接：https://github.com/MoonshotAI/kimi-cli/issues/2403  
   **重要性**：基础准入功能在最新版出现回归，阻断 Linux 用户正常使用。  
   **社区反应**：5月31日新增，已有2条评论，多用户确认受影响。

3. **[bug] linux CLI 输入异常** #2410  
   链接：https://github.com/MoonshotAI/kimi-cli/issues/2410  
   **重要性**：终端输入处理故障，直接影响核心交互体验，Linux 平台特异性问题。  
   **社区反应**：1条评论跟进，与 #2403 共同构成 v1.46 Linux 兼容性警报。

4. **[bug] kimi acp 命令无响应** #2412  
   链接：https://github.com/MoonshotAI/kimi-cli/issues/2412  
   **重要性**：子代理/自动提交相关命令完全卡死，需手动 Ctrl+C 中断，阻塞工作流。  
   **社区反应**：WSL2 环境报告，暂无回复，需确认是否与其他 Linux 输入问题同源。

5. **[enhancement] Please make your kimi code api work as OpenAI-compatible API** #2208  
   链接：https://github.com/MoonshotAI/kimi-cli/issues/2208  
   **重要性**：生态集成核心诉求，用户希望在 Cursor 等 IDE 中直接复用 Kimi K2.6。  
   **社区反应**：持续发酵，已有4条评论，是近期最受关注的功能请求之一。

6. **大 context 请求频繁 ConnectTimeout，httpx connect

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-06-01*

---

### 1. 今日速览
今日社区无新版本发布，但开发活跃度保持高位。议题持续聚焦**本地模型生态**（Gemma 4、DeepSeek V4 的 tool calling 稳定性）与**Desktop/CLI 状态同步**缺陷；同时，多个 PR 推进 TUI 体验增强（Fish shell 补全、实时 token 吞吐量）及新模型/平台集成（Snowflake Cortex、MiniMax M3）。

---

### 2. 版本发布
**无**（过去 24 小时无新 Release）。

---

### 3. 社区热点 Issues

| # | 状态 | 标题 | 链接 | 核心动态与社区反应 |
|---|------|------|------|-------------------|
| 29079 | OPEN | GPT Models takes too long to respond | [链接](https://github.com/anomalyco/opencode/issues/29079) | **114 评论 / 48 👍**，社区最热性能议题。用户反馈 GPT 5.4（xhigh 变体）对简单指令响应从秒级波动到分钟级，严重影响编码流，疑似模型调度或流式处理瓶颈。 |
| 20695 | OPEN | Memory Megathread | [链接](https://github.com/anomalyco/opencode/issues/20695) | **83 评论 / 60 👍**，官方集中跟踪内存泄漏。维护者明确呼吁提供 heap snapshot，拒绝 AI 推测式解决方案，显示团队正系统性定位根因。 |
| 20995 | OPEN | Gemma 4 (e4b) tool calling fails via Ollama | [链接](https://github.com/anomalyco/opencode/issues/20995) | **19 评论 / 45 👍**。Gemma 4 通过 Ollama 返回 `tool_calls` 时，OpenCode 无法识别流式 `tool_calls`，本地模型兼容性受阻。 |
| 21034 | OPEN | gemma-4-26b/31b interaction issues | [链接](https://github.com/anomalyco/opencode/issues/21034) | **17 评论 / 18 👍**。即使应用最新 tokenizer 补丁，模型仍陷入工具循环或失败，与 #20995 共同构成 Gemma 4 可用性危机。 |
| 30070 | OPEN | Desktop /MCP panel shows 0/0 while CLI lists connected MCP servers | [链接](https://github.com/anomalyco/opencode/issues/30070)

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
**日期：2026-06-01**

---

### 1. 今日速览
Qwen Code 今日推送 **v0.17.0 nightly** 版本，重点修复了 `/rewind` 场景下误判 "compressed turn" 的边界问题。社区新增多项功能请求，包括 **MiniMax-M3 模型接入**与 **InstructionsLoaded Hook** 扩展机制；同时，v0.17.0 与 Ollama 本地模型的集成稳定性、Windows 平台 MCP 连接可靠性成为开发者讨论焦点。

---

### 2. 版本发布
**v0.17.0-nightly.20260601.1c48e4121** 已发布  
- **修复**：解决 `rewind` 在 mid-turn message 场景下误报 "compressed turn" 错误的问题，提升会话回退准确性。  
- 该版本由 CI 流水线自动发布，属于 v0.17.0 正式版前的最新 nightly 构建。  
[查看 Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.17.0-nightly.20260601.1c48e4121)

---

### 3. 社区热点 Issues（过去 24 小时）

| # | 标题 | 状态 | 重要性说明 |
|---|------|------|-----------|
| **#4663** | [Add MiniMax-M3 and checkbox-based MiniMax model selection](https://github.com/QwenLM/qwen-code/issues/4663) | OPEN | 社区呼吁接入 MiniMax-M3 官方模型 ID，并将模型选择 UI 从文本输入改为多选框，降低配置门槛。今日新建即获 7 条讨论，反映多模型生态诉求强烈。 |
| **#4641** | [MCP 稳定性 — Windows 下 session 间连接不确定](https://github.com/QwenLM/qwen-code/issues/4641) | OPEN | 配置 8 个 MCP Server 后，每次启动仅 3~5 个随机可用，阻塞 Windows 开发者工作流。属于跨 session 的底层连接可靠性问题。 |
| **#4657** | [v0.17.0 + Ollama + Qwen 3.6 无法完成任务](https://github.com/QwenLM/qwen-code/issues/4657) | OPEN | 用户反馈在最新 nightly 中，通过 OpenAI 兼容接口调用本地 Ollama 模型时，任务创建与文件写入能力完全失效，疑似 v0.17.0 回归。 |
| **#4514** | [tracking(serve): daemon capability gaps & prioritized backlog](https://github.com/QwenLM/qwen-code/issues/4514) | OPEN | 系统梳理 `qwen serve` HTTP/SSE 表面能力缺口，10 条评论聚焦 daemon 模式的企业级 API 完备性，是 serve 架构的核心路线图议题。 |
| **#4664** | [Add InstructionsLoaded hook for instruction file loading](https://github.com/QwenLM/qwen-code/issues/4664) | OPEN | 提议在指令文件加载时触发 Hook，为插件生态提供扩展点，与同日提交的 PR #4665 形成联动，体现社区对扩展性的主动建设。 |
| **#4651** | [auto-dump memory diagnostics to disk on pressure detection](https://github.com/QwenLM/qwen-code/issues/4651) | OPEN | 针对长会话 OOM 崩溃后无迹可寻的痛点，提议在内存压力达到 hard/critical 时自动落盘诊断 JSON。已获 1 个 👍，被标记为 `ready-for-agent`。 |
| **#4493** | [Rider 无法登录 qwen code — OAuth 重定向死循环](https://github.com/QwenLM/qwen-code/issues/4493) | OPEN | JetBrains Rider 用户在登录态网页中遭遇无限重定向，无法调用阿里云 Token Plan，9 条评论显示 IDE 集成认证体验仍是阻塞点。 |
| **#4554** | [feat(telemetry): cover qwen serve daemon end-to-end with OpenTelemetry](https://github.com/QwenLM/qwen-code/issues/4554) | OPEN | 指出 `qwen serve` daemon 进程在 HTTP 路由、session 生命周期、ACP 子进程管理等环节存在可观测性盲区，企业部署需求迫切。 |
| **#4637** | [fix(acp): discontinued qwen-oauth still returned in authMethods, trapping users on JetBrains IDEs](https://github.com/QwenLM/qwen-code/issues/4637) | CLOSED | **P1 级 Bug**：已废弃的 `qwen-oauth` 仍被返回给 JetBrains IDE 用户，导致认证死胡同。虽已关闭，但反映 IDE 插件与后端认证状态同步的深层风险。 |
| **#3881** | [调用本地部署的 qwen3.6-27b 首次提问持续返回 "/" 直到 token 上限](https://github.com/QwenLM/qwen-code/issues/3881) | CLOSED | 本地模型部署场景下的严重输出异常，已关闭但影响广泛，提示本地 LLM 兼容层仍需打磨。 |

---

### 4. 重要 PR 进展（过去 24 小时）

| # | 标题 | 说明 |
|---|------|------|
| **#4490** | [chore(integration): merge daemon_mode_b_main into main](https://github.com/QwenLM/qwen-code/pull/4490) | 将 daemon Mode B 的 F1~F5 功能批量合入主干，是 serve/daemon 架构的一次重大集成，影响后续所有 daemon 相关迭代。 |
| **#4655** | [feat(web-shell): UI improvements, subagent rendering, and scroll-follow rewrite](https://github.com/QwenLM/qwen-code/pull/4655) | Web Shell 全方位重构：引入虚拟滚动减少长对话 DOM 压力，重写子 Agent 权限审批渲染逻辑，并优化自动滚动体验。 |
| **#3778** | [feat(desktop): Add desktop app package with Qwen ACP SDK integration](https://github.com/QwenLM/qwen-code/pull/3778) | 新增 `packages/desktop` 桌面应用包，集成 Qwen ACP SDK，标志着 Qwen Code 从 CLI/IDE 插件向独立桌面客户端延伸。 |
| **#4665** | [Add InstructionsLoaded hook for instruction file loading](https://github.com/QwenLM/qwen-code/pull/4665) | 实现指令文件加载时的 Hook 事件，支持内存发现与 `@` 导入两种场景，为社区插件提供标准化接入点。 |
| **#4654** | [feat(core): auto-dump memory diagnostics to disk on pressure detection](https://github.com/QwenLM/qwen-code/pull/4654) | 当 `MemoryPressureMonitor` 检测到 hard/critical 压力时，自动将诊断 JSON 写入磁盘，解决 OOM 崩溃后无法定位根因的难题。 |
| **#4656** | [Add project MCP pending approval](https://github.com/QwenLM/qwen-code/pull/4656) | 项目级 `.mcp.json` 发现机制：新增安全待审批状态，项目 MCP 在显式批准前不会创建传输层或执行发现，强化供应链安全。 |
| **#4613** | [feat(daemon): keep model & approval-mode state consistent across clients sharing a session](https://github.com/QwenLM/qwen-code/pull/4613) | 修复多客户端（聊天视图/终端/IDE）共享 daemon session 时，当前模型与审批模式状态不同步的问题，提升多端协作一致性。 |
| **#4652** | [feat(input): move physical cursor to visual cursor for IME input](https://github.com/QwenLM/qwen-code/pull/4652) | 将终端物理光标与视觉光标对齐，解决 IME

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*