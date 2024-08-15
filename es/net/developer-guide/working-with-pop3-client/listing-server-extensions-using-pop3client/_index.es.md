---
title: "Listado de extensiones de servidor mediante Pop3Client"
url: /es/net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) El método devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.

## **Recuperación de extensiones de servidor**

En el siguiente ejemplo de código se muestra la recuperación de extensiones de servidor mediante el servidor IMAPClient para Gmail.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}
