---
title: Retrieve and Manage Exchange Server Mailbox Information Using EWS
ArticleTitle: Retrieve and Manage Exchange Server Mailbox Information Using EWS
linktitle: Working with Exchange Mailbox and Messages
type: docs
weight: 20
url: /net/working-with-exchange-mailbox-and-messages/
keywords: c# read email from exchange server
---


## **Get Mailbox Information Using EWS**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class has members that can be used to get mailbox information from an Exchange Server by calling the [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/) method. It returns an instance of type [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Get mailbox information from properties such as [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) and [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). This article shows how to access mailbox information using Exchange Web Services.

If you want to connect to the Exchange Server using Exchange Web Services (EWS), use the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class in the Aspose.Email.Exchange namespace. This class uses EWS to connect to and manage items on an Exchange Server. The following C# code snippet shows you how to get mailbox information using the exchange web services.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials         
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
Console.WriteLine("Mailbox size: " + client.GetMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
Console.WriteLine("Inbox folder URI: " + mailboxInfo.InboxUri);
Console.WriteLine("Sent Items URI: " + mailboxInfo.SentItemsUri);
Console.WriteLine("Drafts folder URI: " + mailboxInfo.DraftsUri);
```

## **Send Email Messages**

You can send email messages using an Exchange Server with the help of the tools in [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). The [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) method accepts a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance as a parameter and sends the email. This article explains how to send email messages using Exchange Web Services.

Aspose.Email provides the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) class to connect to Microsoft Exchange Server using Exchange Web Services. The following code snippet shows you how to use EWS to send emails with Microsoft Exchange Server. The following C# code snippet shows you how to send email messages using EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@ domain.com ";
msg.Subject = "Sending message from exchange server";
msg.HtmlBody = "<h3>sending message from exchange server</h3>";

// Send the message
client.Send(msg);
```

## **Retrieve Sent Item Uri**

A sent email Id can be retrieved from Exchange server with the following sample code:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Register the event handler
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "test message", "This is a test message");

    client.Send(eml);
}
```

where the delegate method is:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Define an event handler method
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
    
    // Now we can get an id of sent email, which was saved in Sent Items folder
    string id = e.SentFolderItemId;
}
```

## **Read Emails from Another User’s Mailbox**

Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other user's mailboxes using Aspose.Email for .NET. This API provides mechanism for accessing folders and emails from other mailboxes using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods) interface. This functionality can be achieved using the overloaded [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) method and providing the user email address as a parameter.

The following C# code snippet shows you how to reading emails using IEWSClient class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Listing Messages**

A list of the email messages in an Exchange mailbox can be fetched by calling the [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method. Get the basic information about messages, such as subject, from, to and message ID, using the ListMessage method.

### **Simple Messages Listing**

To list the messages in an Exchange mail box:

1. Create an instance of the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Call the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method and create a message collection.
1. Loop through the collection and display message information.

The following C# code snippet shows you how to connect to an exchange server using EWS and list messages from the inbox folder.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message ID: " + msgInfo.MessageId);
    Console.WriteLine("Unique URI: " + msgInfo.UniqueUri);
}
```

### **List Messages From Folders**

[The above code snippets](#simple-messages-listing) list all the messages in the Inbox folder. It's possible to get the list of messages from other folders as well. The [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder. Use the [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties) property to get the URI of different folders. The rest of the code is the same as for getting a list of messages. The following code snippet shows you how to list messages from different folders using EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **List Messages with Paging Support**

The following code snippet shows you how to get a list of messages with paging support.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Move paging parameters to separate class");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Total Pages Count
        Console.WriteLine(pageInfo.TotalCount);

        pages.Add(pageInfo);
        while (!pageInfo.LastPage)
        {
            pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage, pageInfo.PageOffset + 1);
            pages.Add(pageInfo);
        }
        int retrievedItems = 0;
        foreach (ExchangeMessagePageInfo pageCol in pages)
            retrievedItems += pageCol.Items.Count;
        // Verify total message count using paging
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}          
```

### **Retrieve Message Type Information**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @"";
const string username = @"username@ASE305.onmicrosoft.com";
const string password = @"password";
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```
### **Retrieve Message Class**

The message class represents the type of an item in the Exchange store. By getting the message class, you can determine the type of the Exchange email message and perform specific operations based on its classification. 

Below is an example of getting the message class using the [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) class of the Aspose.Email for .NET:

**Code sample**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Message Class: {0}", messageInfo.MessageClass);
    }
}
```

## **Saving Messages**

This article shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats:

- Save as EML on disk.
- Save to memory stream.
- Save as MSG.
  
### **Save Messages as EML**

To get messages and save in EML format:

1. Create an instance of the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Provide the mailboxUri, username, password and domain.
1. Call the [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method to get an instance of the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/).
1. Loop through the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/) to get the unique URI for each message.
1. Call the [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) method and pass the unique URI as a parameter.
1. Provide a the [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) method with a path to where you want to save the file.

The following code snippet shows you how to use EWS to connect to the Exchange Server and save messages as EML files.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Create instance of IEWSClient interface by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to get Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in disk
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Save Messages to Memory Stream**

Instead of saving EML files to disk, it is possible to save it to a memory stream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. The following code snippet shows you how to save messages from an Exchange Server mailbox to a memory stream using EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string datadir = RunExamples.GetDataDir_Exchange();
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to get Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in memory stream
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, datadir + stream);
}
```

### **Save Messages as MSG**

The [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) method can directly save the message to EML format. To save the messages to MSG format, first call the [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) method which returns an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. Then call the [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method to save the message to MSG. The following code snippet shows you how to get messages from an Exchange Server mailbox and save them to MSG format using EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Loop through the collection to get Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
    
    // Now get the message details using FetchMessage() and Save message as Msg 
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Fetching Messages**

### **Fetch Messages by URI**

An email message is represented by its unique identifier, URI, and is integral part of the [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) object. In case, only message URI is available, then [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) object can also be retrieved using this available information. The overload version of [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) takes a list of Ids to use [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). The following code snippet shows you how to get [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) from message URI.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Do something ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

### **Fetch Messages from Mailbox**

For listing messages on an Exchange Server [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method is used to get a list of messages from an Exchange Server mailbox. The [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) method gets basic information about messages, for example, the subject, the message ID, from and to. To get the complete message details, Aspose.Email.Exchange provides the [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) method. This method accepts the message URI as a parameter and returns an instance of the [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class then provides message details like body, headers and attachments. Find out more about the MailMessage API, or find out how to manage emails with the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. To fetch messages from Exchange Server Mailbox:

1. Create an instance of type [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Specify the server name, user name, password and domain.
1. Call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) to get the [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
1. Loop through the [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) to get [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) values.
1. Call [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) and pass [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) as parameter.

The following code snippet shows you connect to the Exchange Server mailbox and fetch all the messages using EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to get Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Now get the message details using FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);
 
    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Attachment Name: " + att.Name);
 }
}
```

### **Fetch Messages without Attachments**

{{% alert color="primary" %}}

Note, the [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) method returns message without attachments. To fetch messages with attachments, use the [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) method, described in the section below. 

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/fetchitem) method is more preferred if you want to fetch a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) and operate with MAPI properties. You can also use this method to fetch any Outlook items, such as a contact, an appointment, a task, etc.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Contacts folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Loop through the collection to get Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Now get the message using FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Fetch Emails with Attachments**

The described above [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) method returns message **without attachments**, in an attempt to keep performance.

To fetch messages with attachments, use the more powerful [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) method, which allows to pass the [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/) options.

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

### **Fetch Items with Attachments Using EWS Client**

The [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)(EwsFetchItems options) method of the EwsClient retrieves email items from an Exchange server. It accepts an instance of [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) class as a parameter to define various options for fetching the items.

The following code shows how to get items with attachments:

```cs
// Call the ListMessages method to retrieve a list of message from the Inbox folder
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Create an instance of the EwsFetchItems class and assign it to the options variable
var options = EwsFetchItems.Create();

// Generate a new collection of messages which is then converted to a List.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Fetch only messages containing attachments
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

### **Pre-Fetching Message Size**

Microsoft Outlook InterOp provides the feature of retrieving message size before actually fetching the complete message from the server. In case of Aspose.Email API, the summary information retreived from Exchange server is represented by [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) class. It provides the same feature of retrieving message size using the [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/) property. In order to retrieve the message size, the standard call to [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) is used that retrieves collection of [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). The following code snippet shows you how to display message size using the [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message Size: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

### **Download Messages Recursively**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) method can be used to get messages from folders and subfolders from an Exchange Server mailbox recursively. This requires Exchange Server 2007 or greater, because it uses EWS. The following code snippet shows how to download the whole mailbox (folders and subfolders) of an Exchange Server. The folder structure is created locally and all messages download.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Register callback method for SSL validation event
    ServicePointManager.ServerCertificateValidationCallback += RemoteCertificateValidationHandler;
    try
    {
        DownloadAllMessages();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void DownloadAllMessages()
{
    try
    {
        string rootFolder = domain + "-" + username;
        Directory.CreateDirectory(rootFolder);
        string inboxFolder = rootFolder + "\\Inbox";
        Directory.CreateDirectory(inboxFolder);

        Console.WriteLine("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Call the recursive method to read messages and get sub-folders
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("All messages downloaded.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Recursive method to get messages from folders and sub-folders
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Create the folder in disk (same name as on IMAP server)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Listing messages....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Get subject and other properties of the message
        Console.WriteLine("Subject: " + msgInfo.Subject);

        // Get rid of characters like ? and :, which should not be included in a file name
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
  
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        foreach (ExchangeFolderInfo subfolderInfo in folderInfoCollection)
        {
            ListMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    }
    catch (Exception)
    {
    }
}
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // Ignore the checks and go ahead
}
```

### **Download Messages from Public Folders**

Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to read all public folders, and subfolders, and list and download any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static string dataDir = RunExamples.GetDataDir_Exchange();
public static string mailboxUri = "https://exchange/ews/exchange.asmx"; // EWS
public static string username = "administrator";
public static string password = "pwd";
public static string domain = "ex2013.local";

public static void Run()
{
    try
    {
        ReadPublicFolders();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void ReadPublicFolders()
{
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.ListPublicFolders();
    foreach (ExchangeFolderInfo publicFolder in folders)
    {
        Console.WriteLine("Name: " + publicFolder.DisplayName);
        Console.WriteLine("Subfolders count: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);

    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Folder Name: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir +  msg.Subject + ".msg",  SaveOptions.DefaultMsgUnicode);
    }

    // Call this method recursively for any subfolders
    if (publicFolder.ChildFolderCount > 0)
    {
        ExchangeFolderInfoCollection subfolders = client.ListSubFolders(publicFolder);
        foreach (ExchangeFolderInfo subfolder in subfolders)
        {
            ListMessagesFromSubFolder(subfolder, client);
        }
    }
}
```

## **Moving Messages**

You can move email messages from one folder to another with the help of the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/) method. It takes the parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
  
### **Move Messages between Folders**

The following code snippet shows you how to move a message in a mailbox from the Inbox folder to a folder called Processed. In this example, the application:

1. Reads messages from the Inbox folder.
1. Processes some of the messages based on some criteria (in this example, we find a keyword in the message subject).
1. Moves messages which fulfill the given condition to the processed folder.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("process this message") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Message moved...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Delete Messages**

You can delete email messages from a folder with the help of the [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/exchangeclient/) class [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) method. It takes a  unique URI of a message as a parameter.

The following code snippet shows you how to delete a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Processes messages based on some criteria (in this example, we find a keyword in the message subject).
1. Deletes the message.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
            
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Delete message based on some criteria
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("delete") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Message deleted...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Copy Messages**

Aspose.Email API allows to copy a message from one folder to another folder using the [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/) method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.

### **Copy Messages to Another Folder**

The following code snippet shows you how to copy a message to another folder.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```
