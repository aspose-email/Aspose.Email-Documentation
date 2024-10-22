---
title: "Listando Extensiones del Servidor IMAP"
url: /es/net/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) te permite recuperar las extensiones del servidor que un servidor soporta, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) devuelve los tipos de extensión soportados en forma de un array de cadenas. El siguiente fragmento de código te muestra cómo recuperar las extensiones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}