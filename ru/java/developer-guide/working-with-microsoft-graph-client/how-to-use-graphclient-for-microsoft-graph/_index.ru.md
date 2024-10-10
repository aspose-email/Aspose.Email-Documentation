---
title: "Как использовать GraphClient для Microsoft Graph"
url: /ru/java/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Работа с GraphClient**
Экземпляр класса [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) обрабатывает создание запросов, их отправку в Microsoft Graph API и обработку ответов.
### **Создайте объект ITokenProvider**
Чтобы создать новый экземпляр класса [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient), вам нужно предоставить экземпляр [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), который может аутентифицировать запросы к Microsoft Graph.


~~~Java
ITokenProvider tokenProvider = new ITokenProvider() {
    Date expirationDate = null;

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        // Получает oAuth токен доступа.
        // Если ignoreExistingToken равно true, запрашивает новый токен у сервера. В противном случае поведение зависит от наличия токена.
        // Если токен существует и его срок действия не истек, возвращает текущий токен, иначе запрашивает новый токен у сервера.
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        // Получает oAuth токен доступа.
        // Если токен существует и его срок действия не истек, возвращает текущий токен, иначе запрашивает новый токен у сервера.
        return new OAuthToken("token", expirationDate);
    }
};
~~~
### **Получите объект GraphClient**
После того, как вы настроили TokenProvider, вам нужно получить объект [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient), чтобы делать запросы к сервису.
После того, как у вас есть аутентифицированный [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient), вы можете начать делать вызовы к сервису.


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
### **Список подпаок из папки «Входящие»**


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~
### **Создать корневую папку**


~~~Java
GraphFolderInfo newFolder = client.createFolder("ТЕСТОВАЯ_ПАПКА");
~~~
### **Создать подпапку**


~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "ТЕСТОВАЯ_ПОДПАПКА_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "ТЕСТОВАЯ_ПОДПАПКА_2");
~~~
### **Получить папку**


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~
### **Обновить папку**


~~~Java
GraphFolderInfo originalFolder = client.createFolder("ТЕСТОВАЯ_ПАПКА");
originalFolder.setDisplayName("НОВАЯ_ТЕСТОВАЯ_ПАПКА");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~
### **Копировать папку и содержимое**


~~~Java
GraphFolderInfo parentFolder = client.createFolder("РОДИТЕЛЬСКАЯ_ПАПКА");
GraphFolderInfo testFolder = client.createFolder("ТЕСТОВАЯ_ПАПКА");
GraphFolderInfo testSubFolder = client.createFolder(testFolder.getItemId(), "ТЕСТОВАЯ_ПОДПАПКА");

MapiMessage message = new MapiMessage();
message.setSubject("Тестовая тема");
message.setBody("Тестовое тело");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "от");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");
MapiMessage createdMessage = client.createMessage(testSubFolder.getItemId(), message);

GraphFolderInfo folderCopy = client.copyFolder(parentFolder.getItemId(), testFolder.getItemId());

GraphFolderInfoCollection folderColl = client.listFolders(parentFolder.getItemId());
// ТЕСТОВАЯ_ПАПКА
System.out.println(folderColl.get(0).getDisplayName());

folderColl = client.listFolders(folderColl.get(0).getItemId());
// ТЕСТОВАЯ_ПОДПАПКА
System.out.println(folderColl.get(0).getDisplayName());

GraphMessageInfoCollection listMessages = client.listMessages(folderColl.get(0).getItemId());
// Тестовая тема
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

Функция [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) используется для указания того, что сообщения должны упорядочиваться по возрастанию по их дате отправки. Это позволяет клиенту получать список сообщений из папки [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) в определенном порядке, в данном случае, на основе даты отправки.

Следующий пример кода демонстрирует, как создать запрос, указывающий порядок сообщений по дате отправки, и затем использовать этот запрос для получения страницы сообщений из папки «Входящие», используя Graph API:

```java
// создать запрос на упорядочивание сообщений 'ASC'
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

### **Пагинация в списке сообщений**

API предоставляет поддержку постраничной навигации и фильтрации для списка сообщений. Это очень полезно, когда почтовый ящик содержит большое количество сообщений и требует много времени для получения сводной информации о них. Пример кода ниже покажет вам, как использовать пагинацию для больших наборов сообщений при получении сообщений из Exchange Server, используя IGraphClient:

```java
// отправить тестовые сообщения
for (int i = 0; i < 5; i++) {
    MailMessage eml = new MailMessage(user.EMail, user.EMail, "ping" + i, "тестовое тело");
    client.send(MapiMessage.fromMailMessage(eml));
}
// ожидание входящих
Thread.sleep(10000);

// параметры пагинации
int itemsPerPage = 2;
// создать фильтр для непрочитанных сообщений
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.isRead().equals(false);
MailQuery query = builder.getQuery();

// список сообщений
GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(itemsPerPage), query);
GraphMessageInfoCollection messages = pageInfo.getItems();
while (!pageInfo.getLastPage())
{
    pageInfo = client.listMessages(GraphKnownFolders.Inbox, pageInfo.getNextPage(), query);
    // добавить элементы следующей страницы в общую коллекцию
    messages.addRange(pageInfo.getItems());
}

// установить состояние сообщений как прочитанные
for (GraphMessageInfo message : messages) {
    client.setRead(message.getItemId());
}
```

### **Создать сообщение**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Тема");
message.setBody("Тело");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "от");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Обновить сообщение**


~~~Java
fetchedMessage.setSubject("Обновить сообщение");
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
### **Копировать сообщение**


~~~Java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Переместить сообщение**


~~~Java
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Вложения сообщения**


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
## **API категорий**


~~~Java
String categoryName = "Тестовая категория";
int preset = CategoryPreset.Preset10;
OutlookCategory category = client.createCategory(categoryName, preset);
OutlookCategory fetchedCategory = client.fetchCategory(category.getId());

List<OutlookCategory> categories = client.listCategories();

fetchedCategory.setDisplayName("Обновить категорию");
fetchedCategory.setPreset(CategoryPreset.Preset11);
OutlookCategory updatedCategory = client.updateCategory(fetchedCategory);

client.delete(category.getId());
~~~
## **API переопределений**


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
## **API правил**


~~~Java
InboxRule rule = new InboxRule();
rule.setDisplayName("Тестовое правило");
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

createdRule.setDisplayName("Тестовое правило 1");
createdRule.setEnabled(false);
InboxRule updatedRule = client.updateRule(createdRule);

client.delete(createdRule.getRuleId());
~~~
## **Использование ресурса для поддержки нескольких почтовых ящиков**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// вернуться к текущему почтовому ящику
сlient.setResource(ResourceType.Me);
~~~