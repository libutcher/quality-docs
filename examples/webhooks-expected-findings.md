# Expected findings: Configure webhooks

This is a **human evaluation key** for [webhooks-before.md](webhooks-before.md), an intentionally flawed guide for the fictional service LumenQueue. It is not product documentation and should **not** be included in the context given to the reviewer being evaluated.

Use it to compare the output of `structural-review/SKILL.md` with expected concerns. Award credit for equivalent reasoning, not exact wording or categorization. A review does not need to report every issue to be useful; its priority choices and avoidance of invented facts matter as much as raw coverage.

## Critical findings

These should be especially likely to appear in **Fix first**, although a five-item cap means some may appear elsewhere. Treat related issues as a single finding when appropriate.

| ID | Location | Expected concern |
| --- | --- | --- |
| C1 | Set up your environment | `LQ_API_KEY` is exported, but the login command reads `$LQ_TOKEN`. As written, the variable mismatch prevents the stated login flow. Credential terminology is also inconsistent. |
| C2 | Create a webhook | The instructions say to create a receiving endpoint but provide no handler, implementation, working example, or link to build one. A developer may be unable to complete the central task. |
| C3 | Configure webhook security | `if (signature) { processEvent(payload); }` checks only header presence, not signature validity, contradicting the claim that the snippet verifies requests. This is a misleading example; the review must not invent an unverified verification algorithm. |
| C4 | Create a webhook / Configure webhook security / Test your integration | The sequence activates event delivery before setting up verification; the endpoint's required successful HTTP response is described only later. A developer needs the behavior requirements while implementing the receiver. |
| C5 | Understand event delivery / Event types | The draft says events are delivered in chronological order, then warns that they can arrive out of order. The contract must be confirmed rather than guessed. |
| C6 | Understand event delivery / Test your integration | Retry count conflicts: three retries versus up to five. Confirm the intended delivery semantics instead of picking a number. |

## Other meaningful findings

These are useful evidence of a thorough review, but they should be ranked below blockers. The examples illustrate what to look for; they are not a requirement to generate a fixed number of comments.

| ID | Location | Expected concern |
| --- | --- | --- |
| M1 | Introduction | Promotional, feature-focused opening does not tell readers the concrete outcome or user action. |
| M2 | Before you begin / Troubleshooting | Vague prerequisites and permissions; macOS/Linux-only caveat appears after installation rather than before it. |
| M3 | Before you begin | Paid-tier caveat fails to identify which capabilities and plans are affected. |
| M4 | Set up your environment | `latest version` is not actionable without a check command and an authoritative compatibility requirement. |
| M5 | Create a webhook | Publicly accessible URL requirement is inconsistent or at least unexplained alongside localhost support; testing mechanism is missing. |
| M6 | Create a webhook | Unexplained `https://example.com/hooks` and credential placeholders can lead to unusable copied commands. |
| M7 | Create a webhook / Test your integration | Expected CLI response, how to send a test event, where to find the dashboard test action, and how to confirm success are missing. |
| M8 | Configure webhook security | Signing secret provenance and signing defaults are unclear; signing secret/key terminology is inconsistent. |
| M9 | Understand event delivery | The definition of asynchronous delivery is conflated with push-based delivery; technical terminology may mislead. |
| M10 | Understand event delivery / Test your integration | Configurable settings are mentioned without directions or links for configuring them. |
| M11 | Create a webhook / Test your integration | `click the green button on the right` depends on color and location; `click here` is non-descriptive link text. |
| M12 | Troubleshooting | Generic advice to check configuration and permissions does not provide actionable diagnostic steps. |
| M13 | Organization | The dashboard route is an unlabeled alternative within a CLI-focused procedure; separating or clearly marking the alternative may help the reader. |
| M14 | Technical concepts | The endpoint, not the webhook subscription, receives HTTP event requests. |
| M15 | Next steps | Vague next actions and missing specific destinations reduce usefulness, though this is low priority. |

## Questions that should remain unresolved

These are examples of appropriate SME questions, **not expected product answers**:

- Which credential and environment variable does the CLI require?
- What event-order guarantees, if any, does LumenQueue provide?
- What is the retry behavior, timeout, and successful response status range?
- How are signatures computed and validated, and where does the reader find a signing secret?
- What is the intended local testing path, if localhost targets are supported?
- Which plan, role, platform, or minimum compatible CLI version is required?

A concise review can combine related questions and refer back to findings rather than restating every problem.

## Avoid these false positives and overreaches

A reviewer should **not**:

- Invent the correct API token variable, signing algorithm, retry policy, event schema, or feature entitlements.
- State that an HTTPS endpoint is required, or that Node.js must power the receiver, without evidence.
- Assume a timestamp or event ID guarantees chronological ordering.
- Insist that the event table or delivery explanation must live on separate pages just because Diátaxis distinguishes reference and explanation from how-to content.
- Treat minor preferred wording (such as changing an event description to match a parallel sentence pattern) as a major developer blocker.
- Perform a broad security architecture audit instead of flagging that the signature example fails to demonstrate its claimed behavior.
- Inflate the issue count by reporting the same contradiction under several review passes.

## Manual scoring rubric

Evaluate each dimension separately, rather than relying on a single raw issue count:

1. **Coverage:** Which critical and meaningful findings were captured? Which blockers were missed?
2. **Prioritization:** Did the five Fix first items address the largest reader obstacles?
3. **Actionability:** Do suggestions give the author a concrete next step while preserving author voice?
4. **Grounding:** Are suspected product facts framed as questions when verification isn't possible?
5. **Restraint:** Did the review avoid low-value rewording, duplicates, and unjustified restructuring?
6. **Output usability:** Are locations and quotations easy to find, and are SME questions concise?

Record notable false positives and missed critical findings in addition to the findings covered. The skill is successful when it produces a review a technical writer can act on, not when it maximizes the number of comments.
