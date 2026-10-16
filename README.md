# AI Agent Skills

[English](#english) | [中文](#中文)

## English

Reusable Agent Skills distilled from papers and open-source repos, focused on hands-on AI agent engineering: authorization, tooling, and workflows. Each skill is a folder with a `SKILL.md` (YAML frontmatter + recipe) and an `examples.md` (runnable / follow-along usage examples with acceptance checks).

### Skills

| Skill | Source | One-line purpose |
|---|---|---|
| [sara-tool-authorization](./skills/sara-tool-authorization/) | [arXiv:2608.27146](https://arxiv.org/abs/2608.27146) | Stop untrusted tool outputs (email, web, MCP results) from silently becoming permission to act. |
| [openai-agents-sdk-sandbox](./skills/openai-agents-sdk-sandbox/) | [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | Build multi-agent workflows with the OpenAI Agents SDK: SandboxAgent, MCP, guardrails, handoffs, Realtime. |
| [state-path-tool-menus](./skills/state-path-tool-menus/) | [arXiv:2609.09395](https://arxiv.org/abs/2609.09395) | For large tool/MCP libraries, build an ordered, executable tool menu (producers before consumers) instead of relevance-only retrieval. |

### Install

Copy a skill folder into your agent's skills directory, for example:

```bash
git clone https://github.com/TalentOS-AI/ai-agent-skills.git
cp -r ai-agent-skills/skills/sara-tool-authorization <your-agent>/skills/
```

The `description` field in the frontmatter is what the agent uses to decide when to apply the skill. Agents that have no skills directory can take `SKILL.md` pasted into their instructions.

### Layout

```
.
├── LICENSE
├── README.md
├── templates/
│   └── SKILL.template.md      # starting point for new skills
└── skills/
    └── <skill-name>/
        ├── SKILL.md           # the skill itself
        └── examples.md        # usage examples + acceptance checks
```

### Contributing

1. Read the paper or repo thoroughly (problem, method, results, limits).
2. Copy `templates/SKILL.template.md` to `skills/<kebab-name>/SKILL.md` and fill it in.
3. Add `examples.md` with at least 2 examples (input prompt, expected behavior, acceptance checks).
4. Link the original source. Never invent citations, benchmark numbers, or star counts; only use numbers you verified at the source and say where they came from.
5. Open a pull request.

### License

[MIT](./LICENSE). Skill text is free to reuse; rights to the underlying papers and repos stay with their authors. Always cite the source.

## 中文

从论文和开源仓库提炼出的可复用 Agent Skill，聚焦 AI Agent 实操：授权、工具和工作流。每个 skill 是一个文件夹，内含 `SKILL.md`（YAML 头 + 做法）和 `examples.md`（可运行或可照做的示例与验收要点）。

### Skill 列表

| Skill | 来源 | 一句话用途 |
|---|---|---|
| [sara-tool-authorization](./skills/sara-tool-authorization/) | [arXiv:2608.27146](https://arxiv.org/abs/2608.27146) | 防止邮件、网页、MCP 返回等不可信工具输出悄悄变成执行授权。 |
| [openai-agents-sdk-sandbox](./skills/openai-agents-sdk-sandbox/) | [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | 用 OpenAI Agents SDK 搭多 Agent 工作流：SandboxAgent、MCP、guardrail、handoff、Realtime。 |
| [state-path-tool-menus](./skills/state-path-tool-menus/) | [arXiv:2609.09395](https://arxiv.org/abs/2609.09395) | 工具/MCP 很多时，按可执行路径排工具菜单（生产者在前、消费者在后），而不是只按相关度检索。 |

### 安装

把 skill 文件夹复制到 Agent 的 skills 目录（命令见上方英文部分）。Agent 依据 frontmatter 里的 `description` 判断何时启用；没有 skills 目录的 Agent，可以把 `SKILL.md` 内容粘进指令。

### 目录结构

见上方英文部分：`templates/` 放模板，`skills/<名称>/` 下是 `SKILL.md` 和 `examples.md`。

### 贡献

1. 完整读懂论文或仓库（问题、方法、结果、局限）。
2. 复制 `templates/SKILL.template.md` 到 `skills/<kebab-name>/SKILL.md` 并填写。
3. 写 `examples.md`，至少 2 个示例（输入提示、预期行为、验收要点）。
4. 附原始出处。不编造引用、基准数字或 star 数，数字必须在来源处核实并注明出处。
5. 提交 Pull Request。

### 许可证

[MIT](./LICENSE)。Skill 文本可自由复用，论文与仓库的权利归原作者，使用时请注明来源。


---

Maintained by [TalentOS](https://www.agentbay.asia) · 需要定制 Agent / 技能开发？[找我们定制 / Work with us](https://www.agentbay.asia/contact) · talentos@agentbay.asia
