# Daily Expense Tracker - Production Mobile Web App

This package contains a polished Streamlit app that works on iPhone and Android through a browser and can be added to the home screen like an app.

## What it does

- Prompts for Personal or Business expense.
- Saves amount, date, and time stamp to `daily_expenses.xlsx`.
- Allows optional receipt photo/PDF upload.
- Stores receipt files in the `receipts/` folder and logs the receipt filename/link in Excel.
- Includes Dashboard, History, Settings, Excel download, PIN gate, and test-email button.
- Emails the spreadsheet to `kevin@unlimited-cyber.com` daily at 11:59 PM Central when hosted on a reliable server or scheduled workflow.
- Includes a clickable mobile prototype: `mobile_clickable_prototype.html`.

## Run locally on your computer

```bash
pip install -r requirements.txt
streamlit run app.py
```

Then open the browser address shown by Streamlit.

## Run on iPhone or Android

1. Deploy the app to Streamlit Community Cloud, Render, Railway, or another host.
2. Open the app URL on your phone.
3. On iPhone: Safari > Share > Add to Home Screen.
4. On Android: Chrome > menu > Add to Home screen.

## Email setup

Use an app password, not your normal email password.

Create Streamlit secrets or environment variables:

```toml
SMTP_HOST = "smtp.gmail.com"
SMTP_PORT = 587
SMTP_USER = "your_email@gmail.com"
SMTP_PASSWORD = "your_gmail_app_password"
EMAIL_TO = "kevin@unlimited-cyber.com"
EMAIL_FROM = "your_email@gmail.com"
APP_PIN = "1234"
```

## Important production note

Streamlit Community Cloud may sleep when inactive. For the 11:59 PM email to be reliable, use one of these:

- GitHub Actions workflow included in `.github/workflows/daily-email.yml`.
- A paid always-on host such as Render, Railway, or a small VPS.
- A Windows Task Scheduler or cron job on a computer that stays on.

## Files

- `app.py` - production app.
- `daily_expenses.xlsx` - enhanced Excel workbook.
- `mobile_clickable_prototype.html` - clickable iPhone/Android-style demo screens.
- `receipts/` - receipt storage folder.
- `.streamlit/secrets.toml.example` - Streamlit secret template.
- `.env.example` - local environment template.
- `.github/workflows/daily-email.yml` - scheduled email workflow.
