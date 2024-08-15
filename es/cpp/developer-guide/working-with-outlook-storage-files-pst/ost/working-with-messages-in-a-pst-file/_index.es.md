---
title: "Trabajar con mensajes en un archivo PST"
url: /es/cpp/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---

## **Agregar mensajes a archivos PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir mensajes a las subcarpetas de un archivo PST que hayas creado o cargado. Este artículo agrega dos mensajes del disco a la subcarpeta Bandeja de entrada de un PST. Utilice las clases PersonalStorage y FolderInfo para agregar mensajes a los archivos PST. Para agregar mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la carpeta Inbox.
1. Agregue mensajes del disco a la carpeta Bandeja de entrada llamando al método FolderInfo.addMessage (). La clase FolderInfo expone el método addMessages, que permite agregar una gran cantidad de mensajes a la carpeta, lo que reduce las operaciones de E/S en el disco y mejora el rendimiento. Puedes encontrar un ejemplo completo más abajo, en Añadir mensajes masivos.

Los fragmentos de código que aparecen a continuación muestran cómo agregar mensajes a una subcarpeta de PST llamada Bandeja de entrada.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMessagesToPSTFiles-AddMessagesToPSTFiles.cpp" >}}
### **Guardar mensajes directamente desde PST para transmitirlos**
Para guardar los mensajes de un archivo PST directamente para transmitirlos, sin extraer el msgInfo de los mensajes, utilice el método saveMessageToStream (). El siguiente fragmento de código muestra cómo guardar mensajes directamente desde PST para transmitirlos.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveMessagesDirectlyFromPSTToStream-SaveMessagesDirectlyFromPSTToStream.cs" >}}
### **Extraer un número n de mensajes de un archivo PST**
El siguiente fragmento de código muestra cómo extraer un número determinado de mensajes de un PST. Simplemente proporcione el índice del primer mensaje y el número total de mensajes que se van a extraer.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractNumberOfMessages-ExtractNnumberOfMessages.cpp" >}}
## **Buscar mensajes y carpetas en un PST por criterio**
Los archivos de almacenamiento personal (PST) pueden contener una gran cantidad de datos y la búsqueda de datos que cumplan un criterio específico en archivos tan grandes debe incluir varios puntos de control en el código para filtrar la información. Con la clase PersonalStorageQueryBuilder, Aspose.Email permite buscar registros específicos en un PST en función de un criterio de búsqueda específico. Se pueden buscar mensajes en un PST en función de parámetros de búsqueda como el remitente, el destinatario, el asunto, la importancia del mensaje, la presencia de archivos adjuntos, el tamaño del mensaje e incluso el identificador del mensaje. El PersonalStorageQueryBuilder también se puede usar para buscar subcarpetas.
### **Búsqueda de mensajes y carpetas en PST**
El siguiente fragmento de código muestra cómo usar la clase PersonalStorageQueryBuilder para buscar contenido en un PST según distintos criterios de búsqueda. Por ejemplo, muestra la búsqueda de un PST en función de:

- Importancia del mensaje.
- Clase de mensajes.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos y
- carpetas con un nombre de subcarpeta específico.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SearchMessagesAndFoldersInPST-SearchMessagesAndFoldersInPST.cpp" >}}
## **Extraer archivos adjuntos sin extraer el mensaje completo**
La API Aspose.Email se puede usar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. Para ello, se puede utilizar el método ExtractAttachments de IEWSClient. El siguiente fragmento de código muestra cómo extraer los archivos adjuntos sin extraer el mensaje completo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractAttachmentsFromPSTMessages-ExtractAttachmentsFromPSTMessages.cpp" >}}
## **Agregar archivos a PST**
La funcionalidad clave de Microsoft Outlook es administrar correos electrónicos, calendarios, tareas, contactos y entradas del diario. Además, los archivos también se pueden agregar a una carpeta PST y el PST resultante guarda un registro de los documentos agregados. Aspose.Email ofrece la posibilidad de agregar archivos a una carpeta de la misma manera, además de agregar mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST mediante Aspose.Email.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddFilesToPST-AddFilesToPST.cpp" >}}
