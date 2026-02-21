# Intelligent Gmail Automation Using LLMs (n8n Workflow)

An automated Gmail email processing system powered by an LLM (OpenAI or Groq) using n8n workflows.

This project connects Gmail to an LLM to automatically analyze, categorize, and label incoming emails — eliminating manual inbox triage and enabling intelligent inbox automation.

---

##  Overview

This system automates Gmail processing by:

- Connecting Gmail via OAuth 2.0
- Monitoring incoming emails
- Sending email content to an LLM
- Classifying or analyzing messages
- Automatically applying Gmail labels
- Triggering optional downstream actions

The result: a self-managing, AI-powered inbox.

---

##  Architecture Overview

**User OAuth → Gmail Trigger → Email Parser → LLM → Decision Logic → Gmail Label**

### High-Level Flow

1. Gmail OAuth authentication  
2. Gmail Trigger listens for new emails  
3. Email content is extracted  
4. LLM analyzes the email  
5. Workflow applies label or action  

The architecture is modular and designed for easy extension (notifications, auto-replies, analytics, etc.).

---

##  Features

- OAuth 2.0 Gmail authentication
- Fully automated email processing
- LLM-powered classification
- Modular n8n workflow design
- Secure credential handling
- Extendable decision logic
- Label-based notification support

---

##  Tech Stack

- n8n (Workflow Automation)
- Gmail API
- OAuth 2.0
- OpenAI or Groq (LLM Provider)

---

##  Prerequisites

Before running this project, you need:

- n8n (Cloud or Self-hosted)
- Google Cloud Project
- Gmail API enabled
- OAuth 2.0 Client credentials
- LLM API key (OpenAI, Groq, or supported provider)

---

##  Google OAuth Setup

1. Go to Google Cloud Console  
2. Create a new project  
3. Enable the Gmail API  
4. Navigate to **Credentials → Create OAuth Client ID**  
5. Add your n8n redirect URL  

Example:

https://your-n8n-domain/rest/oauth2-credential/callback


6. Save the Client ID and Client Secret  
7. Configure these credentials inside the Gmail node in n8n  
8. Add your LLM API key inside the LLM node configuration  

(Your can find documention link in .env (https://github.com/shodhanshetty06/N8n-Automations/blob/master/Gmail%20Automation/.env.example) )

---

##  Importing the Workflow

1. Open n8n  
2. Go to Workflows  
3. Click **Import from File**  
4. Select `automation-workflow.json`  
5. Reconnect credentials  
6. Activate the workflow  

---

##  Testing the Automation

1. Activate the workflow  
2. Send a test email to the connected Gmail account  
3. Confirm the LLM processes the email  
4. Verify the correct label is applied  

---

##  Enabling Notifications for Specific Labels (Mobile Gmail)

To receive push notifications only for selected automated labels:

1. Open the Gmail app  
2. Tap the three-line menu (☰) at the top left  
3. Scroll down and tap **Settings**  
4. Select the Gmail account connected to this automation  
5. Tap **Manage labels**  
6. Select the label you want notifications for  
7. Tap **Sync messages**
   - Choose **All** or **Last 30 days**
8. Enable:
   - **Label notifications**
   - **Notify for every message**
9.Uncheck everything in inbox option in settings 
You will now receive notifications only for emails classified under that specific label.

---

##  Project Structure
gmail-llm-automation/
│
├── workflows/
│ └── automation-workflow.json
│
├── docs/
│ ├── architecture-diagram.png
│ └── flowchart.png
│
├── .env.example
├── README.md
└── LICENSE

---

##  Security Notes

- No credentials are stored in this repository  
- Do not commit `.env` files  
- Rotate API keys if exposed  
- Use secure environment variables in production  
- Use least-privilege OAuth scopes  

---

##  Production Considerations

If deploying beyond personal use, consider:

- Handling Gmail API rate limits  
- LLM API fallback logic  
- Retry mechanisms for failed classifications  
- Logging and monitoring workflows  
- Audit logging for compliance  
- Label-based alert escalation  

---

##  Future Improvements

- Multi-label classification  
- Auto-reply functionality  
- Slack / Discord notifications  
- Webhook-based analytics  
- Email summarization dashboard  
- Confidence scoring and human review loop  

---
##  License

MIT License  

---
##  Author

Shodhan Shetty
