# AGENTS.md — GitHub Profile Repo (atheerium/atheerium)

This is a **GitHub Profile README** repo. GitHub renders `README.md` on [github.com/atheerium](https://github.com/atheerium) because the repo name matches the username.

## Repo Structure

```
atheerium/
├── README.md                          # Main profile page content
├── gitartwork.svg                     # Generated: pixel art from contribution graph
├── profile-3d-contrib/                # Generated: 3D contribution chart SVGs
│   ├── profile-night-rainbow.svg      # ← referenced in README.md
│   └── ...
└── .github/
    ├── FUNDING.yml                    # GitHub Sponsors config
    └── workflows/
        ├── profile-3d.yml             # Generates 3D contribution charts (every 15min)
        ├── github-snake.yml           # Generates snake animation (daily)
        ├── gitartwork.yml             # Generates gitartwork.svg (on push)
        ├── pacman.yml                 # Generates Pac-Man animation (every 12h)
        └── main.yml                   # Periodic timestamp to keep actions alive
```

## Generated Files (DO NOT EDIT MANUALLY)

| File | Workflow | Notes |
|---|---|---|
| `profile-3d-contrib/*.svg` | `profile-3d.yml` | 10 SVG variants (different themes). Takes ~15s to generate. |
| `gitartwork.svg` | `gitartwork.yml` | Text "ATH" rendered as contribution pixels. Regenerates on every push. |
| `output` branch | `github-snake.yml`, `pacman.yml` | Snake + Pac-Man animations pushed to separate `output` branch. |

## Customization Points in README.md

### Sections you can edit freely:
- **About Me** (lines 11-25) — bio, current projects, fun facts
- **Typing SVG** (line 105) — `lines=` param is URL-encoded semicolon-separated text
- **Social links** (line 209) — add/remove badge links
- **Featured Projects table** (lines 235-260) — update repo links and descriptions
- **Typing SVG bottom** (line 228) — another animated text banner

### Dynamic badges (auto-update, no action needed):
- Profile views, followers, stars (komarev.com, shields.io)
- GitHub stats cards (github-readme-stats-fast.vercel.app)
- Streak stats (github-readme-streak-stats-eight.vercel.app)
- Top languages (github-readme-stats)
- Trophies (github-trophies.vercel.app)
- Contribution chart (ghchart.rshah.org)
- Git animals (render.gitanimals.org)
- Jokes card (readme-jokes.vercel.app)
- Quotes (quotes-github-readme.vercel.app)

## Workflow Configuration

### Adding a new workflow:
1. Create file in `.github/workflows/`
2. Must include `permissions: contents: write` if it commits back
3. Must include `workflow_dispatch:` to allow manual trigger via `gh workflow run`
4. Use `git pull --rebase origin main` before `git push` to avoid race conditions

### Triggering workflows manually:
```bash
gh workflow run "GitHub-Profile-3D-Contrib" --repo atheerium/atheerium
gh workflow run "gitartwork from a contribution graph" --repo atheerium/atheerium
gh workflow run "GitHub Snake Game" --repo atheerium/atheerium
```

### Checking workflow status:
```bash
gh run list --repo atheerium/atheerium --limit 5
gh run view <run-id> --repo atheerium/atheerium --log-failed
```

## Known Issues & Fixes

### Race condition on push
Multiple workflows pushing to `main` simultaneously causes `! [rejected]`. **Fix**: always use `git pull --rebase origin main` before `git push` in workflow steps.

### Generated SVGs show as broken icon
Means the workflow hasn't run yet. Trigger manually with `gh workflow run`. First generation takes 15-30 seconds.

## Useful Resources

- [GitHub Profile README docs](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)
- [github-profile-3d-contrib](https://github.com/yoshi389111/github-profile-3d-contrib)
- [Platane/snk (snake)](https://github.com/Platane/snk)
- [jasineri/gitartwork](https://github.com/jasineri/gitartwork)
- [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
