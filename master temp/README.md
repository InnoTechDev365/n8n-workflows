🛠 AI Service Manager: Lead-to-Order Automation
This n8n workflow is a specialized solution for service-based businesses (handymen, cleaning, repairs). It acts as a 24/7 manager that handles client inquiries, qualifies leads, and automatically synchronizes orders across your entire tech stack.

🌟 Key Features
Intelligent Onboarding: The AI Agent follows a strict 5-step data collection protocol (Name, Phone, Address, Service Type, Schedule).

Context-Aware Memory: Built-in rules prevent the "annoying bot" effect—the agent never asks for the same information twice.

Triple-Sync Architecture: Once an order is confirmed, the system simultaneously:

Records the lead in Google Sheets.

Stores the structured data in Supabase.

Books the appointment in Google Calendar.

Handover Logic: Detects when a lead is "ready" and triggers the extraction of structured JSON from natural conversation.

🛠 Prerequisites
To deploy this workflow, you need:

n8n (version 1.0+ recommended).

OpenAI API Key (for GPT-4o / GPT-4o-mini).

Supabase Account (for permanent order storage).

Google Cloud Console Credentials (with access to Sheets and Calendar APIs).

🚀 Setup & Installation
1. Database & Sheets Preparation
Google Sheets: Create a sheet with columns: Name, Phone, Address, Service, Date.

Supabase: Create an orders table to match the schema.

Google Calendar: Ensure you have a dedicated calendar for service bookings.

2. Workflow Configuration
Import the master temp.json file.

AI Agent Node: Review the System Message. It is currently set to a "Private Handyman Service" persona. You can change this to any service industry.

Tool Linking: * Re-connect the Google Sheets node.

Re-connect the Supabase node.

Re-connect the Google Calendar node.

Timezone: The current logic is set to Asia/Jerusalem. Change this in the AI Agent system prompt to your local timezone.

🏗 How It Works (The Logic)
The Chat Trigger: Receives the client request.

The Brain: The AI Agent uses Collect Order Data as a custom tool to verify if the "order package" is complete.

The Switch: A Check if Order Saved node acts as a gatekeeper, ensuring data only moves to the database once all 5 required fields are present.

The Execution: Data is parsed and sent to all three external integrations.
