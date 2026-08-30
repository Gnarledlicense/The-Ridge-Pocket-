# The Ridge — Pocket: Backlog

Things discussed and deliberately deferred, not forgotten. Keep this file in the repo and update it as items get built or dropped.

---

## Open items

### 1. Real reminders / push notifications
- **Status:** Deferred, needs a real decision later.
- **Why it's not simple:** A notification firing while the app isn't open requires a Service Worker + the Push API + an actual push server running on a schedule. GitHub Pages is static hosting — it can't run that server itself.
- **Realistic paths, cheapest to most involved:**
  1. Native phone alarm/reminder pointing at the bookmarked URL (zero build, works today).
  2. A small serverless function (e.g. a free Cloudflare Worker) on a timer, using Web Push — a real project, genuinely separate infrastructure from this static site.
  3. iOS specifically only supports Web Push if the app is properly installed to the home screen as a PWA — finicky even then.
- **Decide later:** whether it's worth standing up (2), or (1) is good enough long-term.

### 2. "All" range chart — sparse-data edge case
- **Status:** Identified, not fixed, low urgency until real history builds up.
- **The issue:** "All" always buckets by month. With less than ~30 days of real history, everything collapses into a single monthly point, which renders as a near-invisible sliver instead of a spread-out line.
- **The fix, when it matters:** make "All" choose granularity (daily/weekly/monthly) based on how much real history actually exists, instead of a fixed monthly bucket.
- **Trigger to revisit:** once real logging has been happening for a few weeks and "All" is actually being used.

### 3. Real-time vs. backfilled entries
- **Status:** Raised, not designed.
- **The gap:** the app stores *what a day looked like*, not *when that data was actually entered*. Logging 8 days retroactively looks mathematically identical to living through 8 real days — momentum, streaks, and the Peaks chart can't tell the difference.
- **If it ever matters:** would need a second timestamp per day-record (entered-at, separate from the date it's *for*), and a decision on whether backfilled days should count toward momentum at all, or be flagged/excluded.
- **Not currently planned** — noted here specifically so it doesn't get silently forgotten, since it's the kind of design decision worth doing deliberately rather than as an afterthought.

---

## Resolved (for reference — remove once you trust the list above is complete)
- Skip-day option, specific-weekday scheduling, daily notes, self-compassion message, streak display, penalty flags, emoji-goal generalization, historical snapshot accuracy — all built and shipped.
