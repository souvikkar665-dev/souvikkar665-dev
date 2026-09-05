# Setup

Everything here is configured for your profile repo: **`souvikkar665-dev/souvikkar665-dev`**.
This repository's `README.md` is what is displayed on your GitHub profile page (`https://github.com/souvikkar665-dev`).

---

## 1. Local Assets

All assets have already been generated and placed in `assets/`:
- **Portrait**: `assets/portrait.svg` (dot-matrix rendering of your photo with scan reveal)
- **Skill Radar**: `assets/radar-dark.svg`, `assets/radar-light.svg` (from `assets/skills.json`)
- **Language Radar**: `assets/radar-langs-dark.svg`, `assets/radar-langs-light.svg` (from GitHub API)
- **Project Cards**: `assets/card-Bugatti-Chiron-*.svg`, `assets/card-tech-referee-*.svg`, etc.
- **Stats Card**: `assets/card-stats-dark.svg`, `assets/card-stats-light.svg`

You can open `preview.html` in your browser at any time to preview the portrait and radar charts locally.

---

## 2. Push to GitHub

To push the new profile to GitHub:

```bash
git add .
git commit -m "feat: setup interactive profile readme and workflows"
git push origin main
```

> **Note**: Your repository must remain **public** so that GitHub can render the SVGs in your README.

---

## 3. Enable GitHub Actions Write Permissions

To let the automated workflows update your radar charts, project cards, and snake graph:

1. Go to your repository on GitHub: `https://github.com/souvikkar665-dev/souvikkar665-dev`
2. Click **Settings** → **Actions** → **General**.
3. Under **Workflow permissions**, select **Read and write permissions**.
4. Click **Save**.

---

## 4. Add the Metrics Token (Secret)

The `lowlighter/metrics` workflow requires a GitHub Personal Access Token (PAT) with read permissions to generate your 3D isometric contribution calendar:

1. Go to [GitHub Token Settings](https://github.com/settings/tokens) → **Generate new token (classic)**.
2. Note: `METRICS_TOKEN`.
3. Scopes to check:
   - `read:user`
   - `repo` (optional, if you want private contributions included in counts).
4. Click **Generate token** and copy it.
5. In your repo: **Settings** → **Secrets and variables** → **Actions** → **New repository secret**.
6. Name: `METRICS_TOKEN`
7. Value: *(paste your generated token)* → Click **Add secret**.

---

## 5. Kick off the Workflows

Under the **Actions** tab in your repository, you can manually trigger:
- **Metrics**: Generates the 3D isometric calendar, languages, and achievements into `assets/`.
- **Snake**: Creates the animated snake graph eating your contribution heatmap on the `output` branch.
- **Charts and cards**: Automatically keeps your stats and repo cards synced.

After their first run, they run automatically on schedule (Metrics every 6h, Snake every 12h, Radar daily).
