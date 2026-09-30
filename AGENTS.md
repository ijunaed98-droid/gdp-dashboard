# Base44 Dev Environment

## App
Streamlit app (`streamlit_app.py`) showing a GDP dashboard. Reads `data/gdp_data.csv` (bundled in repo). No external services or credentials required.

## Run
`docker compose -f docker-compose.base44.yml up -d` — uses `python:3.11-slim`, installs `requirements.txt` (streamlit, pandas) on startup, runs Streamlit on internal port 8501 mapped to host port 3000.

## Verify
- Health: `curl http://localhost:3000/_stcore/health` → `ok`
- Page: `curl http://localhost:3000` returns Streamlit HTML shell.

## Live reload
Streamlit `--server.runOnSave true` reruns the script on source file changes. Source is bind-mounted from the repo, so edits appear without rebuilds.

## Notes
- CORS and XSRF protection are disabled so the preview proxy can reach the app.
- No `.env` or secrets needed.
