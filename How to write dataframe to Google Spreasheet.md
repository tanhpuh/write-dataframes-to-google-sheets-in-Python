# Create a project and service account
- Go to https://console.cloud.google.com sign in and create a project.
- Go to IAM & Admin > Service Accounts.
- Create service account (fill form) > Create and Continue > Skip all fields in step 2 and 3 > Done.

# Create JSON credentials file
- To get authorization from the service account we created, we must have a credentials file. Get it by clicking the three vertical dots button > Manage keys.
- Click ADD KEY > Create new key (Select Key type as JSON > Click Create)

# Enable Google Sheets/ Drive API
- Go to https://console.cloud.google.com/apis/library/sheets.googleapis.com. Click Enable.
- Go to https://console.cloud.google.com/marketplace/product/google/drive.googleapis.com. Click Enable.
   
# Access google sheet using libraries.
Install all libraries used as followings:
gspread
gspread-dataframe
google
pydrive
pandas

Default python file:

import pandas as pd
import gspread
from gspread_dataframe import set_with_dataframe
from google.oauth2.service_account import Credentials
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive

scopes = ['https://www.googleapis.com/auth/spreadsheets','https://www.googleapis.com/auth/drive']

credentials = Credentials.from_service_account_file('/path/to/json/credentials/', scopes=scopes)

gc = gspread.authorize(credentials)

gauth = GoogleAuth()
drive = GoogleDrive(gauth)

open a google sheet
gs = gc.open_by_key(your_google_sheet_key)

select a work sheet from its name
worksheet1 = gs.worksheet('your_goole_sheet_name')

https://docs.google.com/spreadsheets/d/{your_google_sheet_key}/edit

# Share your google sheet to the service account
Open Google Sheet and share service account email.





