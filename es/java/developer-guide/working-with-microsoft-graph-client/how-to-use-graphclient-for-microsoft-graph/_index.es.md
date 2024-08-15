---
title: "Cómo usar GraphClient para Microsoft Graph"
url: /es/java/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabajando con GraphClient**
Una instancia del [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) La clase gestiona la creación de solicitudes, las envía a la API de Microsoft Graph y procesa las respuestas.
### **Crear un objeto ITokenProvider**
Para crear una nueva instancia de [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) clase, necesitas proporcionar una instancia de [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), que puede autenticar las solicitudes en Microsoft Graph.


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
### **Obtener un objeto GraphClient**
Después de configurar el TokenProvider, debe obtener un [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) oponerse a realizar solicitudes contra el servicio.
Después de tener un [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) si está autenticado, puede empezar a hacer llamadas contra el servicio.


~~~Java
IGraphClient client = GraphClient.getClient(tokenProvider);
~~~
## **Trabaje con carpetas mediante Microsoft Graph**

### **Listar carpetas**

~~~Java
GraphFolderInfoCollection folders = client.listFolders();
for (GraphFolderInfo folderInfo : folders) {
    System.out.println(folderInfo.getDisplayName());
    for (KeyValuePair<Long, MapiProperty> prop : folderInfo.getProperties()) {
        System.out.println(prop.getValue().getDescriptor().toString() + " " + prop.getValue().getString());
    }
}
~~~
### **Listar subcarpetas de la carpeta Bandeja de entrada**


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~
### **Crear carpeta raíz**


~~~Java
GraphFolderInfo newFolder = client.createFolder("TEST_FOLDER");
~~~
### **Crear subcarpeta**


~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "TEST_SUBFOLDER_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "TEST_SUBFOLDER_2");
~~~
### **Obtener carpeta**


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~
### **Carpeta de actualización**


~~~Java
GraphFolderInfo originalFolder = client.createFolder("TEST_FOLDER");
originalFolder.setDisplayName("NEW_TEST_FOLDER");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~
### **Copiar carpeta y contenido**


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
### **Mover la carpeta y el contenido**


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~
### **Eliminar carpeta**


~~~Java
client.delete(testFolder.getItemId());
~~~
## **Listar mensajes con Microsoft Graph**

~~~Java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
~~~

### **Listar mensajes por fecha de envío**

The [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) La función se usa para indicar que los mensajes deben ordenarse en orden ascendente según la fecha de envío. Esto permite al cliente recuperar la lista de mensajes del [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) carpeta en un orden específico, en este caso, según la fecha de envío.

El siguiente ejemplo de código muestra cómo crear una consulta que especifique el orden de los mensajes por fecha de envío y, a continuación, usar esta consulta para obtener una página de mensajes de la carpeta Bandeja de entrada mediante la API Graph:

```java
// create orderby messages query 'ASC'
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.getSentDate().orderBy(true);
MailQuery query = builder.getQuery();

GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(10), query);
```

### **Recuperar mensaje**


~~~Java
GraphMessageInfo messageInfo = messageInfoColl.get(0);
MapiMessage fetchedMessage = client.fetchMessage(messageInfo.getItemId());
~~~

### **Paginación en la lista de mensajes**

La API proporciona soporte de paginación y filtrado para los mensajes de listado. Esto resulta muy útil cuando un buzón tiene un gran número de mensajes y se necesita mucho tiempo para recuperar la información resumida sobre ellos. En el ejemplo de código que aparece a continuación se muestra cómo usar la paginación para conjuntos de mensajes de gran tamaño al enumerar los mensajes de Exchange Server con iGraphClient:

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

### **Crear mensaje**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Subject");
message.setBody("Body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Mensaje de actualización**


~~~Java
fetchedMessage.setSubject("Update message");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
~~~
### **Enviar mensaje**


~~~Java
client.send(message);
~~~
### **Enviar borrador de mensaje**


~~~Java
MapiMessage draftMessage = client.createMessage(GraphKnownFolders.Drafts, message);
client.send(draftMessage.getItemId());
~~~
### **Copiar mensaje**


~~~Java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Mover mensaje**


~~~Java
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Adjuntos de mensajes**


~~~Java
MapiAttachmentCollection attachments = client.listAttachments(fetchedMessage.getItemId());
for (MapiAttachment att : attachments) {
    client.deleteAttachment(att.getItemId());
}
~~~
### **Eliminar mensaje**


~~~Java
client.delete(message.getItemId());
~~~
## **Categorías Api**


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
## **Anula la API**


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
## **API de reglas**


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
## **Uso de recursos para admitir varios buzones**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// back to the current mailbox
сlient.setResource(ResourceType.Me);
~~~