---
title: "Enviando Solicitudes de Reunión con Exchange Server usando WebDav"
url: /es/java/sending-meeting-requests-with-exchange-server-using-webdav/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

Este artículo muestra cómo enviar una solicitud de reunión a múltiples destinatarios utilizando Microsoft Exchange Server y Aspose.Email. También explica cómo ajustar el código para trabajar con Exchange Web Services.

{{% /alert %}} 
## **Enviar Solicitudes de Reunión usando Web Dav**
Para enviar una solicitud de reunión:

1. Crea una solicitud de reunión utilizando la [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment) clase y establece la ubicación, hora y asistentes.
1. Crea una instancia de la [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) clase y establece la cita utilizando el método [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)).
1. Conéctate al Exchange Server y envía la solicitud de reunión utilizando el método [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)).

Este ejemplo utiliza la [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient) clase, que utiliza el protocolo [WebDAV](http://en.wikipedia.org/wiki/WebDAV) para conectarse al Exchange Server y puede usarse con cualquier versión de Exchange Server en la que WebDAV esté habilitado, por ejemplo, Exchange 2000, 2003 o 2007.

Los fragmentos de código utilizados para enviar la solicitud de reunión se dan a continuación:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}