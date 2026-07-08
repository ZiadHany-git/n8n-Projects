# Telegram AI Bot with n8n & Google Gemini

An automated, intelligent Telegram bot that handles user interactions and responds automatically in Arabic. This project leverages the power of **n8n** for seamless workflow automation and integrates **Google Gemini** as the core LLM (Large Language Model) to generate smart, contextual replies.

---

## 🚀 Features

- **Automated AI Responses:** Uses Gemini to understand incoming user messages and generate accurate, natural Arabic responses.
- **Contextual Memory:** Equipped with a `Simple Memory` node, allowing the AI to recall previous conversation context for a natural chat flow.
- **Low-Code Automation:** Built entirely within n8n using visual workflows, eliminating the need to write complex webhook server code from scratch.

## 🛠️ Tech Stack

- **n8n:** Workflow automation platform managing the webhook integration and logic execution.
- **Google Gemini API:** The underlying AI model powering the chat responses.
- **Telegram Bot API:** For receiving triggers and sending text messages back to the users.
- **ngrok:** Used during development to create a secure tunnel exposing the local n8n instance to Telegram webhooks.

---

## 📐 Workflow Architecture

The sequential flow of this project consists of the following nodes:
1. **Telegram Trigger:** Listens live for any new message updates sent to the bot.
2. **AI Agent:** The central orchestration node that connects the AI model, memory, and prompt instructions.
3. **Google Gemini Chat Model:** Process text generation requests.
4. **Simple Memory:** Maintains chat history for individual users.
5. **Send a Text Message (Telegram Node):** Dynamically passes the AI's response back to the user utilizing the incoming chat ID.

---

## ⚙️ Setup Instructions

### 1. Create a Telegram Bot
- Find `@BotFather` on Telegram and send the `/newbot` command to create your bot.
- Copy and save the provided **API Token**.

### 2. Get your Gemini API Key
- Go to Google AI Studio and generate a free API key.

### 3. n8n Import & Configuration
- Import this workflow JSON file into your n8n instance.
- Configure your credentials for both the Telegram and Google Gemini nodes.
- In the final **Send a Text Message** node, ensure the **Chat ID** field is set to expression mode and dynamically mapped from the trigger: `{{ $json.message.chat.id }}`.
- Map the **Text** field to output the AI Agent's response: `{{ $json.output }}`.
- Click **Publish** in the top-right corner to activate the workflow 24/7.

---

## 📝 Troubleshooting & Notes
- **High Demand Error (503):** If you encounter a `Service Unavailable` or high demand error when using preview models, it is highly recommended to switch to a stable model release (such as `gemini-1.5-flash`). 
- **Auto-Retry:** To maximize uptime, enable **Retry Automatically** under the `Settings` tab of your AI/Gemini nodes within n8n to gracefully handle temporary API spikes.
