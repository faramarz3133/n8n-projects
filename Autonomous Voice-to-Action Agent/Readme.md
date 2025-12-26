# Autonomous Voice-to-Action Agent 🎙️➡️🚀

An intelligent orchestration system that captures voice requests via **ElevenLabs**, processes them using **Google Gemini**, and executes actions through the **Model Context Protocol (MCP)**.

---
<img width="1000" height="500" alt="Autonomous Voice-to-Action Agent" src="https://github.com/user-attachments/assets/4b8ab921-8cf9-44ca-afef-310ce77ca9da" />

<img width="640" height="480" alt="MCP Server" src="https://github.com/user-attachments/assets/63ccc877-f460-48ab-b8c7-0aa5c64e15f3" />


## 📋 How It Works

This agent acts as a digital executive assistant. The workflow is triggered by a voice command which is transcribed and sent to n8n. The AI Agent then decides which tool to use based on your intent.

### Core Workflow:
1. **Trigger:** A Webhook receives the `User_Request` (transcribed audio) from the ElevenLabs Agent.
2. **Brain:** **Google Gemini** (Chat Model) analyzes the request.
3. **Execution:** The **AI Agent** uses the **MCP Client** to access specialized tools.
4. **Response:** The system confirms the action via a "Respond to Webhook" node.

---

## 🛠️ Integrated Tools (via MCP Client)

The agent is equipped with the following capabilities:
- **📧 Gmail Service:** Send professional emails directly through voice commands.
- **📢 Telegram Integration:** Post updates, news, or messages to specific Telegram channels.
- **🌐 Web Search:** Perform real-time searches to provide up-to-date information.

---

## ⚙️ Technical Details (n8n Configuration)

- **Language Model:** Google Gemini (using `googlePalmApi` credentials).
- **Agent Type:** AI Agent (LangChain) with Tool-calling capabilities.
- **Input Handling:** Dynamically maps `{{ $json.body.User_Request }}` from the incoming Webhook.
- **Architecture:** Modular MCP (Model Context Protocol) integration for scalable tool management.

---

## 🚀 Setup Instructions

1. **n8n Workflow:**
   - Import the `Autonomous_Voice-to-Action_Agent.json` file into your n8n instance.
   - Configure your **Google Gemini API** credentials.

2. **ElevenLabs Configuration:**
   - Create a Conversational Agent in ElevenLabs.
   - Set the Webhook URL to point to the **n8n Webhook node** path.

3. **MCP Servers:**
   - Ensure your MCP servers for Gmail, Telegram, and Web Search are active and linked to the **MCP Client** node URL in the workflow.


