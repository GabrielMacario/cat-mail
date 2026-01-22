# Gmail IMAP → CSV → Google Sheets (Colab)

Python script that reads Gmail emails via IMAP, applies dynamic filters from `filters.json`, and saves results incrementally to CSV and Google Sheets using Google Colab OAuth.  
Script em Python que lê emails do Gmail via IMAP, aplica filtros dinâmicos do `filters.json` e salva os resultados incrementalmente em CSV e Google Sheets via OAuth do Google Colab.

## Install

```bash
pip install gspread google-auth
Run (Google Colab)
Authenticate once per session:

from google.colab import auth
auth.authenticate_user()
Run the script:

python main.py
Configuration
Gmail credentials (hardcoded)
Set your Gmail user and App Password directly in the script:

GMAIL_USER = "your_email@gmail.com"
GMAIL_PASS = "YOUR_GMAIL_APP_PASSWORD"
Use a Gmail App Password (not your main Gmail password).
Use uma Senha de App do Gmail (não use sua senha principal).

Google Sheets
Update these constants in the script:

SPREADSHEET_ID = "YOUR_SHEET_ID"
WORKSHEET_NAME = "emails"
The script will create the worksheet if it doesn’t exist.
O script cria a aba caso ela não exista.

Filters (filters.json)
Edit filters.json to control which emails are saved.

Example: only unread emails containing "playstation" in the body:

{
  "imap_search": "UNSEEN",
  "include": {
    "body_contains": ["playstation"]
  },
  "exclude": {}
}
imap_search: IMAP filter applied server-side (e.g., UNSEEN, ALL, SINCE 01-Jan-2026)

include: required matches (AND logic)

exclude: discard matches (OR logic)

A PDF is included in the repository explaining the filter rules.
Um PDF está incluído no repositório explicando as regras de filtros.

Checkpoint (state.json)
The script stores progress in state.json using last_uid to continue from the last processed email.

To reprocess from the beginning:

{ "last_uid": 0 }
