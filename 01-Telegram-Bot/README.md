# Telegram bot using n8n and Gemini 

-In this simple work flow i used the Telegram trigger node to start that flow after receving a message

-after that the message is used an an input to an AI agent node the prompet is in Workflow.json

>[I am using n8n on Docker so I used ngrok to create a tunnel so telegram can communicate with my n8n account ]

-Then the message is sent to Gemini-3-flash {the LLM in this workflow } .

-The respond is sent using sent a text message noe  to the account using it's chat id .

 >[!TIP]
>This workflow is so simple and the porpuse from it is to demonstrate how to deal with http requests and use the Credential with telegram

## Thank you !
