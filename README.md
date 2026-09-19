# sharepoint-sync

FastAPI service that pulls weekly STT sales/stock Excel files from SharePoint
(via Microsoft Graph) and upserts them into MySQL.

## Local setup

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env        # fill in the values
uvicorn main:app --reload
```

## Endpoints

- `GET /` — health check
- `GET /sharepoint/files?folder_path=...` — list files in a SharePoint folder
- `GET /sharepoint/excel?item_id=...` — read the "Stock" sheet of a file
- `POST /sync/stt-reports?limit=N` — sync all (or first N) STT weekly files
- `POST /sync/stt-reports/week?year=YYYY&week=WW` — sync one specific week

## Deploying

See the deployment walkthrough for pushing to GitHub and Railway.
