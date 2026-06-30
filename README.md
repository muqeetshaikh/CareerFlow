# 🚀 CareerFlow: Automated Job Tracker & AI Outreach Pipeline

An intelligent, production-ready workflow automation built on **n8n v1.0+** that eliminates the manual overhead of tracking job applications, generating personalized cold outreach emails with Generative AI, and delivering real-time status updates via Telegram.

---

## 📌 Problem Statement
Consistency is key when applying for jobs, but manually tracking companies, missing application deadlines, and crafting tailored cover letters/cold emails for every single position drains immense time. Job seekers often lose track or compromise on personalization, leading to lower response rates.

## 💡 The Solution
**CareerFlow** turns a simple row entry into an automated pipeline. 
* Whenever a new application is logged in Google Sheets, the pipeline kicks off.
* It leverages **Generative AI (Groq)** to read the specific company and role context, creating a beautifully written, custom email draft in your **Gmail**.
* Simultaneously, it pushes structured notifications to your **Telegram** so you stay on top of your schedule on the go.

---

## 🛠️ Architecture & Node Logic
The workflow flows linearly and efficiently across the following nodes:

1. **Google Sheets Trigger (Polling):** Continuously monitors the target Google Spreadsheet for newly appended data rows (capturing fields like `Company Name`, `Job Role`, and `Application Deadline`).
2. **Basic LLM Chain & Groq Chat Model:** The brain of the automation. It dynamically constructs a prompt with your input parameters and sends it to Groq's high-speed, low-latency model to draft a contextually relevant, personalized email.
3. **Gmail Node (Create a Draft):** Automatically ingests the text response from the AI and maps it into a fresh email draft, ready for a final human review before hitting send.
4. **Telegram Node (Send a Text Message):** Utilizes JSON expression mapping (`{{ $('Google Sheets Trigger').item.json["Company Name"] }}`) to immediately broadcast structured tracking parameters to a Telegram Bot.

---

## ⚙️ How to Setup & Import This Workflow

### Prerequisites
* **n8n** installed or hosted instance (v1.0 or higher recommended).
* Google Account (for Sheets & Gmail integrations).
* Telegram Bot Token & Chat ID.
* Groq API Key.

### Step-by-Step Installation
1. Clone or download the `careerflow-workflow.json` file from this repository.
2. Open your n8n instance and create a new workflow canvas.
3. Click the **three dots menu** in the top-right corner and select **Import from File**. Select the JSON file.
4. Open the **Google Sheets Trigger** and **Gmail** nodes to authenticate via OAuth2 or your credentials.
5. Set up your Telegram credentials by providing your Bot Token and Chat ID.
6. Provide your Groq API key in the Chat Model node.
7. Click **Publish** on the top right to take the workflow live!

---

## 🤝 Project Context
This automation was conceptualized, built, and tested end-to-end within 3 days as part of the **Project ARCHON Weekend n8n Automation Challenge**.

* **Author:** Muqeet Shaikh
* **Project Status:** Production / Fully Functional ✅
