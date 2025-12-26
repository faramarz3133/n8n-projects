🤖 TechNo RAG-Assist: Multimodal AI Support System
TechNo RAG-Assist is an enterprise-grade AI solution designed for "TechNo Academy" to automate customer support using Retrieval-Augmented Generation (RAG). The system ensures that AI responses are strictly grounded in official documentation, eliminating hallucinations and providing 100% factual accuracy.

The project consists of two specialized workflows:

The Query Engine (Main Agent): Handles user interactions via text and voice.

<img width="1669" height="540" alt="RAG-Agent" src="https://github.com/user-attachments/assets/4e4f4760-a34a-4edf-95a0-517b8b62fa4f" />

The Ingestion Pipeline: Automates the loading and vectorization of new documents into the database.

<img width="761" height="478" alt="add file to PGVector Store" src="https://github.com/user-attachments/assets/38332cb7-6747-4ce4-978b-b55bfc3da3b1" />


🏗 System Architecture
1. Main Query Workflow (Rag.json)
This workflow acts as the interface between the user and the academy's knowledge base.

Multimodal Input Processing: Uses a Switch node to distinguish between text and voice messages.

Voice Transcription: If a voice note is received, the Get a file node downloads it, and Gemini 2.5 Flash transcribes it into text.

Agentic Reasoning: An AI Agent powered by Gemini utilizes the Postgres PGVector Store as its primary tool to retrieve specific context before answering.

Persistent Memory: A Postgres Chat Memory node ensures the bot remembers past interactions within the session.

Output Refinement: A JavaScript Code node cleans the AI's output (removing unnecessary characters) before the Telegram node sends the final response.

2. Knowledge Ingestion Workflow (Add file to PGVector Store.json)
This workflow is used to populate or update the "Brain" of the bot.

Form Interface: Uses an On form submission trigger to allow admins to upload new documents (PDF/Text).

Document Loading: The Default Data Loader processes the binary file.

Vectorization: Google Gemini Embeddings convert the text into mathematical vectors.

Storage: The Postgres PGVector Store node inserts the vectors into the database for future retrieval by the main agent.

🛠 Tech Stack
Automation Platform: n8n.

Large Language Model: Google Gemini (Flash & Pro models).

Vector Database: PostgreSQL with the PGVector extension.

Interface: Telegram Bot API.

Embedding Model: Google Gemini Embeddings.

📖 Setup & Usage
Step 1: Data Ingestion
Execute the Add file to PGVector Store workflow.

Access the n8n form and upload your academy's official documents (e.g., refund policies, course FAQs).

The system will automatically index these files into your Postgres database.

Step 2: Querying the Bot
Start the Rag workflow.

Send a text message or a voice note to the Telegram Bot.


The bot will search the PGVector Store, retrieve the relevant facts, and provide a grounded response based on the uploaded files.
