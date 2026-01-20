---
title: Gmail API Support with Aspose.Email for .NET 
ArticleTitle: Working with Gmail Messages and Filters
type: docs
weight: 40
url: /net/integrate-gmail-client-messages-filters/
---

## **Getting Started with IGmailClient**

Aspose.Email for .NET provides robust support for interacting with Gmail through the [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) interface. You can manage messages and filters in a Gmail mailbox — including listing, fetching, sending, appending, and deleting emails, as well as managing custom filters for automatic classification.

To use Gmail features, you need to initialize an IGmailClient instance using your clientId, clientSecret, refreshToken, and target email address. All examples below assume this setup:

```cs
using (IGmailClient client = GmailClient.GetInstance(clientId, clientSecret, refreshToken, email))
{
    // Work with messages or filters
}
```

## **List Messages in a Gmail Mailbox**

Retrieve all messages from the mailbox as lightweight [GmailMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.google/gmailmessageinfo/) objects. The following code sample dmeonstrates how to retrieve a list of available messages in a Gmail mailbox without loading full content:

```cs
var messages = client.ListMessages();
```

## **Fetch and Delete Gmail Messages**

The code sample below demonstrates how to read and delete messages from Gmail using their unique identifiers:

1. Use [client.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listmessages/#igmailclientlistmessages-method) to retrieve a list of messages.
2. Set up a for loop to iterate through the first three messages.
3. Inside the loop, fetch each message using [client.FetchMessage(messages[i].Id)](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchmessage/#igmailclientfetchmessage-method).
4. Print the subject and body of the fetched message.
5. Call [client.DeleteMessage(messages[i].Id, true)](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletemessage/#deletemessage_1) to delete the message and move it to trash.
6. Confirm deletion with the message.

```cs
var messages = client.ListMessages();

for (int i = 0; i < 3; i++)
{
    var msg = client.FetchMessage(messages[i].Id);
    Console.WriteLine($"Message {i + 1}: Subject - {msg.Subject}, Body - {msg.Body}");

    client.DeleteMessage(messages[i].Id, true);
    Console.WriteLine($"Message {i + 1} moved to trash.");
}
```

## **Send a Message via Gmail**

Compose and send an email, including attachments using the SendMessage() method. The code sample below demonstrates how to send an email through Gmail with an attachment:

```cs
MailMessage message = new MailMessage("sender@example.com", "recipient@example.com", "Weekly Report", "Attached is the weekly report.");

string attachmentPath = Path.Combine(TestUtil.GetTestDataPath(), "report.pdf");
message.Attachments.Add(new Attachment(attachmentPath));

string messageId = client.SendMessage(message);
Console.WriteLine($"Message with attachment sent! ID: {messageId}");
```

