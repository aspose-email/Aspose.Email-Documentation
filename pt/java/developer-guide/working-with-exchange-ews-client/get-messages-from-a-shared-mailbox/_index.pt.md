---
title: "Obter Mensagens de uma Caixa de Correio Compartilhada"
url: /pt/java/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---

Aspose.Email suporta o acesso a mensagens de uma caixa de correio compartilhada. Para fazer isso, você se conecta à sua caixa de correio principal usando a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Para acessar mensagens da caixa de correio compartilhada, você passa a caixa de correio compartilhada como um parâmetro de string para o [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20java.lang.String,%20boolean\)) ou [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) método.

O seguinte exemplo de código mostra como acessar mensagens da caixa de correio compartilhada usando o [listItems](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listItems\(java.lang.String,%20java.lang.String\)) método.

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