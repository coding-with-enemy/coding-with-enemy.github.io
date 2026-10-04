# Project page - Coding with "Enemy"

Static landing page for the NeurIPS 2026 paper *Coding with "Enemy": Can Human Developers Detect AI Agent Sabotage?*

## Files

```
website/
├── index.html          # the page (structure + all CSS inline)
├── assets/
│   ├── app.js           # interactive study walkthrough, 5 sabotage trajectories, ECharts
│   ├── sabotage_logo.png
│   └── icons/           # model icons used in the Q1 chart and explorer tabs
│       ├── claude.png       # real
│       ├── gemini.png       # real
│       ├── openai.png       # real
│       └── minimax.png      # PLACEHOLDER - swap for the official MiniMax icon
└── README.md
```

No build step. `index.html` pulls Inter (Google Fonts) and ECharts 5 from CDNs; everything else is local.

**Before publishing:** replace `assets/icons/minimax.png` with the official MiniMax icon (transparent PNG, roughly square). Keep the same filename and no code change is needed.

## Preview locally

```bash
cd website
python3 -m http.server 8000
# open http://localhost:8000/
```

## Deploy to GitHub Pages (coding-with-enemy.github.io)

The Pages repo serves from its root, so copy the **contents** of this folder to the repo root:

```bash
# from a clone of git@github.com:coding-with-enemy/coding-with-enemy.github.io.git
cp -R /path/to/Claude-Code-RedTeam/website/. .
git add -A
git commit -m "Add project landing page"
git push
```

The site is then live at https://coding-with-enemy.github.io/.

## Editing content

- **Numbers / copy:** `index.html` (section text) - the headline detection figure is **94%** throughout.
- **Sabotage trajectories:** the `TRAJECTORIES` array at the top of `assets/app.js`. Text is copied from the paper's redacted figures (`figures/sabotage_trajectories_redacted.tex`); never use the unredacted `sabotage_trajectories.tex`. Mark a malicious code line by setting the second element of its `[line, flag]` pair to `1`.
- **Charts:** the `initCharts()` function in `assets/app.js`.
- **Code button:** points to https://github.com/CHATS-lab/coding-agent-safety-monitor.
