---
title: "Асинхронная работа с IMapClient"
url: /ru/java/working-with-imapclient-asynchronously/
weight: 70
type: docs
---


Сообщения можно получать из почтового ящика асинхронно с помощью Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). В этой статье показано асинхронное получение сообщений из почтового ящика. В этой статье также показано, как составить список сообщений, указав критерии поиска, используя [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

## **Асинхронное получение сообщений**

В следующем фрагменте кода показано, как асинхронно извлекать сообщения.

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

## **Асинхронный список сообщений с помощью MailQuery**

The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) класс можно использовать для указания критериев поиска для асинхронного получения указанного списка сообщений, как показано в следующем примере кода.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
