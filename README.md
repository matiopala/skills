# Agent Skills

Portable, open-source skills for agent harnesses that implement the
[Agent Skills](https://agentskills.io/) format.

The skills in this repository are authored once and can be used with:

- OpenAI Codex
- Pi
- Claude Code

## Available skills

| Skill | Purpose |
| --- | --- |
| [`adr`](skills/adr/SKILL.md) | Capture consequential product and technical decisions, their rationale, and their history. |
| [`bro`](skills/bro/SKILL.md) | Rewrite the previous assistant response in clear, everyday language. |
| [`conventional-commits`](skills/conventional-commits/SKILL.md) | Prepare focused Git commits using a simplified Conventional Commits format. |
| [`decompose`](skills/decompose/SKILL.md) | Break larger designs into reviewable tasks with dependencies, acceptance criteria, and irrefutable proof of completion. |
| [`deliver`](skills/deliver/SKILL.md) | Guide a software change through interviewing, research, planning, implementation, and irrefutable proof of delivery. |
| [`grill-me`](skills/grill-me/SKILL.md) | Conduct an in-depth interview to clarify ideas, examine assumptions, and reach shared understanding. |
| [`product-spec`](skills/product-spec/SKILL.md) | Define user outcomes, required behavior, acceptance criteria, and evidence of product value before technical design. |
| [`show-me`](skills/show-me/SKILL.md) | Explain the current topic with a focused visual. |
| [`tech-spec`](skills/tech-spec/SKILL.md) | Define a technical solution, its acceptance evidence, and its readiness for task decomposition. |

## Install

Clone the repository, then run:

```sh
./scripts/install
```

By default, the installer links every skill into both shared discovery
locations:

- `~/.agents/skills` for Codex and Pi
- `~/.claude/skills` for Claude Code

Because the installed skills are symbolic links, pulling changes in this clone
updates every harness immediately.

Install for one harness only:

```sh
./scripts/install --harness codex
./scripts/install --harness pi
./scripts/install --harness claude
```

Install selected skills:

```sh
./scripts/install conventional-commits
```

Selecting `product-spec`, `tech-spec`, `decompose`, `deliver`, or `grill-me`
also installs their shared `adr` companion. These workflows consult relevant
decisions and capture consequential choices automatically; `grill-me` does
this only for software interviews in a repository. When copying skills
manually, include `adr` alongside these workflows.

The installer refuses to replace existing files or links that point elsewhere.
Set `AGENTS_SKILLS_DIR` or `CLAUDE_SKILLS_DIR` to override either installation
directory.

## Uninstall

```sh
./scripts/uninstall
```

The uninstaller removes only links that point to skills in this clone. It does
not delete skill contents or unrelated installations.

## Validate

```sh
./scripts/validate
```

Validation checks the portable subset of the Agent Skills specification used by
this repository, including required frontmatter and naming conventions.

## Authoring

Each skill lives in `skills/<skill-name>/` and contains a required `SKILL.md`.
Optional scripts, references, and assets belong inside the same skill directory.
Keep harness-specific behavior out of shared instructions unless the skill
cannot work without it.

## License

Licensed under the [Apache License 2.0](LICENSE).
