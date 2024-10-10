---
title: "Как использовать GraphClient для Microsoft Graph"
url: /ru/net/how-to-use-graphclient-for-microsoft-graph/
weight: 20
type: docs
---


## **Работа с GraphClient**

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) — это REST API для доступа к данным Microsoft 365. Реализация Graph Client в Aspose.Email для .NET позволяет получить доступ к Microsoft Graph из нашего API. 
В приведенных ниже примерах мы создадим экземпляр MS Graph Client, предоставив ему токен. Затем мы рассмотрим основные методы для управления папками, их обновления, копирования и удаления. Сообщения, их содержимое и вложения также могут быть доступны или изменены с помощью нашего MS Graph Client. Управление категориями, правилами, блокнотами и переопределениями является расширенной функцией Microsoft Graph Client от Aspose.Email, с которой вы легко познакомитесь.

### **Создание объекта GraphClient**

Создайте [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) объект для выполнения запросов к сервису.
После того, как у вас есть аутентифицированный [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/), вы можете начинать делать вызовы к сервису.

Метод [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) требует наличия экземпляра реализации [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) в качестве первого параметра.

Чтобы получить токен, мы используем [библиотеку аутентификации Microsoft (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Следующие шаги описывают, как получить токен авторизации.

 - Создайте класс AccessParameters для хранения учетных данных.
 - Добавьте [пакет nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client), который содержит бинарные файлы MSAL.NET.
 - Реализуйте [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/), и создайте метод, принимающий параметры доступа и использующий MSAL.NET для получения токена доступа.

Чтобы сохранить учетные данные, добавьте следующий класс `AccessParameters`:

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

Создайте класс `GraphTokenProvider`, который реализует интерфейс [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/). Используйте библиотеку [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) для получения токена.
Смотрите пример такой реализации:

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

            Console.WriteLine("Токен получен");
        }
        catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
        {
            Console.WriteLine("Предоставленный диапазон не поддерживается");
            result = null;
        }

        if (result == null) return null;
        _token = result.AccessToken;
        return result.AccessToken;
    }
```

Далее создайте экземпляр класса `AccessParameters`:

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Ваш идентификатор клиента",
    ClientId = "Ваш идентификатор клиента",
    ClientSecret = "Ваш клиентский секрет",
    UserId = "Идентификатор объекта пользователя"
};
```

Наконец, создайте экземпляр [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) и вызовите метод [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1). Передайте `tokenProvider` в качестве первого параметра и `accessParams.TenantId` в качестве второго:

```csharp
var tokenProvider = new GraphTokenProvider(accessParams);

using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

## **Управление папками**

### **Список папок**

Вызвав метод [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) из MS Graph Client, можно получить список папок. Каждая папка имеет набор параметров, таких как DisplayName, которые можно прочитать в типе [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/).

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Обновление папки**

Чтобы создать папку с помощью MS Graph Client, используйте метод [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder). Вы получите объект [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) и возможность доступа к DisplayName, ItemId, HasSubFolders и другим свойствам.

```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

### **Копирование папки**

Метод [CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) является ключевым методом для копирования объекта папки с помощью MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// копировать Folder2 в Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Перемещение и удаление папки**

Используйте метод [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) для перемещения папки; он принимает newParentId и itemId. Метод [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) используется для удаления метода по идентификатору.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// переместить Folder2 в Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
    
// удалить Folder1
client.Delete(folderInfo1.ItemId)
```

## **Управление сообщениями**

MS Graph Client, реализованный в Aspose.Email для .NET, предоставляет набор методов для управления сообщениями и вложениями:
* [Список](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages) сообщений
* [Получить](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchmessage/#fetchmessage) сообщение
* [Создать](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage) сообщение
* [Отправить](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send) сообщение
* [Копировать сообщение](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copymessage/#copymessage)
* [Переместить](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movemessage/#movemessage) сообщение
* [Создать вложение](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createattachment/#createattachment)
* [Получить вложение](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchattachment/#fetchattachment)
* [Удалить вложение](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deleteattachment/#deleteattachment)
* [Список вложений](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listattachments/#listattachments)


### **Список сообщений**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Входящие"))
    {
        // список сообщений во входящих
        var inboxMessages = client.ListMessages(folder.ItemId);

        foreach (var messageInfo in inboxMessages)
        {
            Console.WriteLine(messageInfo.Subject);
        }
    }
}
```

### **Список сообщений по дате отправки**

Метод [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) из библиотек позволяет вам получать сообщения с разными сортировками (по возрастанию и убыванию) на основе даты отправки. Следующий код показывает, как сортировать сообщения по их дате отправки:

```cs
IGraphClient client = GraphClient.GetClient(provider, TenantId);

var builder = new GraphQueryBuilder();

// создать запрос сортировки сообщений 'DESC'
builder.SentDate.OrderBy(false);
var messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
var messages = messagePageInfo.Items;

builder.Clear();

// создать запрос сортировки сообщений 'ASC'
builder.SentDate.OrderBy(true);
messagePageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(10), builder.GetQuery());
messages = messagePageInfo.Items;
```

### **Перечисление сообщений с поддержкой постраничной навигации с использованием Graph Client** 

API позволяет постранично просматривать и фильтровать сообщения при их перечислении. Это особенно полезно для почтовых ящиков с большим количеством сообщений, так как экономит время, получая только необходимую сводную информацию.

Пример кода и шаги ниже показывают, как получить сообщения из папки "Входящие" с использованием функций постраничной навигации и фильтрации. 

1. Сначала инициализируйте клиент.
2. Затем установите количество элементов для отображения на странице, например, 10.
3. Создайте фильтр, чтобы получить только непрочитанные сообщения, используя класс [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class). Условие builder.IsRead.Equals(false) устанавливает условие для фильтрации непрочитанных сообщений.
4. Вызовите метод [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) на объекте клиента, указав папку (Входящие) и количество элементов на странице (PageInfo(itemsPerPage)) в качестве параметров. Также передайте объект запроса для применения фильтра непрочитанных сообщений.
Объект PageInfo (pageInfo), возвращаемый методом, содержит полученные сообщения для текущей страницы в свойстве Items.
5. Создайте цикл, который продолжается, пока не будет достигнута последняя страница (pageInfo.LastPage является ложным). Полученные сообщения добавляются к существующему списку сообщений с помощью messages.AddRange(pageInfo.Items).


```cs
// чтение непрочитанных сообщений с постраничной навигацией
using var client = GraphClient.GetClient(tokenProvider, config.Tenant);

// параметры постраничной навигации
var itemsPerPage = 10;
// создать фильтр непрочитанных сообщений
GraphQueryBuilder builder = new GraphQueryBuilder();
builder.IsRead.Equals(false);
var query = builder.GetQuery();

// список сообщений
var pageInfo = client.ListMessages(KnownFolders.Inbox, new PageInfo(itemsPerPage), query);
var messages = pageInfo.Items;

while (!pageInfo.LastPage)
{
    pageInfo = client.ListMessages(KnownFolders.Inbox, pageInfo.NextPage, query);
    messages.AddRange(pageInfo.Items);
}

// установить состояние сообщений как прочитанное
foreach (var message in messages)
{
    client.SetRead(message.ItemId);
}

```

### **Получение сообщения**

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    if (folder.DisplayName.Equals("Входящие"))
    {
        // список сообщений во входящих
        var inboxMessages = client.ListMessages(folder.ItemId);

        if (inboxMessages.Count > 0)
        {
            // получить первое сообщение во входящих
            var msg = client.FetchMessage(inboxMessages[0].ItemId);
            
            Console.WriteLine(msg.BodyHtml);
        }
        
    }
}
```

### **Создание сообщения**

```csharp
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Мое сообщение",
    Body = "Привет, это мое сообщение"
};

msg.Recipients.Add("sam@to.com", "Сэм", MapiRecipientType.MAPI_TO);

// создать сообщение во входящих
client.CreateMessage(KnownFolders.Inbox, msg);

```
### **Отправка сообщения**

```csharp
// подготовка сообщения
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Мое сообщение",
    Body = "Привет, это мое сообщение"
};

msg.Recipients.Add("sam@to.com", "Сэм", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "Джон");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// отправить сообщение
client.Send(msg);
```
### **Отправка черновика сообщения**

```csharp
// подготовка сообщения
var msg = new MapiMessage(OutlookMessageFormat.Unicode)
{
    Subject = "Мое сообщение",
    Body = "Привет, это мое сообщение"
};

msg.Recipients.Add("sam@to.com", "Сэм", MapiRecipientType.MAPI_TO);
msg.SetProperty(KnownPropertyList.SenderName, "Джон");
msg.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, "John@from.com");

// добавить сообщение в папку Черновики
var draftMessage = client.CreateMessage(KnownFolders.Drafts, msg);

// отправить черновик сообщения
client.Send(draftMessage.ItemId);
```

### **Отправка сообщения в формате EML**

Создавать и отправлять электронные письма легко с помощью объекта MailMessage. Следующий пример кода демонстрирует, как создать и отправить электронное письмо с использованием Graph API:

```cs
// подготовка сообщения
var eml = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Новое сообщение",
    HtmlBody = "<html><body>Это HTML-содержимое</body></html>"
};

// отправить сообщение
graphClient.Send(eml);
graphClient.Create(KnownFolders.Inbox, eml);
```


### **Копирование сообщения**

```csharp

// скопировать сообщение в папку Входящие
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Перемещение сообщения**

```csharp
// переместить сообщение в папку Входящие
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```
### **Управление вложениями**

```csharp

// создать вложение
var attachment = new MapiAttachment();
attachment.SetProperty(KnownPropertyList.DisplayName, "Мое вложение");
attachment.SetProperty(KnownPropertyList.AttachDataBinary, new byte[1024]);

// добавить вложение к сообщению
var createdAttachment = client.CreateAttachment(messageInfo.ItemId, attachment);

// получить вложение сообщения
var fetchedAttachment = client.FetchAttachment(createdAttachment.ItemId);

// удалить вложение сообщения 
client.DeleteAttachment(createdAttachment.ItemId);

// список вложений сообщения
var attachments = client.ListAttachments(messageInfo.ItemId);   
```
## **Управление событиями в календаре**

Aspose.Email предоставляет API для доступа, управления и взаимодействия с событиями в календаре. Для этих целей он предлагает следующие методы в интерфейсе [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListCalendars()** - Получает коллекцию информации о календарях.

- **ListCalendarItems(string id)** - Получает коллекцию элементов календаря, связанных с указанным идентификатором календаря.

- **FetchCalendarItem(string id)** - Получает конкретный элемент календаря на основе предоставленного идентификатора.

- **CreateCalendarItem(string calId, MapiCalendar mapiCalendar)** - Создает новый элемент календаря в указанном календаре.

- **UpdateCalendarItem(MapiCalendar mapiCalendar)** - Обновляет существующий элемент календаря.

- **UpdateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)** - Обновляет существующий элемент календаря с указанными настройками обновления.

Следующий пример кода демонстрирует, как взаимодействовать с событиями календаря в клиенте Microsoft Graph API с использованием методов, предоставленных Aspose.Email:

```cs

// Список календарей
CalendarInfoCollection calendars = graphClient.ListCalendars();

// Список элементов календаря
MapiCalendarCollection calendarItems = graphClient.ListCalendarItems("calendarId");

// Получить элемент календаря
MapiCalendar calendarItem = graphClient.FetchCalendarItem("calendarItemId");

// Создать элемент календаря
MapiCalendar newCalendarItem = new MapiCalendar(
    location: "Конференц-зал",
    summary: "Командное собрание",
    description: "Обсуждение состояния проекта и обновлений.",
    startDate: startDate,
    endDate: endDate
);

MapiCalendar createdCalendarItem = graphClient.CreateCalendarItem("calendarId", newCalendarItem);

// Обновить элемент календаря
createdCalendarItem.Location = "Zoom Meeting";
MapiCalendar updatedCalendarItem = graphClient.UpdateCalendarItem(createdCalendarItem);
```

## **Управление категориями**
Чтобы управлять категориями с помощью MS Graph от Aspose.Email для .NET, используйте следующие методы:
* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createcategory/#createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchcategory/#fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listcategories/#listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatecategory/#updatecategory)

```csharp
// создать пользовательскую категорию с оранжевым цветом
var category = client.CreateCategory("Моя пользовательская категория", CategoryPreset.Preset1);

// получить категорию
var fetchedCategory = client.FetchCategory(category.Id);

// обновить категорию (изменить цвет на коричневый)
fetchedCategory.Preset = CategoryPreset.Preset2;
var updatedCategory = client.UpdateCategory(fetchedCategory);

// список доступных категорий
var categories = client.ListCategories();

foreach (var cat in categories)
{
    Console.WriteLine(cat.DisplayName);
}

// удалить категорию
client.Delete(fetchedCategory.Id);
```
## **Управление контактами**

Aspose.Email предоставляет API для доступа, управления и взаимодействия с элементами контактов. Для этих целей он предлагает следующие методы в интерфейсе [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface):

- **ListContacts(string id)** - Получает коллекцию MAPI контактов, связанных с указанным идентификатором папки.

- **FetchContact(string id)** - Получает конкретный контакт на основе предоставленного идентификатора элемента.

- **CreateContact(string folderId, MapiContact contact)** - Создает новый контакт в указанной папке.

- **UpdateContact(MapiContact contact)** - Обновляет существующий контакт.

Следующий пример кода демонстрирует, как взаимодействовать с контактами в клиенте Microsoft Graph API, используя методы, предоставленные Aspose.Email:

```cs
// Список контактов
MapiContactCollection contacts = graphClient.ListContacts("contactFolderId");

// Получить контакт
MapiContact contact = graphClient.FetchContact("contactId");

// Создать контакт
MapiContact newContact = new MapiContact("Джейн Смит", "jane.smith@example.com", "XYZ Corporation", "777-888-999");

MapiContact createdContact = graphClient.CreateContact("contactFolderId", newContact);

// Обновить контакт
createdContact.Telephones.PrimaryTelephoneNumber = "888-888-999";

MapiContact updatedContact = graphClient.UpdateContact(createdContact);
```

## **Управление переопределениями**

Чтобы управлять переопределениями с помощью MS Graph от Aspose.Email для .NET, используйте следующие методы:
* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createorupdateoverride/#createorupdateoverride) 
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listoverrides/#listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updateoverride/#updateoverride)

```csharp
// Создать переопределение для пользователя
var userOverride = client.CreateOrUpdateOverride
    (new MailAddress("JohnBrown@someorg.com", "Джон Браун"), ClassificationType.Focused);

// список переопределений
var overrides = client.ListOverrides();

// обновить переопределение
userOverride.Sender.DisplayName = "Джон Браун";
var updatedOverride = client.UpdateOverride(userOverride);

// удалить переопределение
client.Delete(updatedOverride.Id);
```
## **Управление правилами**
Чтобы управлять правилами с помощью MS Graph от Aspose.Email для .NET, используйте следующие методы:
* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createrule/#createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchrule/#fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updaterule/#updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listrules/#listrules)

```csharp
// Создать правило
var rule = PrepareRule("user@someorg.com", "Пользователь");
var createdRule = client.CreateRule(rule);

// Список всех правил, определенных для Входящих
var rules = client.ListRules();

// Получить правило
var fetchedRule = client.FetchRule(createdRule.RuleId);

// Обновить правило
fetchedRule.DisplayName = "Переименованное правило";
fetchedRule.IsEnabled = false;
var updatedRule = client.UpdateRule(createdRule);

// Удалить правило
client.Delete(updatedRule.RuleId);
```

```csharp
InboxRule PrepareRule(string email, string displayName)
{
    var rule = new InboxRule()
    {
        DisplayName = "Мое правило",
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

## **Управление блокнотами**

Чтобы управлять блокнотами с помощью MS Graph от Aspose.Email для .NET, используйте следующие методы:
* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createnotebook/#createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copynotebook/#copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchnotebook/#fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listnotebooks/#listnotebooks)

```csharp
// создать блокнот OneNote
var newNotebook = new Notebook()
{
    DisplayName = "Мой блокнот"
};
var createdNotebook = client.CreateNotebook(newNotebook);

// получить блокнот
var fetchedNotebook = client.FetchNotebook(createdNotebook.Id);

// список блокнотов
var notebooks = client.ListNotebooks();
```