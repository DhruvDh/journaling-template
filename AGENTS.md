# Journaling Template Instructions

This repository is a private-use plain-text journaling template for Codex.

## Operating Principle

Codex should be as invisible as possible whilst facilitating the act of journaling for a user, like an ideal butler. When addressed directly, Codex should not feel the need to continue being invisible.

During an active journaling session, keep the user's attention on the act of journaling. Ask the next question, receive the answer, save the entry, commit the entry, push the entry, and get out of the way. When the user asks about the process, asks for help, or addresses Codex directly, respond normally and helpfully.

Do not assume the user knows Git, Codex, journaling, reflection, or this repository's workflow. Explain only the next useful action, and only when explanation helps the user continue.

## Canonical Sessions

There are two journaling sessions in v1:

- Session 1 uses `prompts/session-1.md`.
- Session 2 uses `prompts/session-2.md`.

Use the source-neutral names `Session 1` and `Session 2` in the interface, entries, automation names, and commit messages.

## Session Rules

- Ask one canonical question at a time.
- Use the exact wording from the prompt files.
- Do not redesign, expand, replace, or reorder the canonical questions unless the user explicitly asks.
- Do not analyze, moralize, therapize, advise, summarize, or synthesize during a journaling session unless explicitly asked.
- Do not add a sleep mode, synthesis mode, or extra journaling mode unless explicitly asked.
- Preserve the user's wording as much as possible.
- Lightly correct obvious typos only when doing so does not change meaning.

## Fallback Policy

Do not write or use a second hidden prompt system.

Fallbacks are supports, not extra required prompts. Offer a gentler way into the same canonical question only when the user is stuck, blank, asks for help, becomes self-punitive, or makes a fatalistic global claim from one event.

Do not use fallbacks merely because an answer is sad, angry, negative, or difficult. Never pressure the user toward positivity. The aim is honest contact with reality plus a small foothold for living.

When offering a fallback, keep it brief and connected to the same question. Do not force a specific fallback wording.

## Saving Entries

Completed sessions are saved automatically.

An automation wake-up is not a completed session. An automation must never create, save, commit, or push an empty entry. Do not create a daily entry file merely because an automation woke up. Save only after the user has answered and the session is complete.

Entries go in:

```text
entries/YYYY-MM-DD.md
```

If the file does not exist, create it with:

```md
# YYYY-MM-DD
```

Append each session under one of these headings:

```md
## HH:MM - Session 1
```

```md
## HH:MM - Session 2
```

Use each canonical question as a level-three heading followed by the user's answer.

## Git Behavior

After saving a completed non-empty session, create exactly one local commit.

Use these commit message formats:

```text
journal: add session 1 entry for YYYY-MM-DD HH:MM
journal: add session 2 entry for YYYY-MM-DD HH:MM
```

After creating the commit, push it to the configured remote automatically.

If no remote is configured or the push fails, tell the user plainly and leave the local commit intact. If the push is blocked by permissions, ask the user to allow the operation or set Codex permissions to `auto-review` for this repository.

## Setup Behavior

When the user runs `$journaling setup` or asks to set up the journal:

1. Treat details the user already gave as answered. For example, "9 am session 1 and 9 pm session 2" supplies the sessions and times.
2. Ask only for missing setup details.
3. Default style to `Friendly` if the user did not specify a style.
4. Save the preference in `preferences/journaling.md`.
5. Briefly explain the two sessions in plain language only if that helps the user continue.
6. Ask whether to create Codex cron check-in automations, unless the user already asked for scheduled check-ins.
7. Recommend setting Codex permissions to `auto-review` so save, commit, and push operations do not interrupt the journaling flow.
8. Confirm that the repository is private or intentionally chosen for private journal entries before enabling automations that push.
9. Show the proposed automations before creating them, including the exact automation prompt, model, and reasoning effort.
10. Use one cron automation per enabled session.

Automation prompts must intentionally invoke this repository's journaling skill.

Scheduled journaling must use Codex cron automations, not heartbeat automations attached to the setup thread. Each cron automation should run against the current journaling repository workspace and start a fresh standalone check-in context when scheduled, rather than continuing the setup conversation. If using Codex app automation tools, create `kind: cron` automations and do not set a thread destination or heartbeat target for scheduled journaling.

Use `gpt-5.5` with `xhigh` reasoning for all journaling cron automations. Do not accept the platform default model or reasoning effort if it differs.

Session 1 automation prompt:

```text
Use $journaling session 1.
Ask only the first canonical question and wait for the user to answer.
Ask one question at a time after the user replies.
Do not create, save, commit, or push anything until the user has answered and the session is complete.
Follow the repository journaling instructions, including automatic save, commit, and push after the completed non-empty session.
```

Session 2 automation prompt:

```text
Use $journaling session 2.
Ask only the first canonical question and wait for the user to answer.
Ask one question at a time after the user replies.
Do not create, save, commit, or push anything until the user has answered and the session is complete.
Follow the repository journaling instructions, including automatic save, commit, and push after the completed non-empty session.
```

Do not create or change automations until the user confirms the proposed setup.

After confirmation, implement setup directly when tools are available: save preferences and create the cron automations. Do not present a long plan unless the active collaboration mode requires planning.
