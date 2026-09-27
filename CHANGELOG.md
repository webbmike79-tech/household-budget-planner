# Changelog — Household Budget & Car Payoff Planner

Notable changes, newest first. The build tag is shown in the app footer.

## 2026.09.27s — 2026-09-27
- The footer now credits the builder: "Created by Speakeasy Support".

## 2026.09.27r — 2026-09-27
- New "401(k) Contribution" dropdown (0%–15%) in the income section: the percent comes out of gross pre-tax for income tax and lowers the estimated take-home; it also flows into the paycheck presets. The old fixed 6%-plus-health presets are gone.
- The paycheck presets now reprice live from what you actually enter — "$10/hour" no longer shows the $80k-salary numbers. Two options, Single and Married Filing Jointly, priced through the same tax engine as the main estimate, including your 401(k) percent.
- Typing your own monthly net pay clears the preset so later gross edits don't overwrite it; a selected preset stays live and re-prices when gross, hours, frequency, state, or locality change.

## 2026.09.27q — 2026-09-27
- Saved county (and city) tax rates now auto-fill from the on-device tax database when the name exactly matches a table entry, and the City/County kind switches to match. Manually typed rates are never overwritten, graduated localities aren't forced into the flat-rate field, and saving an exact table match selects the existing entry instead of adding a duplicate.

## 2026.09.27p — 2026-09-27
- The ZIP property-tax estimator now works offline: a bundled 947-prefix ZIP3-to-state table replaces the network lookup, the estimate re-runs when the home value is entered after the ZIP (entry order no longer matters), and it falls back to the selected tax state when a ZIP isn't recognized.
- The "Add your own…" city/county name field now suggests matching 2026-table entries as you type — tapping a suggestion selects it with its rate, so you never have to know the rate yourself.
- Locality seed expanded from 47 to 262 verified 2026 records: all 92 Indiana counties, 33 more Ohio cities, 33 Pennsylvania municipalities (resident/nonresident where they differ), 22 more Michigan cities (resident/nonresident), 14 Kentucky cities (wage base), Birmingham (AL), Wilmington (DE), and Multnomah County (OR). Seed version bumped 1→2 so existing installs reseed on the next load.


## 2026.09.27o — 2026-09-27
- The "Add your own…" city/county name field now gets an in-page alphabetic keyboard on touch devices, the same way numeric fields get the number pad (some mobile viewers never show the OS keyboard). The lock-screen keyboard was rebuilt on the same shared code with no behavior change.

## 2026.09.27n — 2026-09-27
- Tax tables now live in an on-device IndexedDB database (federal, all 50 states + DC, and city/county local taxes) instead of being baked into the page. If the database is unavailable the app falls back to the built-in tables, so it keeps working offline either way.
- New optional City/County tax picker under the state selector, seeded with 47 verified 2026 local income taxes: New York City and Yonkers (NY), all 23 Maryland counties plus Baltimore City, 6 Ohio cities, Philadelphia and Pittsburgh (PA), St. Louis and Kansas City (MO), Louisville and Lexington-Fayette (KY), Detroit and Grand Rapids (MI), and 3 Indiana counties. Coverage is curated, not nationwide — "Add your own…" covers any locality the list doesn't have.
- Local income tax is now deducted in the take-home estimate and shown in the tax breakdown (e.g. "Local (New York City, NY) $183.40/mo").
- Fixed Bill Calendar week dropdowns not recalculating when changed.

## 2026.09.26m — 2026-09-26
- Pay-frequency switching no longer loses pennies on round trips. The app keeps the exact annualized figure underneath and only rounds what's displayed, so annual → hourly → twice-a-month → every-two-weeks → annual returns the exact original number.
- Editing a pay figure or changing hours/week re-anchors the exact figure.

## 2026.09.26l — 2026-09-26
- Fixed frequency conversion silently doing nothing on a fresh load (the previous unit is now recorded on every page load, not only when restoring saved data).

## 2026.09.26k — 2026-09-26
- Switching pay frequency now converts the entered amount so the paycheck stays mathematically the same (e.g. $60,000/yr → ~$28.85/hr) instead of reinterpreting the same number in the new unit. Applies to both incomes; the previous frequency is remembered across saves.

## 2026.09.26j — 2026-09-26
- The lock/unlock UI is now an in-page card at the top of the page instead of a popup overlay (some Android viewers never delivered taps to the overlay, leaving it stuck).
- The passphrase keyboard is always shown inside the lock card; fields stay editable so normal typing works too.

## 2026.09.26i — 2026-09-26
- Added an in-page alphabetic keyboard and tap-outside-to-close for the passphrase popup (first attempt at the Android keyboard issue).

## 2026.09.26h — 2026-09-26
- ZIP-code property-tax estimator: enter a ZIP and estimated home value and the planner looks up the state and applies its median effective property-tax rate. Renters skip it; manually entered amounts are never overwritten.

## Baseline feature set
- All 50 states + DC (Texas default) with 2026 federal/state tax estimates across all five filing statuses.
- Pay-frequency converter: Annual / Monthly / Twice-a-month / Every-2-weeks / Weekly / Hourly, with hours/week for hourly rates.
- Gross pay auto-estimates monthly take-home; typing take-home directly overrides it.
- Optional second income (filing-status-aware).
- Own / mortgage / rent housing modes, generic car expenses with payoff planning, custom recurring bills, and a 4-week Bill Calendar.
- Touch-friendly in-page numeric keypad.
- Optional encrypted local-data vault (passphrase, PBKDF2-SHA256 + AES-GCM-256).
- CSV formula-injection protection and a content-security policy.
