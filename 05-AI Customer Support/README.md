# AI Customer Support

- This idea is highly demanded by companies and startups.
- The purpose of this workflow is to let an AI model answer FAQ questions using a collection of data that is fed into the model.
- I will explain how to use a **PDF**, **CSV**, or other file types as a data source that the model can use to answer customers' questions.
- Then, we will connect the model to an LLM such as **Gemini Flash** to respond to customers in a professional way.
- Finally, if the model cannot find the answer in the data collection, it will redirect the customer to a real support agent who can help with the issue and respond appropriately.

## First Workflow

- This workflow is used to store the data from our file, whether it is a PDF, CSV, or any other supported type, in a **Qdrant Vector Store**.
- We start with a **Manual Trigger**, then read the file using the **Read/Write Files from Disk** node. In my case, I am using Docker, so I created a folder that Docker can access to store the files used in this project. (I used a PDF file.) This node reads the file and converts its content into **binary** so it can be processed by the following nodes.
- Then, we use the **Qdrant Vector Store** node. (There are many vector stores available, not just Qdrant, but it is one of the most recommended options for beginners.) We connect an **Embedding Model** such as **OpenAI Embeddings** or **Gemini Embeddings** (I used Gemini). The purpose of the embedding model is to convert the text into vectors so it becomes easier to search for semantically similar questions. You can think of it as converting the meaning of the text into numbers that the AI can compare.
- The **Default Data Loader** node is responsible for creating **Documents** from the binary file. At this stage, the data is **not converted into vectors yet**. This node simply prepares the extracted text in the format expected by the Vector Store.
- After that, the documents are inserted into the **Qdrant** node. Remember to set the Qdrant node to **Insert Documents** mode and give your collection a name so you can use it later in other workflows.

## Second Workflow

- After storing the file, we create a new workflow starting with a **Telegram Trigger** connected to the credentials of my Telegram bot. (I use Telegram, but you can use any other platform.) Whenever a customer sends a message, the trigger starts the workflow.
- Next comes the **AI Agent**, which is responsible for searching the vector store that we created in the previous workflow. The vector store is connected to an **Embedding Model**, which converts the customer's question into vectors so they can be compared with the stored vectors.
- The AI Agent is also connected to a **Simple Memory** node so it can remember the conversation during the current session (using the customer's chat ID). It is also connected to an **LLM**.
- When the AI Agent receives a question, it searches for the vectors that are most similar to the question vector. If it finds relevant information, the LLM generates a professional response based on the retrieved documents. If it cannot find the answer, it responds with:
  > "I couldn't find the answer in our knowledge base. I'll connect you to our support team. Please wait."
- Finally, an **IF** node checks whether the AI found an answer. If it didn't, it sends a notification to the real customer support team through **Gmail** (or any other service you choose), allowing a support representative to continue the conversation. This prevents the AI from misleading customers with unreliable or made-up answers.

> [!NOTE]
> This is a simple AI Customer Support workflow. The main purpose of building it is to practice and explore new n8n nodes.
> You can customize this idea and adapt it to any platform you like. This is only the beginning—you can continue improving it and build your own advanced AI customer support system.
>
> If this is your first time building this workflow, you may face some challenges, such as creating a Docker container for Qdrant and configuring a Docker network so that Qdrant and n8n can communicate with each other. Solving these problems yourself is a great learning experience.

> [!TIP]
> I hope this guide was useful to you. Thanks for reading!

 │
 ▼
IF
├── Answer Found → Send to Customer
└── No Answer → Notify Human Support
