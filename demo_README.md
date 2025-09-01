# Azure Flask Demo

This is a minimal Flask app for Azure App Service demo. It displays environment variables set in Azure Web App (App Settings and Connection Strings).

## How to use

1. Deploy to Azure App Service (Free Tier).
2. In Azure Portal, set App Settings and Connection Strings:
   - App Setting: `APP_SETTING_EXAMPLE`
   - Connection String: `CONNECTION_STRING_EXAMPLE`
3. Access the web app to see the values displayed.

## Local Run

Install dependencies:
```
pip install -r requirements.txt
```
Run the app:
```
python app.py
```

Set environment variables locally for testing:
```
$env:APP_SETTING_EXAMPLE="TestAppSetting"; $env:CONNECTION_STRING_EXAMPLE="TestConnectionString"; python app.py
```
