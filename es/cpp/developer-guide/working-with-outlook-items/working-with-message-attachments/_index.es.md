---
title: "Trabajando con Adjunto de Mensajes de Outlook usando la API de C++ Email Parser"
description: "Puedes gestionar los adjuntos de mensajes de Outlook con la Biblioteca C++ Email Parser, guardarlos y eliminarlos, y adjuntar mensajes como un archivo adjunto."
url: /es/cpp/working-with-message-attachments/
weight: 70
type: docs
linktitle: "Trabajando con Adjuntos de Mensajes"
---

## **Gestión de Adjuntos con Aspose Outlook**
Crear y guardar archivos de mensajes de Outlook (MSG) explicó cómo crear y guardar mensajes, y cómo crear archivos MSG con adjuntos. Este artículo explica cómo gestionar adjuntos de Microsoft Outlook con Aspose.Email. Los adjuntos de un archivo de mensaje se acceden y guardan en el disco utilizando la propiedad Attachments de la clase MapiMessage. La propiedad Attachments es una colección del tipo de la clase MapiAttachmentCollection.

### **Guardar Adjuntos de un Archivo de Mensaje de Outlook (MSG)**
Para guardar adjuntos de un archivo MSG:

1. Itera a través de la colección MapiAttachmentCollection y obtén los adjuntos individuales.
1. Para guardar los adjuntos, llama al método Save() de la clase MapiAttachment.

El siguiente fragmento de código muestra cómo guardar adjuntos en el disco local.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Eliminar Adjuntos**
La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar adjuntos de archivos de Mensaje de Microsoft Outlook (.msg):

- Llama al método RemoveAttachments(). Toma la ruta del archivo de mensaje como parámetro. Está implementado como un método estático público, por lo que no necesitas instanciar el objeto.

El siguiente fragmento de código muestra cómo eliminar adjuntos utilizando la Biblioteca C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

También puedes llamar al método estático DestoryAttachment() de la clase MapiMessage. Funciona más rápido que RemoveAttachment(), porque el método RemoveAttachment() analiza el archivo de mensaje.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Agregar Adjuntos MSG**
Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en adjuntos ya sea como mensajes regulares o incrustados. La MapiAttachmentCollection proporciona miembros sobrecargados del método Add para crear mensajes de Outlook con ambos tipos de adjuntos.

### **Incrustando Mensaje como Adjunto**
El siguiente fragmento de código muestra cómo los archivos MSG de Outlook incrustados en un archivo MSG contienen un PR_ATTACH_METHOD cuyo valor es 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}