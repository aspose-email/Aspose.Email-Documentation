---
title: "Trabajar con elementos del calendario en Exchange Server mediante WebDAV"
url: /es/net/working-with-calendar-items-on-exchange-server-using-webdav/
weight: 40
type: docs
---


## **Envío de convocatorias de reunión**
En este artículo se muestra cómo enviar una convocatoria de reunión a varios destinatarios mediante Microsoft Exchange Server y Aspose.Email.

1. Cree una convocatoria de reunión mediante el [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) clase y establece el lugar, la hora y los asistentes.
1. Crea una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) clase y programe la cita usando el [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview) method.
1. Conéctese al servidor Exchange y envíe la convocatoria de reunión mediante el método Send (MailMessage).

En este ejemplo se utiliza el [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) clase, que usa el [WebDAV](https://en.wikipedia.org/wiki/WebDAV) protocolo para conectarse al Exchange Server y se puede usar con cualquier versión de Exchange Server en la que WebDAV esté habilitado, por ejemplo, Exchange 2000, 2003 o 2007. El siguiente fragmento de código muestra cómo enviar la convocatoria de reunión que se indica a continuación.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}
