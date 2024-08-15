---
title: "Trabajando con IBM Notes"
url: /es/net/working-with-ibm-notes/
weight: 130
type: docs
---


## **Acerca de IBM Notes**

IBM Notes es un cliente e IBM Domino es un servidor de una plataforma de software colaborativo cliente-servidor. IBM Notes proporciona funciones de colaboración como el correo electrónico, los calendarios, las listas de tareas pendientes, la gestión de contactos, etc. El archivo de base de datos utilizado por IBM Notes se guarda en el formato Notes Storage Facility (NSF).

## **Detectar que un archivo está en formato NSF**

El ejemplo de código siguiente le mostrará cómo reconocer el formato de archivo NSF:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Lea los mensajes del archivo de almacenamiento NSF**

{{% alert color="primary" %}}

Tenga en cuenta que la implementación de NSF es bastante limitada.
En general, es posible enfrentarse a algunos problemas en los siguientes casos:

1. El archivo se creó con la versión 7 y superior de Notes
 
2. Se utiliza la compresión LZ1

{{% /alert %}}

Aspose.Email proporciona la [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) clase para leer archivos de almacenamiento NSF. El [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) la clase proporciona la [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) método que recorre en iteración los mensajes del archivo de almacenamiento NSF. El siguiente código de ejemplo demuestra el uso del [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) clase y el [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) método para leer los mensajes del archivo de almacenamiento NSF. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}}

Tenga en cuenta que solo se implementa la lectura de mensajes. Todavía no se admite la lectura de carpetas debido a la falta de especificaciones.

{{% /alert %}}
