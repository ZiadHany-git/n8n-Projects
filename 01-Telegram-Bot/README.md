### Telegram Bot Using n8n and Gemini

- In this simple workflow, I used the **Telegram Trigger** node to start the flow immediately after receiving a message.
- After that, the incoming message is used as an input for the **AI Agent** node (the system prompt can be found inside `Workflow.json`).
- *Note: Since I am hosting n8n locally via Docker, I used **ngrok** to create a secure tunnel so Telegram can communicate with my local n8n instance via webhooks.*
- Then, the message payload is sent to **Gemini-1.5-Flash** (the core LLM utilized in this workflow) to generate the text response.
- Finally, the response is sent back to the user using the **Send a Text Message** node, dynamically utilizing the user's specific **Chat ID**.

### 💡 Tip
This workflow is deliberately kept simple. Its main purpose is to demonstrate how to manage incoming HTTP webhook requests and how to securely configure and handle API credentials with Telegram and external LLMs.

Thank you!
