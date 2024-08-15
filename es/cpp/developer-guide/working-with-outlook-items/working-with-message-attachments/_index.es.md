---
title: "Trabajar con archivos adjuntos de mensajes de Outlook mediante la API de analizador de correo electrónico de C++"
description: "Puede administrar los archivos adjuntos de los mensajes de Outlook con la biblioteca analizadora de correo electrónico de C++, guardarlos y eliminarlos e incrustar los mensajes como archivos adjuntos."
url: /es/cpp/working-with-message-attachments/
weight: 70
type: docs
linktitle: "Trabajar con archivos adjuntos de mensajes"
---

## **Administración de archivos adjuntos con Aspose Outlook**
Cómo crear y guardar archivos de mensajes de Outlook (MSG) se explicó cómo crear y guardar mensajes y cómo crear archivos MSG con archivos adjuntos. En este artículo se explica cómo administrar los archivos adjuntos de Microsoft Outlook con Aspose.Email. Se accede a los archivos adjuntos de un archivo de mensajes y se guardan en el disco mediante la propiedad Attachments de la clase MapiMessage. La propiedad Attachments es una colección de tipo MAPIAttachmentCollection.

### **Guardar archivos adjuntos del archivo de mensajes de Outlook (MSG)**
Para guardar los archivos adjuntos de un archivo MSG:

1. Recorra la colección MapiAttachmentCollection y obtenga los archivos adjuntos individuales.
1. Para guardar los archivos adjuntos, llame al método Save () de la clase MapiAttachment.

El siguiente fragmento de código muestra cómo guardar los archivos adjuntos en el disco local.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Eliminar archivos adjuntos**
La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar los archivos adjuntos de los archivos de mensajes de Microsoft Outlook (.msg):

- Llama al método removeAttachments (). Toma la ruta del archivo de mensajes como parámetro. Se implementa como un método estático público, por lo que no es necesario crear una instancia del objeto.

El siguiente fragmento de código muestra cómo eliminar los archivos adjuntos mediante la biblioteca de analizadores de correo electrónico de C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

También puedes llamar al método estático destoryAttachment () de la clase MapiMessage. Funciona más rápido que removeAttachment (), porque el método removeAttachment () analiza el archivo de mensajes.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Agregar archivos adjuntos de MSG**
Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en archivos adjuntos, ya sea como mensajes normales o incrustados. La colección MAPIAttachmentCollection proporciona elementos sobrecargados del método Add para crear mensajes de Outlook con ambos tipos de archivos adjuntos.

### **Incrustar mensaje como archivo adjunto**
El siguiente fragmento de código muestra cómo hacer que los archivos MSG de Outlook incrustados en un archivo MSG contengan un PR_ATTACH_METHOD cuyo valor es igual a 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}
