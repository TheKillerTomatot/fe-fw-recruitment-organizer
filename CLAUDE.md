# Recruitment Planner: project notes

A spoiler-light planner for recruiting characters in Part I of *Fire Emblem: Fortune's Weave*. Live at https://thekillertomatot.github.io/fe-fw-recruitment-organizer/.

## Rules
- **Spoilers:**
  - May be visible: numbers, dates, item names, recruitable characters, lords, paralogue owners, and the hub city's name (Dagsion).
  - Behind the spoiler component: places, quest objectives, puzzle answers, who joins automatically, and story reasons.
  - Nothing from Part II or III.
- Write hints in your own words. Never copy text from guides or the game. No game assets.
- Every game fact needs a source. When guides disagree, say so in the character's details.
- The page makes no network requests: no CDNs, web fonts, analytics or external scripts.
- Keep LF line endings (`.gitattributes`); otherwise the published SHA-256 hash stops matching.
- The maintainer keeps additional notes outside this repository.

## Files
- `index.html` contains the whole tool: HTML, CSS and JavaScript.
- `README.md` holds the user guide, the hash and VirusTotal link for the current release, and the sources.
- `CONTRIBUTING.md` holds the issue guidelines and the **release checklist**.
- `LICENSE` is CC BY-NC-SA 4.0.
- `.gitattributes` keeps LF line endings.

## How `index.html` is organised
The script sections, in order: game data → in-game calendar helpers → rosters (built once) + `checkData()` → HTML helpers → state (load, sanitise, save) → queries → dates and deadlines → rendering → actions → events → start.

Game data tables at the top of the script:
- `ROUTE_TABLES`: per path, `Name|Support|Renown|chapter`. `3-4` means the guides disagree and the earlier chapter is used.
- `TUTORIAL`, `AUTO_JOIN`, `ROUTE_NOTES`.
- `REQUIREMENTS`, built with `gold()`, `item()`, `request()`, `paralogue()` and `talk()`. Values can be per-path maps resolved by `pick()`.
- `PARALOGUES`, keyed by owner. Each entry has `where`, an optional `prerequisite` / `note`, and `routes`, which maps each path to `[accept ranges "M/D-M/D, …", clear-by date, chapter it opens in]`. The chapters come from RPG Site's path walkthroughs and Serenes Forest's paralogue table (checked 2026-10-28).
- `STORY_GATES`, `CUTOFFS`, `APPEARS`, `REQUEST_HINTS`, `ITEM_HINTS`.

## Behaviour that is intended (don't "fix" it)
- **Sections** come from `sectionOf()`: "working" until the needed Support rank is ticked, then "ready" once Renown (and chapter, if entered) is met and `dateLock()` is null; otherwise "locked" (the waiting section).
- **Date lock** (only with an in-game date entered), in `dateLock()`:
  - A character waits while a paralogue window, first appearance or dated story gate is more than `SOON_DAYS` (7) days away.
  - Cut-offs, cleared paralogues and undated gates never lock.
  - A paralogue that is open, opening within 7 days or already past keeps the character in "ready", even if a later date is far away (Fabio).
  - Paralogues count from their first window. Between Talimun's two windows a card can be in "ready" while its badge counts down to the second window; a quest accepted in the first window can still be cleared.
- **Card colours** always show the Renown needed. A red corner (`.person.late`) marks someone recruitable only later than their first chapter, because of a story gate or a paralogue (`late` in `buildRoster`). When a paralogue opens after `minChapter`, the card also says "Earliest Ch. N · paralogue" (`paralogueChapter`). The paralogue chapter is information only: it doesn't move cards between sections, because the date lock already does that when a date is entered.
- **Favorites** only ever hold characters still to recruit. Recruiting removes the star, the toast's Undo restores it, "Put back" does not, and `sanitiseRoute` drops stars on recruited characters when loading or importing.

## Don't break saved progress
- `STORAGE_KEY` stays `'fortunes-weave-recruitment-planner-v5'` and `TOOL_ID` stays `'recruitment-planner'`. Changing either would hide everyone's progress.
- Saved keys are part of the format: Support ticks `"<Name>:<rank>"`, task progress `"request:<Name>"` and `"paralogue:<Owner>"`, and item counts by item name. Renaming a character, item or paralogue owner needs a migration in `sanitiseRoute`.
- `sanitiseState` must keep loading v5 and v6 saves and backups (anything with `routes`), plus the old Dietrich-only v3/v4 format (top-level `checked`). It refuses data whose `tool` names a different tool.

## Testing
- Open `index.html` by double-clicking it, or serve the folder (e.g. `python -m http.server 8765`) and open http://localhost:8765/.
- The browser console must show no `[Recruitment Planner data]` errors.
- Path counts are Cai 37, Dietrich 40, Theodora 39, Leda 37.
- Main flow: tick Support, enter Renown, the card moves sections, and the page doesn't jump.
- **Read the text** of a card's "Requirements & hints" and the shopping-list headings. Missing spaces have slipped in before.
- Date lock: on Dietrich's path with Renown 10 and Support ticked, Peppe waits at 9/1 ("Paralogue opens 9/17") and is in "ready" at 9/10. On Leda's path, Fabio is in "ready" during his paralogue window and waits after clearing it until 10/28.
- Red corners: Cai 3 (Peppe, Ursula, Diego), Dietrich 7, Theodora 5, Leda 4. Ursula on Dietrich's path says "Earliest Ch. 9 · paralogue"; Gaitz and Fabio get the corner without that line, because their story gate (Ch. 12 and Ch. 11) is not earlier than their paralogue.
- Favorites: star someone and mark them recruited. The star is gone and the shopping list widens; Undo brings the star back.
- Check a 375 px width.

## Releases
Follow the checklist in `CONTRIBUTING.md`. The release copy is named `fortune-weave-recruitment-planner-vX.Y.html`.
