# 🚀 CareerFlow: Automated Job Tracker & AI Outreach Pipeline

An intelligent, production-ready workflow automation built on **n8n v1.0+** that eliminates the manual overhead of tracking job applications, scheduling deadlines, generating personalized cold outreach emails with Generative AI, and delivering real-time status updates via Telegram.

---

## 📌 Problem Statement
Consistency is key when applying for jobs, but manually tracking companies, missing application deadlines, and crafting tailored cover letters/cold emails for every single position drains immense time. Job seekers often lose track of key dates or compromise on personalization, leading to lower response rates.

## 💡 The Solution
**CareerFlow** turns a simple spreadsheet row entry into a multi-channel automated pipeline:
* Whenever a new application is logged in Google Sheets, the pipeline kicks off instantly.
* It automatically maps and schedules the target application deadline as a structured event in **Google Calendar**.
* It leverages **Generative AI (Groq - Llama 3.3 70B)** to read the specific company and role context, creating a beautifully written, custom email draft in your **Gmail**.
* Simultaneously, it pushes instant tracking notifications directly to your **Telegram** bot so you stay updated on the go.

---

## 🛠️ Architecture & Node Logic
The workflow flows linearly and efficiently across the following interconnected nodes:

1. **Google Sheets Trigger (Polling):** Continuously monitors the target Google Spreadsheet (`CareerFlow Responses`) for newly appended data rows (capturing fields like `Company Name`, `Job Role`, and `Application Deadline`).
2. **Google Calendar Node (Create an Event):** Ingests the application deadline data and automatically creates a designated event (`Job Application: [Company] - [Role]`) inside the user's primary calendar (`muqeet2703@gmail.com`).
3. **Basic LLM Chain & Groq Chat Model:** The brain of the automation. It utilizes the highly capable `llama-3.3-70b-versatile` model via Groq to construct a tailored, professional follow-up or application email text based on context variables.
4. **Gmail Node (Create a Draft):** Ingests the rich text output from the LangChain LLM model and places it safely into a fresh email draft folder, ready for human review.
5. **Telegram Node (Send a Text Message):** Broadcasts a neat workspace summary detailing the company name, role, and key deadline to a designated Telegram chat ID via custom expression tags.

---

## ⚙️ How to Setup & Import This Workflow

### Prerequisites
* **n8n** installed or hosted instance (v1.0 or higher recommended).
* Google Account (with active OAuth2 configurations for Sheets, Calendar, and Gmail integrations).
* Telegram Bot Token & Chat ID.
* Groq API Key.

### Step-by-Step Installation
1. Clone or download the `CareerFlow-AI job application tracker.json` file from this repository.
2. Open your n8n instance and create a new workflow canvas.
3. Click the **three dots menu** in the top-right corner and select **Import from File**. Select the downloaded JSON file.
4. Open the **Google Sheets Trigger**, **Google Calendar**, and **Gmail** nodes to authenticate your credentials.
5. Set up your Telegram credentials by providing your Bot Token and Chat ID.
6. Provide your Groq API key in the Chat Model node.
7. Click **Publish** on the top right to take the workflow live!

---

## 🤝 Project Context
This automation was conceptualized, built, and tested end-to-end as part of the **Project ARCHON Weekend n8n Automation Challenge**.

* **Author:** Muqeet Shaikh
* **Project Status:** Production / Fully Functional ✅
