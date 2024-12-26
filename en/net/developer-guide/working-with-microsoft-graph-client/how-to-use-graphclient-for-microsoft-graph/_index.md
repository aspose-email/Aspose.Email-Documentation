---
title: Microsoft 365 Data Access and Management with Microsoft Graph
ArticleTitle: Microsoft 365 Data Access and Management with Microsoft Graph
type: docs
weight: 20
url: /net/microsoft-365-data-management-microsoft-graph/
---


## **Optimize Microsoft 365 Data Access and Management with Aspose.Email Graph Client**

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) is a REST API to access the Microsoft 365 data. The implementation of Graph Client in Aspose.Email for .NET allows the access to Microsoft Graph from our API.
In the examples below, we will create an instance of MS Graph Client, providing the token. Then, we will examine the main methods to manage folders, update, copy and delete them. Messages, their content and attachments can also be accessed or changed with our MS Graph Client. Managing categories, rules, notebooks and overrides is an extended feature of Microsoft Graph Client by Aspose.Email.

## **Authenticate and Request with IGraphClient Using MSAL in .NET**

To interact with Microsoft Graph services, you'll need to create an [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) object. Once authenticated, this client allows you to make various service requests. The [GetClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/getclient/#getclient_1) method, which creates the `IGraphClient`, requires an [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) implementation as its first parameter. This `ITokenProvider` is responsible for providing the necessary authentication token. To obtain the token, we'll use the [Microsoft Authentication Library (MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) for .NET.

Here's how to set up the authentication process:

### **Step 1: Setting Up the Authentication**

The following steps will guide you on how to obtain an authorization token:

1. **Create the AccessParameters Class.**

    Define an AccessParameters class to store your credentials.

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

2. **Add the [MSAL.NET Package](https://www.nuget.org/packages/Microsoft.Identity.Client)**.

    Install the `Microsoft.Identity.Client` NuGet package, which contains the MSAL.NET binaries needed for authentication.

3. **Implement the ITokenProvider Interface.**

    Create a `GraphTokenProvider` class that implements the [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) interface. This class will use the MSAL.NET library to acquire an access token.

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

### **Step 2: Create an ITokenProvider Instance**

After defining the `GraphTokenProvider` class, you can create an instance of `AccessParameters` and use it to instantiate the `GraphTokenProvider`.

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Your Tenant ID",
    ClientId = "Your Client ID",
    ClientSecret = "Your Client Secret",
    UserId = "User's Object ID"
};

var tokenProvider = new GraphTokenProvider(accessParams);
```

### **Step 3: Make Requests with IGraphClient**

Finally, use the `GraphTokenProvider` to create an authenticated [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) and start making service requests.

```csharp
using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

With these steps completed, your `IGraphClient` is now ready to interact with Microsoft Graph services using authenticated requests.

## **Connecting to GCC High Endpoints**

The [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) supports connecting to GCC High endpoints by using the [EndPoint](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/endpoint/) property. The following code sample demonstrates how to configure the GraphClient to connect to the GCC High endpoint for listing folders and retrieving messages.

```cs
client.EndPoint = "https://graph.microsoft.us";

var folders = client.ListFolders();
string folderId = folders.Find(x => x.DisplayName == "Inbox").ItemId;
var msgs = client.ListMessages(folderId);
```

## **Manage Folders with IGraphClient**

### **List Folders**

By calling [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) method from MS Graph Client, its possible to get the list of folders. Each folder has a set of parameters like DisplayName, which can be read in [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) type.

```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

### **Update Folders**

To create folder with MS Graph Client, use [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder) method. You will get a [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) object and the possibility to access DisplayName, ItemId, HasSubFolders and other properties.

```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

### **Copy Folders**

[CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) method is the key method to copy the folder object with MS Graph.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// copy Folder2 to Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

### **Move and Delete Folders**

Use [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) method is used to move the folder, it accepts newParentId and itemId. [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) method is used to delete a method by id.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// move Folder2 to Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
    
// delete Folder1
client.Delete(folderInfo1.ItemId)
```

## **Manage Messages with IGraphClient**

MS Graph Client, implemented in Aspose.Email for .NET, provides a set of methods to manage messages and attachments:

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

### **List Messages**

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

### **Filter Messages by Sent Date**

The [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) method from the library collection enables you to retrieve messages with different sorting orders (ascending and descending) based on the date they were sent. The following code sample shows how to order messages by their sent date:

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

### **Enumerate Messages with Paging Support** 

The API allows paging and filtering of the messages when listing them. It is especially helpful for mailboxes with a high volume of messages, as it saves time by retrieving only the necessary summary information.

The code sample and the steps below demonstrate how to retrieve messages from the Inbox folder using paging and filtering features. 

1. First, initiate the client.
2. Then, set the number of items to display per page, for example, 10.
3. Create a filter to only retrieve unread messages using the [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class) class. The builder.IsRead.Equals(false) is setting the condition for filtering unread messages.
4. Call the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) method on the client object, specifying the folder (Inbox) and the items per page (PageInfo(itemsPerPage)) as parameters. It also passes the query object to apply the unread messages filter.
The returned PageInfo object (pageInfo) contains the retrieved messages for the current page in the Items property.
5. Create a loop that continues until the last page is reached (pageInfo.LastPage is false). The retrieved messages are added to the existing messages list using messages.AddRange(pageInfo.Items).

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

### **Fetch Messages**

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

### **Create Messages**

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

### **Send Messages**

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

### **Send Draft Messages**

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

### **Send EML Messages**

Creating and sending emails is easy using the MailMessage object. The following code sample demonstrates how to create and send an email message using Graph API:

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


### **Copy Messages**

```csharp

// copy message to Inbox folder
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```

### **Move Messages**

```csharp
// move message to Inbox folder
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```

### **Manage Attachments**

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

## **Manage Outlook Items with Graph Client**

### **Manage Calendar Events**

Aspose.Email provides APIs to access, manage, and interact with calendar events. For these purposes, it offers the following methods in the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListCalendars()** - Retrieves a collection of calendar information.
- **ListCalendarItems(string id)** - Retrieves a collection of calendar items associated with the specified calendar ID.
- **FetchCalendarItem(string id)** - Retrieves a specific calendar item based on the provided ID.
- **CreateCalendarItem(string calId, MapiCalendar mapiCalendar)** - Creates a new calendar item in the specified calendar.
- **UpdateCalendarItem(MapiCalendar mapiCalendar)** - Updates an existing calendar item.
- **UpdateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)** - Updates an existing calendar item with specified update settings.

The following code sample demonstrates how to interact with calendar events in a Microsoft Graph API client using the methods provided by Aspose.Email:

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

### **Manage Categories**

To manage categories with MS Graph by Aspose.Email for .NET, use the following methods:

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

### **Manage Contacts**

Aspose.Email provides APIs to access, manage, and interact with contact items. For these purposes, it offers the following methods in the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListContacts(string id)** - Retrieves a collection of MAPI contacts associated with the specified folder ID.
- **FetchContact(string id)** - Retrieves a specific contact based on the provided item ID.
- **CreateContact(string folderId, MapiContact contact)** - Creates a new contact in the specified folder.
- **UpdateContact(MapiContact contact)** - Updates an existing contact.

The following code sample demonstrates how to interact with contacts in a Microsoft Graph API client using the methods provided by Aspose.Email:

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

### **Manage Overrides**

To manage overrides with MS Graph by Aspose.Email for .NET, use the following methods:

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

### **Manage Rules**

To manage rules with MS Graph by Aspose.Email for .NET, use the following methods:

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

### **Manage Notebooks**

To manage notebooks with MS Graph by Aspose.Email for .NET, use the following methods:

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

## **Tasks Management in Microsoft Graph**

Aspose.Email provides developers with APIs to access, manage, and interact with users’ tasks and task lists using the following methods of the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- [ListTaskLists()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listtasklists/) - Retrieves a collection of task list information.
- [GetTaskList(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/gettasklist/) - Retrieves a specific task list based on the provided ID.
- [DeleteTaskList(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deletetasklist/) - Deletes the specified task list.
-[ListTasks(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listtasks/) - Retrieves a collection of tasks associated with the specified task list ID.
- [FetchTask(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchtask/) - Retrieves a specific task based on the provided ID.
- [CreateTask(MapiTask task, string taskListUri)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createtask/) - Creates a new task in the specified task list.
- [UpdateTask(MapiTask task)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatetask/#updatetask) - Updates an existing task with the provided information.
- [UpdateTask(MapiTask task, UpdateSettings updateSettings)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatetask/#updatetask_1) - Updates an existing task with specified update settings.

The following code sample demonstrates how to manage task lists:

```cs
// List Task Lists
var taskLists = graphClient.ListTaskLists();

foreach (var tList in taskLists)
{
    Console.WriteLine($"Task List: {tList.DisplayName}");
}

// Get Task List
var taskList = graphClient.GetTaskList("taskListId");

// Delete Task List
graphClient.DeleteTaskList("taskListId");
```

The following code sample demonstrates how to manage tasks:

```cs
// List Tasks in a Task List
MapiTaskCollection tasks = graphClient.ListTasks("taskListId");

// Fetch Task
MapiTask task = graphClient.FetchTask("taskId");

// Create Task
var newTask = new MapiTask
{
    Subject = "New Task",
    DueDate = new DateTime(2023, 12, 31),
    Status = MapiTaskStatus.NotStarted
};

MapiTask createdTask = graphClient.CreateTask(newTask, "taskListUri");

// Update Task
createdTask.Subject = "Updated Task Subject";
MapiTask updatedTask = graphClient.UpdateTask(createdTask);

// Update Task with UpdateSettings
var updateSettings = new UpdateSettings { SkipAttachments  = true };
MapiTask updatedTaskWithSettings = graphClient.UpdateTask(createdTask, updateSettings);
```
