# studio

Manual render runner for the Money Psyche video pipeline.

This public repo holds **only** a GitHub Actions workflow. It checks out a
private content repo (configured via the `CONTENT_REPO` secret) and renders an
episode to Google Drive. No source code or assets live here.

## Run a render
1. Open the **Actions** tab → **Render episode**.
2. Click **Run workflow**, enter the episode id (e.g. `episode01`), and run.
3. Download the finished `.mp4` + `.png` from the Drive output folder.

## Required configuration
_Settings → Secrets and variables → Actions_

**Secrets**
- `CONTENT_REPO` — `owner/repo` of the private content repo to render.
- `CONTENT_TOKEN` — fine-grained PAT with read access to that repo (Contents: read).
- `RCLONE_CONFIG` — the full rclone config, pasted in **as-is** (multi-line, no
  escaping — exactly like the other repos).
- `RCLONE_REMOTE` — e.g. `gdrive:market_db`.

**Variables** (optional — defaults shown)
- `VIDEO_DRIVE_SUBDIR` — `moneypsyche`
- `WHISPER_MODEL` — `large-v3`
