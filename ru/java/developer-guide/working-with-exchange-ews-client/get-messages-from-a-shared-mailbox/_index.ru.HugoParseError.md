---
title: Получение сообщений из общей почтового ящика
type: docs
weight: 160
url: /java/get-messages-from-a-shared-mailbox/
---


Aspose.Email поддерживает доступ к сообщениям из общей почтового ящика. Для этого вы подключаетесь к своему основному почтовому ящику, используя класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Чтобы получить доступ к сообщениям из общей почтового ящика, передайте общий почтовый ящик в качестве строкового параметра в метод [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) или [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)).

Следующий пример кода показывает, как получить доступ к сообщениям из общей почтового ящика, используя метод [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)).

~~~Java
final String mailboxUri = "<HOST>";
final String domain = "";
final String username = "<EMAIL ADDRESS>";
final String password = "<PASSWORD>";
final String sharedEmail = "<SHARED EMAIL ADDRESS>";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

String[] items = client.listItems(sharedEmail, "Inbox");

for (String item : items) {
    MapiMessage msg = client.fetchItem(item);
    System.out.println("Тема:" + msg.getSubject());
}
client.dispose();
~~~