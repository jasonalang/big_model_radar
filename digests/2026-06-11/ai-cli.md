# AI CLI 工具社区动态日报 2026-06-11

> 生成时间: 2026-06-11 03:32 UTC | 覆盖工具: 7 个

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

以下是基于 2026-06-11 社区动态的 AI CLI 工具横向对比分析报告：

---

### 1. 生态全景

当前 AI CLI 生态已进入**工程化深水区**，竞争焦点从“基础代码补全”转向**Agent 可靠性、上下文成本控制和终端原生体验**。各平台密集修复 Shell 假死、Token 异常消耗和跨平台渲染缺陷，显示工具链正从“个人辅助”向“企业级自动化基础设施”演进。与此同时，自主任务模式（如 `/goal`）、TUI 重构和多模型路由能力成为产品差异化的关键战场，整体呈现“**高频迭代、痛点集中、安全加固**”的态势。

---

### 2. 各工具活跃度对比

| 工具 | 今日 Issue 动态 | 今日 PR 动态 | 版本发布 | 关键备注 |
|------|----------------|-------------|---------|---------|
| **OpenAI Codex** | 多条热点（成本/Auth/崩溃） | 多条核心 PR（上下文压缩） | rust-v0.140.0-alpha.4 / alpha.7（2 个） | Windows 桌面端集中崩溃，底层重构上下文窗口 |
| **Gemini CLI** | 10 条热点 Issue | 8 个重点 PR（含 3 项安全修复） | 无 | Agent 稳定性与安全加固为主轴 |
| **GitHub Copilot CLI** | **41 条更新** | 无 | 无 | v1.0.60 回归问题引发终端渲染与插件争议 |
| **OpenCode** | 10 条热点 Issue | 3 个重点 PR（TUI 2.0 等） | v1.17.1 / .2 / .3（3 个补丁） | 24 小时内三连发，紧急修复认证与桌面崩溃 |
| **Claude Code** | 未披露 | 未披露 | 无 | 当日无显著社区动态披露 |
| **Kimi Code CLI** | 未披露 | 未披露 | 无 | 当日无显著社区动态披露 |
| **Qwen Code** | 未披露 | 未披露 | 无 | 当日无显著社区动态披露 |

---

### 3. 共同关注的功能方向

- **Agent 稳定性与执行可靠性**  
  **Gemini CLI**（Shell 假死 #25166、子代理状态误报 #22323）、**OpenCode**（xfyun 引擎繁忙重试）、**Copilot CLI**（后台子代理挂起 #3547）均面临 Agent/子代理中断或假死，社区要求更健壮的进程管理与错误传播。

- **上下文管理与 Token 效率**  
  **OpenAI Codex**（上下文压缩 / Token 预算重构）、**Gemini CLI**（AST 感知文件读取 #22745，降低 Token 噪音

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-11 | 来源：github.com/anthropics/skills*

---

### 1. 热门 Skills 排行

基于官方 PR 队列热度（按评论数排序），当前社区关注度最高的 Skills 如下：

| # | Skill | 功能简述 | 状态 | 链接 |
|---|-------|---------|------|------|
| 1 | **Automation Workflows Builder / AI Experience Consultant / Frontend Design** | 一次性提交三大生产力 Skill，覆盖自动化工作流构建、AI 体验咨询与前端设计定义 | Open | [#1046](https://github.com/anthropics/skills/pull/1046) |
| 2 | **Document Typography** | AI 生成文档的排版质量控制，修复孤字换行、寡段标题、编号错位等通用瑕疵 | Open | [#514](https://github.com/anthropics/skills/pull/514) |
| 3 | **ODT Skill** | OpenDocument（.odt/.ods）创建、模板填充与 HTML 转换，面向开源/ISO 标准文档流 | Open | [#486](https://github.com/anthropics/skills/pull/486) |
| 4 | **Skill Quality Analyzer & Skill Security Analyzer** | 元 Skill（Meta-Skill），对现有 Skill 进行五维质量审计与安全分析，填补生态自我治理空白 | Open | [#83](https://github.com/anthropics/skills/pull/83) |
| 5 | **Frontend Design（改进版）** | 重构现有前端设计 Skill，提升指令清晰度与单轮对话可执行性 | Open | [#210](https://github.com/anthropics/skills/pull/210) |
| 6 | **SAP-RPT-1-OSS Predictor** | 基于 SAP 开源表格基础模型的业务数据预测分析 Skill，面向 ERP 场景 | Open | [#181](https://github.com/anthropics/skills/pull/181) |
| 7 | **Agent Creator** | 任务专属 Agent 集的元 Skill，同步修复多工具并行调用评估逻辑 | Open | [#1140](https://github.com/anthropics/skills/pull/1140) |
| 8 | **Testing Patterns** | 全栈测试指南，涵盖 Testing Trophy、React 组件测试、AAA 模式与边缘场景 | Open | [#723](https://github.com/anthropics/skills/pull/723) |

---

### 2. 社区需求趋势

从 Issues 评论热度与内容提炼，社区最期待的五大方向：

- **企业级共享与治理**（[#228](https://github.com/anthropics/skills/issues/228), [#492](https://github.com/anthropics/skills/issues/492)）：组织级 Skill 库、命名空间信任边界、权限治理是最高频诉求。团队计划用户强烈要求 Org-wide 共享，而非手动传文件。
- **文档工程与版式控制**（[#514](https://github.com/anthropics/skills/pull/514), [#486](https://github.com/anthropics/skills/pull/486), [#189](https://github.com/anthropics/skills/issues/189)）：从 ODT 支持到排版细节，社区希望 Claude 输出可直接交付的“生产级”文档。
- **测试与代码健康**（[#723](https://github.com/anthropics/skills/pull/723), [#147](https://github

---



</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-06-11*

---

### 1. 今日速览
今日社区最突出的动态是 **Windows 桌面端在最新版本（26.608.x）中出现集中性启动崩溃与性能退化**，多个新 Issue 指向安装后无法启动、UI 透明或进程泄漏；与此同时，开发团队正密集推进**上下文窗口压缩（compaction）与 Token 预算（token budget）**的底层重构，24 小时内出现多条相关核心 PR。

---

### 2. 版本发布
- **rust-v0.140.0-alpha.7 / alpha.4**  
  Rust CLI 连续发布两个 Alpha 版本，属于 0.140.0 迭代周期。目前 Release Note 仅标注版本号，预计为后续上下文管理相关接口提供预发布支持。  
  - https://github.com/openai/codex/releases/tag/rust-v0.140.0-alpha.7  
  - https://github.com/openai/codex/releases/tag/rust-v0.140.0-alpha.4  

---

### 3. 社区热点 Issues（精选 10 条）

| Issue | 说明与社区反应 |
|-------|---------------|
| **#14593** [OPEN] Burning tokens very fast<br>👍 265 / 💬 604<br>https://github.com/openai/codex/issues/14593 | **成本敏感型核心痛点**。Business 订阅用户在 VS Code 扩展中持续遭遇 Token 异常高速消耗，直接影响使用成本。该 Issue 已保持数月高热度，成为社区长期追踪的“顶流” Bug。 |
| **#26867** [OPEN] GitHub PR review 仍使用已停用 workspace<br>👍 7 / 💬 13<br>https://github.com/openai/codex/issues/26867 | **账户迁移后的 Auth 残留**。用户从 Business workspace 迁移至 Personal Pro 后，Codex GitHub PR Review 仍尝试调用已停用 workspace，导致工作流中断。近期集中反馈，影响 CI/CD

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报**  
*2026-06-11 | 数据来源: google-gemini/gemini-cli*

---

### 1. 今日速览
今日社区核心焦点集中在 **Agent 稳定性** 与 **安全加固** 两大主题。核心团队刚提交了一个 P1 级 PR，旨在彻底修复 Shell 命令执行后假死的问题（#25166）；同时，过去 24 小时内合并了多项安全修复，包括终端工具确认的防注入锁止和私有 IP 解析加固。Issues 方面，通用 Agent 挂起与 AST 感知代码工具的持续评估仍是讨论热点。

---

### 2. 版本发布
今日无新版本发布。

---

### 3. 社区热点 Issues

| # | 标题 | 重要性 | 社区动态 |
|---|------|--------|----------|
| **#21409** | [Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409) | 🔴 P1 Bug | 通用代理频繁无响应，简单操作（如创建文件夹）也会挂起超过一小时，获 8 个 👍，是近期用户痛点最集中的反馈。 |
| **#24353** | [Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353) | 🔴 P1 Epic | 跟进“行为评估”测试体系，已生成 76 条测试用例并在 6 个模型上运行，是保障 Agent 质量的基础设施工程。 |
| **#22745** | [Assess the impact of AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745) | 🟡 P2 Epic | 探索基于 AST 的文件读取与代码库映射，以减少误读边界、降低 Token 噪音并提升导航效率，评论活跃。 |
| **#22323** | [Subagent recovery after MAX_TURNS is reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323) | 🔴 P1 Bug | 子代理达到最大轮次后仍报告 `status: "success"`，隐藏中断事实，严重影响多 Agent 协作的可靠性。 |
| **#25166** | [Shell command execution gets stuck with "Waiting input"](https://github.com/google-gemini/gemini-cli/issues/25166) | 🔴 P1 Bug | Shell 命令已结束但 CLI 仍显示“等待输入”，获 3 个 👍，今日已有针对性修复 PR 提交。 |
| **#21968** | [Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968) | 🟡 P2 Bug | 开发者反馈模型几乎不会主动调用自定义 Skill 和子代理，必须显式指示，制约自动化体验。 |
| **#26525** | [Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525) | 🟡 P2 Security | Auto Memory 在内容进入模型上下文后才进行 Secret 脱敏，存在数据泄露风险，需确定性脱敏机制。 |
| **#26522** | [Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522) | 🟡 P2 Bug | 低价值会话未被标记为已处理，导致后台提取代理无限重试，浪费计算资源。 |
| **#22186** | [get-shit-done output hook causes crash](https://github.com/google-gemini/gemini-cli/issues/22186) | 🔴 P1 Bug | 特定输出钩子触发崩溃，影响“get-shit-done”等高频工作流的稳定性。 |
| **#21983** | [browser subagent fails in wayland](https://github.com/google-gemini/gemini-cli/issues/21983) | 🔴 P1 Bug | 浏览器子代理在 Wayland 环境下直接失败，影响 Linux 桌面用户的浏览器自动化场景。 |

---

### 4. 重要 PR 进展

| # | 标题 | 状态 | 功能/修复摘要 |
|---|------|------|---------------|
| **#27842** | [fix(core): never let shell exit results hang on the output drain](https://github.com/google-gemini/gemini-cli/pull/27842) | 🟢 Open | **P1 修复**：解决 Shell 命令完成后输出管道无错误处理导致 CLI 假死的问题（修复 #25166）。 |
| **#27502** | [fix(core): resolve P1 crash during terminal resize (ioctl EBADF)](https://github.com/google-gemini/gemini-cli/pull/27502) | 🔴 Closed | 修复终端调整大小时 PTY 已销毁但布局引擎仍调用 `ioctl` 导致的竞态崩溃。 |
| **#27472** | [fix(ui): enforce truncation lockout for tool confirmations to prevent IPI](https://github.com/google-gemini/gemini-cli/pull/27472) | 🔴 Closed | **P1 安全**：在工具确认 UI 引入“截断锁止”，防止攻击者通过间接提示注入（IPI）绕过人工确认。 |
| **#27473** | [fix(security): resolve hostnames before private-IP check](https://github.com/google-gemini/gemini-cli/pull/27473) | 🔴 Closed | 安全修复：在 `isBlockedHost` 中先解析主机名再检查是否为私有 IP，防止绕过网络隔离。 |
| **#27767** | [fix(cli): prevent path traversal vulnerabilities during skill install](https://github.com/google-gemini/gemini-cli/pull/27767) | 🟢 Open | 修复 `installSkill`/`linkSkill` 中的路径遍历漏洞，防止 frontmatter 路径字段逃逸允许目录。 |
| **#27753** | [ci: validate workflow_run origin before consuming the E2E artifact](https://github.com/google-gemini/gemini-cli/pull/27753) | 🟢 Open | CI 安全加固：验证 `workflow_run` 来源，防止 Fork PR 通过工件投毒在主干流水线中执行恶意代码。 |
| **#27698** | [fix(core): Ensure zero-quota limits fail fast to prevent retry loop hang](https://github.com/google-gemini/gemini-cli/pull/27698) | 🟢 Open | 零配额硬限制场景下快速失败，避免陷入 10 次无意义重试循环导致 CLI 长时间挂起。 |
| **#27839** | [fix(core): make read_background_output delay abort-aware](https://github.com/google-gemini/gemini-cli/pull/27839) | 🟢 Open | 修复按 ESC 取消后台输出读取后，因 `setTimeout`

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报 | 2026-06-11**

---

### 1. 今日速览

今日社区无新版本发布及 PR 合并，但 Issues 区在过去 24 小时内迎来 41 条更新，终端渲染缺陷与模型可用性成为绝对焦点。v1.0.60 版本引发的插件钩子回归与流式输出损坏成为开发者新痛点，而 CLI 与 VS Code 之间模型列表持续割裂（尤其是 Gemini 系列）的问题仍在高位发酵。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 社区热点 Issues

| # | 标题 | 状态 | 核心看点 |
|---|------|------|----------|
| **#53** | [Bring back the GitHub Copilot in the CLI commands to not break workflows](https://github.com/github/copilot-cli/issues/53) | OPEN | **社区自救信号**。时隔 9 个月官方仍未回应，评论区已孵化出 `shell-ai` 等社区替代方案（75 👍，34 评论）。 |
| **#1703** | [Copilot CLI does not list all org-enabled models while VS Code Copilot does](https://github.com/github/copilot-cli/issues/1703) | CLOSED | **模型可用性标杆 Issue**。组织已启用的模型（如 Gemini 3.1 Pro）在 VS Code 可用但 CLI 缺失，引发大量企业用户共鸣（54 👍，31 评论）。 |
| **#223** | ["Copilot Requests" permission for fine-grained tokens should be visible for org-owned tokens](https://github.com/github/copilot-cli/issues/223) | OPEN | **企业治理痛点**。组织级 PAT 无法看到 Copilot 权限，迫使企业在自动化场景中使用个人 Token（76 👍，29 评论）。 |
| **#2082** | [ctrl+shift+c no longer copies to clipboard on Linux](https://github.com/github/copilot-cli/issues/2082) | OPEN | **Linux 体验倒退**。v1.0.4 起传统终端复制快捷键失效，虽提供替代方案但打破既有肌肉记忆（21 评论）。 |
| **#1707** | [3rd party MCP servers are disabled, despite no such policy](https://github.com/github/copilot-cli/issues/1707) | CLOSED | **MCP 策略误拦截**。升级至 0.0.418 后第三方 MCP 被组织策略禁用，回退版本即恢复，显示策略校验存在 Bug。 |
| **#2334** | [Please bring back no-alt-screen](https://github.com/github/copilot-cli/issues/2334) | CLOSED | **终端可用性争议**。alt-screen 模式导致无法滚动历史、无法使用终端查找，社区强烈呼吁恢复旧行为（28 👍）。 |
| **#2434** | [Restore support for Gemini Pro](https://github.com/github/copilot-cli/issues/2434) | CLOSED | **模型支持反复**。v1.0.14 移除 `gemini-3-pro-preview` 后，用户明确表示这是其选择 Copilot CLI 而非 Claude Code 的关键原因。 |
| **#3547** | [Background sub-agent silently hangs at total_turns=0 when model="gpt-5.5"](https://github.com/github/copilot-cli/issues/3547) | CLOSED | **Agent 稳定性**。后台子代理在 gpt-5.5 下成功派发后永久挂起，影响自动化工作流可靠性。 |
| **#3727** | [Regression in v1.0.60: userPromptSubmitted hook additionalContext no longer injected](https://github.com/github/copilot-cli/issues/3727) | OPEN | **插件生态回归**。v1.0.60（6 月 5 日发布）破坏插件钩子行为，导致依赖 `additionalContext` 的自定义插件失效。 |
| **#3749** | [Terminal streaming renderer corrupts output - characters doubled/truncated](https://github.com/github/copilot-cli/issues/3749) | OPEN | **渲染质量恶化**。流式输出阶段出现字符重复、截断与行重叠，直接影响长回复的可读性。 |

---

### 4. 重要 PR 进展

今日无更新的 Pull Requests。

---

### 5. 功能需求趋势

从 41 条更新中可提炼出四大社区焦点方向：

1. **模型生态一致性**  
   Gemini 3.1 Pro / Gemini Pro / Gemini Flash 在 CLI 与 VS Code / Web 端的可用性严重不一致，开发者要求 CLI 实时同步官方支持的完整模型矩阵。

2. **终端原生体验**  
   alt-screen 模式、剪贴板复制（Linux `ctrl+shift+c` / Windows 静默失败）、键盘快捷键（`Ctrl+Enter`）及流式渲染质量，成为跨平台用户体验的核心摩擦点。

3. **MCP 与企业治理**  
   第三方 MCP 服务器被组织策略误拦截、组织级 Token 权限缺失，反映出企业场景下的策略引擎与认证链路仍需打磨。

4. **插件与扩展性**  
   自定义 Provider（ACP 模式）、Agent Hook 稳定性及 MCP 快捷调用语法，显示高级用户正将 CLI 作为可编程平台而非单纯聊天工具。

---

### 6. 开发者关注点

- **v1.0.60 版本回归风险**：终端渲染损坏、插件钩子失效、BEL 通知移除等问题集中出现在最新版，社区建议生产环境用户谨慎升级。
- **跨平台终端兼容性**：Linux 与 Windows 的复制、粘贴及键盘快捷键近期频繁出现非预期变更，打破既有终端工作流。
- **会话与认证稳定性**：`--resume` 对含空格会话名静默失败、恢复会话后模型列表报 `Not authenticated`，表明会话状态管理存在边缘场景缺陷。
- **破坏性默认行为**：worktrees 默认启用导致代码难以合并回主工作树，开发者呼吁将此类高风险功能改为显式开启。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-06-11*

---

### 1. 今日速览

OpenCode 团队在过去 24 小时内密集发布了 **v1.17.1 → v1.17.3** 三个补丁版本，紧急修复桌面端崩溃与远程配置认证问题；社区围绕 **TUI 2.0 重构**、 **`/goal` 自主任务模式** 以及 **多模型推理控制** 展开热烈讨论，同时 xfyun 引擎繁忙重试、PDF 错误处理等稳定性 PR 进入评审阶段。

---

### 2. 版本发布

**v1.17.3** — 紧急修复 v1.17.2 桌面端崩溃问题。  
**v1.17.2** — 核心层修复远程配置认证过期后的恢复流程（提示重新登录而非直接失败），并允许子代理使用自身配置权限；桌面端恢复 Linux 启动器与图标标识，解决固定应用无法正确打开的问题。  
**v1.17.1** — References 配置支持使用描述、在文档中展示及 `@` 自动完成隐藏；兼容加载已废弃的 `reference` 配置键；修复 MCP prompt 与 resource 请求问题。

---

### 3. 社区热点 Issues（按关注度排序）

| # | 状态 | 标题 | 评论/👍 | 关键看点 |
|---|------|------|---------|----------|
| [#27167](https://github.com/anomalyco/opencode/issues/27167) | OPEN | [FEATURE] Add native session goals with `/goal` | 40 / 69 | 社区最热功能请求，希望引入类似 Claude Code 的持久化会话目标机制，让代理跨轮次自主推进任务。 |
| [#11831](https://github.com/anomalyco/opencode/issues/11831) | OPEN | YOLO Mode — Auto-Approve All Permission Prompts | 9 / 29 | 高级用户强烈呼吁减少权限中断，通过“YOLO 模式”在尊重显式 `deny` 规则的前提下自动批准所有工具请求。 |
| [#6490](https://github.com/anomalyco/opencode/issues/6490) | OPEN | Web UI 无法浏览或选择用户目录外文件夹（如 `D:\code`） | 10 / 12 | Windows 用户普遍受阻，Web UI 仅展示 Downloads 等默认目录，严重限制多盘符项目导入。 |
| [#30086](https://github.com/anomalyco/opencode/issues/30086) | OPEN | 新版本 CPU 占用过高 | 9 / 1 | 性能回归：多会话场景下 CPU 飙升，用户反馈从同时运行 10 个会话降至 3 个即出现明显卡顿。 |
| [#26762](https://github.com/anomalyco/opencode/issues/26762) | OPEN | Cerebras `zai-glm-4.7` 多轮对话 `reasoning_content` 报错 | 10 / 2 | 含推理内容与工具调用的多轮对话在第二轮助手回合失败，模型兼容性亟待修复。 |
| [#31247](https://github.com/anomalyco/opencode/issues/31247) | OPEN | GitHub Copilot / Claude Opus 4.8 工具调用文本泄漏 | 8 / 0 | 助手消息中反复泄漏 `call read`、`<invoke>` 等原始工具调用标记，污染正常输出。 |
| [#30158](https://github.com/anomalyco/opencode/issues/30158) | OPEN | Web UI 终端按钮自 v1.15.12 起神秘消失 | 7 / 6 | 回归性 Bug，升级后右上角终端入口丢失，降级至 v1.15.11 可恢复。 |
| [#24610](https://github.com/anomalyco/opencode/issues/24610) | OPEN | DeepSeek-V4 需要“禁用思考”按钮 | 4 / 5 | 推理模式默认开启导致翻译等简单任务过度思考，用户希望一键关闭以降低延迟与成本。 |
| [#31481](https://github.com/anomalyco/opencode/issues/31481) | OPEN | `.agents/` 含 Cursor 格式 agent 文件时启动崩溃 | 2 / 0 | YAML 数组格式的 `tools:` 配置引发启动请求批量失败，跨编辑器兼容性需加强。 |
| [#31791](https://github.com/anomalyco/opencode/issues/31791) | OPEN | question 工具 UI 支持图片拖拽/粘贴 | 2 / 0 | 多模态交互需求从主聊天扩展至 question/MCQ 界面，方便截图作答。 |

---

### 4. 重要 PR 进展

| # | 状态 | 标题 | 说明 |
|---|------|------|------|
| [#31796](https://github.com/anomalyco/opencode/pull/31796) | OPEN | **TUI 2.0** | 终端用户界面重大版本升级，涉及架构全面翻新。 |
| [#31826](https://github.com/anomalyco/opencode/pull/31826) | OPEN | refactor(tui): 用 DataProvider 替换 v2 sync | 将 `sync-v2` 上下文替换为面向领域的私有数据层，迁移代理、模型、连接状态等消费者至 `useData`。 |
| [#31819](https://github.com/anomalyco/opencode/pull/31819) | OPEN | fix: xfyun 引擎繁忙时自动重试 | 将“

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*