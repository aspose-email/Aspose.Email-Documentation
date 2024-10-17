---
title: "Cómo usar GraphClient para Microsoft Graph"
url: /es/net/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Trabajando con GraphClient**

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) es una API REST para acceder a los datos de Microsoft 365. La implementación de Graph Client en Aspose.Email para .NET permite acceder a Microsoft Graph desde nuestra API. 
En los ejemplos a continuación, crearemos una instancia de MS Graph Client, proporcionando el token en él. Luego, examinaremos los principales métodos para gestionar carpetas, actualizarlas, copiarlas y eliminarlas. Los mensajes, su contenido y los archivos adjuntos también se pueden acceder o cambiar con nuestro MS Graph Client. La gestión de categorías, reglas, bloc de notas y sobrescrituras es una función avanzada del Microsoft Graph Client por Aspose.Email, que aprenderás con facilidad.

### **Crear objeto GraphClient**

Crea un objeto [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) para hacer solicitudes contra el servicio. 
Después de tener un [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) que esté autenticado, puedes comenzar a hacer llamadas al servicio.

Un método [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) requiere una instancia de implementación de [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) como el primer parámetro.

Para obtener el token, utilizaremos la [Microsoft Authentication Library (MSAL) para .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

 - Crea una clase AccessParameters para almacenar las credenciales.
 - Agrega el paquete nuget [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los binarios de MSAL.NET.
 - Implementa un [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/), y crea un método que acepte los parámetros de acceso y use MSAL.NET para obtener un token de acceso.

Para mantener las credenciales, agrega la siguiente clase `AccessParameters`:

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

Crea la clase `GraphTokenProvider` que implementa la interfaz [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/). Usa la biblioteca [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) para obtener un token.
Ve el ejemplo de tal implementación:

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
            Console.WriteLine("El alcance proporcionado no es compatible");
            result = null;
        }

        if (result == null) return null;
        _token = result.AccessToken;
        return result.AccessToken;
    }
```

A continuación, crea una instancia de la clase `AccessParameters`:

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Tu ID de Inquilino",
    ClientId = "Tu ID de Cliente",
    ClientSecret = "Tu Secreto de Cliente",
    UserId = "ID de Objeto del Usuario"
};
```

Finalmente, crea una instancia de [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) y llama al método [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1). Pasa el `tokenProvider` como su primer parámetro y `accessParams.TenantId` como el segundo:

```csharp
var tokenProvider = new GraphTokenProvider(accessParams);

using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

## **Gestionar Carpetas**

### **Listar Carpetas**

Al llamar al método [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) del MS Graph Client, es posible obtener la lista de carpetas. Cada carpeta tiene un conjunto de parámetros como DisplayName, que se puede leer en el tipo [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/).

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Actualizar Carpeta**

Para crear una carpeta con el MS Graph Client, utiliza el método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder). Obtendrás un objeto [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) y la posibilidad de acceder a DisplayName, ItemId, HasSubFolders y otras propiedades.

```csharp
var folderInfo = client.CreateFolder("NombreDeLaCarpeta");
folderInfo.DisplayName = "OtroNombreDeLaCarpeta";
client.UpdateFolder(folderInfo);
```

### **Copiar Carpeta**

El método [CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) es el método clave para copiar el objeto de carpeta con MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Carpeta1");
var folderInfo2 = client.CreateFolder("Carpeta2");
    
// copiar Carpeta2 a Carpeta1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Mover y Eliminar Carpeta**

Usa el método [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) para mover la carpeta, que acepta newParentId y itemId. El método [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) se usa para eliminar un método por id.

```csharp
var folderInfo1 = client.CreateFolder("Carpeta1");
var folderInfo2 = client.CreateFolder("Carpeta2");
    
// mover Carpeta2 a Carpeta1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
    
// eliminar Carpeta1
client.Delete(folderInfo1.ItemId)
```

## **Gestionar Mensajes**

El MS Graph Client, implementado en Aspose.Email para .NET, proporciona un conjunto de métodos para gestionar mensajes y archivos adjuntos:
* [Listar](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages) mensajes
* [Obtener](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchmessage/#fetchmessage) mensaje
* [Crear](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage) mensaje
* [Enviar](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send) mensaje
* [CopiarMensaje](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copymessage/#copymessage) mensaje
* [Mover](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movemessage/#movemessage) mensaje
* [CrearAdjunto](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createattachment/#createattachment)
* [ObtenerAdjunto](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchattachment/#fetchattachment)
* [EliminarAdjunto](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deleteattachment/#deleteattachment)
* [ListarAdjuntos](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listattachments/#listattachments)


### **Listar Mensajes**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Bandeja de Entrada"))
    {
        // listar mensajes en bandeja de entrada
        var inboxMessages = client.ListMessages(folder.ItemId);

        foreach (var messageInfo in inboxMessages)
        {
            Console.WriteLine(messageInfo.Subject);
        }
    }
}
```

### **Listar Mensajes por su Fecha de Envío**

El método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) de la colección de la biblioteca te permite recuperar mensajes con diferentes órdenes de clasificación (ascendente y descendente) según la fecha en que fueron enviados. El siguiente ejemplo de código muestra cómo ordenar los mensajes por su fecha de envío:

```cs
IGraphClient client = GraphClient.GetClient(provider, TenantId);

var builder = new GraphQueryBuilder();

// crear consulta de mensajes ordenados 'DESC'
builder.SentDate.OrderBy(false);
var messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
var messages = messagePageInfo.Items;

builder.Clear();

// crear consulta de mensajes ordenados 'ASC'
builder.SentDate.OrderBy(true);
messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
messages = messagePageInfo.Items;
```

### **Enumerar Mensajes con Soporte de Paginación usando Graph Client** 

La API permite paginación y filtrado de los mensajes al listarlos. Es especialmente útil para buzones con un alto volumen de mensajes, ya que ahorra tiempo al recuperar solo la información resumida necesaria.

El siguiente ejemplo de código y los pasos a continuación demuestran cómo recuperar mensajes de la carpeta Bandeja de Entrada utilizando las características de paginación y filtrado. 

1. Primero, inicializa el cliente.
2. Luego, establece el número de elementos a mostrar por página, por ejemplo, 10.
3. Crea un filtro para recuperar solo los mensajes no leídos utilizando la clase [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class). El builder.IsRead.Equals(false) establece la condición para filtrar mensajes no leídos.
4. Llama al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) en el objeto del cliente, especificando la carpeta (Bandeja de Entrada) y los elementos por página (PageInfo(itemsPerPage)) como parámetros. También pasa el objeto de consulta para aplicar el filtro de mensajes no leídos. 
El objeto PageInfo devuelto (pageInfo) contiene los mensajes recuperados para la página actual en la propiedad Items.
5. Crea un bucle que continúe hasta que se alcance la última página (pageInfo.LastPage es falso). Los mensajes recuperados se añaden a la lista de mensajes existentes usando messages.AddRange(pageInfo.Items).


```cs
//  leer mensajes no leídos con paginación
using var client = GraphClient.GetClient(tokenProvider, config.Tenant);

// opción de paginación
var itemsPerPage = 10;
// crear filtro de mensajes no leídos
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.IsRead.Equals(false);
var query = builder.GetQuery();

// listar mensajes
var pageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(itemsPerPage), query);
var  messages = pageInfo.Items;

while (!pageInfo.LastPage)
{
    pageInfo = client.ListMessages(KnownFolders.Inbox, pageInfo.NextPage, query);
    messages.AddRange(pageInfo.Items);
}

// establecer el estado de los mensajes como leídos
foreach (var message in messages)
{
    client.SetRead(message.ItemId);
}

```

### **Obtener Mensaje**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Bandeja de Entrada"))
    {
        // listar mensajes en bandeja de entrada
        var inboxMessages = client.ListMessages(folder.ItemId);

        if (inboxMessages.Count > 0)
        {
            // obtener el primer mensaje en bandeja de entrada
            var msg = client.FetchMessage(inboxMessages[0].ItemId);
            
            Console.WriteLine(msg.BodyHtml);
        }
        
    }
}
```

### **Crear Mensaje**

```csharp
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Mi mensaje",
    Body = "Hola, este es mi mensaje"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);

// crear mensaje en bandeja de entrada
client.CreateMessage(KnownFolders.Inbox, msg);

```
### **Enviar Mensaje**

```csharp
// preparar el mensaje
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Mi mensaje",
    Body = "Hola, este es mi mensaje"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// enviar mensaje
client.Send(msg);
```
### **Enviar Mensaje Borrador**

```csharp
// preparar el mensaje
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Mi mensaje",
    Body = "Hola, este es mi mensaje"
};

msg.Recipients.Add("sam@to.com", "Sam", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "John");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// agregar mensaje a la carpeta de borradores
var draftMessage = client.CreateMessage(KnownFolders.Drafts, msg);

// enviar un mensaje borrador
client.Send(draftMessage.ItemId);
```

### **Enviar un Mensaje EML**

Crear y enviar correos electrónicos es fácil utilizando el objeto MailMessage. El siguiente ejemplo de código demuestra cómo crear y enviar un mensaje de correo electrónico utilizando la API de Graph:

```cs
// preparar el mensaje
var eml = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Nuevo mensaje",
    HtmlBody = "<html><body>Este es el cuerpo HTML</body></html>"
};

// enviar el mensaje
graphClient.Send(eml);
graphClient.Create(KnownFolders.Inbox, eml);
```


### **Copiar Mensaje**

```csharp

// copiar mensaje a la carpeta Bandeja de Entrada
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Mover Mensaje**

```csharp
// mover mensaje a la carpeta Bandeja de Entrada
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Gestionar Archivos Adjuntos**

```csharp

// crear un archivo adjunto
var attachment = new MapiAttachment();
attachment.SetProperty(KnownPropertyList.DisplayName, "Mi Adjunto");
attachment.SetProperty(KnownPropertyList.AttachDataBinary, new byte[1024]);

// agregar un archivo adjunto al mensaje
var createdAttachment = client.CreateAttachment(messageInfo.ItemId, attachment);

// obtener un archivo adjunto del mensaje
var fetchedAttachment = client.FetchAttachment(createdAttachment.ItemId);

// eliminar un archivo adjunto del mensaje 
client.DeleteAttachment(createdAttachment.ItemId);

// listar los archivos adjuntos del mensaje
var attachments = client.ListAttachments(messageInfo.ItemId);   
```
## **Gestionar Eventos de Calendario**

Aspose.Email proporciona APIs para acceder, gestionar e interactuar con eventos de calendario. Para estos propósitos, ofrece los siguientes métodos en la interfaz [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListCalendars()** - Recupera una colección de información de calendario.

- **ListCalendarItems(string id)** - Recupera una colección de elementos de calendario asociados con el ID de calendario especificado.

- **FetchCalendarItem(string id)** - Recupera un elemento de calendario específico basado en el ID proporcionado.

- **CreateCalendarItem(string calId, MapiCalendar mapiCalendar)** - Crea un nuevo elemento de calendario en el calendario especificado.

- **UpdateCalendarItem(MapiCalendar mapiCalendar)** - Actualiza un elemento de calendario existente.

- **UpdateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)** - Actualiza un elemento de calendario existente con los ajustes de actualización especificados.

El siguiente ejemplo de código demuestra cómo interactuar con eventos de calendario en un cliente de API de Microsoft Graph utilizando los métodos proporcionados por Aspose.Email:

```cs

// Listar Calendarios
CalendarInfoCollection calendars = graphClient.ListCalendars();

// Listar Elementos de Calendario
MapiCalendarCollection calendarItems = graphClient.ListCalendarItems("calendarId");

// Obtener Elemento de Calendario
MapiCalendar calendarItem = graphClient.FetchCalendarItem("calendarItemId");

// Crear Elemento de Calendario
MapiCalendar newCalendarItem = new MapiCalendar(
    location: "Sala de Conferencias",
    summary: "Reunión de Equipo",
    description: "Discutir el estado y las actualizaciones del proyecto.",
    startDate: startDate,
    endDate: endDate
);

MapiCalendar createdCalendarItem = graphClient.CreateCalendarItem("calendarId", newCalendarItem);

// Actualizar Elemento de Calendario
createdCalendarItem.Location = "Reunión por Zoom";
MapiCalendar updatedCalendarItem = graphClient.UpdateCalendarItem(createdCalendarItem);
```

## **Gestionar Categorías**
Para gestionar categorías con MS Graph por Aspose.Email para .NET, usa los siguientes métodos:
* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createcategory/#createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchcategory/#fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listcategories/#listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatecategory/#updatecategory)

```csharp
// crear una categoría personalizada con color Naranja
var category = client.CreateCategory("Mi categoría personalizada", CategoryPreset.Preset1);

// obtener una categoría
var fetchedCategory = client.FetchCategory(category.Id);

// actualizar categoría (cambiar color a marrón)
fetchedCategory.Preset = CategoryPreset.Preset2;
var updatedCategory = client.UpdateCategory(fetchedCategory);

// listar las categorías disponibles
var categories = client.ListCategories();

foreach (var cat in categories)
{
    Console.WriteLine(cat.DisplayName);
}

// eliminar una categoría
client.Delete(fetchedCategory.Id);
```
## **Gestionar Contactos**

Aspose.Email proporciona APIs para acceder, gestionar e interactuar con elementos de contacto. Para estos propósitos, ofrece los siguientes métodos en la interfaz [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListContacts(string id)** - Recupera una colección de contactos MAPI asociados con el ID de carpeta especificado.

- **FetchContact(string id)** - Recupera un contacto específico basado en el ID de elemento proporcionado.

- **CreateContact(string folderId, MapiContact contact)** - Crea un nuevo contacto en la carpeta especificada.

- **UpdateContact(MapiContact contact)** - Actualiza un contacto existente.

El siguiente ejemplo de código demuestra cómo interactuar con contactos en un cliente de API de Microsoft Graph utilizando los métodos proporcionados por Aspose.Email:

```cs
// Listar Contactos
MapiContactCollection contacts = graphClient.ListContacts("contactFolderId");

// Obtener Contacto
MapiContact contact = graphClient.FetchContact("contactId");

// Crear Contacto
MapiContact newContact = new MapiContact("Jane Smith", "jane.smith@example.com", "XYZ Corporation", "777-888-999");

MapiContact createdContact = graphClient.CreateContact("contactFolderId", newContact);

// Actualizar Contacto
createdContact.Telephones.PrimaryTelephoneNumber = "888-888-999";

MapiContact updatedContact = graphClient.UpdateContact(createdContact);
```

## **Gestionar Sobrescrituras**

Para gestionar sobrescrituras con MS Graph por Aspose.Email para .NET, usa los siguientes métodos:
* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createorupdateoverride/#createorupdateoverride) 
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listoverrides/#listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updateoverride/#updateoverride)

```csharp
// Crear una sobrescritura de usuario
var userOverride = client.CreateOrUpdateOverride
    (new MailAddress("JohnBrown@someorg.com", "JohnBrown"), ClassificationType.Focused);

// listar las sobrescrituras
var overrides = client.ListOverrides();

// actualizar sobrescritura
userOverride.Sender.DisplayName = "John Brown";
var updatedOverride = client.UpdateOverride(userOverride);

// eliminar sobrescritura
client.Delete(updatedOverride.Id);
```
## **Gestionar Reglas**
Para gestionar reglas con MS Graph por Aspose.Email para .NET, usa los siguientes métodos:
* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createrule/#createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchrule/#fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updaterule/#updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listrules/#listrules)

```csharp
// Crear una regla
var rule = PrepareRule("user@someorg.com", "Usuario");
var createdRule = client.CreateRule(rule);

// Listar todas las reglas definidas para la Bandeja de Entrada
var rules = client.ListRules();

// Obtener una regla
var fetchedRule = client.FetchRule(createdRule.RuleId);

// Actualizar una regla
fetchedRule.DisplayName = "Regla Renombrada";
fetchedRule.IsEnabled = false;
var updatedRule = client.UpdateRule(createdRule);

// Eliminar una regla
client.Delete(updatedRule.RuleId);
```

```csharp
InboxRule PrepareRule(string email, string displayName)
{
    var rule = new InboxRule()
    {
        DisplayName = "Mi regla",
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

## **Gestionar Bloc de Notas**

Para gestionar blocs de notas con MS Graph por Aspose.Email para .NET, usa los siguientes métodos:
* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createnotebook/#createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copynotebook/#copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchnotebook/#fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listnotebooks/#listnotebooks)

```csharp
// crear un cuaderno de OneNote
var newNotebook = new Notebook()
{
    DisplayName = "Mi Bloc de Notas"
};
var createdNotebook = client.CreateNotebook(newNotebook);

// obtener un cuaderno
var fetchedNotebook = client.FetchNotebook(createdNotebook.Id);

// listar los cuadernos
var notebooks = client.ListNotebooks();
```