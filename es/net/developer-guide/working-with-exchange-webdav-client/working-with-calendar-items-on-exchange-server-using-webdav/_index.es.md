---
title: "Trabajando con Elementos de Calendario en Exchange Server usando WebDav"
url: /es/net/working-with-calendar-items-on-exchange-server-using-webdav/
weight: 40
type: docs
---

## **Enviando Solicitudes de Reunión**
Este artículo muestra cómo enviar una solicitud de reunión a múltiples destinatarios utilizando Microsoft Exchange Server y Aspose.Email.

1. Crea una solicitud de reunión utilizando la clase [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) y establece la ubicación, hora y asistentes.
1. Crea una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) y establece la cita utilizando el método [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview).
1. Conéctate al Exchange Server y envía la solicitud de reunión utilizando el método Send(MailMessage).

Este ejemplo utiliza la clase [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient), que utiliza el protocolo [WebDAV](https://en.wikipedia.org/wiki/WebDAV) para conectarse al Exchange Server y puede ser utilizada con cualquier versión de Exchange Server en la que WebDAV esté habilitado, por ejemplo, Exchange 2000, 2003 o 2007. El siguiente fragmento de código te muestra cómo enviar la solicitud de reunión a continuación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}