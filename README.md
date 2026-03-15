# Airdrop Farming Tracker

A CLI tool to append daily Airdrop Farming records to Google Sheets and automatically summarize totals.

## Features
- Auto-fill date (YYYY-MM-DD)
- CLI input for Gas, Points, Airdrop Value, Note
- Auto-append to Google Sheets
- Summary totals: gas spent, points earned/spent, airdrops count, airdrop value, profit
- Extra: cost per point, ROI
- Supports multiple records per day
- Reads all historical rows to summarize

## 1) Install Dependencies

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 2) Google Sheets API Setup (Service Account)

1. Go to Google Cloud Console and create a project (or use an existing one).
2. Enable **Google Sheets API** for the project.
3. Create a **Service Account** and generate a **JSON key** file.
4. Share your target Google Sheet with the service account email (Viewer/Editor permission).
5. Keep the JSON key file locally (never commit it).

## 3) Configure Environment

Copy `.env.example` to `.env` and fill in values:

```bash
cp .env.example .env
```

Edit `.env`:

- `GOOGLE_SERVICE_ACCOUNT_JSON`: absolute path to the service account JSON
- `SPREADSHEET_ID` or `SPREADSHEET_URL`
- `SHEET_NAME`: tab name

## 4) Run the Program

```bash
python airdrop_tracker.py
```

### Example Input

```
Gas (required, negative for cost): -3.2
Points Earned (optional): 18
Points Spent (optional, negative): -15
Airdrop Value (required if points < 0): 26.6
Status/Note (optional): zkSync claim
```

### Example Output

```
Summary
Total Gas Spent: 28.85 U
Total Points Earned: 90
Total Points Spent: -15
Airdrops Claimed: 1
Total Airdrop Value: 26.60 U
Net Profit: -2.25 U
Cost per Point: 0.3206 U
ROI: -7.80 %
```

## Optional: OAuth2 Setup (If you prefer OAuth)

If you want OAuth instead of Service Account:
1. Enable Google Sheets API.
2. Create OAuth Client ID (Desktop app).
3. Use google-auth-oauthlib to run an OAuth flow.

This project currently implements **Service Account** for simplicity. If you want OAuth support, tell me and I can add it.

## Notes
- The tool expects the sheet header: `date, gas_fee, points, airdrop_value, status`.
- If the sheet is empty, it auto-inserts the header.
- Gas should be negative for costs. Summary reports total spent as positive.

## Files
- `airdrop_tracker.py` main script
- `requirements.txt` dependencies
- `.env.example` env template

# test
# test
# test
# test
# test
# test
# test
# test
