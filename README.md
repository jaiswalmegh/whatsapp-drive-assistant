# WhatsApp-Driven Google Drive Assistant (n8n)

This project allows you to control Google Drive via WhatsApp commands using **n8n**.  
It supports file listing, deletion, moving, and AI-powered summaries using GPT‑4.

---

## 🚀 Features

- **LIST /folder** – List all files in a folder  
- **DELETE /folder/file.pdf** – Delete a specific file (with confirmation for safety)  
- **MOVE /folder/file.pdf /archive** – Move a file to another folder  
- **SUMMARY /folder** – Summarize all text/PDF/DOCX files in a folder using GPT‑4  

---

## 🛠️ Setup Instructions

### 1. Run n8n using Docker

1. Install [Docker](https://docs.docker.com/get-docker/) & Docker Compose.
2. Run:
   ```bash
   docker compose up -d
n8n will be available at: http://localhost:5678

2. Connect Twilio or WhatsApp Cloud API
Twilio (Sandbox or Production):

Create a Twilio account → Activate WhatsApp Sandbox.

Set your inbound webhook URL to: https://<your-domain>/webhook/whatsapp-webhook
WhatsApp Cloud API (Meta):

Set up a Facebook Developer App → WhatsApp Business API.

Add the same webhook URL to receive messages.

3. Connect Google Drive & Google Sheets
In n8n, go to Credentials → Add Google OAuth2 API (Drive & Sheets).

Grant permission to the same Google account where your Drive is.

The workflow will now be able to list, move, and delete files + log actions in Google Sheets.

4. Connect OpenAI GPT‑4 (Optional for SUMMARY)
In n8n, add OpenAI API credentials using your API key.

The SUMMARY command will call GPT‑4 to summarize text extracted from PDFs, DOCX, or TXT files.

5. Import the Workflow
Open n8n → Click Import.

Select workflow.json from this repository.

Activate the workflow.

📋 Logging
Every command and its result is logged to a Google Sheet for auditing.

Columns: Timestamp, User, Command, Params, Status, Details.

Sample log format: see sample-log-sheet.csv.

📝 Example Commands
LIST /ProjectX

DELETE /ProjectX/report.pdf

MOVE /ProjectX/report.pdf /Archive

SUMMARY /ProjectX

📜 License
Licensed under the MIT License.
