---
title: How to use GraphClient for Microsoft Graph
type: docs
weight: 20
url: /java/how-to-use-graphclient-for-microsoft-graph/
---


## **Working with GraphClient**
An instance of the [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) class handles building requests, sending them to the Microsoft Graph API, and processing the responses.
### **Create an ITokenProvider Object**
To create a new instance of [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) class, you need to provide an instance of [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), which can authenticate requests to Microsoft Graph.


~~~Java
ITokenProvider tokenProvider = new ITokenProvider() {
    Date expirationDate = null;

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        // Gets oAuth access token.
        // If ignoreExistingToken is true, requests new token from a server. Otherwise behavior is depended on whether token exists or not.
        // If token exists and its expiration date is not expired returns current token, otherwise requests new token from a server.
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        // Gets oAuth access token.
        // If token exists and its expiration date is not expired returns current token, otherwise requests new token from a server.
        return new OAuthToken("token", expirationDate);
    }
};
~~~
### **Get a GraphClient object**
After you have set the TokenProvider, you must get a [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) object to make requests against the service.
After you have a [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) that is authenticated, you can begin making calls against the service.


~~~Java
IGraphClient client = GraphClient.getClient(tokenProvider);
~~~
## **Work with Folders using Microsoft Graph**

### **List Folders**

~~~Java
GraphFolderInfoCollection folders = client.listFolders();
for (GraphFolderInfo folderInfo : folders) {
    System.out.println(folderInfo.getDisplayName());
    for (KeyValuePair<Long, MapiProperty> prop : folderInfo.getProperties()) {
        System.out.println(prop.getValue().getDescriptor().toString() + " " + prop.getValue().getString());
    }
}
~~~
### **List Subfolders from Inbox Folder**


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~
### **Create Root Folder**


~~~Java
GraphFolderInfo newFolder = client.createFolder("TEST_FOLDER");
~~~
### **Create Subfolder**


~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "TEST_SUBFOLDER_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "TEST_SUBFOLDER_2");
~~~
### **Get Folder**


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~
### **Update Folder**


~~~Java
GraphFolderInfo originalFolder = client.createFolder("TEST_FOLDER");
originalFolder.setDisplayName("NEW_TEST_FOLDER");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~
### **Copy Folder and Content**


~~~Java
GraphFolderInfo parentFolder = client.createFolder("PARENT_FOLDER");
GraphFolderInfo testFolder = client.createFolder("TEST_FOLDER");
GraphFolderInfo testSubFolder = client.createFolder(testFolder.getItemId(), "TEST_SUBFOLDER");

MapiMessage message = new MapiMessage();
message.setSubject("Test subject");
message.setBody("Test body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");
MapiMessage createdMessage = client.createMessage(testSubFolder.getItemId(), message);

GraphFolderInfo folderCopy = client.copyFolder(parentFolder.getItemId(), testFolder.getItemId());

GraphFolderInfoCollection folderColl = client.listFolders(parentFolder.getItemId());
// TEST_FOLDER
System.out.println(folderColl.get(0).getDisplayName());

folderColl = client.listFolders(folderColl.get(0).getItemId());
// TEST_SUBFOLDER
System.out.println(folderColl.get(0).getDisplayName());

GraphMessageInfoCollection listMessages = client.listMessages(folderColl.get(0).getItemId());
// Test subject
System.out.println(listMessages.get(0).getSubject());
~~~
### **Move Folder and Content**


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~
### **Delete Folder**


~~~Java
client.delete(testFolder.getItemId());
~~~
## **List Messages using Microsoft Graph**

~~~Java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
~~~

### **List Messages by Date Sent**

The [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) feature is used to indicate that the messages should be ordered in ascending order by their sent date. This allows the client to retrieve the list of messages from the [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) folder in a specific order, in this case, based on the sent date.

The following code sample demonstrates how to create a query that specifies ordering of messages by sent date, and then use this query to fetch a page of messages from the Inbox folder using the Graph API:

```java
// create orderby messages query 'ASC'
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.getSentDate().orderBy(true);
MailQuery query = builder.getQuery();

GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(10), query);
```

### **Fetch Message**


~~~Java
GraphMessageInfo messageInfo = messageInfoColl.get(0);
MapiMessage fetchedMessage = client.fetchMessage(messageInfo.getItemId());
~~~

### **Pagination in Message Listing**

The API provides the paging and filtering support for listing messages. This is very helpful when a mailbox has a large number of messages and requires a lot of time for retrieving the summary information about them. The code sample below will show you how to use paging for large message sets when listing messages from Exchange Server using IGraphClient:

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

### **Create Message**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Subject");
message.setBody("Body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Update Message**


~~~Java
fetchedMessage.setSubject("Update message");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
~~~
### **Send Message**


~~~Java
client.send(message);
~~~
### **Send Draft Message**


~~~Java
MapiMessage draftMessage = client.createMessage(GraphKnownFolders.Drafts, message);
client.send(draftMessage.getItemId());
~~~
### **Copy Message**


~~~Java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Move Message**


~~~Java
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Message Attachments**


~~~Java
MapiAttachmentCollection attachments = client.listAttachments(fetchedMessage.getItemId());
for (MapiAttachment att : attachments) {
    client.deleteAttachment(att.getItemId());
}
~~~
### **Delete Message**


~~~Java
client.delete(message.getItemId());
~~~
## **Categories Api**


~~~Java
String categoryName = "Test Category";
int preset = CategoryPreset.Preset10;
OutlookCategory category = client.createCategory(categoryName, preset);
OutlookCategory fetchedCategory = client.fetchCategory(category.getId());

List<OutlookCategory> categories = client.listCategories();

fetchedCategory.setDisplayName("Update Category");
fetchedCategory.setPreset(CategoryPreset.Preset11);
OutlookCategory updatedCategory = client.updateCategory(fetchedCategory);

client.delete(category.getId());
~~~
## **Overrides Api**


~~~Java
int focusedType = ClassificationType.Focused;
ClassificationOverride override = client.createOrUpdateOverride(new MailAddress("testUser@host.com", "testUser"), focusedType);

List<ClassificationOverride> list = client.listOverrides();
for (ClassificationOverride item : list)
    System.out.println(item.getSender().getAddress());

ClassificationOverride fetchedOverride = list.get(0);
fetchedOverride.setClassifyAs(ClassificationType.Other);
fetchedOverride.getSender().setDisplayName("testUser_1");

ClassificationOverride updatedOverride = client.createOrUpdateOverride(fetchedOverride);

fetchedOverride.setClassifyAs(ClassificationType.Focused);
updatedOverride = client.updateOverride(fetchedOverride);

client.delete(updatedOverride.getId());
~~~
## **Rules Api**


~~~Java
InboxRule rule = new InboxRule();
rule.setDisplayName("Test rule");
rule.setPriority(1);
rule.setEnabled(true);
rule.setConditions(new RulePredicates());
rule.getConditions().containsSenderStrings(new StringCollection());
rule.getConditions().containsSenderStrings().addItem("testUser");
rule.setActions(new RuleActions());
rule.getActions().setForwardToRecipients(new MailAddressCollection());
rule.getActions().getForwardToRecipients().addMailAddress(new MailAddress("testUser@host.com", "testUser", true));
rule.getActions().setStopProcessingRules(true);

InboxRule createdRule = client.createRule(rule);

List<InboxRule> listedRules = client.listRules();
for (InboxRule item : listedRules)
    System.out.println(item.getDisplayName());

InboxRule fetchedRule = client.fetchRule(createdRule.getRuleId());

createdRule.setDisplayName("Test rule 1");
createdRule.setEnabled(false);
InboxRule updatedRule = client.updateRule(createdRule);

client.delete(createdRule.getRuleId());
~~~
## **Using Resource to Support Multiple Mailboxes**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// back to the current mailbox
сlient.setResource(ResourceType.Me);
~~~