# fork-watcher

`oss-project-tracker` is a reusable Codex skill for following open-source GitHub projects and developer blogs in the context of an organization's priorities. It first establishes what to track and why, then defines the recurring report. Each organization keeps its own tracking brief and history.

Open this repository in Codex and start with:

```text
Use $oss-project-tracker to set up tracking for our organization.
We care about [priorities] and want to start with [projects or topics].
```

The skill researches relevant repositories and developer writing and records the watchlist and relevance rules. It then establishes the audience, report detail, cadence, and timezone and produces a sourced baseline report. You can provide known context up front or work through setup conversationally.

The default output is a concise Markdown brief in understandable business English. It explains what changed, why it matters to the organization, and what follow-up the evidence supports. Quiet periods receive a short status, and incomplete source coverage is identified explicitly. New sources are proposed before they join the watchlist.

Profiles are stored under `tracking/<profile-id>/`, with a Markdown brief, JSON state, and Markdown reports. Reports cover changes since each source's successful checkpoint, including missed intervals after an outage. The repository contains no preconfigured organization or active tracking schedule.

After setup, requests can be as simple as:

```text
Use $oss-project-tracker to run the payments profile now.
Use $oss-project-tracker to report on that profile every Monday at 09:00 Asia/Nicosia.
Use $oss-project-tracker to exclude dashboard changes from that profile.
Use $oss-project-tracker to pause that profile's schedule.
```

Recurring runs use Codex's native scheduler and return to the current chat by default. The skill tests a manual report before activating a schedule. Because this version stores profiles locally, the computer, desktop app, and repository must be available when it runs. See the [official scheduling guidance](https://learn.chatgpt.com/docs/automations?surface=app).

The skill is under `.agents/skills/oss-project-tracker/`. It uses connected GitHub tools and web browsing; it does not require a custom crawler, database, or standalone bot. All prose artifacts are Markdown, with no Office formats. Repository-local behavior scenarios are documented in `tests/scenarios.md`.
