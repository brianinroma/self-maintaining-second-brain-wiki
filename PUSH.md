# Publishing this repo to GitHub

The repo is already initialised and committed locally. Pick one path.

## Option A — GitHub CLI (fastest)
```bash
cd self-maintaining-wiki
gh auth login                       # one-time, if not already authenticated
gh repo create self-maintaining-wiki --public --source=. --remote=origin --push
```

## Option B — Plain git (create the empty repo on github.com first)
```bash
cd self-maintaining-wiki
git remote add origin https://github.com/<your-username>/self-maintaining-wiki.git
git branch -M main
git push -u origin main
```

## Notes
- Choose `--public` or `--private` to taste (`gh repo create ... --private`).
- The included `.gitignore` excludes `/raw/` and `/wiki/` so you can't accidentally commit real vault content.
- Want a different name? Rename the folder and swap it into the commands above.
