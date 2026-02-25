📝 AI Sales Assistant & Client Briefing Bot
This is a standalone n8n workflow designed to automate the high-value "discovery phase" of a sales funnel. It transforms a standard Telegram bot into a professional Business Analyst that interviews potential clients, refines their requirements, and organizes their input into a structured technical brief.

🚀 Overview
Unlike static forms, this AI-driven assistant engages users in a fluid, human-like dialogue. It is specifically tuned for agencies, freelancers, and software studios to capture leads 24/7 without manual intervention.

Key Features:
Adaptive Interviewing: Uses an AI Agent (GPT-powered) to ask questions sequentially. It recognizes if a user has already provided information and skips redundant questions.

Contextual Awareness: Powered by Window Buffer Memory, the bot remembers the conversation history, allowing for follow-up questions and clarifications.

Lead Qualification: The agent is instructed to focus on extracting the "essence" of the client's needs—business model, goals, platforms, and budget.

Structured Output: Automatically pushes the finalized brief into Google Sheets only after critical contact info (Email) is captured.

🛠 Setup Instructions
1. Prerequisites
n8n installed (Self-hosted or Cloud).

Telegram Bot Token (obtain from @BotFather).

OpenAI API Key (Model recommended: gpt-4o-mini).

Google Cloud Console credentials for Google Sheets access.

2. Installation
Import the Assistant Brief.json file into your n8n instance.

Configure Credentials:

Update the Telegram Trigger with your bot token.

Connect your OpenAI account to the Chat Model node.

Authorize your Google account in the send_brif (Google Sheets) tool node.

Sheet Preparation:
Create a Google Sheet with the following headers: Date, Name, Email, Business_Description, Task, Platforms, Goals, Integrations, Budget_Timeline, Examples.

3. Customization
You can adjust the "personality" or the specific questions by editing the System Message inside the AI Agent node. Currently, it is set to a "Professional Studio Expert" persona.

🏗 Workflow Architecture
Trigger: Telegram Message.

Brain: AI Agent with tools capability.

Memory: Simple Buffer Memory (Session-based via chat_id).

Action Tool: Google Sheets "Append Row" function, triggered by the agent once the brief is complete.

⚠️ Expert Note on Security
The workflow is exported without API keys. However, it does contain the structure of the prompt and the logic for the Google Sheets tool. Ensure you re-select your specific spreadsheet and sheet name in the send_brif node after importing, as Document IDs are unique to your Google Drive.

Automate your intake, focus on the build.
