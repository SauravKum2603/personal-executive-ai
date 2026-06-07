# 🤖 Personal AI Executive Assistant (Telegram + LangChain)

An advanced, multi-tool AI Executive Assistant built using **n8n** and **LangChain**. This workflow acts as a centralized personal productivity engine inside Telegram. Powered by **Google Gemini**, the agent dynamically orchestrates schedules via Google Calendar, drafts/sends emails via Gmail, and interfaces with Fireflies.ai to fetch meeting names, summaries, and full transcripts using natural language commands.

## 🚀 Features
- **Unified Command Center:** Manage emails, calendar invites, and meeting transcripts from a single Telegram chat interface.
- **Dynamic Tool Execution:** The LangChain agent determines the user's intent autonomously and routes actions to the correct database or API endpoint without explicit branching.
- **Email Automation:** Drafts and dispatches emails seamlessly via the integrated Gmail tool.
- **Smart Scheduling:** Creates and blocks out calendar events directly inside Google Calendar.
- **Fireflies.ai Meeting Retrieval:** Uses advanced HTTP Request sub-tools to make POST requests directly to the Fireflies GraphQL API, pulling meeting lists and full transcripts into the chat.
- **Conversational Memory:** Retains multi-turn interaction history using an optimized buffer window memory to keep complex requests contextual.

## 🛠️ Architecture & Nodes Used
As shown on the n8n canvas:
1. **Telegram Trigger:** The front-end interface listening for real-time text instructions.
2. **AI Agent (LangChain):** The orchestration center that maps conversational commands into technical execution protocols.
3. **Google Gemini Chat Model:** Advanced language intelligence handling prompt reasoning and formatting.
4. **Simple Memory (Window Buffer):** Tracks conversation state across multiple chat interactions.
5. **Connected Sub-Tools (The Agent's Hands):**
   - `Gmail Tool`: Sends transactional or drafted emails directly from your account.
   - `Calendar Event Setter`: Injects events and times directly into Google Calendar.
   - `Fireflies Fetch Meeting Names and IDs`: A custom API tool making POST requests to gather historic meeting manifests.
   - `Fireflies Transcript Fetcher`: Interacts with Fireflies endpoints to fetch specific call transcripts and summaries.
6. **Telegram Message Sender:** Delivers the finalized summaries, schedules, or email confirmations straight back to the user.

## 📋 Prerequisites
To deploy this project, you will need authorized credentials for:
- An **n8n instance** (Self-hosted or Cloud)
- A **Telegram Bot API Token** (via `@BotFather`)
- **Google AI Studio API Key** (for Gemini)
- **Google Cloud Console Project** with Gmail and Google Calendar APIs enabled (via OAuth2)
- **Fireflies.ai API Key** (with access to their GraphQL API endpoint)

## 📦 Installation & Setup
1. Clone this repository or download the `My workflow.json` file.
2. Open your n8n dashboard, click **New Workflow** -> **Import from File**, and select your downloaded JSON.
3. Open the credential manager for each respective node and authenticate your accounts:
   - Telegram Bot API
   - Google Gemini API
   - Google Sheets/Workspace OAuth2 (Gmail and Calendar)
   - Fireflies API Header Tokens (inside the HTTP Request sub-tools)
4. Toggle the workflow to **Active** to begin interacting with your virtual assistant.
