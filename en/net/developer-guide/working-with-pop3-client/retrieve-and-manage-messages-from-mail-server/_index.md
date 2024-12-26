---
title: Retrieve and Manage Messages from Mail Server
ArticleTitle: Retrieve and Manage Messages from Mail Server
type: docs
weight: 40
url: /net/retrieve-and-manage-messages-from-mail-server/
---


## **Get Mailbox Information**

We can get information about the mailbox such as the number of messages and the mailbox size using the [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) and [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) methods of the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

- The [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) method returns the size of the mailbox in bytes.
- The [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) method returns an object of type [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

It is also possible to get the number of messages using the [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) property and the size using the [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) property of the [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/) class. The following sample code shows how to get information about the mailbox. It shows how to:

1. Create a [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Connect to a POP3 server.
1. Get the size of the mailbox.
1. Get mailbox info.
1. Get the number of messages in the mailbox.
1. Get the occupied size.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Retrieve Email Count in Mailbox**

The following code snippet shows you how to count the email messages in a mailbox.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email lets developers work with emails in many different ways. For example, they can retrieve header information before deciding whether to download an email. Or they can retrieve emails from a server and save them without parsing them (quicker) or after parsing them (slower).

## **Retrieve Email Headers**

Email headers can give us information about an email message that we can use to decide whether or not to retrieve the whole email message. Typically, the header information contains sender, subject, received date, etc. (Email headers are described in detail in [Customizing Email Headers](https://docs.aspose.com/email/net/create-email-messages/#customize-email-headers). The following examples show how to retrieve email headers from a POP3 server by the message sequence number.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Retrieve Email Messages**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class contains several properties and methods for manipulating email content. By using [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) method of the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class, you can get a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance directly from the POP3 server. The following code snippet shows you how to retrieve a complete email message from the POP3 server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Retrieve Message Summary with Unique Id**

The POP3 Client can retrieve message summary information from the server using the unique id of the message. This provides quick access to the message short information without first retrieving the complete message from the server. The following code snippet shows you how to retrieve message summary information.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **List Messages with MultiConnection**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) provides a [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). The following code snippet demonstrates the use of the multiconnection mode for listing messages and compares its performance with single connection mode.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}}

## **Fetch Messages from Server and Save to Disc**

### **Save Message to Disk without Parsing**

If you want to download email messages from the POP3 server without parsing them, use the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) function. The [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) function does not parse the email message so it is faster than the [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) function. The following code snippet shows how to save a message by its sequence number. In this case, the [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) method saves the message in the original EML format without parsing it.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Parse Message Before Saving**

The following code snippet uses the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) method to retrieve a message from a POP3 server by its sequence number, then save the message to disk using the subject as the file name.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Fetch Group Messages**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) provides a [FetchMessages](https://docs.aspose.com/email/net/working-with-messages-from-server/) method which accepts iterable of Sequence Numbers or Unique ID and returns a list of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). The following code snippet demonstrates the use of the [FetchMessages](https://docs.aspose.com/email/net/working-with-messages-from-server/) method to fetch messages by Sequence Numbers and Unique ID.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}