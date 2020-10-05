# Vue.js dashboard reading from Google Sheets

This repo is a simplified version of the hands on tutorial [How To Build And Deploy Your Dashboard With Python, Google Sheets, and Vue.js](https://towardsdatascience.com/how-to-build-and-deploy-your-dashboard-with-python-google-sheet-and-vue-js-c34140c1afc8) originally published by [Matt](https://medium.com/@matgonzalez736). For detailed steps, please refer to the original story.

### You will find here
How to configure a Vue.js application to read data from a Google Sheet.

### You won't find here
The python script to import data and populate the sheet, as well as the .yml file to publish the dashboard automatically to Github pages.

---
**Requirements**
* A Google accout
* gcloud command-line tool

**Step 1** - Configure a new Google Cloud project.
`gcloud projects create <project_id>`.

**Step 2** - Set the newly created project as default so the following commands apply to it.
 `gcloud config set project <project_id>`

**Step 3** - Enable Google Sheets and Google Drive in your project.
`gcloud services enable sheets.googleapis.com`
`gcloud services enable drive.googleapis.com`

**Step 4** - Create an API Key for the Vue.js application.
* Go to the [credentials panel](https://console.cloud.google.com/apis/credentials) on Google Cloud console.
* Select **Create credentials**, then select **API Key** from the dropdown menu.
* The API key dialog box displays your newly created key, **save it for later use**.
* Click the pencil to edit your key, then go to the restriction API section and check the restrict key option. Select Google sheets API and click on save.

**Step 5** - Create a new Sheet in your Drive, name it `dashboard_data`. Open your sheet and copy its id from the browser's address bar. It is displayed like this: `https://docs.google.com/spreadsheets/d/<your-sheet-id>/` 

**Step 6** - Configure your Vue.js applicaton with the API Key and Sheet Id.
```
mounted() {
    this.ghseetClient = new Gsheet(
        '<your-sheet-id>',
        '<your-api-key>')
    this.getData()
},
``` 

