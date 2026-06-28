# Automated Resume Extraction Workflow (n8n)

This repository contains an n8n workflow that automates the process of extracting key details from resumes received via email. It uses AI (Google Gemini) to parse the resume attachments and logs the structured data directly into a Google Sheet.

## Features
* **Automated Email Monitoring:** Checks Gmail every minute for emails with "Application" or "Resume" in the subject line that contain attachments.
* **AI-Powered Parsing:** Uses Google Gemini (`gemini-2.5-flash`) to extract Name, Qualification, Skills, and Experience from the resume document.
* **Structured Data Logging:** Automatically appends the extracted information as a new row in a specified Google Sheet.

## Workflow Steps
1. **Gmail Trigger:** Polls Gmail every minute for new emails matching `subject:Application OR subject:Resume has:attachment`. It downloads the attachment (prefixing it with `Resume_`).
2. **Analyze Document:** Sends the downloaded resume attachment to Google Gemini with a specific prompt to extract Name, Qualification, Skills, and Experience, requesting the output in JSON format.
3. **Edit Fields:** Parses the raw JSON response from Gemini to prepare the data for the spreadsheet.
4. **Append Row in Sheet:** Appends the extracted data (Name, Qualification, Skills, Experiences) to a designated Google Spreadsheet.

## Prerequisites & Setup
To use this workflow in your own n8n instance, you will need:

1. **n8n installed** (Self-hosted or n8n Cloud).
2. **Google Cloud Project:** You will need OAuth2 credentials set up for Gmail, Google Sheets, and a Google AI Studio API key for Gemini.
3. A **Google Sheet** with the following column headers: `Name`, `Qualification`, `skills`, `Experiences`.

## Installation & Configuration

1. **Import the Workflow:** Download the JSON file from this repository and import it into your n8n instance.  
        [Download Blueprint](automated-resume-extraction.json)
3. **Set up Credentials:** Open the workflow and configure the credentials for the following nodes:
   * *Gmail Trigger* (Gmail OAuth2)
   * *Analyze document* (Google Gemini/PaLM API)
   * *Append row in sheet* (Google Sheets OAuth2)
4. **Update the Google Sheet ID:** In the **"Append row in sheet"** node, update the Document ID to point to your own Google Spreadsheet.
5. **Activate the Workflow:** Toggle the workflow to "Active" in n8n.
