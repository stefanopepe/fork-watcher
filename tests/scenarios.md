# Behavioral validation scenarios

Exercise the skill in an isolated temporary directory with a copied profile and supplied source responses. Do not change a real watchlist, call a live scheduler, or publish a report during these scenarios. Use Markdown and JSON only. A structural validator alone does not establish these behaviors.

| Scenario | Input | Observable result |
| --- | --- | --- |
| Sparse setup | A project seed and organizational description without priorities or timing. | The next response seeks material organizational decisions before designing the report. It does not invent priorities, findings, or a schedule. |
| Related announcements | A release, its official blog announcement, and linked implementation pull request. | One substantive development cites the supporting sources. State retains the individual source items. |
| Status transition | A previously reported open pull request is merged and explicitly included in release notes. | The report explains that the previously proposed capability has shipped, distinguishes status from production readiness, and preserves the prior reporting history. |
| Routine activity | Formatting or UI changes outside the brief's relevance criteria. | The report omits the activity as a finding and records its assessment so it does not reappear as news. |
| Partial coverage | One source fails while other sources produce readable evidence. | The report identifies the gap. Successful sources advance independently, while the failed source retains its successful checkpoint. |
| Catch-up and quiet period | Repeated announcements plus recovery of a failed source, with no material new information. | The report is a short status; it covers the failed source's missed interval without repeating earlier findings. |
| New source | A relevant post refers to another project or source. | The addition is proposed with its relevance explained, and the active watchlist remains unchanged. |

Also inspect these persistence and scheduling rules when changing the corresponding instructions:

- A report that cannot be saved must not advance source checkpoints or mark findings as reported.
- Invalid or concurrently changed state must not be silently reset or overwritten.
- A renamed source or revised brief preserves earlier reporting history.
- Setup alone must not create a schedule. A requested schedule uses the tested profile and confirmed local timing, and its saved prompt includes the profile and absolute storage paths.
- Updating, pausing, or deleting a schedule targets its existing native automation and records only a confirmed tool result.

For packaged skill structure, run the installed skill-creator's `quick_validate.py` against the skill directory using a Python environment with PyYAML available. Check local Markdown links, parse the JSON state template, and confirm that the package contains no unfinished scaffolding or Office files.
