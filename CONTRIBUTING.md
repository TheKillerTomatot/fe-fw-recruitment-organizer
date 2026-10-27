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

1. On `dev`, bump the version in `index.html`: in its header comment and in the badge on the page.
2. Check that the file has LF line endings only. In PowerShell, `([IO.File]::ReadAllBytes("index.html")) -contains 13` must print `False`. Then compute the SHA-256 hash with `Get-FileHash -Algorithm SHA256 index.html`.
3. Update the hash, the version, the VirusTotal link and the file name in the hash commands in `README.md`. Commit on `dev`.
4. Merge `dev` into `main` and push. GitHub Pages updates from `main`.
5. Make a copy of `index.html` named `fortune-weave-recruitment-planner-vX.Y.html`, outside the repository. It has the same contents, so it has the same hash.
6. Upload that copy to [VirusTotal](https://www.virustotal.com).
7. Create a GitHub Release on `main` tagged `vX.Y`. Attach the renamed copy. Write release notes with:
   - a changelog (Fixed / Changed / Unchanged);
   - the online link;
   - the hash;
   - the VirusTotal link.
