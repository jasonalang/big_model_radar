# AI CLI 工具社区动态日报 2026-06-09

> 生成时间: 2026-06-09 02:44 UTC | 覆盖工具: 7 个

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
*基于 2026-06-09 社区动态*

---

### 1. 生态全景

当前 AI CLI 工具整体已从“交互式尝鲜”迈入“生产工程化”深水区：各工具密集修补 Windows/WSL 混合环境适配、安全沙箱与权限边界、以及 MCP/Hook 扩展生态，表明开发者正试图将 Agent 嵌入日常 CI/CD 与大型代码库工作流。与此同时，模型路由复杂性（如新模型 404、配额缓存不一致）和跨平台性能债（尤其是 WSL 路径解析与文件扫描）成为普遍痛点，社区对“默认安全”与“可观测性”的呼声显著高于早期对纯模型能力的追捧。

---

### 2. 各工具活跃度对比

| 工具 | 24h Issues 更新 | 24h PR 更新 | 版本发布 | 今日关键动态 |
|------|----------------|-------------|----------|--------------|
| **OpenAI Codex** | ≥10 条热点 Issue（最高 76 评论/28👍） | 10 条 | v0.138.0 正式版<br>v0.139.0-alpha.1 | CLI ↔ Desktop 无缝切换（`/app`）；本地图片附件支持 |
| **Gemini CLI** | ≥10 条精选 Issue | 9 条 | v0.47.0-nightly | 浏览器代理移除“实验性”标签；1.2TB 数据丢失事故单引发安全反思 |
| **GitHub Copilot CLI** | 33 条 | 1 条（已关闭） | 无 | v1.0.60 出现函数调用 JSON Schema 回归；MCP 服务器异常已修复 |
| **Qwen Code** | ≥6 条（Top 10 列出 6 条，最高 13 评论） | 主分支有合并* | v0.18.0-preview.0 发布流程失败 | Daemon 能力缺口梳理；全局用户记忆与 OOM 修复合入 |
| **Kimi Code CLI** | 4 条（3 开放/1 关闭） | 0 条 | 无 | TypeScript 重写版迁移阵痛：`@filename` 语法与 API Key 认证失效 |
| **Claude Code** | — | — | — | 今日无显著动态披露 |
| **OpenCode** | — | — | — | 今日无显著动态披露 |

*\*Qwen Code 官方提及主分支合并重大修复，但未披露具体 PR 数量。*

---

### 3. 共同关注的功能方向

- **Windows/WSL 混合环境体验**  
  **涉及工具**：OpenAI Codex、GitHub Copilot CLI、Gemini CLI。  
  **具体诉求**：Codex 面临 WSL 路径扫描延迟（`/mnt/c` 反复扫描）与 `CreateProcess /bin/bash` 错误；Copilot CLI 出现 40–80 秒 WSL 启动延迟；Gemini 浏览器子代理在 Wayland 下直接失败。Windows 开发者已成为增长最快的用户群，但执行层、文件系统层与 UI 层均存在显著摩擦。

- **Agent 安全边界与沙箱**  
  **涉及工具**：Gemini CLI、OpenAI Codex、Qwen Code。  
  **具体诉求**：Gemini 社区因 1.2TB 数据丢失事件强烈要求代理在执行 `git reset --force` 等破坏性操作前主动劝阻；Codex 通过 Guardian 自动审查与 Windows deny-read 修复强化安全一致性；Qwen Code 推进原子文件写入与事务回滚，防止 Docker/共享工作区中因 `rename` 导致权限翻车。

- **MCP 与扩展生态可靠性**  
  **涉及工具**：GitHub Copilot CLI、OpenAI Codex、Gemini CLI。  
  **具体诉求**：Copilot 的 `/mcp search` 构造错误 URL 且插件 Hooks（`preToolUse`）静默失效；Codex 社区请求 MCP 工具非交互执行与 Claude Code Hook 兼容；Gemini 则聚焦 MCP 工具发现的原子更新与 SSRF 防护。

- **会话生命周期与上下文管理**  
  **涉及工具**：GitHub Copilot CLI、OpenAI Codex、Qwen Code。  
  **具体诉求**：Copilot 用户呼吁暂停长时间 Agent 会话；Codex 社区反对长粘贴被强制转为 `.txt` 附件；Qwen Code 则合并了全局用户级记忆（`~/.qwen/memories/`）并修复 `--resume` 导致的 OOM。

- **模型路由与多提供商支持**  
  **涉及工具**：OpenAI Codex、GitHub Copilot CLI、Qwen Code。  
  **具体诉求**：Codex 的 GPT-5.5 出现“本地元数据可用但请求 404”；Copilot Pro+ 用户在配额重置后遭遇“model not supported”；Qwen Code 则在 Daemon 模式下梳理 HTTP/SSE 远程能力缺口。

---

### 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线特征 |
|------|----------|----------|--------------|
| **OpenAI Codex** | CLI-Desktop 一体化、企业级安全审查（Guardian）、可观测性追踪 | 跨平台企业团队、需图形化与命令行无缝切换的开发者 | Rust 核心 + 遥测优先；强调 `run_turn`、`build_tool_router` 等全链路 Span 追踪 |
| **Gemini CLI** | 浏览器自动化（Browser Agent）、子代理调度、全栈任务执行 | 需要 Agent 自主浏览网页、执行多步骤任务的自动化用户 | Node.js 栈；通过“通用代理 + 子代理”架构处理复杂任务，正补全 SSRF/零配额等基线稳定性 |
| **GitHub Copilot CLI** | 深度绑定 GitHub/VS Code 生态、键盘优先交互、插件 Hooks | 已有 Copilot 订阅的开发者、VS Code 重度用户 | 闭源生态扩展；聚焦 Vim 模态输入、ESC 行为等终端交互细节，但近期版本质量波动 |
| **Qwen Code** | Daemon 模式、声明式 Agent（Markdown/YAML frontmatter）、开源模型本地部署 | 国内开发者、开源模型偏好者、需要远程 CLI 服务的团队 | 对标 Claude Code 的声明式 Agent 定义；推进 `qwen serve` 作为常驻服务，但工程化（如发布流程）仍在完善 |
| **Kimi Code CLI** | 架构迁移（Python → TypeScript） | 早期尝鲜用户 | 处于新旧版本（`kimi-cli` vs `kimi-code`）交替期，功能冻结与兼容性断裂并存，定位尚不清晰 |

---

### 5. 社区热度与成熟度

- **第一梯队（高活跃，快速迭代，但平台债重）**：**OpenAI Codex** 与 **Gemini CLI**。两者均保持高频 Issue/PR 双轮驱动：Codex 一天内合并 10 个 PR 并发布正式版，Gemini 亦在 SSRF、MCP 原子更新等基础设施上密集投入。但 Codex 的 Windows/WSL 问题占据热点榜半数，Gemini 则刚经历 1.2TB 数据丢失的严重安全事件，说明核心能力尚未完全收敛。

- **第二梯队（高活跃，生态依赖强，但工程节奏偏慢）**：**GitHub Copilot CLI**。24 小时内 33 条 Issue 更新显示用户基数庞大且反馈积极，但仅 1 条 PR 进展，且 v1.0.60 连续出现函数调用回归与 MCP 异常，反映其闭源迭代节奏与社区修复需求之间存在落差。

- **第三梯队（中等活跃，功能追赶期）**：**Qwen Code**。社区围绕 Daemon 模式与声明式 Agent 展开深度技术讨论（如 AST-aware 文件读取），主分支亦合并内存与稳定性修复，但预览版发布流程失败，显示其工程化流水线成熟度仍待加固。

- **第四梯队（低活跃，迁移阵痛期）**：**Kimi Code CLI**。24 小时内仅 4 条 Issue、0 条 PR，且核心问题集中在 TypeScript 重写导致的向后兼容性断裂（`@filename`、API Key 认证），表明其正处于架构换血的功能真空期。

- **静默观察**：**Claude Code** 与 **OpenCode** 今日无显著动态披露，前者作为行业标杆可能处于版本间歇期，后者则缺乏社区声量。

---

### 6. 值得关注的趋势信号

1. **“Windows/WSL 体验”已成为 AI CLI 的下一个主战场**  
   所有主流工具（Codex、Copilot、Gemini）均在同一周期内爆发 Windows 相关问题，表明 AI CLI 的用户群已从早期 macOS/Linux 极客扩散至更广泛的 Windows 开发者。能否在 6–12 个月内解决 WSL 路径解析、文件系统扫描与跨平台认证，将直接决定工具的市场渗透率。

2. **“安全默认”正在从合规选项变为生死线**  
   Gemini 的 1.2TB 数据丢失事件与 Codex 对 Guardian 审查、Windows deny-read 的紧急修补，标志着社区共识已从“Agent 越自主越好”转向“破坏性操作必须默认拦截”。未来，缺乏原子写入、操作回滚与危险命令劝阻的 CLI 工具将难以进入企业代码库。

3. **模型路由与缓存一致性成为通用基础设施挑战**  
   GPT-5.5 的 404 错误、Copilot 配额重置后的模型不可用、Gemini 的 Vertex AI 模型映射错误，共同指向一个趋势：随着多模型、多提供商成为标配，CLI 工具需要更实时的模型状态同步机制，而非依赖本地静态元数据或简单重试。

4. **声明式 Agent 定义或将成为生态标准**  
   Qwen Code 明确对标 Claude Code 的 frontmatter Agent 定义，社区对“Markdown + YAML 配置即可创建自定义

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-09*

---

### 1. 热门 Skills 排行

| 排名 | Skill (PR) | 功能简介 | 社区讨论热点 | 状态 |
|---|---|---|---|---|
| 1 | **agent-creator**<br>[#1140](https://github.com/anthropics/skills/pull/1140) | 任务级 Agent 集元技能，修复多工具并行评估与 Windows 路径兼容 | 直接回应 Issue #1120，解决 `evaluation.py` 在多工具调用时的稳定性问题，被视为 Agent 编排层的基础设施 | Open |
| 2 | **document-typography**<br>[#514](https://github.com/anthropics/skills/pull/514) | AI 生成文档的排版质量控制：防止孤行、寡居段、编号错位 | 击中所有长文档生成的共性痛点，社区认为该 Skill 应作为默认文档能力内置 | Open |
| 3 | **testing-patterns**<br>[#723](https://github.com/anthropics/skills/pull/723) | 全栈测试指南：Testing Trophy、React 组件测试、Mock 策略、E2E | 开发者的刚需 Skill，填补了 Claude Code 在系统化测试方法论上的空白 | Open |
| 4 | **ServiceNow**<br>[#568](https://github.com/anthropics/skills/pull/568) | 企业级 ServiceNow 平台助手，覆盖 ITSM/ITOM/SecOps/IntegrationHub | 覆盖面极广，被视为企业 IT 运维与低代码平台的重磅集成 | Open |
| 5 | **ODT**<br>[#486](https://github.com/anthropics/skills/pull/486) | OpenDocument 文本创建、模板填充及 ODT↔HTML 转换 | 满足开源/ISO 标准文档需求，与现有 DOCX/PDF Skill 形成互补 | Open |
| 6 | **n8n-builder / n8n-debugger**<br>[#190](https://github.com/anthropics/skills/pull/190) | 可视化工作流自动化（n8n）的构建与故障排查 | 工作流自动化是社区高频场景，与低代码/无代码生态深度对接 | Open |
| 7 | **shodh-memory**<br>[#154](https://github.com/anthropics/skills/pull/154) | 跨会话持久化记忆系统，支持主动上下文召回与记忆结构化 | Agent 长期记忆的基础设施，解决 Claude 会话状态丢失问题 | Open |
| 8 | **AURELION**<br>[#444](https://github.com/anthropics/skills/pull/444) | 四层认知框架（Kernel/Advisor/Agent/Memory），面向专业知识管理 | 认知架构派社区关注，强调结构化思维与长期知识沉淀 | Open |

---

### 2. 社区需求趋势

从 Issues 热度与方向提炼，社区最期待的新 Skill 方向集中在：

- **组织级共享与治理**  
  企业用户强烈需求 org-wide Skill 共享（[#228](https://github.com/anthropics/skills/issues/228)），同时担忧社区 Skill 冒用 `anthropic/` 命名空间带来的信任边界问题（[#492](https://github.com/anthropics/skills/issues/492)），催生对 **Agent 治理、审计、权限控制** Skill 的期待。

- **工作流编排与 MCP 化**  
  希望将 Skills 暴露为标准 MCP（[#16](https://github.com/anthropics/skills/issues/16)），并与 n8n、ServiceNow 等外部工作流平台深度集成，实现“AI Agent + 低代码”的双向驱动。

- **质量评估与开发者体验**  
  `skill-creator` 的评估脚本（`run_eval.py`）在 Windows 与描述优化循环上存在系统性 Bug（[#556](https://github.com/anthropics/skills/issues/556)、[#1169](https://github.com/anthropics/skills/issues/1169)），社区急需**官方测试与评估最佳实践**。

- **文档工程与多文件引用**  
  复杂 Skill 需要多文件预加载/内联打包能力（[#1220](https://github.com/anthropics/skills/issues/1220)），同时要求 AI 生成文档具备专业排版（[#514](https://github.com/anthropics/skills/pull/514)）和开源格式支持（[#486](https://github.com/anthropics/skills/pull/486)）。

- **跨平台与云兼容**  
  AWS Bedrock 适配（[#29](https://github.com/anthropics/skills/issues/29)）与 Windows 环境兼容性（[#1050](https://github.com/anthropics/skills/pull/1050)、[#1099](https://github.com/anthropics/skills/pull/1099)）是阻碍企业落地的关键阻塞点。

---

### 3. 高潜力待合并 Skills

以下 PR 虽未合并，但解决明确痛点且近期仍活跃更新，预计近期落地概率较高：

| PR | Skill | 潜力理由 | 最近更新 |
|---|---|---|---|
| [#1140](https://github.com/anthropics/skills/pull/1140) | **agent-creator** | 修复多工具评估与 Windows 支持，关联高热度 Issue #1120 | 2026-06-02 |
| [#363](https://github.com/anthropics/skills/pull/363) | **feature-dev workflow fix** | 修复 TodoWrite 覆盖导致 Phase 6/7 被跳过的关键 Bug，直接影响现有核心 Skill | 2026-06-03 |
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | 通用文档质量能力，无外部依赖，合并阻力小 | 2026-03-13 |
| [#190](https://github.com/anthropics/skills/pull/190) | **n8n-builder / n8n-debugger** | 工作流自动化社区呼声高，且为生产环境实测 Skill | 2026-05-18 |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | 开发者体验核心缺口，内容体系完整 | 2026-04-21 |
| [#568](https://github.com/anthropics/skills/pull/568) | **ServiceNow** | 企业级场景覆盖全面，填补官方 Skill 空白 | 2026-04-23 |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT** | 开源文档标准支持，与现有文档 Skill 形成生态互补 | 2026-04-14 |

---

### 4. Skills 生态洞察

**当前社区最集中的诉求是：将 Claude Code Skills 从“个人效率脚本”升级为具备组织共享、质量评估、跨平台兼容与安全治理能力的“企业级 Agent 基础设施”。**

---



</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
**日期：2026-06-09**

---

### 1. 今日速览
今日社区最显著的动态是 **v0.138.0 正式版发布**，带来了 CLI 与 Desktop 的无缝衔接能力（`/app` 命令）以及本地图片附件支持；同时社区对 **GPT-5.5 模型在本地环境出现“404 Model not found”** 的反馈急剧升温，相关 Issue 已积累 76 条评论。此外，过去 24 小时内合并和关闭的 PR 集中在 Guardian 安全审查遥测、Windows 沙箱修复及 Python SDK 目标操作等方向。

---

### 2. 版本发布

**[rust-v0.138.0](https://github.com/openai/codex/releases/tag/rust-v0.138.0)**  
- **CLI ↔ Desktop 无缝切换**：`/app` 命令现可将当前 CLI 线程直接移交至 macOS 和原生 Windows 上的 Codex Desktop；Windows 工作区启动时也可直接进入 Desktop，无需再停留在手动提示。  
- **本地图片支持**：新增本地图片附件及独立图片生成能力（与社区长期请求的图片生成功能对应）。  

**[rust-v0.139.0-alpha.1](https://github.com/openai/codex/releases/tag/rust-v0.139.0-alpha.1)**  
- 早期预览版本，暂无详细变更说明。

---

### 3. 社区热点 Issues（过去 24 小时更新）

| Issue | 重要性 & 社区反应 |
|-------|------------------|
| **[#26892](https://github.com/openai/codex/issues/26892)** `gpt-5.5` 在 Desktop 与 CLI 均报 404，但本地元数据仍显示可用 | **关键可用性故障**。76 条评论、28 👍，影响面广，涉及模型路由与本地缓存不一致。 |
| **[#25144](https://github.com/openai/codex/issues/25144)** 请求添加选项，禁用长粘贴自动转为 `.txt` 附件 | **高赞同体验需求**（65 👍，52 评论）。开发者希望保留原始提示结构，而非被强制拆分为附件。 |
| **[#25715](https://github.com/openai/codex/issues/25715)** Windows + WSL 作为 Agent 环境时 Desktop 极慢 | **WSL 性能痛点**（36 👍，36 评论）。每轮工具调用延迟极高，阻碍 Windows 开发者正常使用。 |
| **[#25203](https://github.com/openai/codex/issues/25203)** Windows 上 GitHub OAuth 回调失败，提示 "Unable to find Electron app" | **Windows 认证阻塞**（37 评论，21 👍）。导致无法连接 GitHub 账户。 |
| **[#25719](https://github.com/openai/codex/issues/25719)** macOS Desktop 反复触发 `syspolicyd`/`trustd`，CPU 与内存失控 | **macOS 系统级性能问题**（20 👍，20 评论）。与安全策略守护进程交互异常，影响整机性能。 |
| **[#8758](https://github.com/openai/codex/issues/8758)** 支持从 Codex 生成图片（已关闭） | **长期功能请求落地**（55 👍，23 评论）。今日被关闭，疑似随 v0.138.0 的独立图片生成能力得到解决。 |
| **[#21753](https://github.com/openai/codex/issues/21753)** 完整实现 Claude Code Hook 兼容性（29+） | **生态扩展性**（15 👍，11 评论）。社区希望 Codex 提供与 Claude Code 同等完整的自动化生命周期钩子。 |
| **[#24675](https://github.com/openai/codex/issues/24675)** Desktop 在 401 重认证后仍使用过期的 app connector 缓存 | **认证状态管理缺陷**（21 评论，16 👍）。需手动清除缓存才能恢复，严重影响集成体验。 |
| **[#26149](https://github.com/openai/codex/issues/26149)** Windows + WSL 反复扫描 `.codex/.tmp/plugins`，导致每次命令严重延迟 | **WSL 路径性能瓶颈**（16 👍，10 评论）。跨 `/mnt/c` 的重复扫描是主要根因。 |
| **[#22185](https://github.com/openai/codex/issues/22185)** Windows Desktop + WSL 下 `unified_exec` 错误尝试 `CreateProcess /bin/bash` | **WSL 执行层兼容性**（11 评论，7 👍）。路径解析在混合环境中失效。 |

---

### 4. 重要 PR 进展（过去 24 小时更新）

| PR | 功能或修复内容 |
|----|----------------|
| **[#27101](https://github.com/openai/codex/pull/27101)** 通过注入式 Provider 加载用户指令 | 移除 `codex-core` 对 `$CODEX_HOME` 的隐式依赖，由嵌入器负责提供用户级指令，提升架构解耦度。 |
| **[#27107](https://github.com/openai/codex/pull/27107)** 为 `run_turn` 添加追踪 Span | 补齐 app-server 延迟追踪的盲区，覆盖 turn 编排、采样请求准备、工具加载等阶段，便于性能归因。 |
| **[#26880](https://github.com/openai/codex/pull/26880)** 为 worktree Git 读取保留 `fsmonitor` | 修复此前强制禁用 `core.fsmonitor` 导致大仓库全量扫描的问题，显著加速 `status`/`diff` 等操作。 |
| **[#26953](https://github.com/openai/codex/pull/26953)** Python SDK 新增专用 Goal 操作 | 让 Python SDK 能以与 TUI 一致的方式驱动持久化 Goal，避免在 SDK 层引入 Goal 专用 app-server RPC。 |
| **[#27062](https://github.com/openai/codex/pull/27062)** Guardian 自动审查瞬态失败重试 | 当 Guardian（权限自动审查）因模型或网络瞬态错误失败时，增加重试机制，提升自动审查可靠性。 |
| **[#27091](https://github.com/openai/codex/pull/27091)** Guardian 审查间隙主动压缩上下文 | 复用的 Guardian 会话在审查完成后若上下文超过阈值，立即触发压缩，降低后续审查延迟与资源占用。 |
| **[#27017](https://github.com/openai/codex/pull/27017)** 修复 Windows deny-read 在 exec 运行时未生效 | 解决 Windows 下 `shell_command` 与 `exec_command` 未正确解析文件系统覆盖，导致模型可见限制但实际执行未受限的安全一致性问题。 |
| **[#27039](https://github.com/openai/codex/pull/27039)** 新增分离式异步命令钩子 | 允许 `async: true` 的钩子在非阻塞通道运行，并在后续用户 turn 返回信息，扩展自动化场景。 |
| **[#27094](https://github.com/openai/codex/pull/27094)** 为 `build_tool_router` 添加追踪 Span | `append_tool_search_executor` 平均耗时约 113ms，新增 Span 用于追踪工具路由构建成本，指导后续优化。 |
| **[#17931](https://github.com/openai/codex/pull/17931)** 支持加密本地密钥环认证 | Windows Credential Manager 单条凭证上限 2,560 字节，大体积 auth 负载会持久化失败；此 PR 通过加密本地存储绕过该限制。 |

---

### 5. 功能需求趋势

从过去 24 小时的 Issues 与 PR 中，可提炼出社区最关注的五大方向：

1. **Windows + WSL 混合环境体验**  
   性能（重复扫描、路径解析）、认证（OAuth、密钥环）及 UI 渲染问题占据热点榜半数以上，表明 Windows 开发者已成为 Codex 增长最快的用户群，但混合环境的稳定性仍是最大短板。

2. **模型可用性与多提供商支持**  
   GPT-5.5 的 404 错误、Amazon Bedrock 中途停止、`service_tier` 参数兼容性等问题显示，社区对“新模型快速上线”和“第三方提供商无缝切换”有强烈需求。

3. **认证与多账户管理**  
   多账户（个人/企业）、OAuth 回调、过期缓存、密钥环限制等反馈密集，说明 Codex 在真实企业场景下的身份与权限管理仍需完善。

4. **可观测性与性能优化**  
   大量 PR 集中在 Span 追踪（`run_turn`、`build_tool_router`）、Git `fsmonitor`、Guardian 上下文压缩，表明团队正在系统性补齐性能诊断与长尾延迟治理能力。

5. **扩展性与自动化钩子**  
   Claude Code Hook 兼容、异步命令钩子、MCP 工具非交互执行等需求上升，开发者希望将 Codex 深度嵌入 CI/CD 与自动化工作流，而非仅作为交互式助手。

---

### 6. 开发者关注点

- **Windows/WSL 是首要痛点**：从执行层（`/bin/bash` 路径错误）、文件系统层（`/mnt/c` 扫描）到 UI 层（透明侧边栏、Electron 回调），Windows 开发者面临的阻塞性问题最多，亟需平台专项优化。  
- **模型路由与缓存一致性**：GPT-5.5 在本地元数据与远端实际可用性之间出现断层，开发者对“模型列表显示可用但请求失败”的容忍度极低，要求更实时的模型状态同步。  
- **沙箱与权限的精细控制**：社区既希望默认沙箱更安全（如 Windows deny-read 真正生效），又需要为非交互场景（`codex exec` + MCP）提供比 `--dangerously-bypass-approvals-and-sandbox` 更细粒度的白名单机制。  
- **会话与上下文管理**：项目/对话在重启后丢失、长粘贴被强制拆分为附件、缺乏跨任务清空上下文但保留会话 ID 的能力，均指向开发者对“可预测、可编程的会话生命周期”的诉求。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报**  
*2026-06-09*

---

### 1. 今日速览

今日社区发布 `v0.47.0-nightly` 版本，浏览器代理正式移除“实验性”标签，标志其趋于稳定。与此同时，一则已关闭的 **1.2TB 数据丢失** 事故单持续引发社区对代理防御性编程与破坏性操作防护的深刻反思。工程侧则密集推进 MCP 稳定性、SSRF 安全加固及零配额快速失败等核心修复。

---

### 2. 版本发布

**v0.47.0-nightly.20260609.g0567b25a2**  
- 调整 Antigravity 过渡横幅的最大显示次数。  
- 浏览器代理（Browser Agent）相关文档移除“实验性”标识，表明该功能在生产环境中进入成熟阶段。  
🔗 [Release 链接](https://github.com/google-gemini/gemini-cli/releases)

---

### 3. 社区热点 Issues（按关注度精选 10 条）

| # | 标题 | 核心看点与社区反应 |
|---|------|------------------|
| **#27397** | [CRITICAL INCIDENT] Catastrophic Data Loss (1.2TB) | **最严重事件**：代理执行生成的 Node.js 脚本导致 1.2TB 4K 媒体文件永久丢失，根因是代理缺乏防御性编程与破坏性 I/O 校验。虽已关闭，但评论区对“AI 代理的默认安全边界”展开激烈讨论。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/27397) |
| **#21409** | Generalist agent hangs | **高赞（8👍）高频痛点**：通用代理（generalist agent）在简单操作（如创建文件夹）时无限挂起，用户需手动禁止子代理才能规避。社区迫切期待调度层修复。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/21409) |
| **#24353** | Robust component level evaluations | **基础设施方向**：作为行为评估（behavioral evals）的后续，已生成 76 个测试用例，覆盖 6 个模型变体。评论聚焦如何提升组件级评估的鲁棒性，防止回归。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/24353) |
| **#22745** | Assess the impact of AST-aware file reads, search, and mapping | **技术前瞻**：探讨引入 AST 感知工具以精确定位方法边界、减少误读与 Token 噪音。被视为降低多轮交互成本的关键路径。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/22745) |
| **#22323** | Subagent recovery after MAX_TURNS is reported as GOAL success | **状态机缺陷**：`codebase_investigator` 在达到最大轮次后仍报告 `status: "success"`，导致用户误以为分析完成。评论指出这是子代理中断掩码的严重逻辑错误。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/22323) |
| **#21968** | Gemini does not use skills and sub-agents enough | **生态调度问题**：用户配置了 Gradle、Git 等自定义技能，但代理几乎不会主动调用，除非显式指令。社区希望提升技能路由的智能程度。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/21968) |
| **#22672** | Agent should stop/discourage destructive behavior | **安全策略**：与 #27397 数据丢失事件呼应，要求代理在执行 `git reset --force`、数据库修改等危险操作前主动劝阻或要求确认。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/22672) |
| **#25166** | Shell command execution gets stuck with "Waiting input" | **核心体验**：简单命令执行后终端假死，显示“等待输入”但实际已结束。3 个点赞表明影响面广，严重影响脚本化工作流。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/25166) |
| **#26525** | Add deterministic redaction and reduce Auto Memory logging | **隐私合规**：Auto Memory 将本地对话记录发送至后台提取代理，但脱敏发生在内容进入模型上下文之后，存在泄露风险。社区要求确定性脱敏与日志削减。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/26525) |
| **#21983** | browser subagent fails in wayland | **跨平台兼容**：Wayland 环境下浏览器代理直接失败，对 Linux 桌面用户造成阻断。🔗 [链接](https://github.com/google-gemini/gemini-cli/issues/21983) |

---

### 4. 重要 PR 进展（精选 10 条）

| # | 标题 | 功能/修复内容 |
|---|------|--------------|
| **#27749** | Vertex ai model mapping fix | 修复非 API Key / 非 Vertex AI 认证路径下的模型映射：`gemini-3.5-flash` 在 CCPA 路由中被错误拒绝，现统一转换逻辑。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27749) |
| **#27626** | fix(core): block private OAuth metadata URLs | 为 MCP OAuth 元数据发现增加 SSRF 防护，禁止访问私有 IP 段的元数据端点。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27626) |
| **#27744** | fix(web-fetch): resolve DNS before SSRF guard | 在 SSRF 防护前先行 DNS 解析，防止通过 `127.0.0.1.nip.io` 等 wildcard DNS 绕过私有 IP 封锁。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27744) |
| **#27619** | fix(core): implement atomic update in MCP tool discovery | 实现 MCP 工具刷新原子更新：网络瞬断时保留旧工具列表，避免“tool not found”错误。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27619) |
| **#27698** | fix(core): Ensure zero-quota limits fail fast | 零配额硬限制场景下立即失败，避免陷入 10 次重试循环导致 CLI 假死。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27698) |
| **#27429** | fix(core): handle EBADF in resizePty catch block | `--resume` 恢复会话时，旧 PTY 文件描述符失效导致 `EBADF` 崩溃，现与 `ESRCH` 同等静默处理。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27429) |
| **#27438** | feat(core): add configurable per-tool-call timeout | 引入全局可配置的工具调用超时 `tools.callTimeout`，并在 `ToolExecutor` 中统一强制执行。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27438) |
| **#27729** | truncate telemetry metric attributes to 1024 chars | 将遥测指标属性截断至 1024 字符，防止 GCP Monitoring 导出失败时终端被 Node.js 堆栈跟踪淹没。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27729) |
| **#27505** | Prevent extra spaces on width-0 CJK continuation cells | 修复 CJK 宽字符在终端续行时产生多余空格的问题，解决跨平台复制粘贴错误。🔗 [链接](https://github.com/google-gemini/gemini-cli/pull/27505)

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*2026-06-09*

---

### 1. 今日速览
过去 24 小时社区活跃度较高，共有 **33 条 Issue** 获得更新，但无新版本发布。今日焦点集中在 **v1.0.60 回归问题**（函数调用失败、MCP 异常）、**插件 Hooks 的可靠性缺陷**，以及 **Windows/WSL 环境下的性能与终端交互体验**。

---

### 2. 版本发布
今日无新 Release。

---

### 3. 社区热点 Issues（Top 10）

| # | 标题 | 重要性 | 社区反应 |
|---|------|--------|----------|
| **#1928** | [Allow to pause copilot work](https://github.com/github/copilot-cli/issues/1928) | 🔥 高 | 9 条评论。用户在长时间会话中无法暂停并补充上下文，导致 Agent 偏离目标，是高频交互痛点。 |
| **#13** | [CLI input should have a vi/vim input mode](https://github.com/github/copilot-cli/issues/13) | 🔥 高 | 7 评论，**63 👍**。长期高票需求，Vim 用户强烈呼吁在交互式 CLI 中支持模态编辑与键盘导航。 |
| **#3547** | [Background sub-agent silently hangs at total_turns=0 when model="gpt-5.5"](https://github.com/github/copilot-cli/issues/3547) | 🐛 严重 | 6 评论。调用 `gpt-5.5` 的后台子代理会无限挂起，影响自动化工作流可靠性。 |
| **#3436** | [/mcp search constructs wrong URL for custom MCP registries](https://github.com/github/copilot-cli/issues/3436) | 🐛 高 | 5 评论。实验性 `/mcp search` 遗漏 `/v0.1/` 路径段，导致企业自托管 MCP 注册表 404，阻断企业落地。 |
| **#2867** | [Claude Opus 4.6 (high) returns "model not supported" after quota reset](https://github.com/github/copilot-cli/issues/2867) | 🐛 高 | 5 评论。Copilot Pro+ 用户在配额重置后仍被提示模型不支持，涉及计费与模型路由策略。 |
| **#2540** | [Plugin-defined preToolUse hooks do not fire](https://github.com/github/copilot-cli/issues/2540) | 🐛 中高 | 4 评论，3 👍。插件生态关键缺陷：`hooks.json` 定义的 Hook 在主会话和子代理中均不执行。 |
| **#3652** | [WSL experiences 40-80 second startup delays](https://github.com/github/copilot-cli/issues/3652) | ⚡ 性能 | 3 评论。`listSessions` 在 WSL 下导致 VS Code Copilot Chat 极慢启动，严重影响 Windows 开发者体验。 |
| **#3701** | [Copilot CLI bug: runaway MCP server spawning](https://github.com/github/copilot-cli/issues/3701) | 🐛 严重 | 已关闭。IDE 锁文件监听循环导致 MCP 服务器无限生成，已在 1.0.60 相关迭代中修复。 |
| **#3716** | [[Regression] Function call fails](https://github.com/github/copilot-cli/issues/3716) | 🐛 回归 | 1 评论。**v1.0.60 回归**，`tools.function.parameters` JSON Schema 校验失败，阻断工具调用。 |
| **#3709** | [Allow /model to switch between multiple models, including BYOK/local providers](https://github.com/github/copilot-cli/issues/3709) | ✨ 功能 | 1 评论。BYOK 模式下无法通过 `/model` 切换本地模型，用户呼吁单会话内多模型灵活调度。 |

---

### 4. 重要 PR 进展

过去 24 小时仅 **1 条 PR** 更新，社区代码贡献相对平静：

- **[#1960] install: use GITHUB_TOKEN for authenticated GitHub requests**（[链接](https://github.com/github/copilot-cli/pull/1960)）  
  **状态**：已关闭。  
  **内容**：安装脚本现在会读取 `GITHUB_TOKEN` 环境变量，并在 curl/wget 下载及 `git ls-remote` 时携带认证头。该改动可有效规避 GitHub API 速率限制，同时支持从私有仓库安装 Copilot CLI。

---

### 5. 功能需求趋势

从今日 33 条 Issue 中，可提炼出社区最关注的五大方向：

1. **键盘驱动与终端交互**  
   Vim 模态输入（#13）、ESC 保存半输入命令（#3720）、`/model` 选择器交互一致性（#3715）等需求密集出现，开发者强烈希望 CLI 成为“键盘优先”的高效工具。

2. **会话生命周期管理**  
   暂停会话（#1928）、多并发会话内置工具（#2966）、历史记录保留等需求表明，用户在长时间、多任务 Agent 会话中缺乏控制权。

3. **模型生态与成本优化**  
   BYOK/本地模型切换（#3709）、禁用流式传输（#3717）、支持低成本/开源权重模型（#3707）、Free 计划解锁 Claude Sonnet/Opus（#3705）等，反映用户对模型选择灵活性和成本的高度敏感。

4. **MCP 与插件系统可靠性**  
   MCP 注册表 URL 构造（#3436）、Agent 级工具白名单失效（#2638）、Hooks 不触发（#2540, #2201）等问题显示，扩展生态的稳定性仍是当前短板。

5. **Windows/WSL 深度适配**  
   WSL 启动延迟（#3652）、Terminal 复制功能被绕过（#3724）、ReFS/Dev Drive 沙盒限制（#3712）、安装脚本误识别 FreeBSD（#3710）等，Windows 开发者体验存在明显摩擦。

---

### 6. 开发者关注点

- **v1.0.60 稳定性堪忧**：今日出现函数调用 JSON Schema 回归（#3716）及此前 MCP 服务器无限生成（#3701），开发者对近期版本质量表示担忧。
- **插件 Hooks 执行不可靠**：从 `sessionStart` 到 `preToolUse`，多个 Hook 点存在“静默失败”现象，插件开发者难以调试。
- **Windows 环境体验割裂**：WSL 性能、Terminal 集成、路径解析（`~` 与反斜杠，#3719）等问题集中爆发，Windows 用户成为今日反馈主力。
- **模型可访问性与成本**：Pro+ 用户遭遇配额后模型不可用（#2867），Free 用户受限于 Haiku 4.5（#3705），社区呼吁更透明的模型策略与低成本选项。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI 社区动态日报**  
*日期：2026-06-09 | 数据来源：github.com/MoonshotAI/kimi-cli*

---

### 1. 今日速览

过去24小时仓库无新版本发布，也无 PR 合并，社区焦点集中在 TypeScript 重写版（kimi-code）的迁移阵痛上。4 条活跃 Issue 中 3 条为开放性 Bug，涉及 `@filename` 语法失效、API 密钥认证被静默移除及安装异常；另 1 条文档改进 Issue 被关闭，显示官方正加速推进旧版 Python CLI 向新架构过渡。

---

### 2. 版本发布

今日无新版本发布。

---

### 3. 社区热点 Issues

> 注：过去 24 小时内仓库仅更新 4 条 Issue，以下为全部动态，按影响面排序。

1. **#2441 [OPEN] [bug] 新版本现在连 @filename 都不支持了？**  
   🔗 https://github.com/MoonshotAI/kimi-cli/issues/2441  
   **重要性：高。**`@filename` 是用户高频使用的上下文引用语法，突然失效直接打断既有工作流。该 Issue 反映新版在向后兼容性上存在严重疏漏，且未提供替代方案或迁移公告。

2. **#2442 [OPEN] [bug] Broken Workflow**  
   🔗 https://github.com/MoonshotAI/kimi-cli/issues/2442  
   **重要性：高。** 报告 API 密钥认证被“静默移除”（silently removed），属于典型回归缺陷。对依赖 API Key 做自动化/CI 集成的开发者影响极大，缺乏提前通告易引发信任危机。

3. **#2436 [OPEN] [bug] Installation failed**  
   🔗 https://github.com/MoonshotAI/kimi-cli/issues/2436  
   **重要性：中。** 涉及 v1.47.0 安装后配置异常，标题暗示 Kimi Code 安装状态与 CLI 行为存在冲突，可能与新旧版本并存时的路径或配置覆盖有关，属于阻塞性体验问题。

4. **#2376 [CLOSED] [enhancement] [Docs] Add deprecation banner on GitHub Pages**  
   🔗 https://github.com/MoonshotAI/kimi-cli/issues/2376  
   **重要性：中。** 该 Issue 要求为旧版 Python CLI 的 GitHub Pages 添加弃用横幅，并指向 TypeScript 重写版 `kimi-code`。其被关闭意味着官方已确认或执行了文档迁移策略，是判断产品路线的重要信号。

---

### 4. 重要 PR 进展

过去 24 小时内无 Pull Request 更新。

---

### 5. 功能需求趋势

基于近期 Issue 分析，社区当前最关注三大方向：

1. **迁移兼容性**：用户强烈依赖 `@filename` 等旧版交互语法，要求新版提供向后兼容或明确的迁移指南，避免升级即“炸环境”。
2. **认证机制透明度**：API Key 支持的突然变更引发担忧，社区需要清晰的认证方式变更说明与替代方案（如 OAuth、Login Session 等）。
3. **文档与弃用策略**：随着 Python 版加速退场，用户希望在 GitHub Pages、README 等入口获得显眼的弃用提示和安装指引，减少新旧版本（`kimi-cli` vs `kimi-code`）的混淆。

---

### 6. 开发者关注点

1. **破坏性变更零公告**：`@filename` 语法与 API Key 认证在版本迭代中被移除或变更，但缺乏 CHANGELOG 或迁移文档，导致生产环境脚本直接失效。
2. **版本号与架构混乱**：同时存在 `0.11.0` 与 `1.47.0` 等版本号，且涉及 Python 旧版与 TypeScript 新版两条产品线，开发者难以判断应安装和维护哪一个 CLI 工具。
3. **安装与配置可靠性**：新版本的安装流程在部分环境下出现异常，且新旧 CLI 的配置文件可能存在冲突，需要更健壮的安装检测与隔离机制。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-06-09*

---

### 1. 今日速览
今日社区核心围绕 **Daemon 模式能力补全** 与 **内存/稳定性修复** 展开激烈讨论，主分支合并了用户级全局记忆与防 OOM 等重大修复；不过 **v0.18.0-preview.0 发布流程意外失败**，需留意官方修复。此外，声明式 Agent、动态工作流等 Claude Code 对标功能持续高热。

---

### 2. 版本发布
**无正式 Release。**  
⚠️ 注意：[`v0.18.0-preview.0`](https://github.com/QwenLM/qwen-code/issues/4875) 的发布工作流于今日失败（[#4875](https://github.com/QwenLM/qwen-code/issues/4875)），目前 Issue 已开启，等待官方排查。

---

### 3. 社区热点 Issues（Top 10）

| # | 状态 | 标题 | 评论 | 核心看点 |
|---|------|------|------|----------|
| [#4514](https://github.com/QwenLM/qwen-code/issues/4514) | 🔵 OPEN | tracking(serve): daemon capability gaps & prioritized backlog | 13 | **今日最热**。系统梳理 `qwen serve` 在 v0.16-alpha 之后仍缺失的 HTTP/SSE 远程能力，社区正集中讨论 Slash Command 透传之外的 Daemon 缺口。 |
| [#4815](https://github.com/QwenLM/qwen-code/issues/4815) | 🟣 CLOSED | BUG: Severe OOM with `qwen --resume` and Escape key broken | 9 | **P1 严重 Bug**。`--resume` 恢复会话后 10 分钟内必现 OOM，且 Esc 键 100% 失效；已关闭，说明修复已合并。 |
| [#4821](https://github.com/QwenLM/qwen-code/issues/4821) | 🔵 OPEN | feat(agents): support declarative agent definitions via frontmatter files | 6 | **高赞需求**。要求像 Claude Code 2.1.167 一样通过 Markdown + YAML frontmatter 声明式定义 Agent，降低自定义门槛。 |
| [#4747](https://github.com/QwenLM/qwen-code/issues/4747) | 🟣 CLOSED | Feature: Support global user-level auto-memory | 4 | **体验提升**。要求跨项目共享用户记忆（`~/.qwen/memories/`），避免每开新项目都要重新学习用户偏好；已关闭。 |
| [#4095](https://github.com/QwenLM/qwen-code/issues/4095) | 🔵 OPEN | feat: atomic file write & transaction rollback | 4 | **技术债**。Phase 1 的原子写入在 Docker/共享工作区中因 `rename` 重置 inode 属主而翻车，需进一步修复权限问题。 |
| [#4801](https://github.com/QwenLM/qwen-code/issues/4801) | 🟣 CLOSED | Add a dedicated web_search tool | 4 | **工具补齐**。社区认为 Qwen Code 是主流 Code Agent CLI 中唯一缺少 WebSearch 的，该 Issue 推动通过 DashScope 透传实现；已关闭。 |
| [#4782

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*