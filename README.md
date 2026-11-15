# quality-docs

Review developer documentation with the questions an experienced technical writer asks: Can readers find what they need, understand it, and complete their tasks?

**quality-docs** is a growing collection of independent agent skills informed by the editorial practices of a staff-level technical writer specializing in developer documentation. Each skill focuses on a specific aspect of documentation quality, so you can choose the review you need without adopting an entire workflow.

## Available now: Structural review

The [structural-review skill](structural-review/SKILL.md) helps you review a draft or existing developer documentation before sharing it with peers or subject matter experts.

It checks whether:

- The content serves its intended audience and purpose.
- Readers can follow the information and complete the documented task.
- Prerequisites, examples, and expected results are clear.
- Headings, links, and instructions are easy to scan and use.
- Language is direct, precise, and focused on what the reader can do.

The skill prioritizes problems that could confuse or block developers. It suggests focused fixes, preserves the author's voice, and turns unverified technical details into questions rather than guesses.

## Install and use

Copy the `structural-review` directory into your agent's skills location. For example, from a local clone of this repository, install it for personal use in Claude Code:

```bash
mkdir -p ~/.claude/skills
cp -R structural-review ~/.claude/skills/
```

To use it only in one project, copy the directory into that project's `.claude/skills/` instead.

Then ask your agent:

> Review this developer documentation page using the structural-review skill. Focus on what could prevent a developer from understanding the page or completing the task. Don't rewrite the whole document.

Skill discovery and installation paths vary by agent. If your agent doesn't recognize the skill, point it to [`structural-review/SKILL.md`](structural-review/SKILL.md). Avoid installing conflicting versions with the same skill name.

## Review principles

The skills are designed to support, not replace, a technical writer's judgment.

- **Start with the reader.** Evaluate the documentation against the reader's goal, not a preferred template.
- **Find meaningful problems.** Prioritize missing steps, confusing explanations, contradictions, and misleading examples over cosmetic edits.
- **Preserve the author's voice.** Suggest the smallest useful change.
- **Don't invent product facts.** Identify what needs confirmation from an implementation or subject matter expert.
- **Use standards thoughtfully.** Respect project-specific guidance; use frameworks such as [Diátaxis](https://diataxis.fr/) to inform decisions, not dictate them.

## Try the example

Review the intentionally flawed [webhook guide](examples/webhooks-before.md) with the structural-review skill, then compare the result with the [expected findings and evaluation rubric](examples/webhooks-expected-findings.md).

For a blind evaluation, give the agent only the skill and draft—not the answer key.

## More skills

This repository currently contains **one skill**. Future independent skills may cover technical accuracy, security, and style and voice. Each will be usable on its own, without an orchestrator.

## Contributing

Suggestions, examples, and reports of missed issues or unhelpful feedback are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
