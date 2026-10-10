# Checkbox Progress

Original repository: https://github.com/WallaceWyslas/obsidian-checkbox-progress

Obsidian plugin by Wallace Wyslas that shows the progress of the task checkboxes in the active note: a bar and a `completed/total (%)` counter in the status bar (desktop) or in the note header (mobile), with a button to reset all checkboxes and another to jump to the next unchecked one. It ignores frontmatter and code blocks.

Original version: **1.0.0**. This is a fork of the built files (not the source code), so `main.js` is edited by hand. Do not overwrite `main.js` when reinstalling or updating the plugin without reviewing these changes first (they are marked with `// Fork Ciges`).

## Modifications

Support for all the task statuses of the Tasks plugin. The status list is **not hardcoded**: it is read from the Tasks configuration (`statusSettings.coreStatuses` and `customStatuses` in `.obsidian/plugins/obsidian-tasks-plugin/data.json`) on startup and every time that file changes, so adding or changing a status in Tasks is picked up here without touching the plugin. If the file does not exist or cannot be read, the vault's default statuses are used (` `, `/`, `*`, `p`, `x`, `c`, `-`, `>`, `d`).

1. **Checkbox reset:** the button and the "Reset all checkboxes in current note" command set every known status other than ` ` back to `[ ]` (except `NON_TASK` types). Before, it only reset `x`, `X`, `-` and `/`.
2. **Progress counter:** checkboxes are counted according to their Tasks status type:
   - `DONE` (`p`, `x`, `c`): completed, included in the total.
   - `TODO` and `IN_PROGRESS` (` `, `/`, `*`, `>`): pending, included in the total.
   - `CANCELLED` (`-`, `d`) and `NON_TASK`: excluded from the total, since they will not be done.

3. **Go to next unchecked:** the command and the progress bar/counter click now jump to any pending checkbox (Tasks type `TODO` or `IN_PROGRESS`: ` `, `/`, `*`, `>`), not only `[ ]`, in both editor and reading mode.
