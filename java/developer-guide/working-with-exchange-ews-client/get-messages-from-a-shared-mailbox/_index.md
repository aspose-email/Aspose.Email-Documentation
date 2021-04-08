---
title: Get Messages from a Shared Mailbox
type: docs
weight: 160
url: /java/get-messages-from-a-shared-mailbox/
---


Aspose.Email supports accessing messages from the shared mailbox. To achieve this, you connect to your primary mailbox by using the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class. To access messages from the shared mailbox, you pass the shared mailbox as a string parameter to the [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) or [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

The following code sample shows how to access messages from the shared mailbox using the [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) method.

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