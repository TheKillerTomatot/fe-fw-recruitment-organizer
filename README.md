# Fortune's Weave · Part I Recruitment Planner

An unofficial, spoiler-light planner for Part I of *Fire Emblem: Fortune's Weave*. It keeps the recruitable characters on your path organized, so it's easier to see who you can pick up and what each one still needs: Support ranks, Renown, chapter, gifts, requests, paralogues and deadlines. It covers all four lords' paths.

It's a single HTML file. There's nothing to install, no account to create, and it works offline.

## How to use

- **Online:** open **https://thekillertomatot.github.io/fe-fw-recruitment-organizer/**. There's nothing to install.
- **Offline:** download the HTML file from the **[latest release](https://github.com/TheKillerTomatot/fe-fw-recruitment-organizer/releases/latest)** and open it in any modern browser (Chrome, Edge, Firefox or Safari) by double-clicking it. Each release lists the file's hash and its VirusTotal report.

Then pick your lord and enter your Renown. The **How to use** panel at the top of the page explains the rest.

Your progress is saved in your browser on your own device. The online version and a downloaded copy keep separate progress. Use **Export backup** and **Import backup** to move it between them, or to another device or browser.

## Features

- Separate progress for Cai's, Dietrich's, Theodora's and Leda's paths
- Cards sort themselves into "ready", "Support in progress" and "waiting on Renown, chapter or date"
- A shopping list for items, requests and paralogues, with progress shown on each card
- An optional in-game date that shows which paralogue windows are open, coming up or closed, and keeps characters you can't recruit for a while yet out of the "ready" section
- Hints and puzzle answers hidden behind spoiler tags until you tap them

## Verify your copy

Anyone can check that this tool is genuine and does nothing behind your back:

**1. Check the file's fingerprint (SHA-256 hash).** For v6.3 it must be:

```
87A189AD31D8FF6D4F9444F00F4C5B77DD256D854639F90CFD450D04968AE602
```

Get the hash of your downloaded copy with:

- **Windows (PowerShell):** `Get-FileHash -Algorithm SHA256 fortune-weave-recruitment-planner-v6.3.html`
- **macOS:** `shasum -a 256 fortune-weave-recruitment-planner-v6.3.html`
- **Linux:** `sha256sum fortune-weave-recruitment-planner-v6.3.html`

If you downloaded `index.html` from the repository instead, use that name. It's the same file with the same hash.

If the hash doesn't match, your file differs from the published one. Don't use it.

**2. See the antivirus scan.** The [VirusTotal report for this exact file](https://www.virustotal.com/gui/file/87a189ad31d8ff6d4f9444f00f4c5b77dd256d854639f90cfd450d04968ae602) shows the results from dozens of antivirus engines. You can also upload your own copy there.

**3. Watch what it loads.** Open the page, press F12, switch to the **Network** tab and reload. Only the page itself loads: no scripts, fonts, trackers or analytics from anywhere else.

**4. Read the code.** It's one plain, readable file with no hidden or scrambled code. Open it in any text editor.

## Data sources

Recruitment requirements were checked on 26 Oct 2026 against [RPG Site](https://www.rpgsite.net/guide/21391-fire-emblem-fortunes-weave-recruitment-guide-all-characters-in-game-how-to-recruit-them), [Serenes Forest](https://serenesforest.net/fortunes-weave/characters/recruitment/), [LUM](https://lum.gg/fire-emblem-fortunes-weave/recruitment) and [RPG Site's paralogue guide](https://www.rpgsite.net/guide/21387-fire-emblem-fortunes-weave-paralogues-how-to-access-all-paralogue-battles-where-to-find-them). Where the guides disagree, the planner uses the earlier chapter and says so in the character's details. Mistakes are still possible; corrections are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Made with AI

This tool was built with the help of AI assistants (ChatGPT and Claude).

## Disclaimer

This is an unofficial, non-commercial fan-made tool. It is not affiliated with or endorsed by Nintendo or the game's developers. Fire Emblem is a trademark of Nintendo. No game assets are used, and all hints are written in our own words.

## License

© 2026 TheKillerTomatot. Licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). See [LICENSE](LICENSE).

You may use, share and adapt it if you:

- give credit;
- don't use it commercially (no selling, paywalls or ad-funded re-hosting);
- release your changes under the same license.
