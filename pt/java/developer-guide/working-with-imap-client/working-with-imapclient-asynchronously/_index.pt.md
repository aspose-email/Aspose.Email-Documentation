---
title: "Trabalhando com ImapClient Assincronamente"
url: /pt/java/trabalhando-com-imapclient-assincronamente/
weight: 70
type: docs
---


As mensagens podem ser recuperadas da caixa de correio de forma assíncrona usando o Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Este artigo mostra como recuperar mensagens da caixa de correio de forma assíncrona. Este artigo também mostra como listar mensagens fornecendo critérios de busca usando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

## **Recuperar Mensagens Assincronamente**

O seguinte trecho de código mostra como recuperar mensagens de forma assíncrona.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e fazer login no IMAP
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder("Issues/SubFolder");
    ImapMessageInfoCollection messages = client.listMessages();
    IAsyncResult ar = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(ar);
}
~~~

## **Listar Mensagens Assincronamente com MailQuery**

A classe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) pode ser usada para especificar critérios de busca para recuperar uma lista específica de mensagens de forma assíncrona, como é mostrado no seguinte exemplo de código.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~