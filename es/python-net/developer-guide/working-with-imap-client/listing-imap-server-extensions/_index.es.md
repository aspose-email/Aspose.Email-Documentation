---
title: "Listado de Extensiones del Servidor IMAP"
url: /es/python-net/listing-imap-server-extensions/
weight: 40
type: docs
---


## **Listado de Extensiones del Servidor**
El ImapClient de Aspose.Email te permite recuperar las extensiones del servidor que un servidor soporta, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método GetCapabilities() devuelve los tipos de extensiones soportadas en forma de un arreglo de cadenas. El siguiente fragmento de código te muestra cómo recuperar las extensiones.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}