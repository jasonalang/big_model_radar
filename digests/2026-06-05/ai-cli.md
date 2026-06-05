# AI CLI 工具社区动态日报 2026-06-05

> 生成时间: 2026-06-05 02:58 UTC | 覆盖工具: 7 个

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
*基于 2026-06-05 社区动态*

---

### 1. 生态全景

当前 AI CLI 生态呈现**“头部企业化、长尾协议化”**的分化态势。Claude Code、OpenAI Codex 与 GitHub Copilot CLI 正围绕企业治理、IDE 深度集成和沙盒安全构建护城河；而以 Qwen Code、OpenCode 为代表的开源力量则通过 ACP/AGENTS.md 等协议标准与 Daemon 后台架构寻求差异化突破。社区痛点高度趋同：长上下文计费混乱、Windows/Linux 终端稳定性、会话持久化与 AI 自动化的安全边界，标志着行业整体从“功能可用”向“生产级可靠”过渡。

---

### 2.

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

**Claude Code Skills 社区热点报告**  
*数据截止：2026-06-05*

---

### 1. 热门 Skills 排行（按社区关注度）

| 排名 | Skill | 功能简介 | 状态 | 链接 |
|---|---|---|---|---|
| 1 | **document-typography** | AI 生成文档的排版质量控制：修复孤字换行（orphan）、寡段标题（widow）、编号错位等通用排版问题，意图成为所有文档 Skill 的基线约束。 | Open | [#514](https://github.com/anthropics/skills/pull/514) |
| 2 | **odt** | OpenDocument 格式（.odt/.ods）的创建、模板填充及 HTML 转换，面向 LibreOffice 与 ISO 标准开源办公生态。 | Open | [#486](https://github.com/anthropics/skills/pull/486) |
| 3 | **frontend-design** | 对现有前端设计 Skill 的重构，提升单轮对话内指令的可执行性与清晰度，减少模糊描述。 | Open | [#210](https://github.com/anthropics/skills/pull/210) |
| 4 | **skill-quality-analyzer / skill-security-analyzer** | 元 Skill（Meta-Skill）：从结构、文档、安全等五维度自动评估 Skill 质量，被视为生态“自检工具”。 | Open | [#83](https://github.com/anthropics/skills/pull/83) |
| 5 | **agent-creator** | 任务专属 Agent 集生成器；同步修复 `evaluation.py` 多工具并行调用崩溃与 Windows `%APPDATA%` 路径支持。 | Open | [#1140](https://github.com/anthropics/skills/pull/1140) |
| 6 | **servicenow** | 企业级平台 Skill，覆盖 ITSM、SecOps、ITAM/SAM、FSM、IntegrationHub 等全模块，目前最全面的企业服务管理提案。 | Open | [#568](https://github.com/anthropics/skills/pull/568) |
| 7 | **AURELION suite** | 结构化认知 + 记忆框架，含 kernel（思维模板）、advisor、agent、memory 四个 Skill，面向专业知识管理。 | Open | [#444](https://github.com/anthropics/skills/pull/444) |
| 8 | **shodh-memory** | AI Agent 持久化记忆系统，通过 `proactive_context` 在每次用户消息时召回相关记忆，解决跨会话上下文丢失。 | Open | [#154](https://github.com/anthropics/skills/pull/154) |

---

### 2. 社区需求趋势（基于 Issues 提炼）

- **组织级共享与治理**：[#228](https://github.com/anthropics/skills/issues/228) 要求 org-wide Skill 库直接共享，取代手动传输 .skill 文件；[#492](https://github.com/anthropics/skills/issues/492) 揭露社区 Skill 冒用 `anthropic/` 命名空间的信任边界风险，官方身份验证与权限治理成为刚需。
- **基础设施协议化**：[#16](https://github.com/anthropics/skills/issues/16) 强烈呼吁将 Skills 暴露为 MCP（Model Context Protocol），推动 Skill 从“提示词包”向标准化 API 演进。
- **跨平台与企业集成**：[#29](https://github.com/anthropics/skills/issues/29)（AWS Bedrock）、[#568](https://github.com/anthropics/skills/pull/568)（ServiceNow）反映企业用户希望 Skill 无缝接入现有云与 SaaS 生态。
- **开发者工具链稳定性**：[#556](https://github.com/anthropics/skills/issues/556)、[#1099](https://github.com/anthropics/skills/pull/1099)、[#1050](https://github.com/anthropics/skills/pull/1050) 集中暴露 `run_eval.py` 在 Windows 下的触发失败与编码崩溃，评估与调试工具链的健壮性成为基础痛点。
- **模块化与可移植性**：[#1220](https://github.com/anthropics/skills/issues/1220) 提出多引用文件内联打包需求；[#1156](https://github.com/anthropics/skills/issues/1156) 讨论 Skill 可移植性标签的诚实性，社区希望 Skill 工程化程度提升。

---

### 3. 高潜力待合并 Skills

以下 Open PR 功能完整、讨论聚焦且解决明确痛点，预计近期具备较高合并概率：

- **document-typography** ([#514](https://github.com/anthropics/skills/pull/514))：通用文档质量兜底，影响所有文档生成场景，填补排版控制空白。
- **agent-creator + 多工具修复** ([#1140](https://github.com/anthropics/skills/pull/1140))：不仅新增元 Skill，还附带 `evaluation.py` 关键稳定性补丁与 Windows 兼容修复，属于“带补丁的新 Skill”。
- **odt** ([#486](https://github.com/anthropics/skills/pull/486))：填补开源文档格式空白，与现有 PDF/DOCX Skill 形成互补。
- **testing-patterns** ([#723](https://github.com/anthropics/skills/pull/723))

---

**Claude Code 社区动态日报**  
*2026-06-05*

---

### 1. 今日速览

今日社区焦点集中在 **AGENTS.md 行业标准统一** 的呼声（#6235 已突破 4,060+ 👍），同时 Anthropic 发布 **v2.1.163** 强化企业版本管控与插件管理能力；另一方面，**1M 上下文计费错误** 与 **模型 Tool Call 解析失败** 持续发酵，成为开发者体验的主要痛点。

---

### 2. 版本发布

**v2.1.163** 已发布，主要更新如下：

- **企业版本强制合规**：新增托管设置 `requiredMinimumVersion` 与 `requiredMaximumVersion`。若当前版本不在允许范围内，Claude Code 将拒绝启动并引导用户至批准的版本，便于企业 IT 统一管控。
- **插件管理增强**：新增 `/plugin list` 命令，支持列出已安装插件，并可通过 `--enabled` / `--disabled` 筛选状态。

---

### 3. 社区热点 Issues（Top 10）

| # | 标题 | 核心看点 | 链接 |
|---|------|---------|------|
| **#6235** | Feature Request: Support AGENTS.md | 社区最热需求。开发者呼吁支持行业统一的 `AGENTS.md` 标准（Codex、Amp、Cursor 已跟进），认为现有 `CLAUDE.md` 过于专属，不利于跨团队协作。**310 评论，4,060+ 👍** | [链接](https://github.com/anthropics/claude-code/issues/6235) |
| **#8327** | "Organization has been disabled" error when API key overrides Max/Pro subscription | 高活跃认证/计费 Bug。持有有效 Pro/Max 订阅的用户因 `ANTHROPIC_API_KEY` 环境变量覆盖导致被误判为禁用组织，文档与错误提示均不清晰。**117 评论** | [链接](https://github.com/anthropics/claude-code/issues/8327) |
| **#63060** | [BUG] API Error: Usage credits required for 1M context | 高频计费错误。用户在调用 1M 上下文时遭遇 "Usage credits required" 报错，与订阅预期不符，影响大模型长上下文工作流。**63 评论** | [链接](https://github.com/anthropics/claude-code/issues/63060) |
| **#62063** | [BUG] Defaults to 1M context on fresh session with no workaround on Pro plan | 体验断层。新会话默认锁定 1M 上下文，但 Pro 计划无 Usage Credits 导致直接报错，且缺乏降级开关。**54 评论，35 👍** | [链接](https://github.com/anthropics/claude-code/issues/62063) |
| **#62123** | [Bug] Model's tool call could not be parsed (retry also failed) | 模型稳定性危机。Opus 4.7 在 VS Code 等多平台频繁出现 Tool Call 解析失败且重试无效，任务直接中断。**45 评论，91 👍** | [链接](https://github.com/anthropics/claude-code/issues/62123) |
| **#33932** | [FEATURE] VS Code Extension: Diff review UI similar to GitHub Copilot Edits Review | IDE 体验对标。开发者希望 Claude Code VS Code 插件提供类似 Copilot 的 Diff 审查界面，而非逐文件确认。**18 评论，81 👍** | [链接](https://github.com/anthropics/claude-code/issues/33932) |
| **#31888** | Add batch diff review mode: show all changes together before approval | 工作流效率。请求增加 Cursor 式的批量 Diff 审查模式，避免在大型重构中频繁切换文件确认。**8 评论，17 👍** | [链接](https://github.com/anthropics/claude-code/issues/31888) |
| **#36497** | `.claude/skills/` edits prompt for permission despite being documented as exempt | 回归 Bug。v2.1.79 起，`.claude/skills/` 目录编辑触发权限询问，与文档声明的豁免规则矛盾，影响 Skills 自动化。**8 评论，10 👍** | [链接](https://github.com/anthropics/claude-code/issues/36497) |
| **#65051** | Background sessions drop assistant text blocks from transcript (regression 2.1.160 → 2.1.161) | 数据完整性回归。后台 Daemon 会话中，助手文本块在混合 tool_use 响应时丢失，影响审计与上下文连续性。**2 评论** | [链接](https://github.com/anthropics/claude-code/issues/65051) |
| **#65522** | 'Pull request status couldn't be checked' warning fires on every non-GitHub remote | UX 干扰。使用 GitLab、Bitbucket 等非 GitHub 远程仓库时，每次交互都弹出 PR 状态检查警告，无法静默。**2 评论** | [链接](https://github.com/anthropics/claude-code/issues/65522) |

---

### 4. 重要 PR 进展

过去 24 小时共 5 个 PR 更新，其中值得关注的有：

| # | 标题 | 功能/修复内容 | 链接 |
|---|------|--------------|------|
| **#65344** | fix(scripts): correct premature return in markStale and add --debug flag | 修复 `scripts/sweep.ts` 中分页遍历 Issue 时的过早 `return` 逻辑错误；为 `auto-close-duplicates.ts` 增加 `--debug` 标志，提升运维脚本可观测性。 | [链接](https://github.com/anthropics/claude-code/pull/65344) |
| **#44742** | fix: diagnostic tool + root cause analysis for session persistence data loss | **已合并**。针对 VS Code 扩展会话历史丢失的关键 Bug（影响 12+ 重复 Issue），新增 `diagnose-session-persistence.ts` 诊断脚本，帮助用户定位持久化失败根因。 | [链接](https://github.com/anthropics/claude-code/pull/44742) |
| **#65286** | fix(plugins): add missing plugin.json manifest for plugin-dev | 补充 `plugin-dev` 插件缺失的 `.claude-plugin/plugin.json` 清单文件，修复通过标准机制发现与安装该插件的问题。 | [链接](https://github.com/anthropics/claude-code/pull/65286) |
| **#65314** | scripts: add detect-theme-color-issues | 新增分类脚本，自动扫描浅色终端主题下文字不可读的 Issue，并将其归类到已知的 `color7`/`color0` 冲突问题族，减少重复工单。 | [链接](https://github.com/anthropics/claude-code/pull/65314) |

---

### 5. 功能需求趋势

从今日 Issue 分布可提炼出以下四大社区关注方向：

1. **跨 Agent 标准化**：`AGENTS.md` 的支持请求热度断层领先，反映出开发者对跨工具（Claude / Cursor / Codex）统一项目上下文配置的强烈需求，不愿被锁定在单一工具生态。
2. **IDE 深度集成**：VS Code 侧的 Diff Review、批量变更确认、远程会话机器标识等需求密集出现，社区希望 Claude Code 在编辑器内的体验能对标 GitHub Copilot 与 Cursor。
3. **成本与配额透明化**：围绕 1M 上下文窗口的 "Usage Credits" 报错、Pro/Max 计划与 API Key 的权限冲突 Issue 占据高评论区，说明计费策略与错误提示亟需澄清。
4. **企业级治理与自动化**：版本强制合规（v2.1.163 已响应）、插件生命周期管理、自动分支创建的可控性，显示团队级部署场景下的治理需求正在上升。

---

### 6. 开发者关注点

综合过去 24 小时的反馈，开发者当前的核心痛点与高频需求如下：

- **计费模型混乱**：Pro/Max 订阅与 `ANTHROPIC_API_KEY` 的优先级冲突、1M 上下文突然要求 Usage Credits、新会话默认高配额且无降级路径，导致生产环境频繁中断。
- **模型输出可靠性**：`The model's tool call could not be parsed` 在 Opus 4.7 上高频复现，且重试机制失效，严重破坏自动化工作流信任度。
- **自动化行为可控性**：自动创建分支、`.claude/skills/` 目录的权限回退、非 GitHub 仓库的无效警告，均反映出开发者对“静默自动化”边界的敏感。
- **跨平台稳定性**：Windows 11 下 Cowork VM Service 启动失败、大容量文件系统（>17.6 TB）的 `statfs` 32 位截断误报、后台会话文本块丢失等，显示边缘场景的质量保障仍需加强。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex 社区动态日报**  
*2026-06-05*

---

### 1. 今日速览
今日社区焦点集中在 **macOS 系统级稳定性危机**（`syspolicyd` 文件描述符泄漏与主进程循环启动导致系统冻结）以及 **Windows 桌面端多项体验缺陷**（沙盒、插件、窗口渲染）。CLI 侧连续发布 Rust `v0.138.0` 系列 alpha 版本；代码库方面，开发团队正密集推进 Responses Lite、跨平台沙盒策略与远程控制配对等底层能力。

---

### 2. 版本发布
- **Rust CLI v0.138.0-alpha.1 ~ alpha.4**  
  过去 24 小时内连续发布 4 个 alpha 版本，版本号从 `alpha.1` 迭代至 `alpha.4`。目前 Release Note 仅列出版本号，建议开发者关注后续详细变更日志，预计涉及 Codex CLI 核心运行时或 Rust 依赖更新。  
  链接: [v0.138.0-alpha.4](https://github.com/openai/codex/releases/tag/rust-v0.138.0-alpha.4)

---

### 3. 社区热点 Issues（精选 10 条）

| # | 标题 | 重要性 & 社区反应 |
|---|------|------------------|
| **#11023** | [Codex desktop app for Linux](https://github.com/openai/codex/issues/11023) | **社区第一高赞需求**（👍 476 / 评论 97）。Linux 桌面版长期缺位，大量开发者因 macOS 功耗问题希望在 Linux 工作站使用原生应用，呼声极高。 |
| **#20741** | [Codex Desktop project chat histories disappeared after recent update](https://github.com/openai/codex/issues/20741) | **数据丢失级 Bug**（评论 26）。macOS 用户更新后项目聊天记录消失，涉及用户核心资产，社区情绪紧张。 |
| **#25882** | [Codex macOS app relaunches its own main binary in a tight loop, exhausting syspolicyd file descriptors and freezing all app launches system-wide](https://github.com/openai/codex/issues/25882) | **系统级灾难**（评论 12）。应用反复自启导致系统级文件描述符耗尽，波及整个 macOS 应用启动，严重性极高。 |
| **#25719** | [Codex Desktop for macOS repeatedly triggers `syspolicyd` / `trustd` CPU and memory runaway](https://github.com/openai/codex/issues/25719) | **性能灾难**（评论 15 / 👍 13）。与 #25882 同源，持续触发系统安全守护进程，导致 CPU 与内存失控。 |
| **#25715** | [Codex App is Unusable Slow with WSL as Agent environment](https://github.com/openai/codex/issues/25715) | **开发环境阻塞**（评论 21 / 👍 22）。Windows + WSL 场景下常规交互耗时 30-60 秒，严重影响 Windows 开发者生产力。 |
| **#24391** | [Windows sandbox: spawn setup refresh fails on Codex CLI 0.133.0](https://github.com/openai/codex/issues/24391) | **CLI 核心功能受阻**（评论 22 / 👍 22）。Windows 沙盒初始化失败，导致 shell 命令无法执行，阻断工作流。 |
| **#25220** | [Windows Bundled plugins unavailable — copyfile fails on EFS-encrypted WindowsApps files](https://github.com/openai/codex/issues/25220) | **核心功能缺失**（评论 12）。Computer Use、Browser 等捆绑插件因 EFS 加密无法复制，Windows 用户完全丧失插件能力。 |
| **#20683** | [Computer Use crashes SkyComputerUseService when inspecting Outlook on macOS](https://github.com/openai/codex/issues/20683) | **生产力工具崩溃**（评论 11）。Computer Use 在检查 Outlook 时崩溃，影响自动化办公场景稳定性。 |
| **#22851** | [Codex mobile pairing stuck on Waiting for desktop when remote-control daemon cannot use proxy](https://github.com/openai/codex/issues/22851) | **跨端协作受阻**（评论 10）。移动端与桌面端配对在代理环境下卡住，远程开发场景体验断裂。 |
| **#21073** | [Feature Request: Auto-resume CLI session when usage limit resets](https://github.com/openai/codex/issues/21073) | **高赞体验优化**（👍 9 / 评论 6）。请求在用量限制重置后自动恢复 CLI 会话，解决夜间/无人值守任务中断痛点。 |

---

### 4. 重要 PR 进展（精选 10 条）

| # | 标题 | 功能或修复内容 |
|---|------|---------------|
| **#26490** | [Use standalone tools for Responses Lite](https://github.com/openai/codex/pull/26490) | 为 Responses Lite 模式引入独立工具执行器，将网页搜索与图像生成路由至 Codex 自有执行器，绕过托管 Responses 工具限制。 |
| **#26499** | [core: derive exec policy filesystem policy from profile](https://github.com/openai/codex/pull/26499) | 将执行策略的文件系统沙盒策略统一从 `PermissionProfile` 派生，消除生产权限模型与测试/调用方之间的状态分裂。 |
| **#26023** | [Add managed macOS sandbox capabilities](https://github.com/openai/codex/pull/26023) | 为托管权限配置添加类型化的 macOS Seatbelt 沙盒能力，支持在运行时权限转换中保留并下发生效。 |
| **#26307** | [Respect Windows sandbox backend in exec policy](https://github.com/openai/codex/pull/26307) | 修复 Windows 托管文件系统权限在存在真实沙盒后端时的误判，解决如 PowerShell 目录列表被错误拦截的问题。 |
| **#26500** | [Open Windows app workspaces via deep link](https://github.com/openai/codex/pull/26500) | Windows 端 `codex app PATH` 现在通过 `codex://threads/new?path=...` 深度链接直接打开工作区，不再仅打印手动指令。 |
| **#26496** | [Make auto-review on-request prompt more proactive](https://github.com/openai/codex/pull/26496) | 优化 `on-request` 自动审查策略，使需要外网、认证或沙盒外访问的命令更早被识别并升级，减少失败/挂起。 |
| **#26259** | [Add advisory Interrupt hooks for interrupted turns](https://github.com/openai/codex/pull/26259) | 为被中断的 Turn 新增 advisory-only `Interrupt` 钩子，允许处理器发送系统消息，但不可阻塞或改变中断路径。 |
| **#25147** | [Retry streamable HTTP initialize failures](https://github.com/openai/codex/pull/25147) | 针对 RMCP 启动时的流式 HTTP 初始化请求及 `tools/list` 调用增加瞬态失败重试，覆盖可重试 HTTP 状态码与请求层失败。 |
| **#26479** | [Speed up local nextest runs](https://github.com/openai/codex/pull/26479) | 为本地 `just test` 引入有界并行度，在开发者机器上安全并发运行 app-server 集成测试，显著缩短本地测试耗时。 |
| **#26488** | [Treat app-bundled plugin hooks as internal](https://github.com/openai/codex/pull/26488) | 将桌面应用捆绑插件的钩子标记为 durable internal 分类，防止应用退出后通过独立 CLI 运行时分类被伪造。 |

---

### 5. 功能需求趋势
从过去 24 小时 Issues 分布可提炼出社区最关注的五大方向：

1. **Linux 原生桌面支持**  
   以 #11023 为代表，高赞长期需求未解，开发者希望在 Linux 工作站获得与 macOS/Windows 同等体验。
2. **Windows 生态深度适配**  
   涵盖 WSL 性能、沙盒初始化、EFS 加密兼容、窗口管理、企业网络策略等，Windows 已成为当前 Bug 报告最密集的平台。
3. **性能与系统资源治理**  
   macOS 上 `syspolicyd`/`trustd` 失控、文件描述符泄漏、内存只增不减（#26015）等问题，反映出社区对系统级资源占用的焦虑。
4. **会话持久化与可靠性**  
   聊天记录丢失（#20741）、CLI 用量限制后自动恢复（#21073）表明用户对长时任务和数据安全的强需求。
5. **Computer Use / 浏览器自动化稳定性**  
   截图失败、插件不可用、Outlook 崩溃、Chrome URL 读取失败等问题，显示桌面自动化能力在跨平台落地时仍显脆弱。

---

### 6. 开发者关注点
- **macOS 系统稳定性已成“红色警报”**：`syspolicyd` 文件描述符泄漏（#25243、#25719、#25882）不仅是 Codex 自身 Bug，已升级为可冻结整个操作系统的系统级事件，开发者迫切要求官方给出诊断工具与热修复。
- **Windows 桌面端质量门槛**：从安装（Microsoft Store/EFS 加密导致插件复制失败）到运行（最大化渲染异常、内存泄漏、WSL 桥接延迟），Windows 用户体验存在明显断层。
- **数据主权焦虑**：聊天记录无故消失（#20741）与闲置时用量异常消耗（#24818）引发用户对云端同步策略与本地缓存机制的不信任。
- **企业/复杂网络环境适配**：代理穿透（#22851）、企业网络策略拦截（#24814）以及 OAuth 令牌生命周期管理（#26482）是 B 端开发者高频卡点。
- **CLI 与 Desktop 的能力对齐**：CLI 自动恢复、沙盒策略一致性、插件钩子生命周期等底层工程，正成为从“能用”走向“生产可用”的关键分水岭。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI 社区动态日报 | 2026-06-05**

---

### 1. 今日速览

今日社区重点围绕**终端稳定性与企业级部署**展开。v0.45.1 补丁发布修复特定分支问题，同时大量 PR 集中解决 WSL/Windows PTY 兼容性、SSRF 安全防护及 A2A 任务持久化等核心问题。Issues 侧显示符号链接跳过、HDD 启动性能及静默模型回退仍是用户高频痛点。

---

### 2. 版本发布

- **v0.47.0-nightly.20260604.g4196596f7**  
  主要更新 CI 流程：新增优化的 PR 大小标签器与批处理工作流，并修复 fork PR 的写入权限问题（改用 `pull_request_target` 触发器）。  
  [→ Release 详情](https://github.com/google-gemini/gemini-cli/releases/tag/v0.47.0-nightly.20260604.g4196596f7)

- **v0.45.1**  
  补丁版本，将提交 `665228e` cherry-pick 到 `release/v0.45.0-pr-27570` 分支，修复 v0.45.0 的特定问题。  
  [→ Release 详情](https://github.com/google-gemini/gemini-cli/releases/tag/v0.45.1)

---

### 3. 社区热点 Issues

| # | 标题 | 重要性说明 | 社区反应 |
|---|------|-----------|---------|
| [#22171](https://github.com/google-gemini/gemini-cli/issues/22171) | BFS 与 grep 工具静默跳过符号链接 | **P1 Core Bug**：在大量使用 symlink 的项目中，CLI 无法发现链接的 `GEMINI.md` 与文档，导致上下文缺失。 | 10 条讨论，已关闭 |
| [#24264](https://github.com/google-gemini/gemini-cli/issues/24264) | 无法连接任何模型，请求永久卡住 | **企业阻塞问题**：用户完全无法使用任何模型，无错误提示，严重影响工作流。 | 6 条讨论，5 👍 |
| [#21662](https://github.com/google-gemini/gemini-cli/issues/21662) | HDD 冷启动耗时 77 秒 | **P1 性能灾难**：机械硬盘用户遭遇数十秒启动延迟，反映 I/O 密集型初始化逻辑需优化。 | 5 条讨论 |
| [#24039](https://github.com/google-gemini/gemini-cli/issues/24039) | `MODEL_CAPACITY_EXHAUSTED` 时静默回退模型 | **关键 UX 缺陷**：用户显式固定模型后，服务端 429 导致 CLI 静默切换模型，破坏可预期性。 | 5 条讨论，3 👍 |
| [#27334](https://github.com/google-gemini/gemini-cli/issues/27334) | Windows 嵌入式终端后台进程后冻结/闪烁 | **P1 Windows 稳定性**：执行本地构建或进程管理命令后终端假死，阻碍 Windows 开发者使用。 | 5 条讨论 |
| [#27155](https://github.com/google-gemini/gemini-cli/issues/27155) | PTY 内存与文件描述符泄漏 | **技术债务**：`ShellExecutionService` 中长期运行的 MCP 服务器无法被 GC，导致资源耗尽。 | 4 条讨论 |
| [#24098](https://github.com/google-gemini/gemini-cli/issues/24098) | `/copy` 命令后输入无响应 | **日常 UX 摩擦**：复制成功后输入框残留 `/copy` 文本且无法交互，影响高频操作。 | 7 条讨论 |
| [#21597](https://github.com/google-gemini/gemini-cli/issues/21597) | Mercurial 仓库根目录检测失败 | **企业场景缺口**：CLI 强制依赖 `.git` 目录锚定本地策略，导致 Hg 仓库配置加载不完整。 | 7 条讨论 |
| [#27164](https://github.com/google-gemini/gemini-cli/issues/27164) | 代理搜索递归扫描 `.gemini/tmp/` | **自我引用反馈循环**：代理搜索自身会话日志导致上下文递归膨胀，极具代表性。 | 3 条讨论 |
| [#24954](https://github.com/google-gemini/gemini-cli/issues/24954) | 文件更新时关键数据丢失与未授权代码删除 | **Agent 安全**：代理擅自将功能代码替换为文本摘要，引发对自动编辑信任度的担忧。 | 3 条讨论 |

---

### 4. 重要 PR 进展

| # | 标题 | 功能/修复内容 |
|---|------|--------------|
| [#27335](https://github.com/google-gemini/gemini-cli/pull/27335) | 修复 web-fetch 工具开放重定向导致的 SSRF | **安全加固**：`fetchWithTimeout` 原只校验初始 URL，现增加重定向目标拦截，防止内网元数据服务被窃取。 |
| [#27341](https://github.com/google-gemini/gemini-cli/pull/27341) | 剥离 `functionCall.id` / `functionResponse.id` 后再调用 API | **Bug 修复**：解决工具调用后报 "Unknown name 'id'" 400 错误的问题，内部渲染 ID 不再透传 Gemini API。 |
| [#27354](https://github.com/google-gemini/gemini-cli/pull/27354) | WSL 环境下运行 Windows 可执行文件时绕过 node-pty | **兼容性**：针对 WSL 中 Linux PTY 与 Windows `.exe` 互操作异常，自动降级为标准 `child_process`。 |
| [#27348](https://github.com/google-gemini/gemini-cli/pull/27348) | `Ajv validate()` 增加 try/catch 防止畸形 schema 崩溃 | **健壮性**：避免 LLM 发送异常参数形状

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI 社区动态日报**  
*日期：2026-06-05 | 仓库：github.com/github/copilot-cli*

---

### 1. 今日速览
GitHub Copilot CLI 发布 **v1.0.60-0**，新增 AI 计费概览帮助主题与 vim 风格 diff 导航；社区持续聚焦跨平台复制粘贴失效、会话恢复后认证丢失，以及 Windows 平台控制台句柄严重回归问题。

---

### 2. 版本发布：v1.0.60-0
过去24小时发布预发布版本 `v1.0.60-0`，主要更新包括：
- **新增 `billing` 帮助主题**：提供 AI credit 使用功能概览。
- **vim 风格导航**：在 `/diff` 视图中支持 `g`、`G`、`Ctrl+D`、`Ctrl+U` 跳转。
- **Mission Control 集成**：在 `/session info` 中展示已同步会话的分享状态。
- **快捷参数**：`-r` 作为 `--resume` 的简写。
- **LSP 服务器配置**：新增相关配置能力（详情待文档补充）。

---

### 3. 社区热点 Issues（精选10条）

| # | 状态 | 标题 | 重要性说明 | 链接 |
|---|------|------|------------|------|
| **2082** | 🔴 OPEN | Linux 终端 `ctrl+shift+c` 无法复制 | 影响 Ubuntu 等主流发行版的基础交互，19条评论为今日最热。 | [链接](https://github.com/github/copilot-cli/issues/2082) |
| **2398** | 🔴 OPEN | 支持默认权限配置文件 | 高赞（10👍）功能请求，解决每次会话重复配置权限的痛点。 | [链接](https://github.com/github/copilot-cli/issues/2398) |
| **3596** | 🔴 OPEN | 恢复会话后 `/model` 报 `Not authenticated` | 恢复会话后认证状态丢失，8👍，严重影响长会话工作流。 | [链接](https://github.com/github/copilot-cli/issues/3596) |
| **3260** | 🔴 OPEN | SSH + tmux 场景下复制粘贴失效 | 跨平台复杂终端场景（macOS/Linux → Windows Server 2025），远程开发受阻。 | [链接](https://github.com/github/copilot-cli/issues/3260) |
| **3659** | 🔴 OPEN | 插件自带的 hooks 无法执行 | v1.0.57+ 引入的插件生态阻塞问题，影响治理与安全审计 hook。 | [链接](https://github.com/github/copilot-cli/issues/3659) |
| **3677** | 🔴 OPEN | Claude Opus 1M 上下文被误判为 128K | 长上下文模型能力未充分利用，导致过早触发 compaction，影响长代码分析。 | [链接](https://github.com/github/copilot-cli/issues/3677) |
| **3683** | 🔴 OPEN | Windows PowerShell 丢失控制台句柄 | v1.0.57+ 严重回归，`Clear-Host` 与 MSAL 交互认证均失效。 | [链接](https://github.com/github/copilot-cli/issues/3683) |
| **3636** | 🔴 OPEN | 企业 VPN 下语音模式无法启用 | 模型目录获取被 corporate VPN 拦截，反映企业网络兼容性痛点。 | [链接](https://github.com/github/copilot-cli/issues/3636) |
| **3666** | 🟢 CLOSED | 复制换行输出导致空格丢失 | 终端渲染问题（如 `var c` 变成 `varc`），已关闭表明团队已快速修复。 | [链接](https://github.com/github/copilot-cli/issues/3666) |
| **3676** | 🟢 CLOSED | `/session` 不再列出其他会话 | v1.0.59 回归，已快速关闭，显示会话管理模块的迭代响应。 | [链接](https://github.com/github/copilot-cli/issues/3676) |

---

### 4. 重要 PR 进展
过去24小时仓库仅更新 **2条 PR**，且无有效功能合并或修复。当前开放的 PR 均为非相关提交，社区维护者尚未清理：

- **#3651** `Create xcopilotcli`（[@XavierMP14](https://github.com/XavierMP14)）— 空内容提交，疑似测试或误操作。  
  [链接](https://github.com/github/copilot-cli/pull/3651)

- **#3473** `Update project name in README...`（[@CPU-UMS9230E-T7250](https://github.com/CPU-UMS9230E-T7250)）— 包含外部广告链接（TEMU），为垃圾 PR。  
  [链接](https://github.com/github/copilot-cli/pull/3473)

> **建议**：今日重点关注 Issues 区域动态，PR 侧无有效代码贡献进展。

---

### 5. 功能需求趋势
从过去24小时35条活跃 Issue 中，社区最关注的五大方向如下：

1. **会话与认证可靠性**  
   恢复会话后认证失效（#3596、#3680）、BYOK 凭证热刷新（#3682）成为高频痛点，显示长会话管理与凭证生命周期是核心摩擦点。

2. **跨平台终端体验**  
   Linux/Windows/SSH/tmux 场景下的复制粘贴（#2082、#3260）及键盘交互（#3667）问题集中爆发，终端兼容性仍是基础体验瓶颈。

3. **企业级部署兼容**  
   BYOK Azure OpenAI 重试策略（#3679）、

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI 社区动态日报**  
*2026-06-05*

---

### 1. 今日速览
过去 24 小时，社区集中爆发 **403 模型访问权限错误**（`Kimi For Coding is currently only available for Coding Agents`），影响 k2.6 及 kimi-for-coding 模型的正常使用，成为最高优先级故障。与此同时，社区贡献者提交了针对 **Linux 终端滚动自动回底** 问题的修复 PR。此外，性能下降与服务端 `engine overloaded` 的反馈也显著增加。

---

### 2. 版本发布
今日无新版本发布。

---

### 3. 社区热点 Issues
（过去 24 小时共更新 7 条，以下按影响面与紧急度排序）

| # | 状态 | 标题 | 作者 | 社区反应 | 链接 |
|---|------|------|------|----------|------|
| **2425** | OPEN | [bug] 403 Kimi For Coding is currently only available for Coding Agents... | @zhongyr | 🔥 **最高热度**，10 条评论，3 👍。v0.9.0 / macOS，所有消息返回 403，权限校验逻辑疑似异常。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2425) |
| **2427** | OPEN | [bug] Getting "Kimi For Coding is currently only available for Coding Agents" | @fzyz999 | 2 条评论。v1.46.0 / Debian WSL2，使用 k2.6 时复现相同 403，确认问题非个例且跨版本存在。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2427) |
| **2424** | OPEN | [bug] Getting "engine overloaded" with the 2.5 model | @iaindooley | 0 评论。v1.46.0 / Debian 13，过去两天 k2.5 频繁触发引擎过载，反映服务端算力/调度压力。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2424) |
| **2423** | OPEN | [bug] Latest versions are far slower | @lnsy-dev | 0 评论。v1.46.0 / Linux ARM64，反馈最新版本响应速度显著下降，存在性能回归。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2423) |
| **2422** | OPEN | [bug] 对话完成后滚动查看输出内容会自动调到底部 | @venus0707 | 1 条评论。v1.46.0 / Linux，长输出后向上滚动被强制拉回底部，严重影响历史查阅。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2422) |
| **2428** | OPEN | [bug] '/title' not available in VS Code Kimi Code extension | @Seuchezz | 0 评论。v1.46.0 / Linux，VS Code 扩展中 `/title` 命令不可用，IDE 集成功能缺失。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2428) |
| **2430** | CLOSED | [bug] auto logged out in the middle of a task | @TheKevinWang | 0 评论。v1.36.0 / Windows 10，任务中途自动登出导致会话中断，目前已被关闭。 | [链接](https://github.com/MoonshotAI/kimi-cli/issues/2430) |

---

### 4. 重要 PR 进展
（过去 24 小时共更新 6 条，均为社区贡献的修复类 PR）

| # | 状态 | 标题 | 作者 | 功能/修复摘要 | 链接 |
|---|------|------|------|---------------|------|
| **2429** | OPEN | fix: prevent idle cursor blink from forcing scroll to bottom in Linux terminals | @GH-ytym | 修复 Linux 终端下光标闪烁周期性强制滚动至底部的问题（Resolve #2422），改善长输出阅读体验。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2429) |
| **2388** | OPEN | fix(shell): persist pasted text placeholders | @Pluviobyte | 解决长文本粘贴后的 `[Pasted text #1]` 占位符在会话历史召回后丢失的问题（Resolve #1946），确保上下文可读性。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2388) |
| **2387** | OPEN | fix(tools): preserve shell command headline details | @Pluviobyte | 避免 Shell 命令 headline 被过度截断（Resolve #2142），保留更多命令细节便于终端审计。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2387) |
| **2386** | OPEN | fix(session): map undo wire turns to context turns | @Pluviobyte | 修复 `/undo` 和 fork 操作因使用 wire 索引截断上下文导致的错位问题（Resolve #1974, #2049）。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2386) |
| **2383** | OPEN | fix(soul): repair orphan tool_calls when replaying history | @Pluviobyte | 处理会话被强制终止（OOM、`kill -9` 等）后，历史回放中残留的孤儿 `tool_calls` 损坏状态（Resolve #2336）。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2383) |
| **2382** | OPEN | fix(file): convert unsupported image formats to PNG in ReadMediaFile | @Pluviobyte | 读取 `.ico` 等不支持的图片格式时自动转为 PNG（Resolve #2017），兼容 Kimi/Anthropic/Google 等 provider 限制。 | [链接](https://github.com/MoonshotAI/kimi-cli/pull/2382) |

---

### 5. 功能需求趋势
从今日 Issues 与近期 PR 方向可提炼出以下社区关注焦点：

- **模型服务稳定性与权限策略**：403 访问限制与 `engine overloaded` 成为首要痛点，开发者迫切关注 k2.5/k2.6 模型的可用性与服务端状态。
- **性能回归**：v1.46.0 及近期版本被多次反馈响应变慢，性能优化是持续需求。
- **跨平台终端体验**：Linux 下的滚动行为、光标闪烁、VS Code 扩展功能对齐等交互细节优化需求集中。
- **会话状态可靠性**：自动登出、undo 逻辑准确性、异常退出后的历史恢复，反映出长会话场景对数据持久化的高要求。

---

### 6. 开发者关注点
- **403 权限故障排查**：错误提示与实际使用场景（Kimi CLI 本身就是 Coding Agent）存在矛盾，开发者需要官方尽快澄清模型访问策略或修复权限校验逻辑。
- **性能下降根因**：从 v1.36.0 到 v1.46.0，部分用户感知到明显降速，需关注是否与新模型上下文窗口、工具调用开销或网络层改动有关。
- **终端 UX 细节**：Linux 终端的滚动回底、命令标题截断、粘贴占位符丢失等“小毛病”累积，显著影响专业开发者的使用流。
- **数据持久化与容错**：会话异常退出后的状态恢复、undo 的准确性、历史回放一致性，反映出开发者对长会话可靠性的高要求。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

**OpenCode 社区动态日报**  
*2026-06-05*

---

### 1. 今日速览
过去 24 小时无新版本发布，但核心贡献者 @kitlangton 密集推进了 V2 会话架构、公共 Native API 及全局工具挂载等底层改进。与此同时，社区对 Windows 终端稳定性、长对话上下文丢失、提示注入安全漏洞及订阅计费透明度的讨论显著升温，多个高赞 Issue 已进入修复 pipeline。

---

### 3. 社区热点 Issues

| # | 标题 | 状态 | 核心看点 |
|---|------|------|----------|
| [#20695](https://github.com/anomalyco/opencode/issues/20695) | Memory Megathread | 🔥 OPEN | 社区内存问题总帖，90 条评论。维护者呼吁用户提交 heap snapshot 以定位泄漏，明确拒绝 LLM 生成的“伪解决方案”。 |
| [#28846](https://github.com/anomalyco/opencode/issues/28846) | Adjust Go usage limits after DeepSeek V4 Pro 75% price reduction | ✅ CLOSED | 74 👍。DeepSeek V4 Pro 永久降价后，用户要求同步调整 OpenCode Go 订阅用量限制，已关闭说明已响应。 |
| [#27589](https://github.com/anomalyco/opencode/issues/27589) | TUI fails on Alpine Linux (musl) in 1.14.50 | 🔥 OPEN | 27 评论。`getcontext` 符号缺失导致 TUI 在 musl 环境崩溃，属于 1.14.48→1.14.50 的回归，影响容器化部署。 |
| [#27530](https://github.com/anomalyco/opencode/issues/27530) | Error: 4 of 5 requests failed: Unexpected server error | 🔥 OPEN | 26 评论。启动时配置提供者批量失败，阻塞正常使用，社区正在收集服务端日志定位根因。 |
| [#1168](https://github.com/anomalyco/opencode/issues/1168) | Feature Request: Make Links Clickable | 🔥 OPEN | 91 👍。高赞体验需求，希望在 TUI 中支持 Ctrl+点击打开 URL，长期未实现但呼声极高。 |
| [#30811](https://github.com/anomalyco/opencode/issues/30811) | Code quality gets worse as conversations get longer | 🔥 OPEN | 6 评论。系统梳理了长对话劣化的 5 大根因：compaction 丢上下文、无自动验证、token 估算偏差等，引发广泛共鸣。 |
| [#30799](https://github.com/anomalyco/opencode/issues/30799) | Prompt injection via `<system-reminder>` tags | 🔥 OPEN | 3 评论。文件内容未过滤系统标签，存在提示注入风险，属于代码级安全漏洞。 |
| [#27749](https://github.com/anomalyco/opencode/issues/27749) | `/exit` or `/quit` kills the terminal on Windows PowerShell | 🔥 OPEN | 6 评论。Windows 下退出 TUI 直接关闭整个终端窗口而非返回 shell，严重影响 PowerShell 用户工作流。 |
| [#17169](https://github.com/anomalyco/opencode/issues/17169) | Subagent enters infinite retry loop on edit/write tool failure | 🔥 OPEN | 4 评论。子代理工具失败后无限重试，单次调用可导致 $15+ API 费用，成本失控风险极高。 |
| [#12789](https://github.com/anomalyco/opencode/issues/12789) | The requested model is not supported | 🔥 OPEN | 16 评论。GitHub Copilot 提供者下 Claude 模型无法使用，Gemini 表现异常，模型兼容性持续困扰用户。 |

---

### 4. 重要 PR 进展

| # | 标题 | 类型 | 内容摘要 |
|---|------|------|----------|
| [#30832](https://github.com/anomalyco/opencode/pull/30832) | feat(core): attach global native tools | 新功能 | 允许嵌入应用通过 `@opencode-ai/core/public` 定义同进程 Native Tool 并动态挂载到运行中的 OpenCode 实例。 |
| [#30789](https://github.com/anomalyco/opencode/pull/30789) | feat(core): persist v2 session context epochs | 新功能 | 持久化 V2 Session 的精确系统上下文，避免每次重启或轮次后重建特权上下文时出现差异。 |
| [#30836](https

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

**Qwen Code 社区动态日报**  
*2026-06-05*

---

### 1. 今日速览

今日社区发布 `v0.17.1-nightly` 版本，紧急修复了 `/copy` 命令误复制内部思考块的问题。同时，Daemon 模式迎来大规模合并（#4490，46 commits / 386 files），标志着 ACP 协议与 Daemon 架构正加速进入主分支。开发者对背景 Agent（`/fork`）、跨会话统计（`/stats`）及全局记忆的需求显著升温。

---

### 2. 版本发布

**v0.17.1-nightly.20260605.715266537**  
- **修复**：CLI 的 `/copy` 输出现在会跳过模型的内部 thought 片段，仅复制用户可见内容，避免粘贴时混入推理过程。  
[查看 Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.17.1-nightly.20260605.715266537)

---

### 3. 社区热点 Issues

| Issue | 状态 | 核心看点 |
|-------|------|----------|
| **[#4758](https://github.com/QwenLM/qwen-code/issues/4758)** Background auto-update replaces chunks mid-session, breaking cross-authType model switching | **OPEN** | **稳定性痛点**：后台自动更新在会话中途替换 `chunks/` 目录，导致跨 authType 切换模型时模块找不到而崩溃。影响使用 OpenRouter 或多厂商密钥的开发者。 |
| **[#4777](https://github.com/QwenLM/qwen-code/issues/4777)** Deferred-tools listing in the system prompt busts prompt cache on every MCP discovery | **OPEN** | **性能回归**：MCP deferred tools 被写入缓存的系统提示，每次 MCP 发现或工具 reveal 都会使 prompt cache 失效，直接增加 token 成本和延迟。 |
| **[#4597](https://github.com/QwenLM/qwen-code/issues/4597)** feat(stats): 增强 stats 能力，支持跨 session 的全局用量统计，参考 Claude Code | **OPEN** | **高频功能请求**：社区希望 `/stats` 能持久化到 `~/.qwen/usage-history.json`，提供跨会话的交互式仪表盘，而非仅内存中的当前会话数据。 |
| **[#4747](https://github.com/QwenLM/qwen-code/issues/4747)** Feature: Support global user-level auto-memory at ~/.qwen/memories/ | **OPEN** | **生态对齐**：要求像 Claude 一样支持跨项目的全局用户记忆，避免每个新项目都重新学习用户偏好。 |
| **[#4757](https://github.com/QwenLM/qwen-code/issues/4757)** feat(cli): make /fork spawn a background fork agent | **OPEN** | **新功能方向**：希望 `/fork` 不再是 `/branch` 的别名，而是真正派生一个后台 Agent 异步执行任务，不阻塞主会话。 |
| **[#4723](https://github.com/QwenLM/qwen-code/issues/4723)** Does Qwen Code support Rules or Instructions now? | **OPEN** | **配置体验**：开发者询问是否支持类似 Claude Code Rules 或 Copilot Instructions 的跨会话指令系统，用于统一代码风格和行为约束。 |
| **[#4783](https://github.com/QwenLM/qwen-code/issues/4783)** About aes-128-ecb | **OPEN** | **安全质疑**：社区对使用 AES-128-ECB 模式提出担忧，询问是否存在替换方案或强耦合原因，需维护者回应加密策略。 |
| **[#4772](https://github.com/QwenLM/qwen-code/issues/4772)** Desktop: Cannot send message after pressing Escape and re-editing input | **OPEN** | **Desktop 体验**：按 Escape 取消输入后重新编辑，消息无法发送，阻碍桌面端交互流畅性。 |
| **[#4754](https://github.com/QwenLM/qwen-code/issues/4754)** `/model` should not persist to settings by default | **CLOSED** | **UX 改进**：`/model` 临时切换模型不应默认写入 `settings.json`，避免下次启动意外沿用。社区共识明确，已快速关闭。 |
| **[#4712](https://github.com/QwenLM/qwen-code/issues/4712)** /bug, /docs, /insight crash with spawn xdg-open ENOENT on headless Linux | **OPEN** | **兼容性**：在无桌面环境的 Linux/SSH/容器中使用 `/bug` 等命令会因调用 `xdg-open` 而崩溃，影响服务器端使用场景。 |

---

### 4. 重要 PR 进展

| PR | 状态 | 功能/修复摘要 |
|----|------|---------------|
| **[#4490](https://github.com/QwenLM/qwen-code/pull/4490)** feat(daemon): merge daemon-mode feature batch into main | **OPEN** | **核心架构合并**：将 `daemon_mode_b_main` 分支的 46 个 commits、386 个文件批量合入 main，+115k/-12k LOC，涵盖 Daemon 模式完整功能集，为 v0.16-alpha 奠基。 |
| **[#4736](https://github.com/QwenLM/qwen-code/pull/4736)** feat(serve): ACP/REST parity wave 1 — session extensions + memory + files + auth | **OPEN** | **协议扩展**：向 ACP HTTP 传输层新增 24 个 `_qwen/*` 扩展方法，实现 session、memory、files、auth 等 REST 能力对齐，支撑 Zed、JetBrains 等原生 ACP 客户端。 |
| **[#4780](https://github.com/QwenLM/qwen-code/pull/4780)** feat(cli): add /fork background-agent command | **OPEN** | **背景 Agent**：实现 `/fork <directive>`，派生后台 Agent 继承完整会话上下文并异步执行，通过现有后台通知机制回传结果，对应 #4757。 |
| **[#4779](https://github.com/QwenLM/qwen-code/pull/4779)** feat(stats): add interactive /stats dashboard with cross-session tracking | **OPEN** | **统计仪表盘**：提供交互式 `/stats`，含 Session / Activity / Efficiency 三栏，支持跨会话持久化追踪与可视化，直接回应 #4597。 |
| **[#4760](https://github.com/QwenLM/qwen-code/pull/4760)** fix(cli): handle background auto-update breaking cross-authType model switching | **OPEN** | **修复严重 Bug**：解决 #4758，后台 `npm install -g` 替换 chunks 导致动态导入失败的问题，保障会话中切换模型不崩溃。 |
| **[#4781](https://github.com/QwenLM/qwen-code/pull/4781)** fix(core): keep deferred-tools listing out of the cached system prompt | **OPEN** | **Prompt Cache 修复**：将 deferred MCP tools 从缓存的系统提示移至每轮 `<system-reminder>` 注入，避免 MCP 发现时 bust cache，对应 #4777。 |
| **[#4677](https://github.com/QwenLM/qwen-code/pull/4677)** fix(cli): fix vim mode Esc leak, Enter submit, render lag and implement missing VIM commands | **OPEN** | **Vim 体验大修**：修复 Esc 键泄漏、Enter 提交异常、渲染延迟，并补全 NORMAL 模式缺失命令，提升终端编辑器用户效率。 |
| **[#4572](https://github.com/QwenLM/qwen-code/pull/4572)** Harden auto mode self-modification checks | **OPEN** | **安全加固**：防止 Auto Mode 通过 workspace edit 快速路径或宽泛权限规则绕过分类器，写入配置、指令、hooks、skills 等持久化表面。 |
| **[#4563](https://github.com/QwenLM/qwen-code/pull/4563)** refactor(serve): extract DaemonWorkspaceService from AcpSessionBridge | **OPEN** | **架构解耦**：将 workspace 级别的状态/初始化/工具切换/MCP 重启操作从 `AcpSessionBridge` 抽离为 `DaemonWorkspaceService` 门面，简化 ACP 会话层。 |
| **[#4766](https://github.com/QwenLM/qwen-code

</details>

---
*本日报由 [Big Model Radar](https://github.com/jasonalang/big_model_radar) 自动生成。*