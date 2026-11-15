# Contributing to quality-docs

Contributions from technical writers, developer advocates, engineers, and documentation practitioners are welcome.

## Propose a change

Open an issue to suggest an improvement, or a pull request if you have a change ready. Explain the documentation review problem it solves.

For a missed issue or false positive, include a short documentation excerpt or link, the feedback the skill produced, and what you expected instead. Remove private or sensitive information before sharing an example.

Useful contributions include:

- Reproducible examples of false positives or missed issues.
- Improvements to feedback quality, clarity, or review scope.
- New independent skills for distinct documentation tasks.
- Usage examples and guidance for supported agents.

## Design principles

- **One purpose per skill.** Keep the scope clear, and avoid duplicating other review skills.
- **Independent use.** A skill must not require an orchestrator or another skill to function.
- **Evidence over guesses.** Skills must distinguish known issues from information requiring verification.
- **Minimal edits.** Prefer actionable feedback that respects the writer's decisions and voice.
- **Optional customization.** Product-specific terminology and style guides should not be required for baseline use.
- **Useful output.** Prioritize issues that affect developer success rather than generating exhaustive editorial noise.

## Adding a skill

Create a new top-level directory named for the skill, with a `SKILL.md` containing YAML frontmatter for `name` and `description` and clear instructions for when and how to perform the review.

Update the [README](README.md) to link to the new skill, explain what it helps writers do, and describe how it differs from existing skills. When possible, include a short example illustrating a useful finding.

## Testing a change

Try the skill on representative developer documentation. Check whether it identifies meaningful problems, avoids inventing product facts or unnecessary rewrites, and prioritizes issues that could block readers.

For changes to [structural review](structural-review/SKILL.md), you can start with the [intentionally flawed webhook draft](examples/webhooks-before.md). Run the review before consulting the [expected findings](examples/webhooks-expected-findings.md), so the answer key doesn't influence the test.

In your pull request, briefly describe what you tested and any important issues the skill still misses.

## License

By contributing, you agree that your contributions are distributed under this repository's MIT license.
