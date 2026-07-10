# RSS News Automation

- This workflow is used to read news from RSS XML feeds such as:
  - https://feeds.bbci.co.uk/sport/football/rss.xml (Football)
  - https://feeds.bbci.co.uk/news/technology/rss.xml (Technology)
  - and many more.

- First, we start with the **Schedule Trigger**, which is responsible for starting the workflow execution at a specified time interval (for example, every 2 minutes).

- Then, the **RSS Read** node reads all the news articles from the RSS feed at once.

- The **Remove Duplicates** node (as its name suggests) removes duplicate news articles by comparing their **link**, which is provided by the previous node.

- Next, we use the **Loop Over Items** node to process and send each news article individually instead of sending all of them at the same time.

- The **Wait** node adds a delay between each message, allowing the news articles to be sent to the Telegram chat one by one.

- Finally, the **Telegram** node sends a text message using a Telegram bot and a Chat ID (the Chat ID has been removed from the shared `workflow.json` file). This node is responsible for delivering the news articles to the Telegram chat.

## What Have We Learned from This Project?

- What RSS XML feeds are.
- The difference between RSS news feeds and regular news websites.
- How to use useful nodes such as **Wait** and **Loop Over Items** (they are very useful nodes that you will likely use in many of your workflows).
- How to create and edit your own XML RSS feed using simple XML tags such as `<title>` and `<link>`. Don't worry—it's much easier than it looks.

> [!NOTE]
> Some sensitive data has been removed from the `workflow.json` file in this repository.
>
> This workflow is a basic template for an RSS News Reader. Feel free to customize it by adding your own nodes and features to make it more useful and powerful.

### Thanks!
