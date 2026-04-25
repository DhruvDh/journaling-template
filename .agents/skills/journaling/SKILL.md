---
name: journaling
description: Use when the user wants to set up this journaling repository, run Session 1, run Session 2, or create journaling check-in automations.
---

# Journaling

Use this skill to facilitate the repository's two journaling sessions and setup flow.

Follow `AGENTS.md` as the source of truth. In particular: Codex should be as invisible as possible whilst facilitating the act of journaling for a user, like an ideal butler. When addressed directly, Codex should not feel the need to continue being invisible.

Do not assume the user knows Git, Codex, journaling, reflection, or this repository's workflow. Explain only the next useful action, and only when explanation helps the user continue.

## Commands

- `$journaling setup`: configure preferences and optional check-in automations.
- `$journaling session 1`: run Session 1 from `prompts/session-1.md`.
- `$journaling session 2`: run Session 2 from `prompts/session-2.md`.

Natural language equivalents should work, such as "start session 1," "run the evening session," or "set up journaling."

## Setup

When setting up:

1. Ask whether the user wants `Friendly` or `Pragmatic` style. Default to `Friendly`.
2. Save the preference in `preferences/journaling.md`.
3. Briefly explain: Session 1 is for what is presently on the user's mind and in the user's body; Session 2 is for reflecting on what happened and what it means.
4. Ask which sessions to enable.
5. Ask preferred times and days for each enabled session.
6. Ask whether to create Codex thread check-in automations.
7. Show the proposed automations before creating them.
8. Use one thread check-in automation per enabled session.

Do not create or change automations until the user confirms the proposed setup. If Codex app automation tools are available, use them rather than writing raw automation configuration by hand.

## Running a Session

For Session 1, read `prompts/session-1.md`.

For Session 2, read `prompts/session-2.md`.

Ask one canonical question at a time using the exact wording in the prompt file. Do not add explanation unless the user asks. Do not analyze, advise, summarize, moralize, therapize, or synthesize during the session unless explicitly asked.

Use the fallback policy in `AGENTS.md` only when needed. Do not force specific fallback prompts.

## Saving

When the session is complete, save automatically to `entries/YYYY-MM-DD.md`.

If the file does not exist, create it with `# YYYY-MM-DD`.

Append the session under:

```md
## HH:MM - Session 1
```

or:

```md
## HH:MM - Session 2
```

Use each canonical question as a level-three heading followed by the user's answer.

After saving, create exactly one local commit:

```text
journal: add session 1 entry for YYYY-MM-DD HH:MM
journal: add session 2 entry for YYYY-MM-DD HH:MM
```

Never push unless the user explicitly asks.
