---
title: "Как использовать GraphClient для График Майкрософт"
url: /ru/net/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Работа с GraphClient**

[График Майкрософт](https://learn.microsoft.com/en-us/graph/overview) представляет собой REST API для доступа к данным Microsoft 365. Реализация клиента Graph в Aspose.Email для .NET позволяет получить доступ к График Майкрософт из нашего API.
В приведенных ниже примерах мы создадим экземпляр MS Graph Client и введем в него токен. Затем мы рассмотрим основные способы управления папками, их обновления, копирования и удаления. Сообщения, их содержимое и вложения также можно просматривать или изменять с помощью нашего клиента MS Graph. Управление категориями, правилами, записными книжками и переопределениями — это расширенная функция График Майкрософт Client от Aspose.Email, которую вы легко освоите.

### **Создать объект GraphClient**

Create [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) возражать против запросов к сервису.
После того, как вы получите [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) который прошел аутентификацию, вы можете начать звонить в службу.

A [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) метод требует [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) экземпляр реализации в качестве первого параметра.

Чтобы получить токен, мы будем использовать [Библиотека аутентификации Microsoft (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Ниже приведены шаги для получения токена авторизации.

 - Создайте класс AccessParameters для хранения учетных данных.
 - Добавьте [Пакет microsoft.Identity.Client nuget](https://www.nuget.org/packages/Microsoft.Identity.Client) который содержит двоичные файлы MSAL.NET.
 - Внедрить [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/), и создайте метод, принимающий параметры доступа и использующий MSAL.NET для получения токена доступа.

Чтобы сохранить учетные данные, добавьте следующее `AccessParameters` class:

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

Создайте `GraphTokenProvider` класс, реализующий [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) интерфейс. Используйте [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) библиотека для получения токена.
См. пример такой реализации:

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

Затем создайте `AccessParameters` экземпляр класса:

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Your Tenant ID",
    ClientId = "Your Client ID",
    ClientSecret = "Your Client Secret",
    UserId = "User's Object ID"
};
```

Наконец, создайте [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) экземпляр и позвоните [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) метод. Передайте `tokenProvider` в качестве первого параметра и `accessParams.TenantId` в качестве второго:

```csharp
var tokenProvider = new GraphTokenProvider(accessParams);

using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

## **Управление папками**

### **Список папок**

Позвонив [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) метод от MS Graph Client, можно получить список папок. Каждая папка имеет набор параметров, таких как DisplayName, которые можно прочитать [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) type.

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Обновить папку**

Чтобы создать папку с помощью MS Graph Client, используйте [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder) метод. Вы получите [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) объект и возможность доступа к DisplayName, itemID, HasSubfolders и другим свойствам.

```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

### **Скопировать папку**

[CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) метод является ключевым методом копирования объекта папки с помощью MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
   
// copy Folder2 to Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Перемещение и удаление папки**

Use [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) метод используется для перемещения папки, он принимает NewParentID и itemID. [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) метод используется для удаления метода по идентификатору.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
   
// move Folder2 to Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
   
// delete Folder1
client.Delete(folderInfo1.ItemId)
```

## **Управление сообщениями**

MS Graph Client, реализованный в Aspose.Email for .NET, предоставляет набор методов управления сообщениями и вложениями:
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


### **Список сообщений**

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

### **Список сообщений по дате отправки**

The [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) метод из коллекции библиотеки позволяет извлекать сообщения с разным порядком сортировки (по возрастанию и убыванию) в зависимости от даты отправки. В следующем примере кода показано, как упорядочить сообщения по дате отправки:

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

### **Перечисление сообщений с поддержкой пейджинга с помощью Graph Client**

API позволяет разбивать сообщения на страницы и фильтровать их при перечислении. Это особенно полезно для почтовых ящиков с большим объемом сообщений, поскольку позволяет сэкономить время, получая только необходимую сводную информацию.

В примере кода и приведенных ниже шагах показано, как извлекать сообщения из папки «Входящие» с помощью функций разбиения на страницы и фильтрации.

1. Сначала инициируйте клиента.
2. Затем задайте количество элементов, отображаемых на странице, например 10.
3. Создайте фильтр для извлечения непрочитанных сообщений только с помощью [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class) класс. Builder.isRead.equals (false) задает условие фильтрации непрочитанных сообщений.
4. Позвоните [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) метод на клиентском объекте с указанием папки (Inbox) и элементов на странице (PageInfo (itemsPerPage)) в качестве параметров. Он также передает объект запроса для применения фильтра непрочитанных сообщений.
Возвращенный объект PageInfo (PageInfo) содержит полученные сообщения для текущей страницы в свойстве Items.
5. Создайте цикл, который будет продолжаться до тех пор, пока не будет достигнута последняя страница (PageInfo.lastPage имеет значение false). Полученные сообщения добавляются в существующий список сообщений с помощью Messages.addRange (PageInfo.Items).


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

### **Получить сообщение**

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

### **Создать сообщение**

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
### **Отправить сообщение**

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
### **Отправить черновик сообщения**

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

### **Отправить сообщение EML**

С помощью объекта MailMessage легко создавать и отправлять электронные письма. В следующем примере кода показано, как создать и отправить сообщение электронной почты с помощью Graph API:

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


### **Скопировать сообщение**

```csharp

// copy message to Inbox folder
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Переместить сообщение**

```csharp
// move message to Inbox folder
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Управление вложениями**

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
## **Управление событиями в календаре**

Aspose.Email предоставляет API для доступа, управления и взаимодействия с событиями календаря. Для этих целей он предлагает следующие методы в [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListCalendars()** - Извлекает коллекцию календарной информации.

- **Список элементов календаря (строковый идентификатор)** - Извлекает коллекцию элементов календаря, связанных с указанным идентификатором календаря.

- **Избрать элемент календаря (идентификатор строки)** - Извлекает определенный элемент календаря на основе предоставленного идентификатора.

- **Создать элемент календаря (строка CALID, MapCalendar MapCalendar)** - Создает новый элемент календаря в указанном календаре.

- **Обновить элемент календаря (MapCalendar MapCalendar)** - Обновляет существующий элемент календаря.

- **Обновить элемент календаря (MapCalendar MapCalendar, Обновить настройки и обновить настройки)** - Обновляет существующий элемент календаря с заданными настройками обновления.

В следующем примере кода показано, как взаимодействовать с событиями календаря в клиенте График Майкрософт API с помощью методов, предоставляемых Aspose.Email:

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

## **Управление категориями**
Для управления категориями с помощью MS Graph от Aspose.Email for .NET используйте следующие методы:
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
## **Управление контактами**

Aspose.Email предоставляет API для доступа, управления и взаимодействия с контактными данными. Для этих целей он предлагает следующие методы в [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListContacts (строковый идентификатор)** - Извлекает коллекцию контактов MAPI, связанных с указанным идентификатором папки.

- **fetchContact (идентификатор строки)** - Извлекает определенный контакт на основе предоставленного идентификатора товара.

- **Создать контакт (строковый идентификатор папки, контакт MAPI Contact)** - Создает новый контакт в указанной папке.

- **Обновить контакт (контактное лицо Mapi)** - Обновляет существующий контакт.

В следующем примере кода показано, как взаимодействовать с контактами в клиенте График Майкрософт API с помощью методов, предоставляемых Aspose.Email:

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

## **Управление переопределениями**

Для управления переопределениями с помощью MS Graph от Aspose.Email for .NET используйте следующие методы:
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
## **Управление правилами**
Для управления правилами с помощью MS Graph от Aspose.Email for .NET используйте следующие методы:
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

## **Управление ноутбуками**

Для управления записными книжками с помощью MS Graph от Aspose.Email for .NET используйте следующие методы:
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
