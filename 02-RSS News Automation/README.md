# RSS News Automation 
-This workflow used for reading news from xml files like https://feeds.bbci.co.uk/sport/football/rss.xml in football or 
https://feeds.bbci.co.uk/news/technology/rss.xml in technology and alot more .
- First we start with schedule trigger which is responsible for starting the execution after an interval of time let's say 2 sec .
- Then the node RSS read reads the whole news in the site all at once .
- Remoce dublicates node (from it's name ) it remove the dublicated news using it's link and the link is in the output from the previous node .
- Then we go into a loop over items to send each item seperated from the other items so we don't send all news at one time .
- The node wait make a period of time between sending the nodes so the nodes send in the telegram chat slowly and seperated .
- The last node is send a text message in telegram which is connected with a bot and a chat ID (my chat id in this json file ) and ofcorse it's responsible for sending the items to the chat on telegram .

## what we have learned from this project 
1 - what is xml files .
2- what is the difference between the RSS news sites and the normal news sites .
3- new nodes like wait node and loop over item (they are very usefull nodes and i think you will use them in alot of your workflows ).
4- you can also create and edit you xml file on your device with just some words like <title> and <link> don't worry it's super easy .
