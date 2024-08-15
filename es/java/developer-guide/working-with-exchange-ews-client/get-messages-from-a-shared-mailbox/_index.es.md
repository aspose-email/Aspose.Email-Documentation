---
title: "Obtener mensajes de un buzón compartido"
url: /es/java/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---


Aspose.Email admite el acceso a los mensajes del buzón compartido. Para ello, debe conectarse a su buzón de correo principal mediante el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase. Para acceder a los mensajes del buzón compartido, se pasa el buzón compartido como parámetro de cadena al [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) or [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

En el siguiente ejemplo de código se muestra cómo acceder a los mensajes del buzón compartido mediante [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

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