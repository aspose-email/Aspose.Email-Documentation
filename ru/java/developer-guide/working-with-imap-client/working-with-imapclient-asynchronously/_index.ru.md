---
title: "Работа с ImapClient асинхронно"
url: /ru/java/работа-с-imapclient-асинхронно/
weight: 70
type: docs
---


Сообщения могут быть извлечены из почтового ящика асинхронно с использованием Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Эта статья демонстрирует извлечение сообщений из почтового ящика асинхронно. Эта статья также показывает, как перечислить сообщения, предоставив критерии поиска с помощью [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

## **Извлечение сообщений асинхронно**

Следующий фрагмент кода показывает, как извлекать сообщения асинхронно.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Подключение и вход в IMAP
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder("Issues/SubFolder");
    ImapMessageInfoCollection messages = client.listMessages();
    IAsyncResult ar = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(ar);
}
~~~

## **Перечисление сообщений асинхронно с MailQuery**

Класс [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) может быть использован для указания критериев поиска для извлечения заданного списка сообщений асинхронно, как показано в следующем примере кода.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
