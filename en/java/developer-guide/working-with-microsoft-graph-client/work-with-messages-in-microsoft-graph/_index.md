---
title: Work with Messages using Microsoft Graph
ArticleTitle: Work with Messages using Microsoft Graph
type: docs
weight: 20
url: /java/manage-messages-with-microsoft-graph/
---


**Aspose.Email for Java** provides a rich set of APIs for managing messages through Microsoft Graph. You can list, fetch, create, update, move, copy, and delete messages, as well as handle pagination and attachments. The code samples below are examples of the most common operations.

## **List Messages**

You can retrieve messages from a specific folder, such as Inbox, and fetch their full content:

```java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
```

### **List Messages by Date Sent**

To sort messages by sent date in ascending order, you can use the `OrderBy` feature of [GraphQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/graphquerybuilder/):

```java
// create orderby messages query 'ASC'
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.getSentDate().orderBy(true);
MailQuery query = builder.getQuery();

GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(10), query);
```

## **Fetch Message**

Once you have a message reference, you can fetch its complete content:

```java
GraphMessageInfo messageInfo = messageInfoColl.get(0);
MapiMessage fetchedMessage = client.fetchMessage(messageInfo.getItemId());
```

## **Update a Message**

After fetching a message, you can modify its content and update it on the server:

```java
fetchedMessage.setSubject("Update message");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
```


## **Pagination in Message Listing**

When working with large mailboxes, you can use paging to retrieve messages in chunks. The example below demonstrates listing unread messages in pages of two items each:

```java
// send ping test messages
for (int i = 0; i < 5; i++) {
    MailMessage eml = new MailMessage(user.EMail, user.EMail, "ping" + i, "test body");
    client.send(MapiMessage.fromMailMessage(eml));
}
// waiting for inbox
Thread.sleep(10000);

// paging option
int itemsPerPage = 2;
// create unread messages filter
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.isRead().equals(false);
MailQuery query = builder.getQuery();

// list messages
GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(itemsPerPage), query);
GraphMessageInfoCollection messages = pageInfo.getItems();
while (!pageInfo.getLastPage())
{
    pageInfo = client.listMessages(GraphKnownFolders.Inbox, pageInfo.getNextPage(), query);
    // add next page items to common collection
    messages.addRange(pageInfo.getItems());
}

// set messages state as read
for (GraphMessageInfo message : messages) {
    client.setRead(message.getItemId());
}
```

## **Create a Message**

You can create new messages with subject, body, and properties:

```java
MapiMessage message = new MapiMessage();
message.setSubject("Subject");
message.setBody("Body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
```

## **Send Message**

You can send a message directly:

```java
client.send(message);
```

Or send a draft message after creating it in the Drafts folder:

```java
MapiMessage draftMessage = client.createMessage(GraphKnownFolders.Drafts, message);
client.send(draftMessage.getItemId());
```

## **Copy and Move Messages**

Messages can be copied or moved between folders:

```java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
```


## **Manage Attachments**

To list and remove attachments from a message, use the following code sample:

```java
MapiAttachmentCollection attachments = client.listAttachments(fetchedMessage.getItemId());
for (MapiAttachment att : attachments) {
    client.deleteAttachment(att.getItemId());
}
```

## **Delete a Message**

Finally, you can delete a message permanently:

```java
client.delete(message.getItemId());
```