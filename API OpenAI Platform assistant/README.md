OpenAI Assistant + Telegram (with Context Memory)
This n8n workflow provides a robust foundation for deploying a professional AI assistant on Telegram using the OpenAI Assistants API. It features persistent conversation threads and automated message handling.

Key Features
Contextual Memory: Utilizes a Window Buffer Memory node to retain the last 10 interactions per user, ensuring coherent multi-turn conversations.

User Isolation: Dynamically routes sessions using the Telegram from.id, providing a secure and private chat environment for every user.

Assistants API Integration: Designed to work with custom OpenAI Assistants, allowing you to leverage specialized instructions, Knowledge Bases (RAG), and Tools like Code Interpreter.

Scalable Architecture: A streamlined, event-driven design that minimizes latency and is easy to extend with additional logic (e.g., logging or external API calls).

Technical Setup
OpenAI Configuration:

Create an assistant at platform.openai.com.

Configure your model (GPT-4o/GPT-4-turbo) and instructions.

Copy the Assistant ID (starts with asst_).

n8n Configuration:

Credentials: Add your OpenAI API Key and Telegram Bot Token.

Node Parameters: Open the Message a model node and paste your Assistant ID into the designated field.

Memory: The Session ID is pre-configured to use the Telegram user ID for persistent threading.

Deployment:

Activate the workflow.

Send a message to your bot to initialize the first thread.

Workflow Logic
Trigger: Receives inbound messages via Telegram Webhook.

Processing: Sends the text to the OpenAI Assistant while retrieving/updating the specific user's conversation history.

Output: Forwards the AI-generated response back to the user's Telegram chat.
