---
title: "Cómo usar GraphClient para Microsoft Graph"
url: /es/net/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabajando con GraphClient**

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) es una API REST para acceder a los datos de Microsoft 365. La implementación de Graph Client en Aspose.Email para .NET, permite acceder a Microsoft Graph desde nuestra API.
En los siguientes ejemplos, crearemos una instancia de MS Graph Client y le proporcionaremos el token. A continuación, examinaremos los principales métodos para gestionar las carpetas, actualizarlas, copiarlas y eliminarlas. También se puede acceder a los mensajes, su contenido y sus archivos adjuntos o modificarlos con nuestro cliente MS Graph. La administración de categorías, reglas, libretas y anulaciones es una función ampliada de Microsoft Graph Client de Aspose.Email, que aprenderás con facilidad.

### **Crear objeto GraphClient**

Create [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) oponerse a realizar solicitudes contra el servicio.
Después de tener un [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) si está autenticado, puede empezar a hacer llamadas contra el servicio.

A [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) el método requiere un [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) instancia de implementación como primer parámetro.

Para obtener el token usaremos [Biblioteca de autenticación de Microsoft (MSAL) para.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

 - Cree una clase AccessParameters para almacenar las credenciales.
 - Añada el [Paquete nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los archivos binarios de MSAL.NET.
 - Implemente un [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/)y cree un método que acepte los parámetros de acceso y utilice MSAL.NET para obtener un token de acceso.

Para conservar las credenciales, añada lo siguiente `AccessParameters` class:

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

Crea el `GraphTokenProvider` clase que implementa un [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) interfaz. Usa el [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) biblioteca para obtener un token.
Vea el ejemplo de dicha implementación:

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

            Console.WriteLine("Token acquired");
        }
        catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
        {
            Console.WriteLine("Scope provided is not supported");
            result = null;
        }

        if (result == null) return null;
        _token = result.AccessToken;
        return result.AccessToken;
    }
```

A continuación, cree un `AccessParameters` instancia de clase:

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Your Tenant ID",
    ClientId = "Your Client ID",
    ClientSecret = "Your Client Secret",
    UserId = "User's Object ID"
};
```

Por último, crea un [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) instancia y llama a [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) método. Pase el `tokenProvider` como primer parámetro y `accessParams.TenantId` como el segundo:

```csharp
var tokenProvider = new GraphTokenProvider(accessParams);

using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

## **Administrar carpetas**

### **Listar carpetas**

Llamando [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) método de MS Graph Client, es posible obtener la lista de carpetas. Cada carpeta tiene un conjunto de parámetros como DisplayName, que se pueden leer en [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) type.

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Carpeta de actualización**

Para crear una carpeta con MS Graph Client, utilice [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder) método. Obtendrás un [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) objeto y la posibilidad de acceder a DisplayName, ItemID, HasSubfolders y otras propiedades.

```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

### **Copiar carpeta**

[CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) El método es el método clave para copiar el objeto de la carpeta con MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
   
// copy Folder2 to Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Mover y eliminar carpeta**

Use [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) el método se usa para mover la carpeta, acepta newParentID e ItemID. [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) el método se usa para eliminar un método por id.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
   
// move Folder2 to Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
   
// delete Folder1
client.Delete(folderInfo1.ItemId)
```

## **Administrar mensajes**

MS Graph Client, implementado en Aspose.Email para.NET, proporciona un conjunto de métodos para administrar los mensajes y los archivos adjuntos:
* [List](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages) messages
* [Fetch](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchmessage/#fetchmessage) message
* [Create](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage) message
* [Send](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send) message
* [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copymessage/#copymessage) message
* [Move](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movemessage/#movemessage) message
* [CreateAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createattachment/#createattachment)
* [FetchAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchattachment/#fetchattachment)
* [DeleteAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deleteattachment/#deleteattachment)
* [ListAttachments](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listattachments/#listattachments)


### **Listar mensajes**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Inbox"))
    {
        // list messages in inbox
        var inboxMessages = client.ListMessages(folder.ItemId);

        foreach (var messageInfo in inboxMessages)
        {
            Console.WriteLine(messageInfo.Subject);
        }
    }
}
```

### **Listar los mensajes por fecha de envío**

The [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) El método de la colección de la biblioteca le permite recuperar mensajes con diferentes órdenes de clasificación (ascendente y descendente) según la fecha en que se enviaron. El siguiente ejemplo de código muestra cómo ordenar los mensajes por fecha de envío:

```cs
IGraphClient client = GraphClient.GetClient(provider, TenantId);

var builder = new GraphQueryBuilder();

// create orderby messages query 'DESC'
builder.SentDate.OrderBy(false);
var messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
var messages = messagePageInfo.Items;

builder.Clear();

// create orderby messages query 'ASC'
builder.SentDate.OrderBy(true);
messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
messages = messagePageInfo.Items;
```

### **Enumeración de mensajes con soporte de paginación mediante Graph Client**

La API permite la paginación y el filtrado de los mensajes al enumerarlos. Es especialmente útil para los buzones con un gran volumen de mensajes, ya que ahorra tiempo al recuperar solo la información resumida necesaria.

El ejemplo de código y los pasos siguientes muestran cómo recuperar mensajes de la carpeta Bandeja de entrada mediante funciones de paginación y filtrado.

1. En primer lugar, inicie el cliente.
2. A continuación, defina el número de elementos que se mostrarán por página, por ejemplo, 10.
3. Cree un filtro para recuperar solo los mensajes no leídos mediante el [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class) clase. El builder.isRead.equals (false) establece la condición para filtrar los mensajes no leídos.
4. Llame al [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) método en el objeto cliente, especificando la carpeta (Bandeja de entrada) y los elementos por página (PageInfo (ItemsPerPage)) como parámetros. También pasa el objeto de consulta para aplicar el filtro de mensajes no leídos.
El objeto PageInfo (PageInfo) devuelto contiene los mensajes recuperados de la página actual en la propiedad Items.
5. Cree un bucle que continúe hasta llegar a la última página (pageInfo.lastPage es falso). Los mensajes recuperados se agregan a la lista de mensajes existente mediante Messages.addRange (PageInfo.items).


```cs
//  reading unread messages with paging
using var client = GraphClient.GetClient(tokenProvider, config.Tenant);

// paging option
var itemsPerPage = 10;
// create unread messages filter
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.IsRead.Equals(false);
var query = builder.GetQuery();

// list messages
var pageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(itemsPerPage), query);
var  messages = pageInfo.Items;

while (!pageInfo.LastPage)
{
    pageInfo = client.ListMessages(KnownFolders.Inbox, pageInfo.NextPage, query);
    messages.AddRange(pageInfo.Items);
}

// set messages state as read
foreach (var message in messages)
{
    client.SetRead(message.ItemId);
}

```

### **Recuperar mensaje**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Inbox"))
    {
        // list messages in inbox
        var inboxMessages = client.ListMessages(folder.ItemId);

        if (inboxMessages.Count > 0)
        {
            // fetch the first message in inbox
            var msg = client.FetchMessage(inboxMessages[0].ItemId);
           
            Console.WriteLine(msg.BodyHtml);
        }
       
    }
}
```

### **Crear mensaje**

```csharp
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "My message",
    Body = "Hi, it is my message"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);

// create message in inbox
client.CreateMessage(KnownFolders.Inbox, msg);

```
### **Enviar mensaje**

```csharp
// prepare the message
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "My message",
    Body = "Hi, it is my message"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// send message
client.Send(msg);
```
### **Enviar borrador de mensaje**

```csharp
// prepare the message
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "My message",
    Body = "Hi, it is my message"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// add message to Draft folder
var draftMessage = client.CreateMessage(KnownFolders.Drafts, msg);

// send a draft message
client.Send(draftMessage.ItemId);
```

### **Enviar un mensaje EML**

Crear y enviar correos electrónicos es fácil con el objeto MailMessage. El siguiente ejemplo de código muestra cómo crear y enviar un mensaje de correo electrónico mediante la API Graph:

```cs
// prepare the message
var eml = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "New message",
    HtmlBody = "<html><body>This is the HTML body</body></html>"
};

// send the message
graphClient.Send(eml);
graphClient.Create(KnownFolders.Inbox, eml);
```


### **Copiar mensaje**

```csharp

// copy message to Inbox folder
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Mover mensaje**

```csharp
// move message to Inbox folder
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Administrar archivos adjuntos**

```csharp

// create an attachment
var attachment = new MapiAttachment();
attachment.SetProperty(KnownPropertyList.DisplayName, "My Attachment");
attachment.SetProperty(KnownPropertyList.AttachDataBinary, new byte[1024]);

// add an attachment to message
var createdAttachment = client.CreateAttachment(messageInfo.ItemId, attachment);

// fetch a message attachment
var fetchedAttachment = client.FetchAttachment(createdAttachment.ItemId);

// delete a message attachment
client.DeleteAttachment(createdAttachment.ItemId);

// list the message attachments
var attachments = client.ListAttachments(messageInfo.ItemId);  
```
## **Administrar los eventos del calendario**

Aspose.Email proporciona API para acceder, administrar e interactuar con los eventos del calendario. Para estos fines, ofrece los siguientes métodos en el [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListCalendars()** - Recupera una colección de información del calendario.

- **ListCalendarItems (identificador de cadena)** - Recupera una colección de elementos del calendario asociados al ID de calendario especificado.

- **fetchCalendarItem (identificador de cadena)** - Recupera un elemento de calendario específico en función del ID proporcionado.

- **createCalendarItem (cadena calID, mapiCalendar mapiCalendar)** - Crea un nuevo elemento de calendario en el calendario especificado.

- **Actualizar elemento de calendario (MapiCalendar MapiCalendar)** - Actualiza un elemento de calendario existente.

- **Actualizar elemento de calendario (MapiCalendar, MapiCalendar, actualizar configuración, actualizar configuración)** - Actualiza un elemento del calendario existente con la configuración de actualización especificada.

El siguiente ejemplo de código muestra cómo interactuar con los eventos del calendario en un cliente de la API de Microsoft Graph mediante los métodos proporcionados por Aspose.Email:

```cs

// List Calendars
CalendarInfoCollection calendars = graphClient.ListCalendars();

// List Calendar Items
MapiCalendarCollection calendarItems = graphClient.ListCalendarItems("calendarId");

// Fetch Calendar Item
MapiCalendar calendarItem = graphClient.FetchCalendarItem("calendarItemId");

// Create Calendar Item
MapiCalendar newCalendarItem = new MapiCalendar(
    location: "Conference Room",
    summary: "Team Meeting",
    description: "Discuss project status and updates.",
    startDate: startDate,
    endDate: endDate
);

MapiCalendar createdCalendarItem = graphClient.CreateCalendarItem("calendarId", newCalendarItem);

// Update Calendar Item
createdCalendarItem.Location = "Zoom Meeting";
MapiCalendar updatedCalendarItem = graphClient.UpdateCalendarItem(createdCalendarItem);
```

## **Administrar categorías**
Para administrar categorías con MS Graph de Aspose.Email para.NET, utilice los siguientes métodos:
* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createcategory/#createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchcategory/#fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listcategories/#listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatecategory/#updatecategory)

```csharp
// create a custom category with Orange color
var category = client.CreateCategory("My custom category", CategoryPreset.Preset1);

// fetch a category
var fetchedCategory = client.FetchCategory(category.Id);

// update category (change color to brown)
fetchedCategory.Preset = CategoryPreset.Preset2;
var updatedCategory = client.UpdateCategory(fetchedCategory);

// list available categories
var categories = client.ListCategories();

foreach (var cat in categories)
{
    Console.WriteLine(cat.DisplayName);
}

// delete a category
client.Delete(fetchedCategory.Id);
```
## **Administrar contactos**

Aspose.Email proporciona API para acceder, administrar e interactuar con los elementos de contacto. Para estos fines, ofrece los siguientes métodos en el [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListContacts (identificador de cadena)** - Recupera una colección de contactos MAPI asociados al ID de carpeta especificado.

- **fetchContact (identificador de cadena)** - Recupera un contacto específico en función del identificador del artículo proporcionado.

- **CreateContact (string folderId, mapiContact contact)** - Crea un nuevo contacto en la carpeta especificada.

- **UpdateContact (contacto de MapiContact)** - Actualiza un contacto existente.

El siguiente ejemplo de código muestra cómo interactuar con los contactos en un cliente de la API de Microsoft Graph mediante los métodos proporcionados por Aspose.Email:

```cs
// List Contacts
MapiContactCollection contacts = graphClient.ListContacts("contactFolderId");

// Fetch Contact
MapiContact contact = graphClient.FetchContact("contactId");

// Create Contact
MapiContact newContact = new MapiContact("Jane Smith", "jane.smith@example.com", "XYZ Corporation", "777-888-999");

MapiContact createdContact = graphClient.CreateContact("contactFolderId", newContact);

// Update Contact
createdContact.Telephones.PrimaryTelephoneNumber = "888-888-999";

MapiContact updatedContact = graphClient.UpdateContact(createdContact);
```

## **Administrar anulaciones**

Para gestionar las anulaciones con MS Graph de Aspose.Email para .NET, utilice los métodos siguientes:
* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createorupdateoverride/#createorupdateoverride)
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listoverrides/#listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updateoverride/#updateoverride)

```csharp
// Create an user's override
var userOverride = client.CreateOrUpdateOverride
    (new MailAddress("JohnBrown@someorg.com", "JohnBrown"), ClassificationType.Focused);

// list the overrides
var overrides = client.ListOverrides();

// update override
userOverride.Sender.DisplayName = "John Brown";
var updatedOverride = client.UpdateOverride(userOverride);

// delete override
client.Delete(updatedOverride.Id);
```
## **Administrar reglas**
Para administrar las reglas con MS Graph de Aspose.Email para.NET, utilice los métodos siguientes:
* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createrule/#createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchrule/#fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updaterule/#updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listrules/#listrules)

```csharp
// Create a rule
var rule = PrepareRule("user@someorg.com", "User");
var createdRule = client.CreateRule(rule);

// List all rules defined for Inbox
var rules = client.ListRules();

// Fetch a rule
var fetchedRule = client.FetchRule(createdRule.RuleId);

// Update a rule
fetchedRule.DisplayName = "Renamed rule";
fetchedRule.IsEnabled = false;
var updatedRule = client.UpdateRule(createdRule);

// Delete a rule
client.Delete(updatedRule.RuleId);
```

```csharp
InboxRule PrepareRule(string email, string displayName)
{
    var rule = new InboxRule()
    {
        DisplayName = "My rule",
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

## **Administrar cuadernos**

Para administrar libretas con MS Graph de Aspose.Email para.NET, utilice los siguientes métodos:
* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createnotebook/#createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copynotebook/#copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchnotebook/#fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listnotebooks/#listnotebooks)

```csharp
// create a OneNote notebook
var newNotebook = new Notebook()
{
    DisplayName = "My Notebook"
};
var createdNotebook = client.CreateNotebook(newNotebook);

// fetch a notebook
var fetchedNotebook = client.FetchNotebook(createdNotebook.Id);

// list the notebooks
var notebooks = client.ListNotebooks();
```
