# Roller Derby Officials Scheduler

A standalone browser-based scheduler for flat track roller derby officiating.

## Versioning

- Current version: `1.06`
- Default increment rule: increase by `0.01` for each update unless explicitly requested otherwise.
- Keep this README updated with a per-version changelog entry whenever features or behavior change.

Version files to update on each release:

- `index.html` -> `APP_VERSION`
- `version.json` -> `version`

## Version history

### 1.06

- Updated lock assignment flow so the official dropdown now only shows officials who can perform the currently selected role.
- Updated Day Overview last column label from `Total Available` to `Total Available Officials`.

### 1.05

- Reworked Day Overview into per-day visual tables.
- In each day table, each game is a row.
- Role columns now use role short names only, and each cell shows the count of officials who can perform that role for that specific game.
- Added a final `Total Available` column showing how many officials are available for each game.
- Added `Head NSO` as a standard default role with short name `HNSO`.

### 1.04

- In generated schedule tables, role rows now show only each role short name (no `#1/#2/#3` suffixes).
- Unassigned schedule slots are now displayed as empty cells instead of the text `blank`.
- Excel copy output now leaves unassigned slots as empty-space cells instead of the text `blank`.
- Added a top-right `What's New` toggle that expands/collapses latest changes pulled from the two newest README version entries.
- Clicking the top-right version label now opens `README.md` in a new tab.

### 1.03

- Schedule generation now allows incomplete staffing: if not all slots can be filled, remaining slots are kept as `blank` instead of failing generation.
- Generated schedule matrix now shows separate rows per role slot (for example `Outside Pack Ref #1`, `#2`, `#3`) instead of combining multiple officials in one cell.
- Excel copy output now matches the per-slot row format and includes `blank` for unfilled slots.

### 1.02

- Added built-in demo name pools with 100 first names and 100 last names for generated officials.
- Updated demo official generation so created officials can have 1 to 4 roles.
- Updated demo official generation so some officials get a preferred role and some do not.
- Updated demo official behavior: it first creates enough officials to reach minimum role coverage, then each later click adds 10 extra officials.

### 1.01

- Added automatic version manifest check (`version.json`) with cache-busting reload when a newer deployed version is detected.
- Added cache-control meta hints to reduce stale page caching in browsers.

### 1.00

- Added an on-page version badge in the top-right corner so you can quickly confirm which build is loaded.

## What it does

- Lets you add matches with date and time.
- Lets you generate schedules per selected day.
- Includes a day overview with per-day tables showing role coverage by game.
- Uses one unified officials pool (Ref and NSO mixed as needed).
- Lets you define one role list where roles can be Ref, NSO, or both.
- Lets you edit role counts inline without recreating roles.
- Lets you rename roles and assign optional short names.
- Lets you add and edit officials with role capabilities and match-level unavailability.
- Lets each official have an optional preferred role.
- Generates a complete schedule for the selected day.
- Shows generated schedule as a table matrix: roles on rows, matches on columns.
- Lets you copy the generated table directly to Excel (tab-separated format).
- Supports locked assignments (specific official -> specific role -> specific match).
- Prioritizes break-friendly rotation across games when possible.
- Supports JSON export/import for sharing full schedules.
- Includes a top action bar with Download Site, Export Schedule JSON, and Import Schedule JSON.
- Top action bar also has Clear Matches, Clear Officials, Generate Demo Officials, and Reset to Default Settings.
- Default roles are pre-seeded to the current league role set (including short names and required counts).

## How to use

1. Open `index.html` in a browser.
2. Add matches with day, time, and name.
3. Add roles and set required count per match.
4. Add officials, select all roles they can perform, and optionally set a preferred role.
5. Mark unavailable matches per official.
6. Use Edit on any official to quickly update availability, roles, or preference.
7. Select a day and click Generate Schedule for Selected Day.
8. Optional: lock assignments for specific match/role/official in the lock controls above the schedule.
9. Use Copy Table for Excel to copy a matrix that can be pasted directly into a spreadsheet.
10. Use Day Overview to see which days are likely short on people.
11. Use Export Schedule JSON / Import Schedule JSON (top buttons) to share or load data.
12. Use Download Site (top button) to save an offline copy of the scheduler page.
13. Use Clear Matches or Clear Officials (top buttons) to reset those sections without deleting roles.
14. Use Generate Demo Officials to auto-create enough officials to cover missing role counts.
15. Use Reset to Default Settings to clear all data and restore the default roles from scratch.

## Default roles

The app starts with these default roles when a new user opens it (or after Reset to Default Settings):

| Role | Short | Required per match |
| --- | --- | --- |
| Head Ref | HR | 1 |
| Head NSO | HNSO | 1 |
| Outside Pack Ref | OPR | 3 |
| Jammer Ref | JR | 2 |
| Inside Pack Ref | IPR | 1 |
| Penalty Box Timer | PBT | 2 |
| Penalty Box Manager | PBM | 1 |
| Jam Timer | JT | 1 |
| Score Board Operator | SO | 1 |
| Score Keeper | SK | 2 |
| Penalty Lineup Tracker | PLT | 2 |

## Notes

- Scheduling data is saved in browser local storage.
- Current storage key: `rollerderby-official-scheduler-v3`.
- Storage location: your browser profile localStorage for the origin used to open `index.html`.
- To move both app and data to another computer: download the site and export the schedule JSON, then import the JSON on the other computer.
- Existing v1 and v2 data is migrated automatically.
- Preferred role is a tie-breaker only; break rotation and fairness are prioritized first.
- Locked assignments are enforced during schedule generation.
- If staffing is insufficient, generation still succeeds and leaves unfilled slots as `blank`.
- Unfilled slots are displayed as empty cells in the schedule table and export.
- If a role has a short name, it is shown in official role selection and preferred role dropdown.
- Generate Demo Officials creates placeholder officials to satisfy role counts where needed.
- Demo officials use mixed role profiles (1 to 4 roles) and mixed preferred-role usage.
- Once minimum role coverage is reached, Generate Demo Officials adds 10 extra officials per click.
- Reset to Default Settings clears matches, officials, and generated schedules, then restores default roles.
- If generation fails, adjust constraints (more officials, fewer slots, or availability updates).
