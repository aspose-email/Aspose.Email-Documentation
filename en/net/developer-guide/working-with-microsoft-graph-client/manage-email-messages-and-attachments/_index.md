---
title: Manage Email Messages & Attachments with Microsoft Graph
ArticleTitle: Manage Email Messages & Attachments with Microsoft Graph
type: docs
weight: 40
url: /net/manage-email-messages-attachments-microsoft-graph/
---


Aspose.Email [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) provides a wide range of methods to manage email messages and their attachments via Microsoft Graph.

**Available Operations:**

- List messages

- Filter and page through messages

- Fetch message content

- Create and send messages (including drafts and EML)

- Copy and move messages

- Manage attachments (create, fetch, delete, list)


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

## **List Messages**

To retrieve messages from a folder such as "Inbox", use the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) method.

1. Retrieve the list of folders using [client.ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders).
2. Loop through each folder.
3. Check if the folder's display name is "Inbox".
4. If it is, list the messages in the inbox using [client.ListMessages(folder.ItemId)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1).
5. Loop through each message in the inbox.
6. Print the subject of each message to the console.

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

## **List Messages Asynchronously with Microsoft Graph**

The following code sample demonstrates how to access the Inbox folder, fetch a page of email messages with `ListMessagesAsync`, and print their subjects:

```cs
var folders = await client.ListFoldersAsync();
foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}

var folderId = folders.Find(x => x.DisplayName == "Inbox").ItemId;
var msgsPage = await client.ListMessagesAsync(folderId, new PageInfo(15) { PageOffset = 0 }, null);
var msgs = msgsPage.Items;
foreach (var msg in msgs)
{
    Console.WriteLine(msg.Subject);
}
```

## **Filter Messages by Sent Date**

The [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) method from the library collection enables you to retrieve messages with different sorting orders (ascending and descending) based on the date they were sent. The following code sample shows how to order messages by their sent date:

1. Initialize the Graph Client 
   - Create an instance of [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) using [GraphClient.GetClient()](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/#methods) with the provider and TenantId.

2. Create Query Builder
   - Instantiate a [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class) object.

3. Order Messages by Date in:
-  **Descending Order**
   - Use `builder.SentDate.OrderBy(false)` to set the order to descending.
   - Call [client.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) to get messages from the Inbox with a limit of 10, using the query from [builder.GetQuery()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/).
   - Store the retrieved messages in the messages variable.

- **Ascending Order**
   - Set the order to ascending by calling `builder.SentDate.OrderBy(true)`.
   - Use [client.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) again to fetch messages from the Inbox, now in ascending order.
   - Store these messages in the messages variable.

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

## **List Messages with Paging and Filtering** 

Use paging when working with large mailboxes. The example below retrieves unread messages in pages of 10 and marks them as read after processing:

1. Initiate the client.
2. Set the number of items to display per page, for example, 10.
3. Create a filter to only retrieve unread messages using the [GraphQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphquerybuilder/#graphquerybuilder-class) class. The `builder.IsRead.Equals(false)` is setting the condition for filtering unread messages.
4. Call the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) method on the client object, specifying the folder (Inbox) and the items per page (PageInfo(itemsPerPage)) as parameters. It also passes the query object to apply the unread messages filter.
The returned PageInfo object (pageInfo) contains the retrieved messages for the current page in the Items property.
5. Create a loop that continues until the last page is reached (pageInfo.LastPage is false). The retrieved messages are added to the existing messages list using `messages.AddRange(pageInfo.Items)`.

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

## **Fetch a Message**

Retrieve the full content of a specific message. The following code sample demonstrates how to retrieve and display the latest message in the Inbox for display or processing:

1. Call [client.ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) to retrieve all available folders in the mailbox and store them in the folders variable.
2. Iterate through each folder in the folders collection using a foreach loop.
3. Inside the loop, check if the folder display name equals "Inbox".
4. If the folder is the Inbox, retrieve the messages using [client.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listmessages/#listmessages_1) with the folder ItemId.
5. Check if there are any messages in the inbox by verifying that inboxMessages.Count is greater than 0.
6. If there are messages, fetch the first message using [client.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchmessage/) with the first message ItemId.
7. Output the HTML body of the fetched message.

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

## **Microsoft Graph Queries with OData**

Aspose.Email for .NET provides **OData query support** for Microsoft Graph. This allows developers to apply advanced filtering, sorting, selection, paging, and expansion when working with Graph resources such as folders, messages, contacts, calendar items, and more. The **`Aspose.Email.Clients.Graph.ODataQueryBuilder`** class is build to construct OData query parameters in a structured way instead of manually building query strings. This way, you can retrieve only necessary fields (`Select`) for efficiency, use filtering (`Filter`) and sorting (`OrderBy`) to organize data. You can also implement pagination (`Top`, `Skip`) for large datasets, expand related entities (`Expand`) in one call, and enable counting and full-text search for advanced scenarios.

Below is the list of [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) methods that support an optional **`ODataQueryBuilder`** parameter:

* `ListFolders`
* `ListMessages`
* `ListContacts`
* `ListCalendarItems`
* `ListAttachments`
* `ListCategories`
* `ListOverrides`
* `ListRules`
* `ListTaskLists`
* `ListTasks`
* `ListNotebooks`

The following code sample demonstrates how to use **`ODataQueryBuilder`** to list folders and retrieve filtered, sorted, and paged email messages from a mailbox:

```csharp
var accessParameters = Settings.User1;

var provider = new AzureConfidentialTokenProvider(
    accessParameters.TenantId,
    accessParameters.ClientId,
    accessParameters.ClientSecret);

var client = GraphClient.GetClient(provider, accessParameters.TenantId);

client.Resource = Aspose.Email.Clients.Graph.ResourceType.Users;
client.ResourceId = accessParameters.Username;
client.EndPoint = "https://graph.microsoft.com";

// Example 1: List folders ordered by name
var builder = new ODataQueryBuilder { OrderBy = "name asc" };
var folders = client.ListFolders(builder);

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}

// Example 2: Retrieve filtered and paged messages from Inbox
var folderId = folders.Find(x => x.DisplayName == "Inbox").ItemId;

builder = new ODataQueryBuilder
{
    Filter = "startswith(name,'A')",
    OrderBy = "name asc",
    Top = 10,
    Skip = 5,
    Select = new[] { "name", "age" },
    Expand = new[] { "children", "parents" },
    Count = true,
    Search = "\"John Doe\"",
    Format = "json"
};

var msgs = client.ListMessages(folderId, builder);

foreach (var msg in msgs)
{
    Console.WriteLine(msg.Subject);
}
```


## **Create a Message**

Use the [CreateMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage) method to save a new message directly into a specific folder, such as the Inbox. The following example demonstrates how to construct a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) and add it to the mailbox.


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

## **Send Messages**

The [Send](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send_1) method of [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) allows you to send an email message directly using a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object. In this example, a simple message is created, configured with sender and recipient details, and then sent.

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

### **Send a Draft Message**

You can save a message to the Drafts folder and send it later using [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/). This approach allows you to prepare a message, review or modify it before sending, and then dispatch it when ready. The following code sample demonstrates how to create an email, add metadata, store it as a draft, and then send it:

1. Create a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) with subject, body, and recipients.
2. Set sender details using message properties.
3. Save the message to the Drafts folder using [CreateMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage).
4. Send the draft by passing its ItemId to the [Send()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send_1) method.

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

### **Send an EML Message**

Use the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class to create and send EML-formatted messages. The following code sample demonstrates how to create and send an email message using Graph API:

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


## **Copy Messages**

To create a duplicate of an existing email message, use the [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copymessage/) method of the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) interface.

```csharp

// copy message to Inbox folder
var copiedMsg = client.CopyMessage(KnownFolders.Inbox, msg.ItemId);
```

## **Move Messages**

To transfer an existing email message from its current location to a new folder, use the [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movemessage/) method of the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) interface.

```csharp
// move message to Inbox folder
var movedMsg = client.MoveMessage(KnownFolders.Inbox, msg.ItemId);
```

## **Manage Attachments**

The [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) in Aspose.Email for .NET allows you to work with email attachments programmatically. This includes creating, retrieving, deleting, and listing attachments associated with a message. The following code sample demonstrates full attachment lifecycle management for Outlook messages via Microsoft Graph API using Aspose.Email. You can customize the attachment content and metadata as needed.

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


