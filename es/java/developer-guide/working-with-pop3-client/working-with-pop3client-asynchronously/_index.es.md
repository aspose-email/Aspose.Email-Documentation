---
title: "Trabajando con Pop3Client Asincrónicamente"
url: /es/java/trabajando-con-pop3client-asincronicamente/
weight: 60
type: docs
---

## **Trabajando con Pop3Client Asincrónicamente**

Los mensajes también se pueden recuperar de los buzones de correo de forma asincrónica utilizando el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) de Aspose.Email. Este artículo muestra cómo recuperar mensajes de un buzón de correo de forma asincrónica. También muestra cómo listar mensajes proporcionando criterios de búsqueda utilizando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

### **Recuperando Mensajes Asincrónicamente**

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
client.setHost("pop.gmail.com");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.SSLImplicit);
client.setUsername("username");
client.setPassword("password");

try {
    Pop3MessageInfoCollection messages = client.listMessages();
    System.out.println("Número total de mensajes en la bandeja de entrada:" + messages.size());
    IAsyncResult asyncResult = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(asyncResult);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

### **Listar Mensajes Asincrónicamente con MailQuery**

La clase [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) se puede utilizar para especificar criterios de búsqueda para recuperar una lista de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Asunto");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~