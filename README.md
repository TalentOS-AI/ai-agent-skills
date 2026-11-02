# AI Agent Skills

[English](#english) | [中文](#中文)

## English

Reusable Agent Skills distilled from papers and open-source repos, covering AI agent engineering (authorization, tooling, workflows) and research / academic workflows (papers, citations, figures, literature). Each skill is a folder with a `SKILL.md` (YAML frontmatter + recipe) and an `examples.md` (runnable / follow-along usage examples with acceptance checks).

### Skills

| Skill | Source | One-line purpose |
|---|---|---|
| [sara-tool-authorization](./skills/sara-tool-authorization/) | [arXiv:2608.27146](https://arxiv.org/abs/2608.27146) | Stop untrusted tool outputs (email, web, MCP results) from silently becoming permission to act. |
| [openai-agents-sdk-sandbox](./skills/openai-agents-sdk-sandbox/) | [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | Build multi-agent workflows with the OpenAI Agents SDK: SandboxAgent, MCP, guardrails, handoffs, Realtime. |
| [state-path-tool-menus](./skills/state-path-tool-menus/) | [arXiv:2609.09395](https://arxiv.org/abs/2609.09395) | For large tool/MCP libraries, build an ordered, executable tool menu (producers before consumers) instead of relevance-only retrieval. |

### Research / academic skills

| Skill | Source | One-line purpose |
|---|---|---|
| [acl-latex-paper](./skills/acl-latex-paper/) | Iris / TalentOS | Write/compile ACL-family LaTeX papers (template, anonymity, page limits, compile checks). |
| [acl-paper-figures](./skills/acl-paper-figures/) | [alphaXiv/OpenResearch orx-figures](https://github.com/alphaXiv/OpenResearch) (MIT, adapted) | Build print-size ACL/two-column matplotlib figures (Okabe-Ito, greyscale-safe) with audit helpers. |
| [annotation-project](./skills/annotation-project/) | Iris / TalentOS | Design labeled datasets: scheme, guidelines, IAA, LLM pre-annotation, data statement/licensing. |
| [citation-audit](./skills/citation-audit/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) (MIT, adapted) | Audit every bibliography entry for reality, attribution, and claim support (MBA/CSSCI-aware). |
| [citation-verification](./skills/citation-verification/) | Iris / TalentOS | Resolve every citation against DOI/Crossref/Anthology/arXiv before sharing refs. |
| [deslop](./skills/deslop/) | [stephenturner/skill-deslop](https://github.com/stephenturner/skill-deslop) (MIT, adapted) | Strip AI writing tells and defensive hedging from academic prose (EN + Chinese journal extras). |
| [literature-review](./skills/literature-review/) | Iris / TalentOS | Systematic literature search protocol, multi-source querying, snowballing, review matrix. |
| [openalex](./skills/openalex/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) (MIT, adapted) | Search OpenAlex for works, citation counts, affiliations, funding, DOI metadata via public API. |
| [rebuttal-letter](./skills/rebuttal-letter/) | Iris / TalentOS | Structure conference rebuttals / journal response-to-reviewers letters. |
| [research-skill-router](./skills/research-skill-router/) | Iris / TalentOS | Route research tasks to the right local skill; install external MIT/Apache skills on demand. |
| [scientific-visualization](./skills/scientific-visualization/) | [K-Dense-AI](https://github.com/K-Dense-AI/scientific-agent-skills) (MIT) | Post-figure QA: palette/contrast audit, PDF metadata, export planning. |
| [scipilot-figure-skill](./skills/scipilot-figure-skill/) | [Haojae/scipilot-figure-skill](https://github.com/Haojae/scipilot-figure-skill) (MIT) | Chart-type advice and viz anti-pattern checklist. |
| [semantic-scholar](./skills/semantic-scholar/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) (MIT, adapted) | Search Semantic Scholar for published venue papers with citations/TLDR via public API. |
| [venue-deadlines](./skills/venue-deadlines/) | Iris / TalentOS | Track official CFP deadlines (AoE conversion) and sourced acceptance rates. |


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
        ├── examples.md        # usage examples + acceptance checks (engineering skills)
        └── …                  # research skills may ship helpers/scripts/references instead
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

从论文和开源仓库提炼出的可复用 Agent Skill，覆盖 AI Agent 实操（授权、工具、工作流）与科研/学术流程（论文、引用、作图、文献）。每个 skill 是一个文件夹，内含 `SKILL.md`（YAML 头 + 做法）和 `examples.md`（可运行或可照做的示例与验收要点）。

### Skill 列表

| Skill | 来源 | 一句话用途 |
|---|---|---|
| [sara-tool-authorization](./skills/sara-tool-authorization/) | [arXiv:2608.27146](https://arxiv.org/abs/2608.27146) | 防止邮件、网页、MCP 返回等不可信工具输出悄悄变成执行授权。 |
| [openai-agents-sdk-sandbox](./skills/openai-agents-sdk-sandbox/) | [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | 用 OpenAI Agents SDK 搭多 Agent 工作流：SandboxAgent、MCP、guardrail、handoff、Realtime。 |
| [state-path-tool-menus](./skills/state-path-tool-menus/) | [arXiv:2609.09395](https://arxiv.org/abs/2609.09395) | 工具/MCP 很多时，按可执行路径排工具菜单（生产者在前、消费者在后），而不是只按相关度检索。 |

### 科研 / 学术 skill

| Skill | 来源 | 一句话用途 |
|---|---|---|
| [acl-latex-paper](./skills/acl-latex-paper/) | Iris / TalentOS | 撰写与编译 ACL 系 LaTeX 论文（模板、匿名、页限、编译检查）。 |
| [acl-paper-figures](./skills/acl-paper-figures/) | [alphaXiv/OpenResearch orx-figures](https://github.com/alphaXiv/OpenResearch)（MIT，改编） | 按 ACL/双栏印刷尺寸做 matplotlib 图（Okabe-Ito、灰度安全）并自检。 |
| [annotation-project](./skills/annotation-project/) | Iris / TalentOS | 标注数据集：方案、指南、一致性、LLM 预标、数据说明与许可。 |
| [citation-audit](./skills/citation-audit/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)（MIT，改编） | 逐条核验参考文献是否真实、归因正确、支撑主张（兼顾 MBA/CSSCI）。 |
| [citation-verification](./skills/citation-verification/) | Iris / TalentOS | 分享参考文献前用 DOI/Crossref/Anthology/arXiv 解析每条引用。 |
| [deslop](./skills/deslop/) | [stephenturner/skill-deslop](https://github.com/stephenturner/skill-deslop)（MIT，改编） | 去掉学术文风里的 AI 套话与防御性表述（含中文期刊补充）。 |
| [literature-review](./skills/literature-review/) | Iris / TalentOS | 系统文献检索：多源查询、滚雪球、综述矩阵。 |
| [openalex](./skills/openalex/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)（MIT，改编） | 用 OpenAlex 公开 API 查论文、引用、机构、资助与 DOI 元数据。 |
| [rebuttal-letter](./skills/rebuttal-letter/) | Iris / TalentOS | 组织会议 rebuttal / 期刊回复审稿意见信。 |
| [research-skill-router](./skills/research-skill-router/) | Iris / TalentOS | 把科研任务路由到合适本地 skill；按需安装外部 MIT/Apache skill。 |
| [scientific-visualization](./skills/scientific-visualization/) | [K-Dense-AI](https://github.com/K-Dense-AI/scientific-agent-skills)（MIT） | 成图后质检：配色对比、PDF 元数据、导出规划。 |
| [scipilot-figure-skill](./skills/scipilot-figure-skill/) | [Haojae/scipilot-figure-skill](https://github.com/Haojae/scipilot-figure-skill)（MIT） | 图表类型建议与可视化反模式清单。 |
| [semantic-scholar](./skills/semantic-scholar/) | [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)（MIT，改编） | 用 Semantic Scholar 公开 API 查已发表会议/期刊论文与引用/TLDR。 |
| [venue-deadlines](./skills/venue-deadlines/) | Iris / TalentOS | 跟踪官方 CFP 截稿（AoE 换算）与有出处的录用率。 |


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
