---
title: "Como usar GraphClient para Microsoft Graph"
url: /pt/net/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabalhando com GraphClient**

[Microsoft Graph](https://learn.microsoft.com/pt-br/graph/overview) é uma API REST para acessar os dados do Microsoft 365. A implementação do Graph Client no Aspose.Email para .NET permite acessar o Microsoft Graph a partir da nossa API. 
Nos exemplos abaixo, vamos criar uma instância do MS Graph Client, fornecendo o token para ele. Em seguida, examinaremos os principais métodos para gerenciar pastas, atualizá-las, copiá-las e excluí-las. Mensagens, seus conteúdos e anexos também podem ser acessados ou alterados com nosso MS Graph Client. Gerenciar categorias, regras, cadernos e substituições é uma funcionalidade ampliada do Microsoft Graph Client pelo Aspose.Email, que você aprenderá com facilidade.

### **Criar Objeto GraphClient**

Crie um objeto [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) para fazer solicitações contra o serviço.
Depois de ter um [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) que está autenticado, você pode começar a fazer chamadas ao serviço.

Um método [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) requer uma instância de implementação de [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) como o primeiro parâmetro.

Para obter o token, usaremos a [Microsoft Authentication Library (MSAL) para .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

As etapas a seguir descrevem como obter o token de autorização.

 - Crie uma classe AccessParameters para armazenar credenciais.
 - Adicione o [pacote nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contém os binários do MSAL.NET.
 - Implemente um [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/), e crie um método que aceite parâmetros de acesso e utilize o MSAL.NET para obter um token de acesso.

Para manter as credenciais, adicione a seguinte classe `AccessParameters`:

```csharp
public class AccessParameters
{
    public string TenantId { get; init; }
    public string ClientId { get; init; }
    public string ClientSecret { get; init; }
    public string UserId { get; init; }
    public Uri Authority => new ($"https://login.microsoftonline.com/{TenantId}");
    public string ApiUrl => "https://graph.microsoft.com/.default";
}
```

Crie a classe `GraphTokenProvider` que implementa a interface [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/). Utilize a biblioteca [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) para obter um token. Veja um exemplo de tal implementação:

```csharp
using Microsoft.Identity.Client;
using Microsoft.Identity.Web;
using Aspose.Email.Clients;

public class GraphTokenProvider : ITokenProvider
{
    private readonly IConfidentialClientApplication _app;
    private readonly string[] _scopes;
    private string? _token;

    public GraphTokenProvider(AccessParameters accessParams)
    {
        _app = ConfidentialClientApplicationBuilder.Create(accessParams.ClientId)
            .WithClientSecret(accessParams.ClientSecret)
            .WithAuthority(accessParams.Authority)
            .Build();

        _app.AddInMemoryTokenCache();

        _scopes = new[] { accessParams.ApiUrl };
    }

    public void Dispose()
    {
        throw new NotImplementedException();
    }

    public OAuthToken GetAccessToken()
    {
        return GetAccessToken(false);
    }

    public OAuthToken GetAccessToken(bool ignoreExistingToken)
    {
        if (!ignoreExistingToken && _token != null)
        {
            return new OAuthToken(_token);
        }

        _token = GetAccessTokenAsync().GetAwaiter().GetResult();
        return new OAuthToken(_token);
    }

    private async Task<string?> GetAccessTokenAsync()
    {
        AuthenticationResult? result;

        try
        {
            result = await _app.AcquireTokenForClient(_scopes)
                .ExecuteAsync();

            Console.WriteLine("Token adquirido");
        }
        catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
        {
            Console.WriteLine("Scope fornecido não é suportado");
            result = null;
        }

        if (result == null) return null;
        _token = result.AccessToken;
        return result.AccessToken;
    }
```

Em seguida, crie uma instância da classe `AccessParameters`:

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Seu ID do Tenant",
    ClientId = "Seu ID do Cliente",
    ClientSecret = "Seu Segredo do Cliente",
    UserId = "ID do Objeto do Usuário"
};
```

Por fim, crie uma instância de [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) e chame um método [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1). Passe o `tokenProvider` como seu primeiro parâmetro e `accessParams.TenantId` como o segundo:

```csharp
var tokenProvider = new GraphTokenProvider(accessParams);

using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

## **Gerenciar Pastas**

### **Listar Pastas**

Ao chamar o método [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) do MS Graph Client, é possível obter a lista de pastas. Cada pasta possui um conjunto de parâmetros como DisplayName, que podem ser lidos no tipo [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/).

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Atualizar Pasta**

Para criar uma pasta com o MS Graph Client, utilize o método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder). Você receberá um objeto [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) e a possibilidade de acessar DisplayName, ItemId, HasSubFolders e outras propriedades.

```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

### **Copiar Pasta**

O método [CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) é o método-chave para copiar o objeto da pasta com o MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// copiar Folder2 para Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Mover e Excluir Pasta**

Use o método [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) para mover a pasta, ele aceita newParentId e itemId. O método [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) é usado para excluir um método por id.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// mover Folder2 para Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
    
// excluir Folder1
client.Delete(folderInfo1.ItemId)
```

## **Gerenciar Mensagens**

O MS Graph Client, implementado no Aspose.Email para .NET, fornece um conjunto de métodos para gerenciar mensagens e anexos:
* [List](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages) mensagens
* [Fetch](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchmessage/#fetchmessage) mensagem
* [Create](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage) mensagem
* [Send](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send) mensagem
* [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copymessage/#copymessage) mensagem
* [Move](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movemessage/#movemessage) mensagem
* [CreateAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createattachment/#createattachment)
* [FetchAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchattachment/#fetchattachment)
* [DeleteAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deleteattachment/#deleteattachment)
* [ListAttachments](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listattachments/#listattachments)


### **Listar Mensagens**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Inbox"))
    {
        // listar mensagens na caixa de entrada
        var inboxMessages = client.ListMessages(folder.ItemId);

        foreach (var messageInfo in inboxMessages)
        {
            Console.WriteLine(messageInfo.Subject);
        }
    }
}
```

### **Listando Mensagens por Data de Envio**

O método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) da coleção da biblioteca permite que você recupere mensagens com diferentes ordens de classificação (ascendente e descendente) com base na data em que foram enviadas. O seguinte exemplo de código mostra como ordenar mensagens pela data de envio:

```cs
IGraphClient client = GraphClient.GetClient(provider, TenantId);

var builder = new GraphQueryBuilder();

// criar consulta para ordenar mensagens 'DESC'
builder.SentDate.OrderBy(false);
var messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
var messages = messagePageInfo.Items;

builder.Clear();

// criar consulta para ordenar mensagens 'ASC'
builder.SentDate.OrderBy(true);
messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
messages = messagePageInfo.Items;
```

### **Enumerando Mensagens com Suporte a Paginação usando o Graph Client** 

A API permite paginação e filtragem das mensagens ao listá-las. Isso é especialmente útil para caixas de entrada com um grande volume de mensagens, pois economiza tempo ao recuperar apenas as informações resumidas necessárias.

O exemplo de código e as etapas abaixo demonstram como recuperar mensagens da pasta Inbox usando recursos de paginação e filtragem. 

1. Primeiro, inicie o cliente.
2. Em seguida, defina o número de itens a serem exibidos por página, por exemplo, 10.
3. Crie um filtro para recuperar apenas mensagens não lidas usando a classe [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class). O builder.IsRead.Equals(false) está definindo a condição para filtrar mensagens não lidas.
4. Chame o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) no objeto cliente, especificando a pasta (Inbox) e os itens por página (PageInfo(itemsPerPage)) como parâmetros. Ele também passa o objeto de consulta para aplicar o filtro de mensagens não lidas.
O objeto PageInfo retornado (pageInfo) contém as mensagens recuperadas para a página atual na propriedade Items.
5. Crie um loop que continua até a última página ser atingida (pageInfo.LastPage é falso). As mensagens recuperadas são adicionadas à lista de mensagens existente usando messages.AddRange(pageInfo.Items).

```cs
// lendo mensagens não lidas com paginação
using var client = GraphClient.GetClient(tokenProvider, config.Tenant);

// opção de paginação
var itemsPerPage = 10;
// criar filtro de mensagens não lidas
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.IsRead.Equals(false);
var query = builder.GetQuery();

// listar mensagens
var pageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(itemsPerPage), query);
var  messages = pageInfo.Items;

while (!pageInfo.LastPage)
{
    pageInfo = client.ListMessages(KnownFolders.Inbox, pageInfo.NextPage, query);
    messages.AddRange(pageInfo.Items);
}

// definir o estado das mensagens como lidas
foreach (var message in messages)
{
    client.SetRead(message.ItemId);
}

```

### **Buscar Mensagem**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Inbox"))
    {
        // listar mensagens na caixa de entrada
        var inboxMessages = client.ListMessages(folder.ItemId);

        if (inboxMessages.Count > 0)
        {
            // buscar a primeira mensagem na caixa de entrada
            var msg = client.FetchMessage(inboxMessages[0].ItemId);
            
            Console.WriteLine(msg.BodyHtml);
        }
        
    }
}
```

### **Criar Mensagem**

```csharp
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Minha mensagem",
    Body = "Oi, esta é minha mensagem"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);

// criar mensagem na caixa de entrada
client.CreateMessage(KnownFolders.Inbox, msg);

```
### **Enviar Mensagem**

```csharp
// preparar a mensagem
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Minha mensagem",
    Body = "Oi, esta é minha mensagem"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// enviar mensagem
client.Send(msg);
```
### **Enviar Mensagem em Rascunho**

```csharp
// preparar a mensagem
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Minha mensagem",
    Body = "Oi, esta é minha mensagem"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// adicionar mensagem à pasta de Rascunhos
var draftMessage = client.CreateMessage(KnownFolders.Drafts, msg);

// enviar uma mensagem de rascunho
client.Send(draftMessage.ItemId);
```

### **Enviar uma Mensagem EML**

Criar e enviar e-mails é fácil usando o objeto MailMessage. O seguinte exemplo de código demonstra como criar e enviar uma mensagem de e-mail usando a API Graph:

```cs
// preparar a mensagem
var eml = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Nova mensagem",
    HtmlBody = "<html><body>Este é o corpo HTML</body></html>"
};

// enviar a mensagem
graphClient.Send(eml);
graphClient.Create(KnownFolders.Inbox, eml);
```


### **Copiar Mensagem**

```csharp

// copiar mensagem para a pasta da Caixa de Entrada
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Mover Mensagem**

```csharp
// mover mensagem para a pasta da Caixa de Entrada
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Gerenciar Anexos**

```csharp

// criar um anexo
var attachment = new MapiAttachment();
attachment.SetProperty(KnownPropertyList.DisplayName, "Meu Anexo");
attachment.SetProperty(KnownPropertyList.AttachDataBinary, new byte[1024]);

// adicionar um anexo à mensagem
var createdAttachment = client.CreateAttachment(messageInfo.ItemId, attachment);

// buscar um anexo da mensagem
var fetchedAttachment = client.FetchAttachment(createdAttachment.ItemId);

// excluir um anexo da mensagem 
client.DeleteAttachment(createdAttachment.ItemId);

// listar os anexos da mensagem
var attachments = client.ListAttachments(messageInfo.ItemId);   
```
## **Gerenciar Eventos de Calendário**

Aspose.Email oferece APIs para acessar, gerenciar e interagir com eventos de calendário. Para esses fins, ele oferece os seguintes métodos na interface [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListCalendars()** - Recupera uma coleção de informações de calendário.

- **ListCalendarItems(string id)** - Recupera uma coleção de itens de calendário associados ao ID de calendário especificado.

- **FetchCalendarItem(string id)** - Recupera um item de calendário específico com base no ID fornecido.

- **CreateCalendarItem(string calId, MapiCalendar mapiCalendar)** - Cria um novo item de calendário no calendário especificado.

- **UpdateCalendarItem(MapiCalendar mapiCalendar)** - Atualiza um item de calendário existente.

- **UpdateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)** - Atualiza um item de calendário existente com as configurações de atualização especificadas.

O seguinte exemplo de código demonstra como interagir com eventos de calendário em um cliente da API Microsoft Graph usando os métodos fornecidos pelo Aspose.Email:

```cs

// Listar Calendários
CalendarInfoCollection calendars = graphClient.ListCalendars();

// Listar Itens do Calendário
MapiCalendarCollection calendarItems = graphClient.ListCalendarItems("calendarId");

// Buscar Item de Calendário
MapiCalendar calendarItem = graphClient.FetchCalendarItem("calendarItemId");

// Criar Item de Calendário
MapiCalendar newCalendarItem = new MapiCalendar(
    location: "Sala de Conferência",
    summary: "Reunião da Equipe",
    description: "Discutir o status do projeto e atualizações.",
    startDate: startDate,
    endDate: endDate
);

MapiCalendar createdCalendarItem = graphClient.CreateCalendarItem("calendarId", newCalendarItem);

// Atualizar Item de Calendário
createdCalendarItem.Location = "Reunião no Zoom";
MapiCalendar updatedCalendarItem = graphClient.UpdateCalendarItem(createdCalendarItem);
```

## **Gerenciar Categorias**
Para gerenciar categorias com o MS Graph pelo Aspose.Email para .NET, use os seguintes métodos:
* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createcategory/#createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchcategory/#fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listcategories/#listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatecategory/#updatecategory)

```csharp
// criar uma categoria personalizada com cor laranja
var category = client.CreateCategory("Minha categoria personalizada", CategoryPreset.Preset1);

// buscar uma categoria
var fetchedCategory = client.FetchCategory(category.Id);

// atualizar categoria (alterar cor para marrom)
fetchedCategory.Preset = CategoryPreset.Preset2;
var updatedCategory = client.UpdateCategory(fetchedCategory);

// listar categorias disponíveis
var categories = client.ListCategories();

foreach (var cat in categories)
{
    Console.WriteLine(cat.DisplayName);
}

// excluir uma categoria
client.Delete(fetchedCategory.Id);
```
## **Gerenciar Contatos**

Aspose.Email fornece APIs para acessar, gerenciar e interagir com itens de contato. Para esses fins, ele oferece os seguintes métodos na interface [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListContacts(string id)** - Recupera uma coleção de contatos MAPI associados ao ID da pasta especificada.

- **FetchContact(string id)** - Recupera um contato específico com base no ID do item fornecido.

- **CreateContact(string folderId, MapiContact contact)** - Cria um novo contato na pasta especificada.

- **UpdateContact(MapiContact contact)** - Atualiza um contato existente.

O seguinte exemplo de código demonstra como interagir com contatos em um cliente da API Microsoft Graph usando os métodos fornecidos pelo Aspose.Email:

```cs
// Listar Contatos
MapiContactCollection contacts = graphClient.ListContacts("contactFolderId");

// Buscar Contato
MapiContact contact = graphClient.FetchContact("contactId");

// Criar Contato
MapiContact newContact = new MapiContact("Jane Smith", "jane.smith@example.com", "XYZ Corporation", "777-888-999");

MapiContact createdContact = graphClient.CreateContact("contactFolderId", newContact);

// Atualizar Contato
createdContact.Telephones.PrimaryTelephoneNumber = "888-888-999";

MapiContact updatedContact = graphClient.UpdateContact(createdContact);
```

## **Gerenciar Substituições**

Para gerenciar substituições com o MS Graph pelo Aspose.Email para .NET, use os seguintes métodos:
* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createorupdateoverride/#createorupdateoverride) 
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listoverrides/#listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updateoverride/#updateoverride)

```csharp
// Criar uma substituição de usuário
var userOverride = client.CreateOrUpdateOverride
    (new MailAddress("JohnBrown@someorg.com", "JohnBrown"), ClassificationType.Focused);

// listar as substituições
var overrides = client.ListOverrides();

// atualizar substituição
userOverride.Sender.DisplayName = "John Brown";
var updatedOverride = client.UpdateOverride(userOverride);

// excluir substituição
client.Delete(updatedOverride.Id);
```
## **Gerenciar Regras**
Para gerenciar regras com o MS Graph pelo Aspose.Email para .NET, use os seguintes métodos:
* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createrule/#createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchrule/#fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updaterule/#updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listrules/#listrules)

```csharp
// Criar uma regra
var rule = PrepareRule("user@someorg.com", "User");
var createdRule = client.CreateRule(rule);

// Listar todas as regras definidas para a Caixa de Entrada
var rules = client.ListRules();

// Buscar uma regra
var fetchedRule = client.FetchRule(createdRule.RuleId);

// Atualizar uma regra
fetchedRule.DisplayName = "Regra Renomeada";
fetchedRule.IsEnabled = false;
var updatedRule = client.UpdateRule(createdRule);

// Excluir uma regra
client.Delete(updatedRule.RuleId);
```

```csharp
InboxRule PrepareRule(string email, string displayName)
{
    var rule = new InboxRule()
    {
        DisplayName = "Minha regra",
        Priority = 1,
        IsEnabled = true,
        Conditions = new RulePredicates(),
        Actions = new RuleActions()
    };

    rule.Conditions.ContainsSenderStrings = new StringCollection { displayName };
    rule.Actions.ForwardToRecipients = new MailAddressCollection
        { new MailAddress(email, displayName, true) };
    rule.Actions.StopProcessingRules = true;

    return rule;
}
```

## **Gerenciar Cadernos**

Para gerenciar cadernos com o MS Graph pelo Aspose.Email para .NET, use os seguintes métodos:
* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createnotebook/#createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copynotebook/#copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchnotebook/#fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listnotebooks/#listnotebooks)

```csharp
// criar um caderno OneNote
var newNotebook = new Notebook()
{
    DisplayName = "Meu Caderno"
};
var createdNotebook = client.CreateNotebook(newNotebook);

// buscar um caderno
var fetchedNotebook = client.FetchNotebook(createdNotebook.Id);

// listar os cadernos
var notebooks = client.ListNotebooks();
```