---
title: "Trabajando con ImapClient Asincrónicamente"
url: /es/java/trabajando-con-imapclient-asincronicamente/
weight: 70
type: docs
---

Los mensajes se pueden recuperar de la bandeja de entrada de forma asincrónica utilizando el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) de Aspose.Email. Este artículo muestra cómo recuperar mensajes de la bandeja de entrada de forma Asincrónica. Este artículo también muestra cómo listar mensajes proporcionando criterios de búsqueda utilizando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

## **Recuperar Mensajes Asincrónicamente**

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

## **Listar Mensajes Asincrónicamente con MailQuery**

La clase [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) se puede utilizar para especificar criterios de búsqueda para recuperar una lista especificada de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
ImapMessageInfoCollection messages = client.endListMessages(asyncResult);
~~~