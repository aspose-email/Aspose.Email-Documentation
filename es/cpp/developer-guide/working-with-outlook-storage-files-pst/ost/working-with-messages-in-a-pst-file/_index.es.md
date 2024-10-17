---
title: "Trabajando con Mensajes en un Archivo PST"
url: /es/cpp/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---

## **Añadiendo Mensajes a Archivos PST**
Crear un Nuevo Archivo PST y Añadir Subcarpetas mostró cómo crear un archivo PST y añadirle una subcarpeta. Con Aspose.Email puedes añadir mensajes a subcarpetas de un archivo PST que has creado o cargado. Este artículo añade dos mensajes desde el disco a la subcarpeta de Bandeja de Entrada de un PST. Utiliza las clases PersonalStorage y FolderInfo para añadir mensajes a archivos PST. Para añadir mensajes a la carpeta Bandeja de Entrada de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con los contenidos de la carpeta Bandeja de Entrada.
1. Añade mensajes desde el disco a la carpeta Bandeja de Entrada llamando al método FolderInfo.AddMessage(). La clase FolderInfo expone el método AddMessages que permite añadir un gran número de mensajes a la carpeta, reduciendo las operaciones de E/S a disco y mejorando el rendimiento. Un ejemplo completo se puede encontrar a continuación, en Añadiendo Mensajes Masivos.

Los fragmentos de código a continuación muestran cómo añadir mensajes a una subcarpeta PST llamada Bandeja de Entrada.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMessagesToPSTFiles-AddMessagesToPSTFiles.cpp" >}}
### **Guardando Mensajes Directamente de PST a Flujo**
Para guardar mensajes de un archivo PST directamente a un flujo, sin extraer la MsgInfo para los mensajes, utiliza el método SaveMessageToStream(). El siguiente fragmento de código te muestra cómo guardar mensajes directamente de PST a flujo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveMessagesDirectlyFromPSTToStream-SaveMessagesDirectlyFromPSTToStream.cs" >}}
### **Extrayendo un Número n de Mensajes de un Archivo PST**
El siguiente fragmento de código te muestra cómo extraer un número dado de mensajes de un PST. Simplemente proporciona el índice del primer mensaje y el número total de mensajes a extraer.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractNumberOfMessages-ExtractNnumberOfMessages.cpp" >}}
## **Buscar Mensajes y Carpetas en un PST por Criterio**
Los archivos de Almacenamiento Personal (PST) pueden contener una gran cantidad de datos y buscar datos que cumplan con criterios específicos en archivos tan grandes requiere incluir múltiples puntos de verificación en el código para filtrar la información. Con la clase PersonalStorageQueryBuilder, Aspose.Email hace posible buscar registros específicos en un PST basado en un criterio de búsqueda especificado. Se puede buscar en un PST mensajes basados en parámetros de búsqueda como remitente, receptor, asunto, importancia del mensaje, presencia de archivos adjuntos, tamaño del mensaje e incluso ID del mensaje. La PersonalStorageQueryBuilder también se puede utilizar para buscar subcarpetas.
### **Buscando Mensajes y Carpetas en PST**
El siguiente fragmento de código te muestra cómo usar la clase PersonalStorageQueryBuilder para buscar contenidos en un PST basado en diferentes criterios de búsqueda. Por ejemplo, muestra cómo buscar un PST basado en:

- Importancia del mensaje.
- Clase del mensaje.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos, y
- carpetas con un nombre de subcarpeta específico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SearchMessagesAndFoldersInPST-SearchMessagesAndFoldersInPST.cpp" >}}
## **Extraer Archivos Adjuntos Sin Extraer el Mensaje Completo**
La API de Aspose.Email se puede utilizar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. El método ExtractAttachments de IEWSClient se puede utilizar para hacer esto. El siguiente fragmento de código te muestra cómo extraer archivos adjuntos sin extraer el mensaje completo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractAttachmentsFromPSTMessages-ExtractAttachmentsFromPSTMessages.cpp" >}}
## **Añadiendo Archivos a PST**
La funcionalidad clave de Microsoft Outlook es gestionar correos electrónicos, calendarios, tareas, contactos y entradas de diario. Además, también se pueden añadir archivos a una carpeta PST y el PST resultante mantiene un registro de los documentos añadidos. Aspose.Email proporciona la facilidad de añadir archivos a una carpeta de la misma manera que añadir mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código te muestra cómo añadir documentos a una carpeta PST utilizando Aspose.Email.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddFilesToPST-AddFilesToPST.cpp" >}}