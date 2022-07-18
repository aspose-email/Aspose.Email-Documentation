---
title: Working with Exchange Mailbox and Messages
type: docs
weight: 20
url: /net/working-with-exchange-mailbox-and-messages/
---


## **Getting Mailbox Information Using EWS**
The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class has members that can be used to get mailbox information from an Exchange Server by calling the IEWSClient.GetMailboxInfo() method. It returns an instance of type [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo). Get mailbox information from properties such as [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri) and [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). This article shows how to access mailbox information using Exchange Web Services.

If you want to connect to the Exchange Server using Exchange Web Services (EWS), use the IEWSClient class in the Aspose.Email.Exchange namespace. This class uses EWS to connect to and manage items on an Exchange Server. The following code snippet shows you how to get mailbox information using the exchange web services.

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
## **Sending Email Messages**
You can send email messages using an Exchange Server with the help of the tools in [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). The IEWSClient.Send() method accepts a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance as a parameter and sends the email. This article explains how to send email messages using Exchange Web Services.

Aspose.Email provides the IEWSClient class to connect to Microsoft Exchange Server using Exchange Web Services. The following code snippet shows you how to uses EWS to send emails using Microsoft Exchange Server. The following code snippet shows you how to sends email messages using EWS.

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

## **Getting Sent Item Uri**
Sent email's Id can be retrieved from Exchange server with the following sample code. This alos uses 

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

## **Reading Emails from other User’s Mailbox**
Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other user's mailboxes using Aspose.Email for .NET. This API provides mechanism for accessing folders and emails from other mailboxes using the IEWSClient class. This functionality can be achieved using the overloaded [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo) method and providing the user email address as a parameter.

The following code snippet shows you how to reading emails using IEWSClient class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Listing Messages**
A list of the email messages in an Exchange mailbox can be fetched by calling the IEWSClient.ListMessage method. Get the basic information about messages, such as subject, from, to and message ID, using the ListMessage method.
### **Simple Messages Listing**
To list the messages in an Exchange mail box:

1. Create an instance of the [IEWSClient](https://reference.aspose.com/error/404?path=email/net/aspose.email.exchange/exchangeclient) class.
1. Call the ListMessage method and create a message collection.
1. Loop through the collection and display message information.

The following code snippet shows you how to connects to an exchange server using EWS and lists messages from the inbox folder.

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

### **Listing Messages From Different Folders**
[The above code snippets](#simple-messages-listing), list all the messages in the Inbox folder. Its possible to get the list of messages from other folders as well. The IEWSClient.ListMessages() method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder. Use the IEWSClient.MailboxInfo.xxxFolderUri property to get the URI of different folders. The rest of the code is same as for getting a list of messages. The following code snippet shows you how to listing messages from different folders using EWS.

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

### **Listing Messages with Paging Support**
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
### **Getting Message Type Information from ExchangeMessageInfo**

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
## **Saving Messages**
This article shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats:

- Save as EML on disk.
- Save to memory stream.
- Save as MSG.
### **Saving Messages to EML**
To get messages and save in EML format:

1. Create an instance of the IEWSClient class.
1. Provide the mailboxUri, username, password and domain.
1. Call the IEWSClient.ListMessages() method to get an instance of the ExchangeMessagesInfoCollection collection.
1. Loop through the ExchangeMessagesInfoCollection collection to get the unique URI for each message.
1. Call the IEWSClient.SaveMessage() method and pass the unique URI as a parameter.
1. Provide a the SaveMessage() method with a path to where you want to save the file.

The following code snippet shows you how to use EWS to connect to the Exchange Server and save messages as EML files.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Create instance of IEWSClient class by giving credentials
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
### **Saving Messages to a Memory Stream**
Instead of saving EML files to disk, it is possible to save it to a memory stream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class. The following code snippet shows you how to save messages from an Exchange Server mailbox to a memory stream using EWS.

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
### **Saving Messages in MSG Format**
The IEWSClient.SaveMessage() method can directly save the message to EML format. To save the messages to MSG format, first call the IEWSClient.FetchMessage() method which returns an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class. Then call the MailMessage.Save() method to save the message to MSG. The following code snippet shows you how to gets messages from an Exchange Server mailbox and saves them to MSG format using EWS.

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
## **Getting ExchangeMessageInfo from Message URI**
An email message is represented by its unique identifier, URI, and is integral part of the ExchangeMessageInfo object. In case, only message URI is available, then ExchangeMessageInfo object can also be retrieved using this available information. The overload version of ListMessages takes a list of Ids to use ExchangeMessageInfoCollection. The following code snippet shows you how to get ExchangeMessageInfo from message URI.

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
## **Fetch Messages from an Exchange Server Mailbox**
Listing Messages on an Exchange Server used the ListMessages() method to get a list of messages from an Exchange Server mailbox. The ListMessage() method gets basic information about messages, for example, the subject, the message ID, from and to. To get the complete message details, Aspose.Email.Exchange provides the IEWSClient.FetchMessage() method. This method accepts the message URI as a parameter and returns am instance of the Aspose.Emai.Mail.MailMessage class. The MailMessage class then provides message details like body, headers and attachments. Find out more about the MailMessage API, or find out how to manage emails with the MailMessage class. To fetch messages from Exchange Server Mailbox:

1. Create an instance of type IEWSClient.
1. Specify the server name, user name, password and domain.
1. Call ListMessages to get the ExchangeMessageInfoCollection.
1. Loop through the ExchangeMessageInfoCollection collection to get ExchangeMessageInfo.UniqueURI values.
1. Call IEWSClient.FetchMessage() and pass ExchangeMessageInfo.UniqueURI() as parameter.

The following code snippet shows you connect to the Exchange Server mailbox and fetches all the messages using EWS.

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

### **Using the FetchItem method to fetch a message**

The [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/fetchitem) method is more preferred if you want to fetch a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) and operate with MAPI properties. You can also use this method to fetching any Outlook item, such as a contact, appointment, task, etc.

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

## **Pre-Fetch Message Size**
Microsoft Outlook InterOp provides the feature of retrieving message size before actually fetching the complete message from the server. In case of Aspose.Email API, the summary information retreived from Exchange server is represented by ExchangeMessageInfo class. It provides the same feature of retrieving message size using the Size property. In order to retrieve the message size, the standard call to IEWSClient's ListMessages is used that retrieves collection of ExchangeMessagInfo. The following code snippet shows you how to display message size using the ExchangeMessageInfo class.

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
## **Download Messages Recursively**
The [EWSClient](https://reference.aspose.com/net/email/aspose.email.clients.exchange.webservice/ewsclient)’s [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listsubfolders/index) method can be used to get messages from folders and subfolders from an Exchange Server mailbox recursively. This requires Exchange Server 2007 or greater, because it uses EWS. The following code snippet shows you how to download the whole mailbox (folders and subfolders) of an Exchange Server. The folder structure is created locally and all messages download.

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
## **Download Messages from Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email's [EWSClient](https://reference.aspose.com/net/email/aspose.email.clients.exchange.webservice/ewsclient) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to reads all public folders, and subfolders, and lists and downloads any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.

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
You can move email messages from one folder to another with the help of the IEWSClient class Move method. It takes the parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
### **Moving Messages between Folders**
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
## **Deleting Messages**
You can delete email messages from a folder with the help of the ExchangeClient class DeleteMessage method. It takes the message's unique URI as a parameter.

The following code snippet shows you how to delete a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Process messages based on some criteria (in this example, we find a keyword in the message subject).
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
## **Copying Messages**
Aspose.Email API allows to copy a message from one folder to another folder using the CopyItem method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.
### **Copying a Message to Another Folder**
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
