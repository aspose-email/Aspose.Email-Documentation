---
title: "Listado de extensiones de servidor IMAP"
url: /es/net/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) El método devuelve los tipos de extensión admitidos en forma de una matriz de cadenas. El siguiente fragmento de código muestra cómo recuperar extensiones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}
