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
- `PARALOGUES`, keyed by owner. Each entry has `where`, an optional `prerequisite` / `note`, and `routes`, which maps each path to `[accept ranges "M/D-M/D, …", clear-by date]`.
- `STORY_GATES`, `CUTOFFS`, `APPEARS`, `REQUEST_HINTS`, `ITEM_HINTS`.

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
- Check a 375 px width.

## Releases
Follow the checklist in `CONTRIBUTING.md`. The release copy is named `fortune-weave-recruitment-planner-vX.Y.html`.
