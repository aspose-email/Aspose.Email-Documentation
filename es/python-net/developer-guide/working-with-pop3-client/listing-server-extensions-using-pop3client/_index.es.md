---
title: "Listado de extensiones de servidor mediante Pop3Client"
url: /es/python-net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---

## **Listado de extensiones de servidor mediante Pop3Client**
Pop3Client de Aspose.Email le permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método getCapabilities () devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.
### **Recuperación de extensiones de servidor**
En el siguiente ejemplo de código se muestra la recuperación de extensiones de servidor mediante el servidor IMAPClient para Gmail.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}
