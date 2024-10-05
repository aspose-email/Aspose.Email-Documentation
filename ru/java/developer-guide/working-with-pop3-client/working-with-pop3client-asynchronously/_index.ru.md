---
title: "Работа с Pop3Client Асинхронно"
url: /ru/java/working-with-pop3client-asynchronously/
weight: 60
type: docs
---

## **Работа с Pop3Client Асинхронно**

Сообщения также могут быть извлечены из почтовых ящиков асинхронно с помощью Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). В этой статье показано, как асинхронно извлекать сообщения из почтового ящика. Также показывается, как перечислять сообщения, указывая критерии поиска с помощью [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

### **Асинхронное Извлечение Сообщений**

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
    System.out.println("Общее количество сообщений в папке Входящие:" + messages.size());
    IAsyncResult asyncResult = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(asyncResult);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

### **Асинхронное Перечисление Сообщений с MailQuery**

Класс [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) может быть использован для указания критериев поиска для извлечения списка сообщений асинхронно, как показано в следующем фрагменте кода.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Тема");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~