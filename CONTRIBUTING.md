# Contributing

Thanks for helping make the planner better! The project currently has one maintainer, so all changes go through them.

## Report a mistake or suggest an idea

The best way to help is to [open an issue](https://github.com/TheKillerTomatot/fe-fw-recruitment-organizer/issues).

**Data corrections:** please include
- the lord's path (Cai, Dietrich, Theodora or Leda);
- the character;
- what the planner says and what it should say;
- where the correct information comes from (a guide link or your own playthrough).

**Bugs:** say what you did, what you expected, what happened instead, and which browser you used.

## Pull requests

Pull requests are currently limited to the maintainer. If you'd like to contribute code or data directly, open an issue first.

## Content rules

- **No spoilers.** Keep story details out. Hints, puzzle answers and anything that reveals the story go behind the planner's spoiler tags.
- **Your own words.** Write hints yourself. Don't copy text from guides, and don't add game assets (images, logos, music, fonts).
- **Sources.** Requirements such as Support, Renown or gifts need a source.

## Licensing

By contributing, you agree that your contribution is licensed under [CC BY-NC-SA 4.0](LICENSE), like the rest of the project.

## Releasing a new version (maintainer)

1. Bump the version in the HTML file's header comment and in the badge on the page.
2. Compute the new SHA-256 hash (`Get-FileHash -Algorithm SHA256 fortune_weave_part1_recruitment_tracker.html` in PowerShell).
3. Update the hash, the version and the VirusTotal link in `README.md`.
4. Upload the file to [VirusTotal](https://www.virustotal.com) and create a GitHub Release with the file attached.
