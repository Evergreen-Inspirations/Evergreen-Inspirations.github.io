# Paused Not Dropped — health and care, phase one

## Implemented
- Today, Health and Care Team navigation in the existing single-file app.
- Dated capacity in named 10-point steps (-100 ER visit to +100 everything wanted), mood and context check-ins.
- Goal progress derived from task statuses: completed / non-dropped tasks, with all status counts shown. Tasks count equally per linked goal; historical manually entered progress stays in saved data but is no longer used.
- Task status dropdowns and a Touched today badge based on local calendar dates, excluding old or undated log entries.
- Achievement, maintenance, health, recovery, connection, joy and care entries.
- Symptom episodes with context, interventions, impact, timestamped updates and resolution.
- Providers, linked appointments, questions, notes, orders and follow-up dates.
- Medication/supply notes, injection history and lab result history.
- Editing and reversible archiving.
- Model version 2, legacy migration, full snapshot backups and a local pre-replacement recovery copy.

## Validate
Run `node private-tools/paused-not-dropped.test.mjs` from the repository root.
Browser smoke checks covered check-in creation, episode updates and resolution, provider/visit linking, editing, reload persistence, archive/restore and a phone-width layout without horizontal overflow. All browser examples were synthetic and local.

## Rollout
The app remains one self-contained HTML file at its existing URL. Refresh the app on both phone and computer before using the expanded data; old open versions discard unfamiliar fields when normalizing a snapshot.
The existing Apps Script accepts the same JSON payload envelope; no script changes are required for this first version. Google Sheets stores the complete payload, not individual tabs for each collection. A live Google Sheets round trip with the user's credentials has not been performed.
Sync is still manual and replaces device data. Before replacement, confirm the direction and download a backup if needed. A recovery snapshot is saved locally before import/load.
The existing no-cors save cannot confirm server acceptance. The UI describes this honestly. The current single-cell backend has a conservative 45,000-character payload guard; larger histories require a backend storage upgrade. No automatic merging is implemented.

## Next increments
- Trend charts and date filtering; usable summaries for appointments.
- More tailored migraine, fatigue, mobility and treatment forms.
- Testosterone dashboard, prescribed-schedule supply estimates and upcoming care summary.
- Larger Sheet storage, confirmed saves and conflict-aware sync.
- Gentle visual recognition of progress on low-capacity days, without prescribing a productivity score.

No personal health entries or sync credentials are embedded in the new code.
