# Establish and revise a tracking profile

Use this workflow for initial setup or a substantive change of priorities, watchlist, or output. Preserve established choices unless the user changes them. Read an existing brief before asking questions.

## Understand the organization before designing the report

Begin with authorized workspace context and what the user has already said. Establish the organization's work, relevant technology dependencies, current priorities, and decisions the tracking should inform. Useful questions connect projects to intent: “Which part of your product depends on this project?” or “What change would make you reconsider adoption?” Avoid a long generic questionnaire or inventing organizational facts.

Ask for missing information in small groups while continuing independent research. Mark assumptions and unresolved questions explicitly. Separate facts about the organization from your interpretation of what may matter to it. Do not send confidential organizational details in public searches; research public project names and technical topics instead.

Default to engineering and strategy together. Identify both operational concerns, such as compatibility or upgrade effort, and choices about capabilities, adoption, and project direction. An individual source or project may serve only one of these purposes.

## Establish what to track and how

Start from the projects, repositories, or technical topics the user provides. Verify project identities and canonical repositories, then look for official developer blogs, release notes, and relevant maintainer writing. Prefer primary sources; record why a secondary source is needed when it supplies otherwise unavailable evidence.

Create a proposed watchlist with stable project and source IDs. Record each source's URL, kind, project, relevance, and coverage, such as releases plus selected pull requests or a developer blog's project-specific category. A repository may cover several GitHub activity types under one source ID. A blog can be a separate source for the same project. Distinguish an official project source from an individual maintainer's personal opinion.

Translate priorities into practical inclusion rules. For example, if adoption depends on a stable API, track compatibility changes, release readiness, and maintainer statements about support. Exclude routine refactoring unless evidence connects it to a priority. Decide which issues, labels, paths, or technical themes warrant closer inspection, without prescribing filters that the sources cannot support.

Show the proposed tracking approach before treating it as settled. Incorporate corrections in the same conversation. Do not make this an extra approval gate if the user has already supplied a clear watchlist or authorized you to select sources. During later runs, newly discovered sources remain proposals until the user requests an addition.

## Define the output after the tracking approach

Once the organizational purpose and source coverage are clear, recommend a report that serves the reader's decisions. Establish:

- The audience and what they need to understand or decide.
- The report's structure and level of technical detail; default to a brief with evidence.
- Cadence, local time, and named timezone. Use an established timezone from the user context; ask only when it is unknown or ambiguous. Do not infer cadence from the timezone or invent a recurring time.
- The initial lookback period, agreed during setup. Recommend the previous 30 days for a baseline unless the question calls for another period.
- The report destination, defaulting to Markdown in this profile and a concise summary in the current chat.

Use a short status during quiet periods, including any coverage gaps. The default is periodic reporting rather than immediate alerts. Sending a report through email, Slack, or another messaging service requires an explicit request with a destination; saving local Markdown does not authorize external distribution.

Start from [the brief template](../assets/brief-template.md), replacing its prompts with actual decisions. For unresolved settings, state what is unknown rather than leaving an apparently complete configuration. Choose a stable, descriptive, lowercase profile ID; do not overwrite a different organization's profile. Set its brief revision to 1 and increment it when priorities, watchlist, or relevance rules change. Report formatting or timing changes alone do not require reassessing old items.

Initialize [state.json](../assets/state-template.json) with that profile ID. Leave source checkpoints empty until a manual run actually reads and processes the sources. Do not create fictional findings or timestamps to fill a baseline.

## Test and activate the workflow

Run [the reporting workflow](run.md) manually once priorities, sources, and the initial period are sufficient. Timing may remain unset for this manual report. Save a genuine sourced baseline and explain any tool or source limitations. A baseline is the current starting position, not a claim that every item was newly announced during setup.

Use the sample to resolve material output problems. When recurring tracking is requested, timing is known, and the manual run demonstrates usable coverage, follow [scheduling.md](scheduling.md). Do not activate a schedule whose essential sources cannot be reached without unattended approvals. Explain the specific missing capability instead.

## Revise without losing history

Change only the requested parts of the brief. Keep source IDs stable when a canonical URL moves, retaining the previous URL as an alias. Initialize newly added sources from the configured lookback period; preserve other sources' coverage. Retire removed sources without deleting their historical observations.

When relevance rules or organizational priorities change, reassess the configured lookback period under the new brief revision. Keep prior reporting history so the report can explain that an older development became relevant under the revised scope. Changing cadence does not reset checkpoints. Update the saved automation if the user changes its timing; a Markdown edit alone does not change a live schedule.
