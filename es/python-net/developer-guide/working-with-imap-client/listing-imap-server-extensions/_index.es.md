---
title: "Listado de extensiones de servidor IMAP"
url: /es/python-net/listing-imap-server-extensions/
weight: 40
type: docs
---


## **Listado de extensiones de servidor**
ImapClient de Aspose.Email le permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método getCapabilities () devuelve los tipos de extensión admitidos en forma de una matriz de cadenas. El siguiente fragmento de código muestra cómo recuperar extensiones.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}
