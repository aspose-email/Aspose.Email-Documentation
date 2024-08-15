---
title: "Trabajando con IMAPClient de forma asincrónica"
url: /es/java/working-with-imapclient-asynchronously/
weight: 70
type: docs
---


Los mensajes se pueden recuperar del buzón de forma asíncrona mediante Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Este artículo muestra la recuperación de mensajes del buzón de forma asincrónica. Este artículo también muestra cómo enumerar los mensajes proporcionando criterios de búsqueda mediante [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

## **Recuperar mensajes de forma asincrónica**

El siguiente fragmento de código muestra cómo recuperar mensajes de forma asincrónica.

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

## **Listar mensajes de forma asincrónica con MailQuery**

The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) La clase se puede usar para especificar los criterios de búsqueda para recuperar una lista específica de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
