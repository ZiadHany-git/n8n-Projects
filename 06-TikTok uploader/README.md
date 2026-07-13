# The Idea

- This project is designed to upload images from your device to TikTok automatically.
- This will help you post every day without any effort, and even if you forget to share your videos or images, this workflow will handle the job for you.

> [!TIP]
> I am using local images in this workflow without any video generation process using a Chat Model. The images are stored locally on my device.
>
> You can absolutely add an AI Agent node and use any Chat Model you want, but I prefer this approach to share my content on TikTok.

## First Workflow

- First, we need to get the API access tokens from TikTok to allow the workflow to publish content.
- Unfortunately, there is no official community node for TikTok in n8n, so I used HTTP Request nodes to handle the API communication.

- We start with a Manual Trigger in this first workflow. Remember, the main purpose of this workflow is to obtain API access and allow n8n to control the TikTok account.

> [!NOTE]
> To be continued...
