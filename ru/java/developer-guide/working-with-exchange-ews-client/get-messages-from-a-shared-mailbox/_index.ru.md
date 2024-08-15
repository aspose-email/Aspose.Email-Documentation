---
title: "Получайте сообщения из общего почтового ящика"
url: /ru/java/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---


Aspose.Email поддерживает доступ к сообщениям из общего почтового ящика. Для этого вы подключаетесь к своему основному почтовому ящику с помощью [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс. Чтобы получить доступ к сообщениям из общего почтового ящика, вы передаете общий почтовый ящик в виде строкового параметра [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) or [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

В следующем примере кода показано, как получить доступ к сообщениям из общего почтового ящика с помощью [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

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
    System.out.println("Subject:" + msg.getSubject());
}
client.dispose();
~~~