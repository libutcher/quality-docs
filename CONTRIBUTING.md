# Contributing to quality-docs

Contributions from technical writers, developer advocates, engineers, and documentation practitioners are welcome.

## Propose a change

Open an issue or pull request describing the documentation review problem you want to solve. Useful contributions include:

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

Update the README's available-skills table and explain how the new skill differs from existing skills. When possible, include a short example illustrating a useful finding.

## Testing a change

Try the skill on a representative developer documentation draft. Check that the review identifies genuine issues, avoids inventing product facts, and doesn't rewrite the author unnecessarily. Include any useful before-and-after examples in your contribution.

## License

By contributing, you agree that your contributions are distributed under this repository's MIT license.
