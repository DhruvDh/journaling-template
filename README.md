# Journaling Template

This is a small Codex journaling template. It is for writing private plain-text journal entries with two simple sessions.

Codex's job here is to stay out of the way. It asks one question at a time, saves the entry, commits it locally, and pushes it to your configured remote.

## Start Here

Use this template to create your own private journal repository.

Do not fork this public template for private journal entries. GitHub says forks of public repositories are public and their visibility cannot be changed. A repository created from a template can choose its own visibility.

1. On GitHub, click **Use this template**.
2. Choose **Create a new repository**.
3. Set the new repository to **Private**.
4. Open your private repository in Codex.
5. Run:

```text
$journaling setup
```

The setup will first ask whether you prefer a `Friendly` or `Pragmatic` conversational style. If you are not sure, use `Friendly`.

For the smoothest experience, set Codex permissions to `auto-review` for this repository. The journal saves entries, creates local Git commits, and pushes those commits after completed sessions, so routine version-control actions may otherwise be interrupted by approval prompts. Because entries are pushed automatically, use a private repository for your journal.

## The Two Sessions

The template has two sessions. You can use either one without knowing anything about journaling.

Session 1 is for what is presently on your mind and in your body.

Session 1:

```text
$journaling session 1
```

Session 2 is for reflecting on what happened and what it means.

Session 2:

```text
$journaling session 2
```

Codex will ask one question at a time. You do not need to know how to journal or reflect before using this. Answer plainly. A sentence is enough if that is what comes.

When you complete a session, Codex saves it automatically to:

```text
entries/YYYY-MM-DD.md
```

Codex also creates one local Git commit for the saved session and pushes it to your configured remote.

## Automations

During setup, Codex can help you create recurring cron check-ins for either session. These scheduled check-ins start fresh standalone check-in contexts instead of staying attached to the setup conversation. Codex will use details you already gave, ask only for missing preferences, show the proposed automations, and wait for confirmation before creating them.

Each automation intentionally invokes `$journaling session 1` or `$journaling session 2`.

When an automation wakes up, it only starts the check-in by asking the first question. It waits for you to answer before continuing. If you do not answer, it does not create an empty entry, commit, or push anything. Entries are saved, committed, and pushed only after you complete a session.

## Credits

The two prompt sets are inspired by The School of Life and Jared Henderson.

## GitHub Notes

- GitHub docs on creating a repository from a template: https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template
- GitHub docs on fork visibility: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-permissions-and-visibility-of-forks
