Personal AI Second Brain (n8n + Supabase + Whisper)
A high-performance intelligence assistant designed for seamless knowledge capture, organization, and retrieval via Telegram. This system processes multimodal inputs (text and voice), indexes them into a semantic vector store, and enables context-aware information retrieval through a conversational AI agent.

🏗 System Architecture
The workflow is built on an event-driven model within n8n:

Interface: Telegram Bot API for real-time interaction.

Speech Processing: OpenAI Whisper for high-accuracy voice-to-text transcription.

Cognitive Engine: LangChain-powered AI Agent with dynamic system memory.

Vector Database: Supabase (pgvector) for long-term semantic storage and retrieval.

Orchestration: n8n automated pipelines for routing, data preparation, and logic execution.

🚀 Key Features
Multimodal Capture: Automatic handling of text and voice notes. Whisper integration ensures voice inputs are transcribed and indexed instantly.

Semantic Retrieval: Information is retrieved based on intent and meaning rather than simple keywords, using vector embeddings.

Knowledge Management: Built-in CRUD capabilities allowing users to list, view, and edit stored goals or records directly through the Telegram interface.

Contextual Intelligence: The agent utilizes the Supabase Vector Store as a tool to cross-reference new inputs with existing knowledge.

🛠 Tech Stack
Workflow Engine: n8n (Advanced AI Agent nodes).

Database: Supabase (PostgreSQL + pgvector).

Models: OpenAI GPT-4o (Reasoning) & Whisper (Audio).

Deployment: Webhook-based integration with Telegram Bot API.

⚙️ Setup & Configuration
1. Database Schema
Ensure your Supabase instance has the pgvector extension enabled. Create a documents table with the following structure:

id: uuid (primary key)

content: text

metadata: jsonb

embedding: vector(1536)

2. n8n Configuration
Import the provided JSON workflow.

Configure credentials for Telegram, OpenAI, and Supabase.

In the Telegram nodes, ensure Resize Keyboard is enabled under Reply Markup options for a clean UI.

3. Agent Integration
Verify the Supabase Vector Store node is connected to the AI Agent as a Tool.

Set the Binary Property in the Whisper node to data to match the Telegram download output.

📋 Usage Commands
/start — Initialize the assistant and display the Quick Start guide.

Voice/Text Message — Automatically indexes the content into the vector store.

📋 Все цели — Triggers a semantic search to list all current records.

✍️ Редактировать — Initiates the interactive editing protocol for existing entries.
