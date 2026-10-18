# unattended-agent-decide-and-record

**Operating rules for unattended AI agent sessions: decide yourself and log it, ask the human only for what is irreversible or outward-facing.**

[![test](https://github.com/Kein-chronicle/unattended-agent-decide-and-record/actions/workflows/test.yml/badge.svg)](https://github.com/Kein-chronicle/unattended-agent-decide-and-record/actions/workflows/test.yml) ![license](https://img.shields.io/badge/license-MIT-blue.svg)

## Why

Long "finish it yourself" runs die on option menus. An agent that stops to ask which of three equal choices to take is not unattended. These rules say what to decide alone (and write down), what must still go to a person, and what to do when a login expires mid-run.

> **Status: doc-only.** Guidance for prompts and operating contracts, not enforcement code. Pair it with hooks or gates if you need a hard stop.

## Install

**As a Claude Code skill** (Claude uses it when the task matches the skill description):

```sh
git clone https://github.com/Kein-chronicle/unattended-agent-decide-and-record.git ~/.claude/skills/decide-and-record
```

For a single project, clone into `<project>/.claude/skills/decide-and-record` instead, then start a new Claude Code session.

**Just read it:** the whole skill is [SKILL.md](SKILL.md). It is plain Markdown; copy any part into your own `CLAUDE.md` or prompts.

**Requires:** nothing to read it; Python 3.10+ only to run `validate.py`.

## What it covers

- Decide yourself, then record: the decision, the alternatives and the reason go in a log, not a question.
- Ask the human: only for what cannot be decided from the request, the code or sensible defaults.
- Never skip confirmation for destructive, irreversible or outward-facing actions.
- The failure mode this prevents, and how to handle login or session expiry in unattended work.

## Limits

- Guidance for prompts and operating contracts, not enforcement code. Pair it with hooks or gates if you need a hard stop.

## Related projects

These solve neighbouring problems; use them when they fit better.

- **Claude Code permission modes and hooks**: enforce what an agent may do; this says what it should decide alone

## More from the same collection

Small, tested tools that grew out of running AI agents and game/app pipelines for months:

- [**claude-code-memory-lint**](https://github.com/Kein-chronicle/claude-code-memory-lint): Lint a Claude Code memory folder: orphan files, missing files, oversized index lines, and the index lines that are silently cut at load.
- [**claude-code-session-cost**](https://github.com/Kein-chronicle/claude-code-session-cost): Estimate what a Claude Code project cost from its session logs, sub-agents included, with both cache-TTL price assumptions shown.
- [**claude-code-launchd-loops**](https://github.com/Kein-chronicle/claude-code-launchd-loops): Generate a macOS launchd job that runs Claude Code headless on a schedule, from one command.

## Development

```sh
python3 validate.py
```

This only validates the skill file (frontmatter and referenced paths). See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).

If this saved you a debugging session, a star helps other people find it. Bug reports and failing test cases are even better.

<sub>Keywords: claude-code, claude-skills, agent-skills, ai-agents, autonomous-agents, prompt-engineering, workflow, human-in-the-loop</sub>
