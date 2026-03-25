# Roller Derby Officials Scheduler

A standalone browser-based scheduler for flat track roller derby officiating.

## What it does

- Lets you add matches with date and time.
- Lets you generate schedules per selected day.
- Includes a day overview to estimate staffing pressure and likely shortage per day.
- Uses one unified officials pool (Ref and NSO mixed as needed).
- Lets you define one role list where roles can be Ref, NSO, or both.
- Lets you edit role counts inline without recreating roles.
- Lets you rename roles and assign optional short names.
- Lets you add and edit officials with role capabilities and match-level unavailability.
- Lets each official have an optional preferred role.
- Generates a complete schedule for the selected day.
- Supports JSON export/import for sharing full schedules.
- Includes a top action bar with Download Site, Export Schedule JSON, and Import Schedule JSON.
- Top action bar also has Clear Matches and Clear Officials (roles are preserved).

## How to use

1. Open `index.html` in a browser.
2. Add matches with day, time, and name.
3. Add roles and set required count per match.
4. Add officials, select all roles they can perform, and optionally set a preferred role.
5. Mark unavailable matches per official.
6. Use Edit on any official to quickly update availability, roles, or preference.
7. Select a day and click Generate Schedule for Selected Day.
8. Use Day Overview to see which days are likely short on people.
9. Use Export Schedule JSON / Import Schedule JSON (top buttons) to share or load data.
10. Use Download Site (top button) to save an offline copy of the scheduler page.
11. Use Clear Matches or Clear Officials (top buttons) to reset those sections without deleting roles.

## Notes

- Scheduling data is saved in browser local storage.
- Current storage key: `rollerderby-official-scheduler-v3`.
- Storage location: your browser profile localStorage for the origin used to open `index.html`.
- To move both app and data to another computer: download the site and export the schedule JSON, then import the JSON on the other computer.
- Existing v1 and v2 data is migrated automatically.
- Preferred role is used as a tie-breaker when multiple assignments are valid.
- If a role has a short name, it is shown in official role selection and preferred role dropdown.
- If generation fails, adjust constraints (more officials, fewer slots, or availability updates).
