# Run a tracking report

Read `brief.md` and `state.json` for the selected profile. Use the active brief as the source of organizational priorities and report settings, even when chat history suggests an older scope. Resolve missing material configuration in an interactive run; report it as a configuration failure during an unattended run. Do not invent settings or recover corrupt state by silently replacing it with an empty history.

## Collect evidence with explicit coverage

1. Fix a UTC cutoff at the start of the run. For each active source, start at its last successfully covered cutoff, or the configured initial lookback if it has none. Include the boundary again and deduplicate by item identity. After an outage, cover the missed interval rather than just the latest nominal reporting period.
2. Query releases and relevant pull requests, issues, and discussions through the available GitHub connector. Use updated activity as well as creation dates so older work that changes status is discovered. Read developer posts through a feed or archive and retrieve the relevant full posts. Search results and snippets help discover evidence but do not substitute for reading it.
3. Follow pagination and narrow broad result sets by time or topic where needed. If a result cap, missing page, inaccessible endpoint, or unreadable article prevents the intended scan, mark that source partial or failed. Search indexing alone does not establish complete blog coverage. Record the retrieval method and its limits.
4. Inspect primary evidence for candidate findings, including the release contents when claiming that merged work shipped. A merged pull request and a later release in the same repository do not alone establish inclusion in that release. Treat benchmark and roadmap statements as attributed claims unless independently supported.
5. Use a bounded recovery attempt when a source fails: retry a transient error once, or use a public primary-source alternative. Honor rate limits and stop repeated retries during the current run. Continue other sources and preserve the failure for the next run.

For a partial scan, report verified findings with the gap disclosed. Advance that source's checkpoint only when the configured scan is complete; an archive page that loads does not prove that unreadable candidate posts were assessed. Complete coverage means the agreed tracking method was executed, not that all possible project activity was exhaustively examined.

## Decide what changed and why it matters

Assess each retrieved candidate against the saved priorities, exclusion rules, and open decisions. Save enough of the assessment to avoid treating the same item as new on the next run. Give attention to material capability changes, compatibility or support changes, credible adoption signals, or project direction when the brief makes them relevant. Do not fill space with routine activity.

Use the canonical URL or a stable provider ID as an item's key. Retain URL aliases when available. Group a release, its announcement post, and associated pull requests into one development with supporting links. Keep each source item in state, even when several items support one finding.

Compare the substance with the last assessment and, separately, the last report. A changed timestamp, typo, new reaction, or repeated announcement is insufficient for another finding. A proposed feature becoming available in a release can be material; explain that transition without presenting the earlier proposal as new. Cross-source deduplication must use meaning, not just matching URLs.

When a previously assessed item becomes relevant under a revised brief, identify the changed scope and the item's original date. Do not imply that it was just published. A newly discovered source may supply evidence for a current finding, but list it as a proposed watchlist addition with its relevance explanation. Do not silently subscribe to it.

## Write the report for its intended reader

Start with the strongest supported conclusion about what changed for the organization. Develop the connection from observation to implication in natural business English. Use headings only when they help the configured report; these are default content requirements, not mandatory headings:

- **Opening assessment:** What deserves attention and why, including uncertainty that changes the conclusion.
- **Relevant developments:** Concise project updates with source dates, links adjacent to claims, status, organizational relevance, and material limits. Explain necessary technical terms.
- **Suggested follow-ups:** Decisions or checks supported by the findings. Do not invent owners, deadlines, adoption readiness, or an obligation to act.
- **Source proposals and coverage:** Useful additions, sources checked, actual intervals, and specific failures or limits. Keep this compact, using a table when comparison helps.

Avoid quantitative importance scores unless the brief defines meaningful criteria. Separate facts from your assessment in the prose without turning every paragraph into labeled fragments. Do not substitute excitement, activity counts, or headline language for evidence.

A quiet-period report should say that no material changes were found in the successfully checked sources. If any source is incomplete, qualify the statement and identify the gap; if every source failed, report that no assessment was possible. Keep the same coverage and persistence rules for quiet runs.

Save each report as Markdown. Include its profile ID, brief revision, run ID, UTC cutoff, and whether the run is complete, partial, or failed. Label the initial report as a baseline. The main report period may include multiple source-specific intervals after a failure; make those differences visible in coverage.

## Save state without losing evidence

Start from [the state template](../assets/state-template.json). Use UTC RFC 3339 timestamps in state. Populate only actual observations; use `null` where no successful observation exists.

| Record | Minimum content |
| --- | --- |
| `version`, `profile_id` | State format version 1 and the matching profile ID. |
| `last_run` | Run ID, report path relative to the profile, cutoff, completion time, brief revision, and status (`complete`, `partial`, or `failed`). |
| `sources[source_id]` | `last_successful_through`, `last_attempt_at`, status, retrieval method, and any coverage gap or error. |
| `items[item_key]` | Source ID, canonical URL and aliases, project ID, observed status and material summary, assessment revision, disposition (`reported`, `duplicate`, or `excluded`), and related item keys. Preserve `last_reported_status`, `last_reported_summary`, and `last_report` separately, using null before an item has been reported. |
| `proposed_sources` | Candidate URL, project, relevance explanation, and when it was proposed; these are not active sources. |
| `automation` | Native automation ID, kind, destination reference, saved timing and timezone, and confirmed status, or null if none exists. |

Reuse previously saved source and item records instead of rebuilding history from only this run. Keep failed and retired sources' history. For source failures, update the attempt and error information while preserving `last_successful_through`. Successful sources can advance independently.

Write and verify the report before replacing state. Prepare the updated JSON in a temporary file in the profile directory, parse it successfully, then replace `state.json` atomically. Recheck that the original state has not changed before replacement; if another run or schedule edit changed it, stop and reload rather than overwrite it. Avoid simultaneous runs of one profile.

If report persistence fails, do not advance any source checkpoint or mark findings as reported. If state persistence fails after the report was saved, say so and retain the previous state. On retry, inspect any newer saved report before emitting the same findings again, and reconcile only observations supported by that report or freshly retrieved evidence. Never advance a checkpoint merely to match a wall-clock reporting period.

Finish with a short chat summary and an absolute Markdown link to the saved report. State material coverage or persistence failures in that summary. Quiet periods still receive a short status. A manual run does not create or modify a schedule unless that was also requested.
