---
title: "Асинхронная работа с Pop3Client"
url: /ru/java/working-with-pop3client-asynchronously/
weight: 60
type: docs
---

## **Асинхронная работа с Pop3Client**

Сообщения также можно получать из почтовых ящиков асинхронно с помощью Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). В этой статье показано, как асинхронно извлекать сообщения из почтового ящика. В ней также показано, как составить список сообщений, указав критерии поиска, используя [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

### **Асинхронное получение сообщений**

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

### **Асинхронный список сообщений с помощью MailQuery**

The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) класс можно использовать для указания критериев поиска для асинхронного получения списка сообщений, как показано в следующем примере кода.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
