---
title: "Как использовать GraphClient для Microsoft Graph"
url: /ru/java/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Работа с GraphClient**
Пример [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) класс обрабатывает запросы на сборку, отправляет их в Microsoft Graph API и обрабатывает ответы.
### **Создайте объект ITokenProvider**
Чтобы создать новый экземпляр [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) класс, вам необходимо предоставить экземпляр [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), который может аутентифицировать запросы к Microsoft Graph.


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
### **Получите объект GraphClient**
После того, как вы установили TokenProvider, вы должны получить [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) возражать против запросов к сервису.
После того, как вы получите [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) который прошел аутентификацию, вы можете начать звонить в службу.


~~~Java
IGraphClient client = GraphClient.getClient(tokenProvider);
~~~
## **Работа с папками с помощью Microsoft Graph**

### **Список папок**

~~~Java
GraphFolderInfoCollection folders = client.listFolders();
for (GraphFolderInfo folderInfo : folders) {
    System.out.println(folderInfo.getDisplayName());
    for (KeyValuePair<Long, MapiProperty> prop : folderInfo.getProperties()) {
        System.out.println(prop.getValue().getDescriptor().toString() + " " + prop.getValue().getString());
    }
}
~~~
### **Список подпапок из папки «Входящие»**


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~
### **Создать корневую папку**


~~~Java
GraphFolderInfo newFolder = client.createFolder("TEST_FOLDER");
~~~
### **Создать подпапку**


~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "TEST_SUBFOLDER_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "TEST_SUBFOLDER_2");
~~~
### **Получить папку**


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~
### **Обновить папку**


~~~Java
GraphFolderInfo originalFolder = client.createFolder("TEST_FOLDER");
originalFolder.setDisplayName("NEW_TEST_FOLDER");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~
### **Скопировать папку и содержимое**


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
### **Переместить папку и содержимое**


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~
### **Удалить папку**


~~~Java
client.delete(testFolder.getItemId());
~~~
## **Список сообщений с помощью Microsoft Graph**

~~~Java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
~~~

### **Список сообщений по дате отправки**

The [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) функция используется для указания того, что сообщения должны быть упорядочены в порядке возрастания по дате отправки. Это позволяет клиенту получить список сообщений из [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) папка в определенном порядке, в данном случае в зависимости от даты отправки.

В следующем примере кода показано, как создать запрос, определяющий порядок сообщений по дате отправки, а затем использовать этот запрос для извлечения страницы сообщений из папки «Входящие» с помощью Graph API:

```java
// create orderby messages query 'ASC'
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.getSentDate().orderBy(true);
MailQuery query = builder.getQuery();

GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(10), query);
```

### **Получить сообщение**


~~~Java
GraphMessageInfo messageInfo = messageInfoColl.get(0);
MapiMessage fetchedMessage = client.fetchMessage(messageInfo.getItemId());
~~~

### **Разбивка на страницы в списке сообщений**

API обеспечивает поддержку разбиения на страницы и фильтрации сообщений со списком. Это очень удобно, если в почтовом ящике содержится большое количество сообщений и для получения сводной информации о них требуется много времени. В приведенном ниже примере кода показано, как использовать пейджинг для больших наборов сообщений при отображении сообщений с сервера Exchange с помощью iGraphClient:

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

### **Создать сообщение**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Subject");
message.setBody("Body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Обновить сообщение**


~~~Java
fetchedMessage.setSubject("Update message");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
~~~
### **Отправить сообщение**


~~~Java
client.send(message);
~~~
### **Отправить черновик сообщения**


~~~Java
MapiMessage draftMessage = client.createMessage(GraphKnownFolders.Drafts, message);
client.send(draftMessage.getItemId());
~~~
### **Скопировать сообщение**


~~~Java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Переместить сообщение**


~~~Java
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Вложения в сообщения**


~~~Java
MapiAttachmentCollection attachments = client.listAttachments(fetchedMessage.getItemId());
for (MapiAttachment att : attachments) {
    client.deleteAttachment(att.getItemId());
}
~~~
### **Удалить сообщение**


~~~Java
client.delete(message.getItemId());
~~~
## **Категории Api**


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
## **Переопределяет API**


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
## **Правила Api**


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
## **Использование ресурса для поддержки нескольких почтовых ящиков**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// back to the current mailbox
сlient.setResource(ResourceType.Me);
~~~