---
title: Managing Messages on IMAP Server
ArticleTitle: Retrieve and List Emails from IMAP Server
type: docs
weight: 20
url: /net/managing-messages-on-imap-server/
---

## **Retrieving and Listing Messages**

### **How to Obtain Identification Information for Messages in a Mailbox**

When retrieving and processing email messages, you can obtain detailed identification information, such as sequence numbers and unique IDs, using the following features provided by the latest version of Aspose.Email for .NET:

[Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) class: Represents the identification information about a message in an IMAP mailbox.

[ImapMessageInfo.SequenceNumber](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/sequencenumber/) property: Retrieves the sequence number of the message.

[ImapMessageInfo.UniqueId](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/uniqueid/) property: Retrieves the unique identifier of the message.

[Aspose.Email.MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) property: Represents additional identification information about the message within the mailbox.

The following code snippet demonstrates how to obtain identification information for messages in an IMAP mailbox:

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class by providing the necessary parameters such as the IMAP server host, port, email address, password, and security options.
2. Use the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_20) method to retrieve a list of messages from the "INBOX" folder. Limit the list to the first five messages using the Take(5) method.
3. Extract the sequence numbers of the listed messages by using the [SequenceNumber](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/sequencenumber/) property of each message.
4. Use the [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages_2) method to retrieve the full details of the messages from the server, using the sequence numbers obtained in the previous step.
5. Loop through the fetched messages and for each message, retrieve and display the following information:

- The sequence number of the message.
- The ItemId.SequenceNumber property.
- The subject of the message.

```cs
using (var client = new ImapClient(imapHost, port, emailAddress, password, securityOption))
{
    // List the first 5 messages from the inbox
    var msgs = client.ListMessages("INBOX").Take(5);
    
    // Get sequence numbers of the messages
    var seqIds = msgs.Select(t => t.SequenceNumber);
    
    // Fetch messages based on sequence numbers
    var msgsViaFetch = client.FetchMessages(seqIds);
    
    for (var i = 0; i < 5; i++)
    {
        var thisMsg = msgsViaFetch[i];
        Console.WriteLine($"Message ID: {seqIds.ElementAt(i)} SequenceNumber: {thisMsg.ItemId.SequenceNumber} Subject: {thisMsg.Subject}");
    }
}
```

### **List MIME Message IDs from Server**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) provides the MIME [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) for message identification without extracting the complete message. The following code snippet shows you how to list MIME messageId.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

### **List Messages from Server**

Aspose.Email provides a 2-member overloaded variant of [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) to retrieve a specified number of messages based on a query. The following code snippet shows you how to list Messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

### **List Messages Recursively**

The IMAP protocol supports listing messages recursively from a mailbox folder. This helps list messages from subfolders of a folder as well. The following code snippet shows you how to list messages recursively.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

### **List Messages with MultiConnection**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides a [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). The following code snippet demonstrates the use of the multiconnection mode for listing messages and compares its performance with single connection mode.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}}

### **List Messages with Paging Support**

In scenarios, where the email server contains a large number of messages in the mailbox, it is often desired to list or retrieve the messages with paging support. Aspose.Email API's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) lets you retrieve the messages from the server with paging support.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

### **List Message Attachments** 

To get information about attachments such as name, size without fetching the attachment data, try the following APIs:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Represents an attachment information. 
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Represents a collection of the [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) class. 
- *Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)* - Gets an information for each attachment in a message.

The code sample with steps below will show you how to use the APIs:

1. Call the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) method on the imapClient object. This method will return an ImapMessageInfoCollection containing information about the messages in the mailbox.
2. Iterate through each message in the messageInfoCollection using a foreach loop.
3. Call the [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) method on the imapClient object, passing the SequenceNumber property of the message object as a parameter. This method will return an ImapAttachmentInfoCollection containing information about the attachments in the message.
4. Iterate through each attachment in the attachmentInfoCollection using a foreach loop.
5. Within the inner loop, you can access the information about each attachment using properties of the attachmentInfo object.
   
```cs
var messageInfoCollection = imapClient.ListMessages();
    
foreach (var message in messageInfoCollection)
{
    var attachmentInfoCollection = imapClient.ListAttachments(message.SequenceNumber);

    foreach (var attachmentInfo in attachmentInfoCollection)
    {
        Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);
    }
}
```

## **Fetching and Saving Messages**

### **Fetch Messages from Server**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class can fetch messages from an IMAP server and save the messages in EML format to a local disk. The following steps are required to save the messages to disk:

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Specify a hostname, port, username, and password in the ImapClient [constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor).
1. Select the folder using [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/) method.
1. Call the [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) method to get the [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) object.
1. Iterate through the [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) collection, call the [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) method and provide the output path and file name.

The following code snippet shows you how to fetch email messages from a server and save them.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

### **Fetch Messages in Descending Order**

Aspose.Email provides [ImapClient.ListMessagesByPage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) method which lists messages with paging support. Some overloads of [ImapClient.ListMessagesByPage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) accept [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) as a parameter. [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) provides an [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) property which, when set to **false**, returns emails in descending order.

The following example code demonstrates the use of [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) property of the [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) class to change the order of emails.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

### **Save Messages in MSG Format**

To save emails in MSG format, the [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/) method needs to be called. It returns the message in an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. The [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) method can then be called to save the message to MSG. The following code snippet shows you how to save messages in MSG Format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

### **Group Fetched Messages**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides a [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) method which accepts iterable of Sequence Numbers or Unique ID and returns a list of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). The following code snippet demonstrates the use of the [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) method to fetch messages by Sequence Numbers and Unique ID.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}

### **Fetch Folders and Read Messages Recursively**

In this article, most of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) features are used to create an application that lists all the folders and sub-folders recursively from an IMAP server. It also saves the messages in each folder and sub-folder in MSG format on a local disk. On the disk, folders and messages are created and saved in the same hierarchical structure as on the IMAP server. The following code snippet shows you how to get the messages and sub-folders information recursively.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Handling Special Message Information**

### **Retrieve Extra Parameters as Summary Information**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

### **Get List-Unsubscribe Header Information**

List-Unsubscribe header contains the URL for unsubscribing from email lists e.g. advertisements, newsletters, etc. To get the List-Unsubscribe header, use the [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) property of the [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) class. The following example shows the use of the [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) property to get the List-Unsubscribe header.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}
