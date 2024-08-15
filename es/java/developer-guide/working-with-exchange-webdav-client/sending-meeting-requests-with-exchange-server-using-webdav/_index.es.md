---
title: "Envío de convocatorias de reunión con Exchange Server mediante WebDAV"
url: /es/java/sending-meeting-requests-with-exchange-server-using-webdav/
weight: 110
type: docs
---

{{% alert color="primary" %}}

En este artículo se muestra cómo enviar una convocatoria de reunión a varios destinatarios mediante Microsoft Exchange Server y Aspose.Email. También explica cómo ajustar el código para que funcione con los servicios web de Exchange.

{{% /alert %}}
## **Enviar convocatorias de reunión mediante Web Dav**
Para enviar una convocatoria de reunión:

1. Cree una convocatoria de reunión mediante el [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment) clase y establece el lugar, la hora y los asistentes.
1. Crea una instancia del [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) clase y programe la cita usando el [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)) method.
1. Conéctese al servidor Exchange y envíe la convocatoria de reunión mediante [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)) method.

En este ejemplo se utiliza el [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient) clase, que usa el [WebDAV](http://en.wikipedia.org/wiki/WebDAV) protocolo para conectarse al Exchange Server y se puede usar con cualquier versión de Exchange Server en la que WebDAV esté habilitado, por ejemplo, Exchange 2000, 2003 o 2007.

Los fragmentos de código utilizados para enviar la convocatoria de reunión se muestran a continuación:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}
