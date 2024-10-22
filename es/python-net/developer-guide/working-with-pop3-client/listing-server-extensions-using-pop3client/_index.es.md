---
title: "Listando extensiones del servidor usando Pop3Client"
url: /es/python-net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---

## **Listando extensiones del servidor usando Pop3Client**
El Pop3Client de Aspose.Email te permite recuperar las extensiones del servidor que un servidor soporta como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método GetCapabilities() devuelve los tipos de extensiones soportadas en forma de un array de cadenas.
### **Recuperando extensiones del servidor**
El siguiente ejemplo de código demuestra cómo recuperar extensiones del servidor usando ImapClient para el servidor de Gmail.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}