# AI CLI 工具社区动态日报 2026-06-13

> 生成时间: 2026-06-13 02:57 UTC | 覆盖工具: 7 个

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
*数据截止：2026-06-13*

---

### 1. 生态全景

当前 AI CLI 工具正经历从“智能代码补全”向“自主 Agent Orchestration”的关键跃迁。主流工具日均迭代频繁，OpenAI Codex 与 Qwen Code 单日活跃 PR 均达 10 条级别，Claude Code 连续推送 3 个版本紧急修复模型访问管控。社区焦点已从基础功能可用性转向跨平台远程执行、长会话状态持久化及企业级成本管控，同时 Windows 平台稳定性与终端渲染质量成为共性技术债务。

---

### 2. 各工具活跃度对比

| 工具 | 24h

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-13*

---

### 1. 热门 Skills 排行（按社区关注度）

| 排名 | Skill | 功能简述 | 社区讨论热点 | 状态 |
|---|---|---|---|---|
| 1 | **Automation Workflows Builder / Frontend Design / AI Experience Consultant** | 一次性提交三大技能，覆盖前端设计、AI 体验咨询与自动化工作流编排 | 低代码/无代码自动化需求激增，被视为连接业务与开发的关键桥梁 | Open | [PR #1046](https://github.com/anthropics/skills/pull/1046) |
| 2 | **Document Typography** | AI 生成文档的排版质量控制，修复孤字换行、寡段标题、编号错位等通病 |

---

**Claude Code 社区动态日报**  
*2026-06-13*

---

### 1. 今日速览

今日社区被 `claude-fable-5` 模型访问异常“刷屏”，大量开发者在会话中途遭遇模型不可用或内容策略误拦截，成为 Issue 区绝对焦点。产品侧连续推送 v2.1.175–v2.1.177 三个版本，重点强化模型访问管控、多语言会话标题及 Bedrock 集成。长期来看，社区对自主 Agent 架构、子代理能力增强及企业级计费层级的需求仍在持续升温。

---

### 2. 版本发布

过去 24 小时连续发布 3 个版本：

- **v2.1.177**：常规维护版本，官方未提供详细变更日志。  
- **v2.1.176**：会话标题现支持按对话语言自动生成（可通过 `language` 设置固定语言）；新增 `footerLinksRegexes` 设置，支持通过正则匹配在页脚展示链接徽章；改进 Bedrock 凭证管理。  
- **v2.1.175**：新增 `enforceAvailableModels` 托管设置，启用后 `availableModels` 白名单将同时约束 Default 模型（若默认模型不在允许列表，则自动回退至首个允许模型），且用户/项目级设置无法再扩大管理员配置的模型范围。

---

### 3. 社区热点 Issues（按关注度精选 10 条）

| # | 标题 | 评论/👍 | 核心看点 |
|---|------|---------|----------|
| [#56913](https://github.com/anthropics/claude-code/issues/56913) | Make autonomous Claude Code actually viable: tiered Opus brains + Sonnet workers + persistent state | 26 / 0 | 社区对“真正自主 Agent”的架构提案，呼吁分层智能体与持久化状态，代表长期演进方向。 |
| [#49917](https://github.com/anthropics/claude-code/issues/49917) | [BUG] Claude Desktop Windows installer fails with AddPackage HRESULT 0x80073CF6 | 26 / 6 | Windows 平台顽固安装故障，早期“成功”安装留下的不一致状态导致后续重装失败。 |
| [#38183](https://github.com/anthropics/claude-code/issues/38183) | [BUG] SendMessage tool referenced but not available — agent continuation broken | 19 / 21 | **高赞严重缺陷**：`resume` 参数移除后 `SendMessage` 工具缺失，导致 Agent 工作流续接断裂。 |
| [#16294](https://github.com/anthropics/claude-code/issues/16294) | [BUG] API Error 400 "no low surrogate in string" when Bash output contains invalid Unicode | 16 / 1 | Bash 输出包含非法 Unicode 时触发 API 400 错误，底层编码处理缺陷。 |
| [#68129](https://github.com/anthropics/claude-code/issues/68129) | [BUG] Fable is not available | 15 / 1 | **今日新发**：大量用户集中反馈 `claude-fable-5` 完全不可用。 |
| [#14321](https://github.com/anthropics/claude-code/issues/14321) | [FEATURE] enable extended thinking for subagents | 9 / 25 | **高赞功能请求**：要求为子代理开放 Extended Thinking，当前受限严重影响复杂任务分解。 |
| [#47509](https://github.com/anthropics/claude-code/issues/47509) | feat: Team plan needs a Max 20x equivalent tier for power users | 8 / 37 | **高赞商业诉求**：Team 计划最高仅 6.25x，重度用户呼吁推出对标个人 Max 20x 的企业层级。 |
| [#68126](https://github.com/anthropics/claude-code/issues/68126) | [Bug] Anthropic API Error: Invalid or Inaccessible Model Configuration | 8 / 0 | **今日新发**：会话进行中突然报错 `claude-fable-5[1m]` 模型配置无效或不可访问。 |
| [#50911](https://github.com/anthropics/claude-code/issues/50911) | CronCreate durable:true silently dropped — returns "Session-only" | 7 / 1 | `durable: true` 被静默忽略，定时任务随会话结束而丢失，影响自动化可靠性。 |
| [#67688](https://github.com/anthropics/claude-code/issues/67688) | [BUG] [SUGGESTION] Fable classifier broken completely | 6 / 1 | Fable 模型分类器完全失效，导致请求无法正确路由到新模型。 |

---

### 4. 重要 PR 进展

过去 24 小时内仓库仅更新 **1 条** Pull Request：

- **[#26360](https://github.com/anthropics/claude-code/pull/26360)** `[已关闭]` **Fix issues being auto-closed despite human activity**  
  修复 Issue 在存在人类活跃评论的情况下仍被自动关闭的问题。核心改动：1) Triage 工作流现在识别并移除 `stale`/`autoclose` 标签；2) 优化 `closeExpired()` 逻辑，避免误杀有人类参与的议题。

---

### 5. 功能需求趋势

从今日 Issues 中可提炼出四大社区关注方向：

1. **自主 Agent 与持久化架构**  
   社区不再满足于“结对编程”，而是希望 Claude Code 成为可长期运行的编排大脑（#56913）。关键子需求包括：分层智能体（Opus 决策 + Sonnet 执行）、跨会话持久状态、无界定时任务（#50911）以及防止子代理无限制递归（#68110）。

2. **Fable 模型生态成熟化**  
   `claude-fable-5` 的上线伴随大量稳定性问题：模型访问权限突然丢失、分类器路由故障、内容策略误判（Ansible/Playwright 等正常开发行为被拦截）。社区急需该模型在可用性、路由准确性和策略宽容度上达到生产标准。

3. **企业级管控与计费**  
   管理员侧需要更严格的模型白名单（v2.1.175 的 `enforceAvailableModels` 是回应），而重度团队需要更高配额层级（#47509 呼吁 Max 20x 团队版）。

4. **子代理工具链完善**  
   包括为子代理开放 Extended Thinking（#14321）、修复 SendMessage 工具缺失导致的续接断裂（#38183），以及 Advisor 工具在长上下文（~100K tokens）下的可用性（#67609）。

---

### 6. 开发者关注点

- **Fable 访问中断与内容误报**：今日最高频痛点。开发者在会话中途、甚至毫无变更的情况下失去 `claude-fable-5` 访问权；部分正常技术任务（如编写 Ansible 脚本、Playwright 本地登录测试）被内容策略误判并强制降级到 Opus，导致工作流中断。
- **Agent 系统可靠性**：`SendMessage` 工具移除后的续接断裂（#38183）已持续数月；子代理递归调用缺乏深度/数量限制，造成 Token 指数级燃烧（#68110）；Advisor 工具在长会话中失效（#67609）。
- **平台兼容性债务**：Windows 安装包残留状态导致无法重装（#49917）、TUI 中 `Ctrl-V` 粘贴失效（#68136）等问题持续影响非 macOS 开发者体验。
- **状态与成本可控性**：`CronCreate` 的 `durable` 标志被静默忽略（#50911），会话级任务无法持久化；同时 Team 计划配额天花板过低，迫使重度用户购买个人 Max 计划（#47509）。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-06-13*

---

### 1. 今日速览
今日社区焦点集中在 **Windows 平台稳定性危机**（多起沙盒启动失败与应用崩溃）与 **跨 OS 执行架构的大规模重构** 上。开发团队密集推送了 `v0.140.0-alpha` 系列 CLI 更新，并在 PR 端集中落地 `unified-exec` 与 `PathUri` 跨平台路径系统。与此同时，macOS 系统级资源耗尽与 Dock 崩溃问题也引发高度关注。

---

### 2. 版本发布
**CLI Rust 组件连续迭代：`v0.140.0-alpha.14` → `alpha.17`**  
过去 24 小时内，OpenAI 连续发布了 4 个 CLI 的 Alpha 版本（`alpha.14` 至 `alpha.17`），均为 `rust-v0.140.0` 预发布线。官方未提供详细 ChangeLog，推测为内部跨平台执行引擎与路径解析模块的渐进式更新。建议生产环境用户保持观察，等待正式版发布。

---

### 3. 社区热点 Issues（精选 10 条）

| # | 状态 | 标题 | 核心看点 |
|---|------|------|----------|
| [#12564](https://github.com/openai/codex/issues/12564) | ✅ CLOSED | 允许重命名任务/线程标题以改善历史导航 | **高票需求（111👍）**，用户长期呼吁的 UX 改进终于关闭，可大幅提升多线程项目管理效率。 |
| [#25243](https://github.com/openai/codex/issues/25243) | 🔴 OPEN | macOS Codex 重启循环耗尽 `syspolicyd` 文件描述符 | **系统级严重 Bug**。应用反复自启导致 macOS 安全守护进程资源枯竭，影响整机应用启动，Pro 用户反馈。 |
| [#9046](https://github.com/openai/codex/issues/9046) | 🔴 OPEN | 模型上下文窗口溢出：Codex ran out of room | **核心体验痛点**。仅开启新对话即触发上下文上限，25 条讨论仍未解决，严重影响长任务连续性。 |
| [#27175](https://github.com/openai/codex/issues/27175) | 🔴 OPEN | Windows 桌面版 `26.602.71036` 更新后崩溃/无法访问 | **高优先级稳定性问题**。空会话状态下仍崩溃，影响 ChatGPT Pro 付费用户，疑似与最新构建兼容性有关。 |
| [#25220](https://github.com/openai/codex/issues/25220) | 🔴 OPEN | Windows 捆绑插件不可用（Computer Use、Browser 等） | **Windows 生态兼容性**。因 EFS 加密与 `copyfile` 失败导致核心插件集体失效，中国区 Windows 11 用户复现率高。 |
| [#27817](https://github.com/openai/codex/issues/27817) | 🔴 OPEN | 网络安全策略误报：正常财务税务工作被标记 | **安全策略过度敏感**。授权的个人财务场景被误判为网络安全风险，暴露出现有安全分类器的业务场景覆盖不足。 |
| [#24098](https://github.com/openai/codex/issues/24098) | ✅ CLOSED | Windows 提升沙盒失败：`spawn setup refresh` | **已修复的 Windows 沙盒回归**。CLI 更新后高权限沙盒失效，回退或修复方案已确认，为近期同类问题提供参考。 |
| [#22335](https://github.com/openai/codex/issues/22335) | 🔴 OPEN | CLI 远程压缩反复失败，恢复后任务连续性丢失 | **数据/会话管理缺陷**。`remote compaction` 失败导致线程历史断裂，影响 Pro 用户在高推理级别下的长会话恢复。 |
| [#27979](https://github.com/openai/codex/issues/27979) | 🔴 OPEN | Windows Codex App `26.609.4994.0` 更新后无法打开 | **严重可用性故障**。应用直接无法启动，About 对话框均不可见，阻碍用户正常进入工作流。 |
| [#27694](https://github.com/openai/codex/issues/27694) | 🔴 OPEN | macOS Dock 外部显示器崩溃：`setDockTile` 递归 | **macOS 桌面稳定性**。`CodexDockTilePlugin` 无限递归导致 Dock 崩溃，影响外接显示器场景，Apple Silicon 用户反馈。 |

---

### 4. 重要 PR 进展（精选 10 条）

| # | 状态 | 标题 | 功能/修复摘要 |
|---|------|------|---------------|
| [#28014](https://github.com/openai/codex/pull/28014) | 🟡 OPEN | `unified-exec`: 无主机沙盒启动远程命令 | **跨 OS 执行架构核心**。允许 app-server 直接向 exec-server 发送命令，跳过本地沙盒构造，为 Linux 控制 Windows 执行器铺路。 |
| [#27819](https://github.com/openai/codex/pull/27819) | 🟡 OPEN | `path-uri`: 跨平台渲染原生路径 | **基础协议层改造**。在 `PathUri` 迁移过程中，确保 API 边界向用户展示原生路径而非 URI 编码，支撑跨 OS 远程执行。 |
| [#28012](https://github.com/openai/codex/pull/28012) | 🟡 OPEN | 添加 fail-closed 插件脚本解析器 | **安全加固**。引入插件脚本命令的预解析与可信路径规范化，采用“默认拒绝”策略，为后续插件生命周期管理提供前置校验。 |
| [#27971](https://github.com/openai/codex/pull/27971) | 🟡 OPEN | 跨进程协调云配置包缓存 | **性能优化**。解决多进程共享 `CODEX_HOME` 时的缓存惊群问题，通过所有权协调避免并发 CLI 与 app-server 重复拉取云端配置。 |
| [#27459](https://github.com/openai/codex/pull/27459) | ✅ CLOSED | 按认证路由门控插件 MCP 服务器 | **插件权限治理**。将认证感知能力下沉至 `PluginsManager`，统一管控插件暴露的 App 与 MCP 表面，已合入主线。 |
| [#28008](https://github.com/openai/codex/pull/28008) | 🟡 OPEN | 添加外部代理导入结果统计 | **生态集成**。为外部 Agent 配置导入引入 `importId` 与完成通知契约，支持按迁移项分组报告导入结果，便于 IDE 侧追踪。 |
| [#27937](https://github.com/openai/codex/pull/27937) | 🟡 OPEN | 添加 hermetic Wine exec-server 测试 | **跨 OS 测试基础设施**。在 Wine 环境中运行 Windows exec-server 测试，确保 Linux 宿主对 Windows 执行器的远程控制行为可验证、可复现。 |
| [#28002](https://github.com/openai/codex/pull/28002) | 🟡 OPEN | 通过 compact 请求发送 turn state | **协议一致性**。将内联压缩请求纳入当前逻辑 turn 的状态生命周期，确保压缩与采样请求共享同一 session 状态。 |
| [#27713](https://github.com/openai/codex/pull/27713) | 🟡 OPEN | 原型：多提供商工作负载身份认证 | **企业级身份体系**。替代原有的 Azure-only 原型，支持跨云工作负载身份认证，**标记为 do-not-merge**，处于早期评审阶段。 |
| [#28006](https://github.com/openai/codex/pull/28006) | 🟡 OPEN | `core`: 保留执行器环境标识 | **跨 OS 状态保持**。在 turn context 与 rollouts 中固化执行器的 cwd、路径约定与 shell 信息，避免将远程路径错误映射到 app-server 本地。 |

---

### 5. 功能需求趋势
从今日 Issues 与近期讨论中，可提炼出社区最关注的五大方向：

1. **Windows 平台稳定性与沙盒可靠性**  
   `spawn setup refresh`、`CreateProcessAsUserW failed`、`os error 740` 等错误高频出现，涉及 UAC、EFS 加密、权限提升与路径解析，已成为最大痛点集群。
2. **跨平台/跨 OS 执行与路径统一**  
   WSL、非标准驱动器安装、远程 exec-server 等场景推动社区强烈要求原生路径与 URI 的透明转换，以及 Linux ↔ Windows 的无缝控制。
3. **上下文与会话连续性管理**  
   上下文窗口溢出、远程压缩失败、聊天历史丢失、旧线程 cwd 失效等问题表明，长会话的状态持久化与恢复机制仍需加强。
4. **Computer Use / Browser 插件在 Windows 上的可用性**  
   捆绑插件（Chrome、LaTeX、Browser）因沙盒或文件系统问题集体失效，直接影响 Agent 能力的落地。
5. **安全策略的精准度与业务场景适配**  
   正常的财务、税务、授权安全研究被误标为“网络安全风险”，社区呼吁更细粒度的安全分类与申诉机制。

---

### 6. 开发者关注点
- **Windows 沙盒启动失败已成“流行病”**：从 Desktop 到 CLI，从 `node_repl` 到 `Computer Use`，`windows sandbox failed: spawn setup refresh` 及其变体（error 740、error 5）是今日最高频的报错，开发者急需官方提供统一的诊断工具或回退机制。
- **数据丢失焦虑上升**：多起 Issue 涉及聊天记录全失、设置无法保存、线程历史断裂，用户对 Codex 作为生产工具的可靠性产生疑虑。
- **macOS 系统级副作用**：除功能 Bug 外，`syspolicyd` 文件描述符耗尽与 Dock 递归崩溃表明 Codex 正深入影响操作系统底层资源，需更严格的资源隔离测试。
- **跨 OS 架构落地在即**：今日 PR 密集出现 `PathUri`、`unified-exec`、`NativePathString` 等关键词，预示 Codex 即将支持真正的异构 OS 远程执行，开发者应提前关注路径与 shell 约定的兼容性改造。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报**  
*2026-06-13*

---

### 1. 今日速览
今日社区发布 `v0.48.0-nightly.20260613` 版本，重点修复 MCP 工具发现的原子更新与 Vertex AI 模型映射问题。Issues 侧持续聚焦 Agent 稳定性，多个 P1 级挂起与状态误报问题获得新进展；PR 侧则集中交付了终端兼容性、认证流程与工具响应截断等关键修复。

---

### 2. 版本发布
**v0.48.0-nightly.20260613.g9e5599c32**  
- **核心修复**：实现 MCP 工具发现的原子更新，避免并发场景下工具列表不一致。  
- **模型映射**：修复 Vertex AI 的模型映射逻辑。  
- **体验优化**：新增文档与迁移命令，提升版本升级体验。  
[查看 Release](https://github.com/google-gemini/gemini-cli/releases)

---

### 3. 社区热点 Issues

| # | 标题 | 重要性 | 社区反应 |
|---|------|--------|----------|
| **#24353** | [Robust component level evalutions](https://github.com/google-gemini/gemini-cli/issues/24353) | P1 / Agent | 7 条讨论。作为行为评测的后续 EPIC，关系到 76 个已有评测用例的组件级细化，是质量基础设施的核心工作。 |
| **#22745** | [Assess the impact of AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745) | P2 / Agent | 7 条讨论。探索基于 AST 的精准代码导航，可显著减少文件读取轮次与 Token 噪音，长期架构价值高。 |
| **#21409** | [Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409) | P1 / Bug | 7 评论，8 👍。通用 Agent 在简单任务（如创建文件夹）上无限挂起，用户被迫禁用子 Agent，影响基础可用性。 |
| **#22323** | [Subagent recovery after MAX_TURNS is reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323) | P1 / Bug | 6 评论。子 Agent 达到最大轮次后仍返回 `status: "success"`，导致中断被隐藏，严重误导用户。 |
| **#21968** | [Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968) | P2 / Feature | 6 评论。用户反馈模型几乎不会主动调用自定义 Skill 和子 Agent，需显式指令才生效，智能调度能力不足。 |
| **#27538** | [ERROR ioctl(2) failed, EBADF](https://github.com/google-gemini/gemini-cli/issues/27538) | P2 / Core | 5 评论，已关闭。终端伪终端文件描述符异常，导致在特定 Node.js 环境下崩溃，属于底层稳定性问题。 |
| **#26525** | [Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525) | P2 / Security | 5 评论。Auto Memory 在日志与模型上下文中存在敏感信息泄露风险，社区呼吁确定性脱敏而非依赖模型自律。 |
| **#26522** | [Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522) | P2 / Bug | 5 评论。低价值会话被无限重试，造成资源浪费与索引污染。 |
| **#25166** | [Shell command execution gets stuck with "Waiting input"](https://github.com/google-gemini/gemini-cli/issues/25166) | P1 / Core | 4 评论，3 👍。简单 Shell 命令执行后仍显示“等待输入”，是高频遇到的终端交互阻塞问题。 |
| **#21983** | [browser subagent fails in wayland](https://github.com/google-gemini/gemini-cli/issues/21983) | P1 / Bug | 4 评论。浏览器子 Agent 在 Wayland 会话下直接失败，限制 Linux 桌面用户的使用场景。 |

---

### 4. 重要 PR 进展

| # | 标题 | 说明 |
|---|------|------|
| **#27875** | [chore/release: bump version to 0.48.0-nightly.20260613.g9e5599c32](https://github.com/google-gemini/gemini-cli/pull/27875) | 自动化版本提升，对应今日 Nightly 发布。 |
| **#27870** | [fix(core): cap pending tool responses](https://github.com/google-gemini/gemini-cli/pull/27870) | 为待处理的工具响应设置上限，防止超大结果导致上下文爆炸与 Agent 异常。 |
| **#27867** | [fix(a2a-server): prevent crash when tasks metadata endpoint returns 501](https://github.com/google-gemini/gemini-cli/pull/27867) | 修复 A2A 服务端点在返回 501 时的崩溃问题，提升服务端鲁棒性。 |
| **#27708** | [fix(ci): harden AI prompt around untrusted data](https://github.com/google-gemini/gemini-cli/pull/27708) | 强化 CI 工作流，避免将不可信数据直接注入 AI Prompt，通过中间文件隔离。 |
| **#27694** | [fix: dedupe home agent directories](https://github.com/google-gemini/gemini-cli/pull/27694) | 去重项目级与用户级 Agent 目录，解决主目录工作区下重复加载的问题。 |
| **#27854** | [Fix/pending tools and trust overrides](https://github.com/google-gemini/gemini-cli/pull/27854) | 防止 Agent 在等待用户批准工具时过早推进状态，并强制文件写入顺序执行以消除竞态。 |
| **#27873** | [fix(core): improve SKILL.md frontmatter parsing robustness](https://github.com/google-gemini/gemini-cli/pull/27873) | 增强 SKILL.md 前置元数据解析：支持 UTF-8 BOM、忽略尾部空白、规范化非字符串 YAML 值。 |
| **#27872** | [fix(core): strip line/range suffix from at-command paths](https://github.com/google-gemini/gemini-cli/pull/27872) | 去除 `@` 命令路径中的行号后缀（如 `:12`），避免文件系统操作挂起或崩溃。 |
| **#27871** | [fix(core): merge existing refresh token when caching credentials](https://github.com/google-gemini/gemini-cli/pull/27871) | 缓存凭证时合并已有 refresh token，修复重复授权后令牌丢失问题。 |
| **#27467** | [fix(core): handle multi-line escaped quotes in stripShellWrapper](https://github.com/google-gemini/gemini-cli/pull/27467) | 使用 `shell-quote` 正确解析包含转义引号的多行命令，解决 `stripShellWrapper` 提取失败。 |

---

### 5. 功能需求趋势

从过去 24 小时活跃 Issue 中，可提炼出以下四大社区关注方向：

1. **Agent 可靠性与状态透明**  
   子 Agent 挂起、MAX_TURNS 后误报成功、以及 Skill/子 Agent 调度不积极等问题占据 P1/P2 主流，表明社区核心诉求已从“功能可用”转向“行为可预测”。

2. **AST-aware 代码理解**  
   多个 EPIC 级 Issue 探讨基于 AST 的文件读取与代码库映射，目标是减少多轮文件读取、降低 Token 消耗，并提升大规模代码库下的定位精度。

3. **安全与隐私治理**  
   Auto Memory 的日志脱敏、确定性 redaction、以及无效记忆补丁的隔离成为安全领域焦点，用户希望敏感数据处理从“模型自律”变为“工程强制”。

4. **终端与 IDE 生态兼容**  
   Wayland、tmux、Termux、Theia IDE、终端 resize 性能等议题显示，开发者正在将 Gemini CLI 集成到多样化的复杂开发环境中，对底层终端适配提出更高要求。

---

### 6. 开发者关注点

- **Agent 死锁与挂起**：Generalist Agent 在简单任务上无限等待、Shell 命令结束后仍显示“等待输入”是最高频痛点，直接影响日常开发流。
- **子 Agent 行为不透明**：达到轮次上限却返回成功、忽略 `settings.json` 配置、以及不主动使用已配置 Skill，导致用户对自动化决策缺乏信任。
- **终端环境兼容性**：从 `ioctl EBADF`、tmux 背景色误判到 Termux 的 `linker64` 崩溃，表明在 Node.js 伪终端与各类终端模拟器之间的适配仍需大量打磨。
- **认证与配置回归**：Gateway 认证方式在设置 `GOOGLE_GEMINI_BASE_URL` 时被拒绝、凭证缓存丢失 refresh token，说明配置链路在新增特性后存在回归风险。
- **工具调用边界**：超过 128 个工具时触发 400 错误、ripgrep 执行失败后的降级策略、以及 MCP 工具发现的原子性，反映出工具生态扩展带来的工程挑战。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*2026-06-13*

---

### 1. 今日速览
今日 Copilot CLI 发布 **v1.0.62-1**，带来 YOLO 模式指示器、会话级扩展及 GitHub 服务端搜索等更新，但社区反馈显示**终端流式渲染质量**已成为最突出的痛点，多个 Issue 集中报告字符重复、截断及推理文本乱码问题。同时，关于恢复旧版 CLI 工作流（#53）和自定义 Slash 命令（#618）的长期呼声依然保持高热。

---

### 2. 版本发布
**v1.0.62-1** 已发布，主要更新包括：

- **YOLO 模式可视化**：在底部状态栏显示 "allow all" 指示器，并支持通过自定义 `statusLine.command` 读取该授权状态。
- **GitHub 搜索增强**：在 Issues 或 Pull Requests 标签页按下 `/` 键，可直接调用 GitHub 服务端过滤搜索。
- **会话级扩展与画布**：新增对 session-scoped extensions 和 canvases 的支持。
- **SDK 内存配置**：允许 SDK 客户端配置会话内存阈值（session memory threshold）。

---

### 3. 社区热点 Issues（过去 24 小时）

| Issue | 状态 | 评论/反应 | 核心看点 |
|-------|------|-----------|----------|
| [#53](https://github.com/github/copilot-cli/issues/53) Bring back the GitHub Copilot in the CLI commands | OPEN | 37 评论 / 75 👍 | **社区最高声量需求**。官方移除旧 CLI 命令后严重破坏工作流，用户已自发维护 `shell-ai` 等替代方案，但半年未获官方回应。 |
| [#618](https://github.com/github/copilot-cli/issues/618) Support custom slash commands from `.github/prompts` | CLOSED | 31 评论 / 99 👍 | 用户呼吁与 VS Code 扩展对齐，支持从仓库级 prompts 目录加载自定义 Slash 命令，现已关闭或已解决。 |
| [#1481](https://github.com/github/copilot-cli/issues/1481) SHIFT + ENTER should spawn a line break | CLOSED | 26 评论 / 15 👍 | 交互体验修复。将 `SHIFT+ENTER` 统一为换行（而非执行），与主流聊天应用习惯保持一致。 |
| [#3749](https://github.com/github/copilot-cli/issues/3749) Terminal streaming renderer corrupts output | OPEN | 5 评论 / 7 👍 | **渲染严重缺陷**。流式输出时出现字符翻倍、截断及重复行，影响 thinking 与最终回复的展示。 |
| [#3755](https://github.com/github/copilot-cli/issues/3755) Reasoning/thinking display garbles streamed text | OPEN | 5 评论 / 2 👍 | 开启 `showReasoning` 后，推理文本出现大量重叠碎片（如 "fromply from"），与 #3749 同属终端渲染危机。 |
| [#2627](https://github.com/github/copilot-cli/issues/2627) Configurable system prompt to reduce token overhead | OPEN | 2 评论 / 17 👍 | 系统提示词固定消耗约 20.5K tokens，用户希望自定义以节省上下文窗口，尤其在长会话中至关重要。 |
| [#1999](https://github.com/github/copilot-cli/issues/1999) Cannot enter `@` on German keyboard (Alt-Gr + q) | OPEN | 9 评论 / 1 👍 | 德语键盘布局下 `AltGr` 组合键失效，导致无法输入 `@` 等关键符号，直接阻断 CLI 使用。 |
| [#2306](https://github.com/github/copilot-cli/issues/2306) Enterprise policy authorization error | OPEN | 6 评论 / 3 👍 | 企业用户每周间歇性触发 "not authorized" 错误，持续影响生产环境稳定性。 |
| [#3784](https://github.com/github/copilot-cli/issues/3784) Tokio reactor panic on Linux ARM64 (v1.0.62-1) | OPEN | 1 评论 | **新版本严重崩溃**。在 Linux ARM64 上发送首条消息后进程以 code 134 中止，阻塞该平台用户升级。 |
| [#3048](https://github.com/github/copilot-cli/issues/3048) Support custom providers via ACP | CLOSED | 5 评论 / 4 👍 | 请求 ACP 模式尊重 `COPILOT_PROVIDER_*` 环境变量，以支持 OpenRouter 等第三方模型端点。 |

---

### 4. 重要 PR 进展

过去 24 小时内，仓库仅更新 **1 条 Pull Request**，且无功能性代码合并：

- [#3771](https://github.com/github/copilot-cli/pull/3771) **Initial project setup** (OPEN) — 作者 `@limenpchuolto112-creator`，内容为空白初始化提交，疑似测试或误提 PR，目前无实质代码审查活动。

> **小结**：今日 PR 侧极为冷清，社区焦点完全集中在 Issue 反馈与版本稳定性讨论上。

---

### 5. 功能需求趋势

从过去 24 小时的 33 条活跃 Issue 中，可提炼出以下五大社区关注方向：

1. **终端渲染与流式输出稳定性**  
   字符重复、截断、乱码及推理文本重叠成为最密集的 Bug 集群，直接影响核心交互体验。
2. **键盘输入与国际化（i18n）**  
   德语、波兰语等依赖 `AltGr` 的键盘布局在 Windows 与 Linux 下均存在输入失效问题。
3. **企业合规与策略管控**  
   第三方 MCP 服务器被组织策略拦截、授权状态波动、以及本地/远程配置冲突（如 `/chronicle reindex`）是企业用户的主要阻碍。
4. **上下文与内存管理**  
   可配置系统提示词、自动压缩（compaction）逻辑优化、以及通过 `.copilot/goals.md` 实现跨会话长期目标，反映用户对长会话成本控制的需求。
5. **模型生态与可观测性**  
   自定义 Provider（ACP）、多模态图片粘贴、模型兼容性（如 Opus 4.5），以及通过 OpenTelemetry 暴露成本/计费指标。

---

### 6. 开发者关注点

- **终端可靠性危机**：流式输出渲染是今日最大痛点，多个独立 Issue 指向同一类底层问题，建议开发者暂缓升级至 v1.0.62-1 若依赖 Linux ARM64 或高频使用 reasoning 模式。
- **非英语键盘支持不足**：`AltGr` 组合键失效并非个案，德语、波兰语用户均报告无法输入关键符号，CLI 的跨平台输入层亟需修复。
- **企业环境稳定性**：授权策略间歇性报错与 MCP 服务器被组织策略禁用，导致企业用户无法构建可靠的自动化工作流。
- **成本与 Token 开销**：固定系统提示词 + 工具定义消耗近 30K tokens，开发者强烈希望获得“瘦身”配置与 OpenTelemetry 成本指标，以实现可观测的预算管理。
- **版本回归风险**：v1.0.62-1 在 Linux ARM64 出现 Tokio reactor panic，提示新版本在特定平台的 QA 覆盖存在缺口。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI 社区动态日报 | 2026-06-13

## 1. 今日速览

过去 24 小时社区无新版本发布，但 3 个高活跃 Issue 持续暴露工具在**任务执行稳定性**、**用量计费透明度**及**Web 组件可靠性**方面的痛点；同时有一个针对 Python 3.13 兼容性的关键修复 PR 等待合并。

---

## 2. 版本发布

**今日无新版本发布。**

---

## 3. 社区热点 Issues

> 过去 24 小时内仓库共有 **3 条** Issue 发生更新，以下按社区关注度（👍 + 评论数）全部列出：

### #1994 kimiCode 用量计算有问题
- **链接**: https://github.com/MoonshotAI/kimi-cli/issues/1994
- **状态**: Open | 👍 7 | 💬 6
- **核心问题**: 用户反馈 K2.6 模型思维链过长，导致 2 小时订阅额度仅够执行约 2 个任务；实际 Token 消耗与官方宣传的“按 API 请求次数估算”存在明显落差。
- **社区反应**: 该 Issue 获得较高赞同，反映出开发者对**长推理模型成本可控性**的普遍焦虑，计费模型透明度成为近期争议焦点。

### #640 [bug] Kimi CLI stuck in reading one file again and again and stuck in a loop
- **链接**: https://github.com/MoonshotAI/kimi-cli/issues/640
- **状态**: Open | 👍 1 | 💬 8
- **核心问题**: 在 Linux + 自定义 Anthropic Endpoint（`mimo-v2-flash`）环境下，CLI 陷入重复读取同一文件的死循环，无法继续任务。
- **社区反应**: 8 条评论显示用户正在尝试复现和定位，问题与**第三方模型适配**及**Agent 循环控制逻辑**相关，影响实际工作流。

### #2435 [Bug] Kimi Work tab: "Daimon control WS not ready" + infinite reload at 99%
- **链接**: https://github.com/MoonshotAI/kimi-cli/issues/2435
- **状态**: Open | 👍 0 | 💬 1
- **核心问题**: Windows 平台下 `kimi web` 的 Work 标签页因 WebSocket 守护进程初始化失败，导致页面在 99% 进度无限重载，功能完全不可用。
- **社区反应**: 刚创建不久即被顶起，说明**跨平台 Web UI 稳定性**仍是 Windows 用户的阻塞性问题。

---

## 4. 重要 PR 进展

> 过去 24 小时内仓库共有 **1 条** PR 发生更新：

### #1597 fix: guard trafilatura import to prevent cascading tool load failure on Python 3.13
- **链接**: https://github.com/MoonshotAI/kimi-cli/pull/1597
- **状态**: Open
- **内容摘要**: Python 3.13 下 `charset-normalizer` 的 mypyc 编译二进制文件与解释器不兼容，导致 `trafilatura` 导入失败，并级联引发整个 `web` 工具集加载崩溃。该 PR 通过增加防御性导入（guard import）阻断级联失败，恢复工具链在最新 Python 版本上的可用性。
- **意义**: 属于**底层兼容性修复**，对使用 Python 3.13 的开发者至关重要，可避免整个 CLI 工具生态因单一依赖损坏而瘫痪。

---

## 5. 功能需求趋势

基于近期社区反馈，开发者最关注的方向集中在：

1. **用量计费与成本可视化**  
   长思维链模型（如 K2.6）的 Token 消耗速度远超预期，社区迫切需要更细粒度的用量预估、思维链长度控制或独立的计费策略。

2. **Agent 执行可靠性**  
   文件循环读取、任务死循环等问题表明，开发者对 Agent 的**循环检测**与**任务边界控制**有强需求，期望工具具备更强的自我纠错能力。

3. **跨平台与 Web 功能稳定性**  
   Windows 环境下 WebSocket 与守护进程的兼容性问题频发，说明 `kimi web` 的跨平台交付质量仍需加强。

4. **第三方模型/端点适配**  
   使用自定义 Anthropic Endpoint 或其他非官方模型时，易出现异常行为，社区希望获得更完善的第三方接入文档与兼容性保障。

---

## 6. 开发者关注点

- **痛点一：订阅成本与产出不成正比**  
  开发者普遍接受按 Token 计费，但认为当前宣传文案中的“300-1200 次 API 请求”与实际长推理场景严重不符，要求官方明确长思维链模型的成本换算方式。

- **痛点二：任务卡死与调试困难**  
  Agent 陷入循环后缺乏有效的中断或诊断机制，开发者只能手动重启会话，严重影响编码流（Flow）体验。

- **痛点三：Python 新版本兼容滞后**  
  Python 3.13 已发布一段时间，但底层依赖（如 `trafilatura`、`charset-normalizer`）的编译二进制兼容性仍未完全解决，升级环境存在风险。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-06-13*

---

### 1. 今日速览

Qwen Code **v0.18.0 正式发布**，但社区最激烈的讨论集中在 **OAuth 免费额度政策大幅收缩**（#3203，127 条评论）。与此同时，开发者集中报告了多个 **P1 级工具执行与取消相关的稳定性 Bug**，核心团队则在密集推进 **Daemon 模式（Web Shell、Transport 抽象、背压控制）** 的成熟度与 CLI 交互体验优化。

---

### 2. 版本发布

**[v0.18.0](https://github.com/QwenLM/qwen-code/releases/tag/v0.18.0)** 已发布。  
根据近期合并记录，该版本至少包含一项 CLI 体验修复：**复制输出时自动跳过模型的 thought 推理片段**（`fix(cli): skip thought parts in copy output`），减少用户粘贴时的噪音。详细 Release Notes 待官方补充。

---

### 3. 社区热点 Issues（按关注度排序）

| # | 标题 | 核心看点 |
|---|------|----------|
| [#3203](https://github.com/QwenLM/qwen-code/issues/3203) | **Qwen OAuth Free Tier Policy Adjustment** | **社区最火议题（127 评论）**。官方计划将免费额度从 1,000 请求/天骤降至 **100 请求/天**，并将在 2026-08-20 彻底关闭免费入口。开发者普遍关注迁移成本与替代方案。 |
| [#4514](https://github.com/QwenLM/qwen-code/issues/4514) | **tracking(serve): daemon capability gaps** | **15 评论**。系统性梳理 `qwen serve` HTTP/SSE 接口在远程调用、ACP 兼容、非交互场景下的真实能力缺口，是 Daemon 模式的路线图级议题。 |
| [#4488](https://github.com/QwenLM/qwen-code/issues/4488) | **VSCode 插件左侧栏不显示** | **7 评论**。VSCode 1.120.0 新版中插件图标“闪一下即消失”，影响大量 IDE 用户，需紧急适配。 |
| [#4821](https://github.com/QwenLM/qwen-code/issues/4821) | **支持通过 frontmatter 声明式定义 Agent** | **6 评论**。对标 Claude Code 2.1.167，希望用 Markdown + YAML 替代 TypeScript 硬编码，降低自定义 Agent 门槛。 |
| [#4554](https://github.com/QwenLM/qwen-code/issues/4554) | **feat(telemetry): OpenTelemetry 端到端覆盖** | **6 评论，已关闭**。Daemon 模式的 OpenTelemetry 链路追踪已实现，并在 `main` 分支完成本地 OTLP 冒烟验证。 |
| [#4877](https://github.com/QwenLM/qwen-code/issues/4877) | **OpenWork 无法区分不同提供商的同名模型** | **4 评论**。`modelProviders` 中相同模型 ID（如 `glm-5`）在不同 `baseUrl` 下无法辨别，阻碍多提供商并发配置。 |
| [#5016](https://github.com/QwenLM/qwen-code/issues/5016) | **Qwen Code executes a tool after cancellation** | **P1 / 2 评论**。SIGINT 取消流式工具调用后，后台仍会执行被中断响应中的工具任务，存在严重的竞态与安全风险。 |
| [#5055](https://github.com/QwenLM/qwen-code/issues/5055) | **Trojan:JS/ShaiWorm.DBA!MTB 误报** | **P1 / 2 评论**。Windows 版 VSIX 安装包（v0.18.0）被多款杀毒软件报毒，直接影响分发与安装信任。 |
| [#5018](https://github.com/QwenLM/qwen-code/issues/5018) | **长程任务注意力不集中，出现大量遗忘** | **3 评论**。使用 `qwen3.7-max` 进行长程任务时，模型频繁遗忘前文上下文，长上下文记忆机制亟待优化。 |
| [#5015](https://github.com/QwenLM/qwen-code/issues/5015) | **Qwen Code executes repeated identical tool calls** | **P1 / 2 评论**。模型流式输出重复相同工具调用时，客户端未去重直接执行，易触发服务端 `Repetitive tool calls` 400 错误并终止会话。 |

---

### 4. 重要 PR 进展

| # | 标题 | 功能/修复摘要 |
|---|------|---------------|
| [#5040](https://github.com/QwenLM/qwen-code/pull/5040) | **feat(sdk): DaemonTransport abstraction** | 为 `DaemonClient` 引入可插拔传输层，支持 REST+SSE、ACP HTTP+SSE、ACP WebSocket 三种模式，无需分叉现有基础设施。 |
| [#5066](https://github.com/QwenLM/qwen-code/pull/5066) | **feat(web-shell): daemon web-shell improvements** | Web Shell 新增结构化 Token 用量追踪、完整 Settings 面板（含 i18n/主题/语言选择）、重试策略与流式指标。 |
| [#5069](https://github.com/QwenLM/qwen-code/pull/5069) | **feat(web-shell): revamp floating todo panel** | 将“当前任务”浮动面板从静态展示改为可交互组件，优化空间占用与进度可视化，解决编号错乱问题。 |
| [#5071](https://github.com/QwenLM/qwen-code/pull/5071) | **fix(cli): submit fast tool results after stream end** | 修复工具结果在流结束后、React 回调替换前被丢弃的竞态，确保快速工具完成仍能正确提交。 |
| [#5070](https://github.com/QwenLM/qwen-code/pull/5070) | **fix(cli): ignore expired live agents in focus navigation** | 修复 [#5067](https://github.com/QwenLM/qwen-code/issues/5067)：键盘焦点跳转不再命中已过期但未清理的终端 Agent，消除“幽灵选中位”。 |
| [#5033](https://github.com/QwenLM/qwen-code/pull/5033) | **fix(serve): Add prompt queue backpressure** | 为 `qwen serve` 增加提示队列背压机制，防止高并发场景下内存无限增长导致 OOM。 |
| [#5003](https://github.com/QwenLM/qwen-code/pull/5003) | **feat(tui): remove tool group borders and collapse completed tool results** | TUI 移除工具组圆角边框，并在紧凑模式下折叠已完成的工具结果块，减少视觉噪音。 |
| [#5057](https://github.com/QwenLM/qwen-code/pull/5057) | **fix(core): Persist file history snapshot updates** | 在 tracked edit 实际添加或恢复备份后，立即持久化最新文件历史快照，避免守护进程重启后状态回退。 |
| [#5039](https://github.com/QwenLM/qwen-code/pull/5039) | **fix(cli): use id+baseUrl for precise model identity** | 设置中新增 `model.id` / `model.baseUrl` / `model.provider` 字段，解决同名模型在不同 endpoint 下的身份歧义。 |
| [#5060](https://github.com/QwenLM/qwen-code/pull/5060) | **Add TrustedRouter provider preset** | 新增第三方提供商 TrustedRouter 的预设与常量注册，扩展多厂商兼容生态。 |

---

### 5. 功能需求趋势

从过去 24 小时 Issues 分布看，社区需求呈现 **五大集中方向**：

1. **Daemon / 服务端化（Serve Mode）**  
   远程 HTTP/SSE 能力补齐、OpenTelemetry 可观测性、Web Shell 体验、prompt 队列背压——表明开发者正将 Qwen Code 从本地 CLI 向长期运行服务迁移。
2. **IDE 集成与 UI 体验**  
   VSCode 插件兼容性、Virtualized History 渲染、statusline 换行、终端 resize 碎片——前端与插件层的 polish 需求密集。
3. **工具调用与 Agent 可靠性**  
   重复工具调用去重、取消后仍执行、后台 Agent 权限队列、长程任务遗忘——Agent 执行引擎的鲁棒性成为当前最大痛点。
4. **配置与生态迁移**  
   声明式 Agent（frontmatter）、Claude 配置一键导入（`/import-config`）、

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*