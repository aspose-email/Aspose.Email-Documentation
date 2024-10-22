---
title: "Cómo usar GraphClient para Microsoft Graph"
url: /es/java/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabajando con GraphClient**
Una instancia de la clase [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) se encarga de construir solicitudes, enviarlas a la API de Microsoft Graph y procesar las respuestas.
### **Crear un objeto ITokenProvider**
Para crear una nueva instancia de la clase [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient), necesitas proporcionar una instancia de [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), que puede autenticar solicitudes a Microsoft Graph.


~~~Java
ITokenProvider tokenProvider = new ITokenProvider() {
    Date expirationDate = null;

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        // Obtiene el token de acceso oAuth.
        // Si ignoreExistingToken es verdadero, solicita un nuevo token desde el servidor. De lo contrario, el comportamiento depende de si el token existe o no.
        // Si el token existe y su fecha de expiración no ha caducado, devuelve el token actual; de lo contrario, solicita un nuevo token desde el servidor.
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        // Obtiene el token de acceso oAuth.
        // Si el token existe y su fecha de expiración no ha caducado, devuelve el token actual; de lo contrario, solicita un nuevo token desde el servidor.
        return new OAuthToken("token", expirationDate);
    }
};
~~~
### **Obtener un objeto GraphClient**
Después de haber configurado el TokenProvider, debes obtener un objeto [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) para hacer solicitudes al servicio.
Después de tener un [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) que esté autenticado, puedes comenzar a hacer llamadas al servicio.


~~~Java
IGraphClient client = GraphClient.getClient(tokenProvider);
~~~
## **Trabajar con carpetas usando Microsoft Graph**

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
### **Listar subcarpetas de la carpeta de entrada**


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
### **Actualizar carpeta**


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
### **Mover carpeta y contenido**


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~
### **Eliminar carpeta**


~~~Java
client.delete(testFolder.getItemId());
~~~
## **Listar mensajes usando Microsoft Graph**

~~~Java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
~~~

### **Listar mensajes por fecha de envío**

La función [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) se usa para indicar que los mensajes deben ordenarse en orden ascendente por su fecha de envío. Esto permite al cliente recuperar la lista de mensajes de la carpeta [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) en un orden específico, en este caso, basado en la fecha de envío.

El siguiente ejemplo de código muestra cómo crear una consulta que especifica el orden de los mensajes por fecha de envío, y luego usar esta consulta para recuperar una página de mensajes de la carpeta de entrada usando la API de Graph:

```java
// crear consulta de mensajes ordenada 'ASC'
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

La API proporciona soporte de paginación y filtrado para listar mensajes. Esto es muy útil cuando un buzón tiene un gran número de mensajes y requiere mucho tiempo para recuperar la información resumida sobre ellos. El siguiente ejemplo de código te mostrará cómo usar la paginación para conjuntos de mensajes grandes al listar mensajes desde Exchange Server usando IGraphClient:

```java
// enviar mensajes de prueba de ping
for (int i = 0; i < 5; i++) {
    MailMessage eml = new MailMessage(user.EMail, user.EMail, "ping" + i, "cuerpo de prueba");
    client.send(MapiMessage.fromMailMessage(eml));
}
// esperando por la bandeja de entrada
Thread.sleep(10000);

// opción de paginación
int itemsPerPage = 2;
// crear filtro de mensajes no leídos
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.isRead().equals(false);
MailQuery query = builder.getQuery();

// listar mensajes
GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(itemsPerPage), query);
GraphMessageInfoCollection messages = pageInfo.getItems();
while (!pageInfo.getLastPage())
{
    pageInfo = client.listMessages(GraphKnownFolders.Inbox, pageInfo.getNextPage(), query);
    // agregar elementos de la siguiente página a la colección común
    messages.addRange(pageInfo.getItems());
}

// establecer el estado de los mensajes como leídos
for (GraphMessageInfo message : messages) {
    client.setRead(message.getItemId());
}
```

### **Crear mensaje**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Asunto");
message.setBody("Cuerpo");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Actualizar mensaje**


~~~Java
fetchedMessage.setSubject("Actualizar mensaje");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
~~~
### **Enviar mensaje**


~~~Java
client.send(message);
~~~
### **Enviar mensaje borrador**


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
### **Adjuntos de mensaje**


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
## **API de categorías**


~~~Java
String categoryName = "Categoría de prueba";
int preset = CategoryPreset.Preset10;
OutlookCategory category = client.createCategory(categoryName, preset);
OutlookCategory fetchedCategory = client.fetchCategory(category.getId());

List<OutlookCategory> categories = client.listCategories();

fetchedCategory.setDisplayName("Actualizar categoría");
fetchedCategory.setPreset(CategoryPreset.Preset11);
OutlookCategory updatedCategory = client.updateCategory(fetchedCategory);

client.delete(category.getId());
~~~
## **API de sobrescrituras**


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
rule.setDisplayName("Regla de prueba");
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

createdRule.setDisplayName("Regla de prueba 1");
createdRule.setEnabled(false);
InboxRule updatedRule = client.updateRule(createdRule);

client.delete(createdRule.getRuleId());
~~~
## **Usando recurso para soportar múltiples buzones**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// volver al buzón actual
сlient.setResource(ResourceType.Me);
~~~