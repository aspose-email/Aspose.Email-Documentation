---
title: "Como usar GraphClient para Microsoft Graph"
url: /pt/java/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabalhando com GraphClient**
Uma instância da classe [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) gerencia a construção de solicitações, o envio delas para a API do Microsoft Graph e o processamento das respostas.
### **Criar um Objeto ITokenProvider**
Para criar uma nova instância da classe [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient), você precisa fornecer uma instância de [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), que pode autenticar solicitações ao Microsoft Graph.


~~~Java
ITokenProvider tokenProvider = new ITokenProvider() {
    Date expirationDate = null;

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        // Obtém o token de acesso oAuth.
        // Se ignoreExistingToken for verdadeiro, solicita um novo token a partir de um servidor. Caso contrário, o comportamento depende de o token existir ou não.
        // Se o token existir e sua data de expiração não estiver expirada, retorna o token atual, caso contrário, solicita um novo token a partir de um servidor.
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        // Obtém o token de acesso oAuth.
        // Se o token existir e sua data de expiração não estiver expirada, retorna o token atual, caso contrário, solicita um novo token a partir de um servidor.
        return new OAuthToken("token", expirationDate);
    }
};
~~~
### **Obter um objeto GraphClient**
Após definir o TokenProvider, você deve obter um objeto [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) para fazer solicitações contra o serviço.
Depois de ter um [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) autenticado, você pode começar a fazer chamadas contra o serviço.


~~~Java
IGraphClient client = GraphClient.getClient(tokenProvider);
~~~
## **Trabalhar com Pastas usando Microsoft Graph**

### **Listar Pastas**

~~~Java
GraphFolderInfoCollection folders = client.listFolders();
for (GraphFolderInfo folderInfo : folders) {
    System.out.println(folderInfo.getDisplayName());
    for (KeyValuePair<Long, MapiProperty> prop : folderInfo.getProperties()) {
        System.out.println(prop.getValue().getDescriptor().toString() + " " + prop.getValue().getString());
    }
}
~~~
### **Listar Subpastas da Pasta de Entrada**


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~
### **Criar Pasta Raiz**


~~~Java
GraphFolderInfo newFolder = client.createFolder("TEST_FOLDER");
~~~
### **Criar Subpasta**


~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "TEST_SUBFOLDER_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "TEST_SUBFOLDER_2");
~~~
### **Obter Pasta**


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~
### **Atualizar Pasta**


~~~Java
GraphFolderInfo originalFolder = client.createFolder("TEST_FOLDER");
originalFolder.setDisplayName("NEW_TEST_FOLDER");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~
### **Copiar Pasta e Conteúdo**


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
### **Mover Pasta e Conteúdo**


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~
### **Deletar Pasta**


~~~Java
client.delete(testFolder.getItemId());
~~~
## **Listar Mensagens usando Microsoft Graph**

~~~Java
GraphMessageInfoCollection messageInfoColl = client.listMessages(GraphKnownFolders.Inbox);
for (GraphMessageInfo messageInfo : messageInfoColl) {
    MapiMessage message = client.fetchMessage(messageInfo.getItemId());
}
~~~

### **Listar Mensagens por Data de Envio**

O recurso [OrderBy](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) é utilizado para indicar que as mensagens devem ser ordenadas em ordem crescente pela data de envio. Isso permite ao cliente recuperar a lista de mensagens da pasta [GraphKnownFolders.Inbox](https://reference.aspose.com/email/java/com.aspose.email/graphknownfolders/#Inbox) em uma ordem específica, neste caso, com base na data de envio.

O seguinte exemplo de código demonstra como criar uma consulta que especifica a ordenação das mensagens pela data de envio e, em seguida, usar essa consulta para buscar uma página de mensagens da pasta de Entrada usando a API Graph:

```java
// criar consulta orderby mensagens 'ASC'
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.getSentDate().orderBy(true);
MailQuery query = builder.getQuery();

GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(10), query);
```

### **Buscar Mensagem**


~~~Java
GraphMessageInfo messageInfo = messageInfoColl.get(0);
MapiMessage fetchedMessage = client.fetchMessage(messageInfo.getItemId());
~~~

### **Paginação na Listagem de Mensagens**

A API fornece suporte para paginação e filtragem na listagem de mensagens. Isso é muito útil quando uma caixa de entrada possui um grande número de mensagens e requer muito tempo para recuperar as informações resumidas sobre elas. O exemplo de código abaixo mostrará como usar a paginação para grandes conjuntos de mensagens ao listar mensagens do Exchange Server usando IGraphClient:

```java
// enviar mensagens de teste de ping
for (int i = 0; i < 5; i++) {
    MailMessage eml = new MailMessage(user.EMail, user.EMail, "ping" + i, "corpo do teste");
    client.send(MapiMessage.fromMailMessage(eml));
}
// esperando pela caixa de entrada
Thread.sleep(10000);

// opção de paginação
int itemsPerPage = 2;
// criar filtro para mensagens não lidas
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.isRead().equals(false);
MailQuery query = builder.getQuery();

// listar mensagens
GraphMessagePageInfo pageInfo = client.listMessages(GraphKnownFolders.Inbox, new PageInfo(itemsPerPage), query);
GraphMessageInfoCollection messages = pageInfo.getItems();
while (!pageInfo.getLastPage())
{
    pageInfo = client.listMessages(GraphKnownFolders.Inbox, pageInfo.getNextPage(), query);
    // adicionar itens da próxima página à coleção comum
    messages.addRange(pageInfo.getItems());
}

// definir estado das mensagens como lidas
for (GraphMessageInfo message : messages) {
    client.setRead(message.getItemId());
}
```

### **Criar Mensagem**


~~~Java
MapiMessage message = new MapiMessage();
message.setSubject("Assunto");
message.setBody("Corpo");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "de");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");

MapiMessage createdMessage = client.createMessage(GraphKnownFolders.Inbox, message);
~~~
### **Atualizar Mensagem**


~~~Java
fetchedMessage.setSubject("Atualizar mensagem");
MapiMessage updatedMessage = client.updateMessage(fetchedMessage);
~~~
### **Enviar Mensagem**


~~~Java
client.send(message);
~~~
### **Enviar Mensagem de Rascunho**


~~~Java
MapiMessage draftMessage = client.createMessage(GraphKnownFolders.Drafts, message);
client.send(draftMessage.getItemId());
~~~
### **Copiar Mensagem**


~~~Java
MapiMessage copiedMessage = client.copyMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Mover Mensagem**


~~~Java
MapiMessage movedMessage = client.moveMessage(GraphKnownFolders.Inbox, draftMessage.getItemId());
~~~
### **Anexos de Mensagem**


~~~Java
MapiAttachmentCollection attachments = client.listAttachments(fetchedMessage.getItemId());
for (MapiAttachment att : attachments) {
    client.deleteAttachment(att.getItemId());
}
~~~
### **Deletar Mensagem**


~~~Java
client.delete(message.getItemId());
~~~
## **API de Categorias**


~~~Java
String categoryName = "Categoria Teste";
int preset = CategoryPreset.Preset10;
OutlookCategory category = client.createCategory(categoryName, preset);
OutlookCategory fetchedCategory = client.fetchCategory(category.getId());

List<OutlookCategory> categories = client.listCategories();

fetchedCategory.setDisplayName("Atualizar Categoria");
fetchedCategory.setPreset(CategoryPreset.Preset11);
OutlookCategory updatedCategory = client.updateCategory(fetchedCategory);

client.delete(category.getId());
~~~
## **API de Sobrescritas**


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
## **API de Regras**


~~~Java
InboxRule rule = new InboxRule();
rule.setDisplayName("Regra de Teste");
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

createdRule.setDisplayName("Regra de Teste 1");
createdRule.setEnabled(false);
InboxRule updatedRule = client.updateRule(createdRule);

client.delete(createdRule.getRuleId());
~~~
## **Usando Recurso para Suportar Várias Caixas de Correio**


~~~Java
сlient.setResource(ResourceType.Users);
сlient.setResourceId("mailbox");
сlient.listMessages("mailfolder")
// voltar para a caixa de correio atual
сlient.setResource(ResourceType.Me);
~~~