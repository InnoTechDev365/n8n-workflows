🧠 AI Knowledge-Base Ecosystem (RAG) for n8n
Welcome to a professional-grade Retrieval-Augmented Generation (RAG) implementation built entirely in n8n. This ecosystem allows you to transform static documentation into a dynamic, AI-powered assistant that provides accurate answers based exclusively on your proprietary data.

📐 Architecture Overview
The system is engineered into two decoupled workflows to ensure scalability and ease of maintenance:

The Ingestion Pipeline (database loading1.json): This handles the lifecycle of your knowledge base, from monitoring cloud storage to indexing vector data.

The Intelligence Interface (Assistant1.json): The front-end AI Agent that interacts with users via Telegram, utilizing the vector store to provide grounded responses.

🛠 Technical Requirements
To deploy this ecosystem, you will need:

n8n Instance (Self-hosted or Cloud).

OpenAI API Key (For embeddings and LLM logic).

Supabase Project (With the pgvector extension enabled).

Google Cloud Console Account (For Google Drive monitoring).

Telegram Bot Token.

🚀 Setup & Deployment
1. Database Schema
Ensure your vector database table is set up correctly. Execute the following logic in your Supabase SQL Editor:

SQL
-- -- Включаем расширение pgvector
CREATE EXTENSION IF NOT EXISTS vector;

-- Таблица для хранения документов
CREATE TABLE documents (
  id bigserial PRIMARY KEY,
  content text,
  metadata jsonb,
  embedding vector(1536)
);
…  metadata jsonb,
  similarity float
)
LANGUAGE plpgsql
AS $$
#variable_conflict use_column
BEGIN
  RETURN QUERY
  SELECT
    id,
    content,
    metadata,
    1 - (documents.embedding <=> query_embedding) AS similarity
  FROM documents
  WHERE metadata @> filter
  ORDER BY documents.embedding <=> query_embedding
  LIMIT match_count;
END;
$$;


-- Example: Enable pgvector and create your table with 1536 dimensions
2. Workflow Configuration
Import the .json files into your n8n instance.

Ingestion Setup:

Open the database loading1 workflow.

In the Google Drive Trigger, set the Folder ID to: [INSERT YOUR GOOGLE DRIVE FOLDER ID HERE].

Credential Assignment:

Re-assign your credentials to the OpenAI, Supabase, and Telegram nodes.

Agent Tooling:

In the Assistant1 workflow, ensure the Vector Store Tool is correctly linked to the AI Agent node.

📝 Persona & Logic Customization
AI Agent Prompt
You can modify the "personality" and rules of your assistant by editing the System Message in the AI Agent node:

Current Configuration: [INSERT A BRIEF DESCRIPTION OF YOUR SYSTEM PROMPT HERE]

Data Processing
Chunk Size: [INSERT CHUNK SIZE, e.g., 1000]

Chunk Overlap: [INSERT OVERLAP, e.g., 200]

💡 Expert Recommendations
Memory: Currently uses Window Buffer Memory. For long-term persistence, consider a database-backed memory provider.

Syncing: The ingestion pipeline is set to poll every [INSERT POLLING INTERVAL]. Adjust this based on how often your documents change.

Accuracy: To minimize hallucinations, ensure the System Message instructs the agent to answer only from the provided context.

🔒 Security & Privacy
Zero Leakage: This template has been scrubbed of all pinData, API keys, and personal session IDs.

Data Sovereignty: Your data remains within your n8n and Supabase instances.

Crafted by [INSERT YOUR NAME/BRAND]
