# Journal goals

Goal management and achievement acknowledgement are owner-only. Reads use the journal's current SQL visibility rules, including profile privacy and accepted friendships. APIs authenticate members and return private/no-store responses. Goal progress never exposes entry notes.

Volume counts distinct dated original sends in the chosen discipline, either at an exact grade or at that grade and harder. Repeats and undated sends do not contribute. First-grade milestones complete at the chosen grade or harder; an existing send at that grade or harder prevents creating the milestone. Training counts training entries. Climbing days count distinct session dates. New areas count first logged visits to direct climb areas, not ancestors or repeat visits.

Dates are civil dates in each goal's saved timezone. Weeks start Monday; months and years are calendar periods. Presets include existing logs within the window. Custom ranges preserve explicit start/end dates. Grade milestones cannot recur. Training supports week/month/custom deadlines and weekly/monthly recurrence; other goal types also support yearly recurrence.

Active contains unfinished one-time goals whose deadline has not passed, and current recurring goals. Expired one-time goals appear in History as Not met and free capacity. Editing preserves historical dates; Restart creates a new goal and leaves the old attempt intact. The five-active-goal limit is enforced in the write statement, including concurrent requests. Edits that remain inactive or do not increase active count are allowed at capacity. Corrected logs can reactivate an unexpired goal; all reactivated goals remain visible and new creation is blocked at capacity.

History includes met and missed results and groups each goal once per selected year, retaining recurring history even after conversion to one-time. Only met results count as achievements. One-time results belong to their completion year, or deadline year when missed; recurring periods belong to their start year. Cadence changes preserve ended periods and apply the new calendar window to the current attempt. Overlapping old/new windows may both include a log, but the goal is counted once in the yearly total. Snapshots retain the original type, grade, target, cadence and timezone; progress remains derived from logs.

Initial journal reads share one goal aggregate query. History pagination uses stable calendar bounds: three months for weekly routines, twelve for monthly routines, five years for yearly routines. Contribution requests identify the period by start and end dates so overlapping cadences cannot be confused. All reads recheck visibility; no cross-request result cache is used.

Achievement detection is independent of the contributing log date. New goals start detection immediately; pre-feature history is baselined silently on the owner's first visit. Unseen achievements remain pending across days and devices, including backdated logs. View or dismiss acknowledges the displayed goal/period keys together. Corrected/deleted logs remove invalid pending results, while acknowledgement remains durable so deleting and relogging does not celebrate the same period again.

Form styling and interaction examples live in Components / Goals / Goal form. Patterns / Goals shows the real components together in the Journal.
