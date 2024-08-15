---
title: "Creación y almacenamiento de archivos MSG de Outlook con la API de correo electrónico de C++"
description: "La API de análisis de correo electrónico de C++ admite la creación de archivos MSG de mensajes de Outlook con archivos adjuntos, cuerpo RTF y guarda el mensaje en estado de borrador."
url: /es/cpp/creating-and-saving-msg-files/
weight: 10
type: docs
linktitle: "Crear y guardar archivos MSG"
---

## **Creación y almacenamiento de archivos MSG**
Aspose.Email admite la creación de archivos de mensajes de Outlook (MSG). En este artículo se explica cómo:

- Crea mensajes MSG.
- Crea mensajes MSG con archivos adjuntos.
- Crea un mensaje MSG con un cuerpo RTF.
- Guarda un mensaje como borrador.
- Trabaja con compresión corporal.

### **Creación y almacenamiento de mensajes de Outlook**
La clase MailMessage tiene el método Save () que puede guardar los archivos MSG de Outlook en un disco o en una transmisión. Los fragmentos de código que aparecen a continuación crean una instancia de la clase MailMessage y establecen propiedades como desde, para, asunto y cuerpo. El método Save () toma el nombre del archivo como argumento. Además, los mensajes de Outlook se pueden crear con un cuerpo RTF comprimido mediante las opciones de mapiConversionOptions. Para configurarlo, cree una nueva aplicación de Windows y añada una referencia al archivo dll Aspose.Email en el proyecto.

1. Cree una nueva instancia de la clase MailMessage y defina las propiedades From, To, Subject y Body.
1. Llame al método FromMailMessage de la clase MailMessage, que acepta objetos del tipo MailMessage. El método fromMailMessage () convierte el MailMessage en un MailMessage (MSG).
1. Llame al método mapiMessage.save () para guardar el archivo MSG.

Escriba el siguiente código en el evento de clic del botón de control de la aplicación Windows.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cpp" >}}

### **Creación de archivos MSG con RTF Body**
También puede crear archivos de mensajes de Outlook (MSG) con cuerpos de texto enriquecido (RTF) con Aspose.Email. El cuerpo RTF admite el formato de texto. Cree uno estableciendo la propiedad MailMessage.htmlBody. Al convertir una instancia de MailMessage en una instancia de MailMessage, el cuerpo HTML se convierte en RTF. De esta forma, se conserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un formato de encabezado, negrita y subrayado aplicado en el cuerpo del HTML. Este formato se conserva cuando el HTML se convierte a RTF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cpp" >}}

### **Guardar el mensaje en estado de borrador**
Los correos electrónicos se guardan como borradores cuando alguien ha empezado a editarlos pero quiere volver a ellos para completarlos más tarde. Aspose.Email permite guardar un mensaje de correo electrónico en estado de borrador mediante la configuración de una marca de mensaje. A continuación se muestra un ejemplo de código para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cpp" >}}

### **Implicaciones de la compresión corporal**
El método de compresión corporal RTF se puede utilizar para generar un MSG de menor tamaño. Sin embargo, esto resulta en una velocidad más lenta. Para crear mensajes con una velocidad mejorada, defina la marca como falsa. Este indicador, a su vez, afecta a los archivos PST creados: los archivos MSG más pequeños dan como resultado un PST más pequeño, y los archivos MSG grandes generan una creación de PST más lenta.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetBodyCompression-SetBodyCompression.cpp" >}}

