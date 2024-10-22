---
title: "Listando Extensiones del Servidor usando Pop3Client"
url: /es/net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) te permite recuperar las extensiones del servidor que un servidor admite, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad particular. El método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) devuelve los tipos de extensión admitidos en forma de un arreglo de cadenas.

## **Recuperando Extensiones del Servidor**

El siguiente ejemplo de código demuestra cómo recuperar las extensiones del servidor usando ImapClient para el servidor de Gmail.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}