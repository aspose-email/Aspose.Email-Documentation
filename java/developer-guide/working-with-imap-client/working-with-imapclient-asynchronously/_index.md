---
title: Working with ImapClient Asynchronously
type: docs
weight: 70
url: /java/working-with-imapclient-asynchronously/
---


Messages can be retrieved from mailbox asynchronously by using the Aspose.Email's [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient). This article shows retrieving messages from mailbox Asynchronously. This article also shows how to list messages by providing search criteria using [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery).
## **Retrieve Messages Asynchronously**
The following code snippet shows you how to retrieve messages asynchronously.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder("Issues/SubFolder");
    ImapMessageInfoCollection messages = client.listMessages();
    IAsyncResult ar = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(ar);
}
~~~
## **List Messages Asynchronously with MailQuery**
The [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) class can be used to specify search criteria for retrieving a specified list of messages asynchronously as is shown in the following code sample.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
