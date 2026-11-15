# quality-docs

Independent agent skills for reviewing and improving developer documentation.

Each skill focuses on a specific kind of documentation review. Install and use only the skills you need—no orchestrator or shared configuration is required.

## Available skills

| Skill | What it reviews | Status |
| --- | --- | --- |
| [Structural review](structural-review/SKILL.md) | Audience fit, organization, completeness, examples, scannability, accessibility, and plain language | Available |

Additional independent skills may be added over time, including technical accuracy, security review, and style and voice.

## Use a skill

Each skill lives in its own directory and contains a `SKILL.md` file with the instructions and metadata for compatible coding agents.

For an agent that supports the Agent Skills directory convention, copy the skill directory to the appropriate skills location. For example, for a personal Claude Code installation:

```bash
mkdir -p ~/.claude/skills
cp -R structural-review ~/.claude/skills/
```

Run that command from the root of a local clone of this repository. For a project-local Claude Code installation, copy the folder into `.claude/skills/` in your project instead.

Then ask your agent to use the skill on a draft, for example:

> Review this developer documentation draft using the structural-review skill. Focus on problems that could prevent a developer from completing the task. Don't rewrite the whole page.

Agent discovery, invocation, and directory locations vary by tool. If your agent does not discover the skill automatically, point it to the `SKILL.md` file or provide its contents as instructions.

## Review philosophy

These skills are designed to support experienced technical writers, not replace their judgment.

- Prioritize developer success over superficial editorial polish.
- Make specific, actionable recommendations.
- Preserve the author's voice.
- Distinguish verified problems from questions that need technical review.
- Keep the skills independent, reusable, and configurable without requiring a shared workflow.

The structural review skill uses [Diátaxis](https://diataxis.fr/) to reason about content purpose. Project style guides take priority when supplied. External editorial references are optional aids, not requirements for every review.

## Contributing

Ideas, improvements, and reports of unhelpful or incorrect feedback are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
