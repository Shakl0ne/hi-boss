<div align="center">

# hi-boss · 向上管理参谋

**把领导/甲方的一句话，解读出话里的深层意思，给出不卑不亢的回复方向与句式参考。**

</div>

---

## 中文

### 这是什么

一个 **Claude / OpenCode / AI Agent Skill**。你只需要把领导或甲方（含跨部门协作方、业务方）的
一句话发进来，加上任何你知道的背景，它会帮你：

1. **看透对方没说出来的话** —— 对方在扛什么、按什么立场、真正想要什么。
2. **给出回复方向 + 句式参考** —— 1 个稳妥版 + 1 个敢争版，不卑不亢。

本质：换位思考，从对方出发，说出对方想听的、同时保住自己的专业立场。单轮对话，不做长期记忆。

### 核心价值

- **识别 9 种沟通类型**：感受 / 分享 / 归因 / 建议 / 批评 / 询问 / 命令 / 说服 / 娱乐，自动归类后给出对应回应策略。
- **双层分析**：分类定方向，再拆解「对方的利益点 → 隐藏需求 → 压力来源」。
- **低风险兜底**：默认给「稳妥版」，需要主见时再给「敢争版」，都由你决定发不发。
- **不谄媚、不硬杠**：回复从对方出发，但始终保住你自己的专业立场。

### 方法论

分类心法参考了沟通领域的常见模型；倾听与需求拆解的思路参考了《非暴力沟通》（NVC）的
观察—感受—需要—请求框架。只借鉴框架思想，不复制任何原文内容。

### 安装（Claude Code / OpenCode / Codex）

本 skill 遵循通用的 **Agent Skills 规范**（`SKILL.md` + frontmatter 的 `name`/`description`），
一个包可跨三种工具复用。`SKILL/` 就是可安装的 skill 目录。

**快速对照**

| 工具 | 位置 | 安装方式 |
|---|---|---|
| Claude Code | `~/.claude/skills/`（全局）· `.claude/skills/`（项目） | 复制目录 |
| OpenCode | 项目 `.opencode/skills/` 或配置 `skills` 数组 | 复制目录 / 配置路径 |
| Codex CLI | `~/.codex/skills/`（全局）· `.agents/skills/`（项目） | 复制目录 |
| DeepSeek Harness | `~/.dsh/skills/`（全局）· `.dsh/skills/`（项目） | 复制目录 |

#### Claude Code
```bash
mkdir -p ~/.claude/skills
cp -r SKILL ~/.claude/skills/hi-boss
```
放好后**自动发现 + 热重载**，新会话即可用。`~/.claude/skills/` 是全局技能目录；
若只给单个项目用，放到该项目的 `.claude/skills/hi-boss/` 即可。

#### OpenCode
```bash
# 方式一：项目级，直接放进 .opencode/skills/
mkdir -p .opencode/skills
cp -r SKILL .opencode/skills/hi-boss
```
```jsonc
// 方式二：全局/共享路径，在 opencode.jsonc 的 skills 数组加一行
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["./SKILL"]
}
```

#### Codex CLI
```bash
mkdir -p ~/.codex/skills
cp -r SKILL ~/.codex/skills/hi-boss   # 全局（$CODEX_HOME 默认 ~/.codex）
# 项目级则放到 .agents/skills/hi-boss/
```
从 cwd 向上逐层探测，放对目录后自动注册。

#### DeepSeek Harness（`dsh`）
DeepSeek 官方的 agent harness 框架（`deepseek.ai` → `deepseek-harness`，CLI `dsh`）原生支持
`SKILL.md` 规范。它是一个插件化 agent 微内核，可统一编排 Codex、Claude Code 等底层 agent，
不是即装即聊的单一 CLI。
```bash
mkdir -p ~/.dsh/skills
cp -r SKILL ~/.dsh/skills/hi-boss   # 全局（默认根，$DSH_HOME 可改）
# 项目级则放到 .dsh/skills/hi-boss/
```
认目录形态 `<skill-name>/SKILL.md` 或扁平 `<skill-name>.md`；共享 agent 配置根 `~/.agents/skills` 亦可。

装好后在对话里把领导/甲方的那句话贴进来，加上可选背景即可。

---

## English

### What is this

A **Claude / OpenCode / AI Agent Skill** ("向上管理" = managing up). You paste a single message
from your boss or a client (or a cross-team stakeholder), optionally with context, and it helps you:

1. **Read between the lines** — what the other person is really carrying, where they stand, what they truly want.
2. **Get a reply direction + phrasing** — one safe version and one assertive version, without sycophancy or stubbornness.

Core idea: think from the other person's perspective, say what they need to hear, while holding your own
professional ground. Single-turn, no long-term memory.

### Highlights

- **9 communication types recognized**: feeling / sharing / attributing / advising / criticizing /
  asking / commanding / persuading / joking. Auto-classifies and returns the matching response strategy.
- **Two-layer analysis**: classify to pick direction, then unpack "stake → hidden need → pressure source".
- **Low-risk by default**: default to the safe reply; switch to an assertive one when you want to take a stand.
- **Respectful, not sycophantic**: replies start from the other person's needs but keep your own position.

### Methodology

The communication taxonomy is informed by common frameworks in the field; the listening and needs‑unpacking
draw on the Nonviolent Communication (NVC) observe–feel–need–request model. No original book text is reproduced.

### Install (Claude Code / OpenCode / Codex)

This skill follows the standard **Agent Skills convention** (`SKILL.md` with YAML frontmatter
`name`/`description`), so one package works across all three tools. `SKILL/` is the installable skill directory.

**Quick reference**

| Tool | Location | How to install |
|---|---|---|
| Claude Code | `~/.claude/skills/` (global) · `.claude/skills/` (project) | copy directory |
| OpenCode | project `.opencode/skills/` or the `skills` array in config | copy directory / config path |
| Codex CLI | `~/.codex/skills/` (global) · `.agents/skills/` (project) | copy directory |
| DeepSeek Harness | `~/.dsh/skills/` (global) · `.dsh/skills/` (project) | copy directory |

#### Claude Code
```bash
mkdir -p ~/.claude/skills
cp -r SKILL ~/.claude/skills/hi-boss
```
It is auto-discovered and hot-reloaded — just start a new session. `~/.claude/skills/` is the
global location; for a single project, place it in that project's `.claude/skills/hi-boss/` instead.

#### OpenCode
```bash
# Option 1 — project-level: drop it into .opencode/skills/
mkdir -p .opencode/skills
cp -r SKILL .opencode/skills/hi-boss
```
```jsonc
// Option 2 — global/shared: add a line to the skills array in opencode.jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["./SKILL"]
}
```

#### Codex CLI
```bash
mkdir -p ~/.codex/skills
cp -r SKILL ~/.codex/skills/hi-boss   # global ($CODEX_HOME defaults to ~/.codex)
# project-level: use .agents/skills/hi-boss/
```
Codex probes `.agents/skills/` upward from the cwd, so the skill auto-registers once it's in place.

#### DeepSeek Harness (`dsh`)
DeepSeek's official agent harness framework (CLI `dsh`) natively supports the `SKILL.md`
convention. It is a plugin-based agent microkernel that can orchestrate Codex, Claude Code,
etc. underneath — not a single turnkey chat CLI.
```bash
mkdir -p ~/.dsh/skills
cp -r SKILL ~/.dsh/skills/hi-boss   # global (default root; override with $DSH_HOME)
# project-level: use .dsh/skills/hi-boss/
```
It accepts either a directory form `<skill-name>/SKILL.md` or a flat `<skill-name>.md`.
The shared agent config root `~/.agents/skills` also works.

> 💡 If you're just **using DeepSeek as the model backend** behind one of the frontends above
> (opencode / codex / cline, etc.), install the skill into that **frontend host's** directory
> (e.g. `~/.codex/skills/`, `.opencode/skills/`) — the frontend loads the skill, the model backend doesn't.

Once installed, paste your boss's or client's message into the conversation, optionally with context,
and get the read-between-the-lines interpretation plus a reply direction.

---

## License

MIT © Shakl0ne