---
title: "Obtener mensajes de un buzón compartido"
url: /es/net/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---


Aspose.Email admite el acceso a mensajes desde el buzón compartido. Para lograr esto, te conectas a tu buzón principal utilizando la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Para acceder a los mensajes del buzón compartido, pasas el buzón compartido como un parámetro de cadena al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) o [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

El siguiente ejemplo de código muestra cómo acceder a los mensajes del buzón compartido utilizando el método [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-GetMessagesFromSharedMailbox-1.cs" >}}