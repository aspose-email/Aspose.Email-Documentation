---
title: "Deletando Mensagens do Servidor"
url: /pt/java/deleting-messages-from-server/
weight: 50
type: docs
---


## **Deletando Mensagens**

A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) pode deletar mensagens de um servidor IMAP. A função [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) é usada para deletar mensagens. Ela recebe o número de sequência da mensagem ou o ID único como parâmetro. O [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece os métodos [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) e [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) para deletar mensagens uma por uma ou múltiplas. O seguinte trecho de código mostra como deletar uma mensagem de email com o ID da mensagem 1 de um servidor IMAP.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Anexar mensagem de teste
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Mensagem para deletar");
    eml.setBody("Ei! Esta mensagem será deletada!");
    String emlId = client.appendMessage(eml);

    // Deletar mensagem anexada
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Deletando Múltiplas Mensagens**

Múltiplos emails podem ser deletados da caixa de entrada usando o [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) da API Aspose.Email. O método [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) oferece várias opções para deletar múltiplas mensagens do servidor usando IDs únicos, números de sequência ou elementos [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/). O seguinte trecho de código mostra como deletar múltiplas mensagens.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Anexar mensagens de teste
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Mensagem para deletar " + i);
        eml.setBody("Ei! Esta mensagem será deletada!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Deletar em massa mensagens anexadas
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~