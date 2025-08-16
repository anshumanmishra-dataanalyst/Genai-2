# Genai-2
# Automated Job Search & Cover Letter Generator

## Project Description

This project automates the job search process using n8n, integrating job listing APIs, a custom match scoring system, Google Gemini for cover letter generation, Google Sheets for logging, and daily email notifications for top matches. The workflow fetches current job listings, evaluates their relevance based on your skills, generates tailored cover letters, stores results in Google Sheets, and sends a daily summary email.

---

## Features

- **Automated Job Fetching:** Retrieves the latest job listings from Google Jobs (via SerpAPI) or Indeed (via JSearch/RapidAPI).
- **Match Scoring:** Compares each job against your skills and computes a match score for prioritization.
- **AI-powered Cover Letter Generation:** Uses the Google Gemini model to create personalized cover letters for each job.
- **Google Sheets Integration:** Logs every relevant job, match score, and cover letter in Google Sheets for easy access and tracking.
- **Daily Email Notification:** Sends a daily summary of top job matches, including links and cover letters, straight to your inbox.

---

## How to Run

### Prerequisites
- [n8n installed locally](https://docs.n8n.io/hosting/installation/) (`npm i n8n -g` or use Docker)
- API keys for SerpAPI, JSearch/RapidAPI, Google Gemini, Google Sheets, and an SMTP or Gmail account.
- Your list of target skills.

### Running Locally

1. **Clone this repository:**
2. **Set up environment variables** for all API keys and credentials (recommended: `.env` file or n8n credential management).

3. **Start n8n:**
Access the editor at [http://localhost:5678](http://localhost:5678)

4. **Import the workflow:**  
Upload the provided n8n workflow JSON (`workflow.json`) in the n8n UI.

5. **Configure nodes:**
- Update API keys, spreadsheet IDs, your email, and the skills array in the Set or Function node.
- Adjust email formatting if desired.

6. **Run the workflow:**
- Trigger manually, on a schedule (via Cron node), or as you prefer.

### Running in Production or with n8n Cloud

- Deploy n8n as per [official instructions](https://docs.n8n.io/hosting/).
- Follow the same configuration/import steps.

---

## Screenshots

### Google Sheet Sample

| Title             | Company     | Location      | Match Score | Cover Letter              | URL                       | Posted Date |
|-------------------|-------------|--------------|-------------|---------------------------|---------------------------|-------------|
| Data Analyst      | Acme Corp   | London, UK   | 85%         | [cover letter snippet...] | https://joburl.example... | 2025-08-14  |
| Automation Eng.   | ExampleLtd  | Berlin, DE   | 92%         | [cover letter snippet...] | https://joburl.example... | 2025-08-15  |

### Email Example

> **Subject:** Today’s Top Job Matches
>
> Hi! Here are your top job matches for today:
>
> **1. Automation Engineer at ExampleLtd (92%)**
>
> [https://joburl.example.com](https://joburl.example.com)
>
> **Cover Letter:**  
> Dear Hiring Manager, ... [Gemini-generated cover letter snippet] ...
>
> **2. Data Analyst at Acme Corp (85%)**
>
> [https://joburl.example.com](https://joburl.example.com)
>
> **Cover Letter:**  
> Dear Team, ... [Gemini-generated cover letter snippet] ...
>
> _See all results in your attached Google Sheet._

### n8n Workflow Screenshot

![Sample n8n workflow](./images/n8n_workflow_sample.png)

---

## Notes

- Edit the skills list in the workflow’s Function/Set node to reflect your own experience.
- For API rate limits or errors, the workflow includes recommended retries and cleanup steps.
- You can always add or remove integrations (e.g. more job boards, other notification methods).

---

Enjoy your fully automated job searching assistant!
