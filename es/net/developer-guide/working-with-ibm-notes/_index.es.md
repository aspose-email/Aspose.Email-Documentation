---
title: "Trabajando con IBM Notes"
url: /es/net/working-with-ibm-notes/
weight: 130
type: docs
---


## **Acerca de IBM Notes**

IBM Notes es un cliente y IBM Domino es un servidor de una plataforma de software colaborativo cliente-servidor. IBM Notes proporciona características de colaboración como correo electrónico, calendarios, listas de tareas, gestión de contactos, etc. El archivo de base de datos utilizado por IBM Notes se guarda en el formato Notes Storage Facility (NSF).

## **Detectar que un archivo está en formato NSF**

El siguiente ejemplo de código te mostrará cómo reconocer el formato de archivo NSF:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Leer mensajes del archivo de almacenamiento NSF**

{{% alert color="primary" %}}

Nota, la implementación de NSF es bastante limitada.
En general, es posible enfrentar algunos problemas en los siguientes casos:

1. El archivo fue creado por la versión 7 de Notes o superior
  
2. Se utiliza compresión LZ1

{{% /alert %}}

Aspose.Email proporciona la clase [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) para leer archivos de almacenamiento NSF. La clase [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) ofrece el método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) que itera sobre los mensajes en el archivo de almacenamiento NSF. El siguiente código de ejemplo demuestra el uso de la clase [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) y del método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) para leer mensajes del archivo de almacenamiento NSF.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}} 

Ten en cuenta que solo se ha implementado la lectura de mensajes. La lectura de carpetas aún no está soportada debido a la falta de especificación.

{{% /alert %}}