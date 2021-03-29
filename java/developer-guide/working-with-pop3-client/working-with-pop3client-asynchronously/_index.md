---
title: Working with Pop3Client Asynchronously
type: docs
weight: 60
url: /java/working-with-pop3client-asynchronously/
---

## **Working with Pop3Client Asynchronously**
Messages can be retrieved from mailboxes asynchronously as well by using the Aspose.Email [Pop3Client](https://apireference.aspose.com/email/java/com.aspose.email/Pop3Client). This article shows how to retrieve messages from a mailbox asynchronously. It also shows how to list messages by providing search criteria using [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/MailQuery).
### **Retrieving Messages Asynchronously**


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
client.setHost("pop.gmail.com");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.SSLImplicit);
client.setUsername("username");
client.setPassword("password");

try {
    Pop3MessageInfoCollection messages = client.listMessages();
    System.out.println("Total Number of Messages in inbox:" + messages.size());
    IAsyncResult asyncResult = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(asyncResult);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~
### **List Messages Asynchronously with MailQuery**
The [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/MailQuery) class can be used to specify search criteria for retrieving a list of messages asynchronously as is shown in the following code sample.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
