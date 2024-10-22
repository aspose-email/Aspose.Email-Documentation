---
title: "Obtener mensajes de un buzón compartido"
url: /es/java/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---

Aspose.Email admite el acceso a mensajes desde el buzón compartido. Para lograr esto, te conectas a tu buzón principal utilizando la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Para acceder a los mensajes del buzón compartido, pasas el buzón compartido como un parámetro de cadena al método [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) o [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)).

El siguiente ejemplo de código muestra cómo acceder a mensajes del buzón compartido utilizando el método [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)).

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