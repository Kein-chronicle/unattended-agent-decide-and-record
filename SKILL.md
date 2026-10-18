---
name: decide-and-record
description: Rules for autonomous or unattended agent sessions: when to decide yourself and log it versus when to ask the human. Use when running long "finish it yourself" sessions with a stop-hook or goal loop, when an agent keeps interrupting an unattended run with option menus, or when writing the operating contract for background workers.
---

# decide-and-record

An autonomous session that stops to ask "A or B?" when it already has a recommendation is not autonomous - it is a
chat with extra latency. But "never ask" is also wrong. The boundary:

## Decide yourself, then record

Condition: you can name a best option and give a reason.
1. Do the recommended thing now.
2. Write the decision into the project's decision log (what was chosen, why, what the alternative was, how to revert).
3. Keep going. The human reviews and overrides afterwards, at the cost of redoing, not of waiting.

## Ask the human

Only when no recommendation can be justified because the answer depends on the human's taste or strategy
(e.g. "which of two product directions should we take?"). Even then: minimise, and if unsure proceed down the best-evidenced path and log it.

## Never skip confirmation for

Irreversible or outward-facing actions - pushing to a remote, deleting data, publishing, sending messages, spending
money - and for ambiguous scope. "Don't ask" applies to *choices inside the task*, never to *crossing the task's
boundary*. In an unattended run nobody may answer: **park that item** (write down what is needed and why), keep working on everything else, and report it at the end.

## Failure mode this prevents

A hook that rejects turns ending in "here are the options" prose can push the agent to over-correct by calling the
question tool round after round, each time with a recommended option already marked. The intent was "make a
decision", not "ask every time". When a rule is written to stop one bad behaviour, check the opposite bad behaviour
isn't now the cheapest way to comply.

## Login/session expiry in unattended work

Use the project's documented login procedure first, but **only credentials and sessions that were explicitly provisioned for the agent**. Never defeat or work around MFA, passkeys, biometrics or an OS
password prompt, never type a password you were not given for this purpose, and never read stored secrets or session files to get in. Escalate to a human when the procedure itself says so
(biometric prompt, OS password, ambiguous account) or it was followed and failed. A blanket "never log in, just wait" in a worker contract overrides the better, project-specific procedure, but an agent
must still stop at the edge of what it was authorised to do.
