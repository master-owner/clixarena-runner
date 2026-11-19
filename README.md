# CLIXARENA Runner (Public Repo + Docker)

This public repository contains `.github/` workflows and `docker/Dockerfile` so you get unlimited GitHub Actions minutes with all encoding tools pre-installed in a Docker container, while keeping your scripts, subtitles, fonts, and `mappings.json` in your **Private** `clixarena-core` repo.

## Setup
1. Create a **Private** repository (`clixarena-core`) from `clixarena-core-private.zip`.
2. Push `clixarena-runner-public.zip` to this **Public** repository (`clixarena-runner`).
3. In this **Public** runner repo (`Settings -> Secrets and variables -> Actions`):
   - **Variable**: `CORE_REPO` = `your-username/clixarena-core`
   - **Variable** (optional): `CORE_REF` = `main`
   - **Secret**: `CORE_PAT` = Fine-grained GitHub PAT with **Contents: Read & Write** scoped ONLY to `clixarena-core`.
   - **Secrets**: `VK_ACCESS_TOKEN`, `MAPPING_PASSWORD`, `TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID`, `TELEGRAM_API_ID`, `TELEGRAM_API_HASH`, `ABYSS_API_KEY`, `BYSE_API_KEY`.
4. Run **Actions -> Build and Push Runner Image to GHCR** once (or it runs automatically when `docker/Dockerfile` is pushed) to build `ghcr.io/<your-username>/clixarena-runner:latest`.
   - Make sure the GHCR package visibility is **Public** (or readable by your Actions token).
5. In `clixarena-control` (Cloudflare Worker):
   - Set `GITHUB_REPO` = `your-username/clixarena-runner`
   - Set `CORE_REPO` = `your-username/clixarena-core`
