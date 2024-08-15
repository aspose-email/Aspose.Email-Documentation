---
title: "Trabajando con Pop3Client de forma asincrónica"
url: /es/java/working-with-pop3client-asynchronously/
weight: 60
type: docs
---

## **Trabajando con Pop3Client de forma asincrónica**

Los mensajes también se pueden recuperar de los buzones de forma asincrónica mediante Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). En este artículo se muestra cómo recuperar mensajes de un buzón de forma asincrónica. También muestra cómo enumerar los mensajes proporcionando criterios de búsqueda mediante [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

### **Recuperación de mensajes de forma asincrónica**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
client.setHost("pop.gmail.com");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.SSLImplicit);
client.setUsername("username");
client.setPassword("password");

try {
    Pop3MessageInfoCollection messages = client.listMessages();
    System.out.println("Total Number of Messages in inbox:" + messages.size());
    IAsyncResult asyncResult = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(asyncResult);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

### **Listar mensajes de forma asincrónica con MailQuery**

The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) La clase se puede usar para especificar criterios de búsqueda para recuperar una lista de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~
