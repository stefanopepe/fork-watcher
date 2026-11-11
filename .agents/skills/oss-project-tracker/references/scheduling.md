# Schedule a tested tracking profile

Use the host's native automation tools for scheduling. Discover `automation_update` and read its current schema and instructions before calling it. Do not install a cron job, write scheduler configuration files, or substitute an external scheduling service.

## Establish timing and destination

A request to build or configure this skill is not a request to start tracking an unspecified organization. Schedule a concrete profile only after recurring tracking is requested, cadence and named timezone are known, and a manual report has tested its essential sources and output. These prerequisites do not require another permission question when already established.

Default to a heartbeat that returns to the current chat. Use a standalone scheduled task only when the user requests separate runs or standalone project work. For that case, resolve the project using the native project tools. Keep the model and reasoning effort at the host's defaults unless the user requests otherwise or the tool requires explicit values.

Use the existing local storage root for every run so checkpoints and reports persist. For this local workflow, the computer, desktop app, and repository need to be available at run time. Do not choose isolated worktrees that split one profile's state between checkouts. Explain this operational requirement when showing the schedule.

Convert the user's local timing using its named timezone through supported scheduler fields. Check the tool-returned timing when available, especially across daylight-saving changes. If the available tool cannot express the requested timezone or cadence faithfully, explain the limitation and retain a proposal instead of claiming that the schedule is active. Do not show raw recurrence rules to the user.

## Use a durable prompt

The saved prompt must explicitly invoke `$oss-project-tracker`, name the profile ID, and include absolute paths to the profile storage root and the installed `SKILL.md`. Make clear that each run must:

- Read the current brief and state rather than relying on chat memory.
- Follow the skill's reporting workflow for changes since each source's successful checkpoint, including missed intervals.
- Save the Markdown report and updated state, then return the short summary and report link, including quiet-period status and coverage gaps.
- Keep new sources as proposals and leave source checkpoints unchanged for incomplete scans.
- Report missing configuration or access rather than starting an unattended interview or claiming a successful check.

Describe the work in cohesive, user-readable prose. The prompt should reference the saved brief rather than copy its full watchlist or priorities, so ordinary profile edits take effect on the next run. Keep scheduler notification preferences in the scheduler's fields rather than in this prompt.

## Create or update the actual schedule

Check `state.json` for an automation ID. Before creating a new schedule, inspect available native automation records for a matching profile and storage root; follow the tool's documented discovery method. Avoid duplicates. If discovery is unavailable and the profile may already be scheduled, resolve that uncertainty rather than blindly create another job.

Use the native tool to create or update the resolved schedule, preserving unrelated existing settings. Change only the requested timing, status, destination, or prompt. For pause or deletion, affect the identified schedule and retain the tracking history.

Record the returned automation ID, destination, timing, timezone, and actual status in state only after the tool confirms the operation. A proposal, pending action, or rejected call is not an active schedule. Update the report settings in the brief to match confirmed timing, without resetting coverage or item history. For deletion, clear the active automation reference after success.

If the tool succeeds but saving the reference fails, report that the schedule exists and give its returned identifier; do not create another one on retry. If access is denied or the scheduler is unavailable, retain the tested profile and explain what is missing without claiming that it will run.

Show the user the resulting cadence, timezone, destination, and active or paused status in plain language. Link the latest sample report so the recurring output is reviewable.

For current host behavior, consult [official scheduled-task guidance](https://learn.chatgpt.com/docs/automations?surface=app) when needed.
