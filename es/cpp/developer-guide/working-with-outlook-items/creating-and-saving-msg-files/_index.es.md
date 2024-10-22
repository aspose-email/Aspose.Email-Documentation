---
title: "Creación y Guardado de Archivos MSG de Outlook usando la API de Email en C++"
description: "La API de Analizador de Email en C++ soporta la creación de archivos de mensaje de Outlook MSG con adjuntos, cuerpo RTF y guardar el mensaje en estado de borrador."
url: /es/cpp/creando-y-guardando-archivos-msg/
weight: 10
type: docs
linktitle: "Creación y Guardado de Archivos MSG"
---

## **Creación y Guardado de Archivos MSG**
Aspose.Email soporta la creación de archivos de mensaje de Outlook (MSG). Este artículo explica cómo:

- Crear mensajes MSG.
- Crear mensajes MSG con adjuntos.
- Crear un mensaje MSG con un cuerpo RTF.
- Guardar un mensaje como borrador.
- Trabajar con compresión de cuerpo.

### **Creación y Guardado de Mensajes de Outlook**
La clase MailMessage tiene el método Save() que puede guardar archivos MSG de Outlook en disco o en un stream. Los fragmentos de código a continuación crean una instancia de la clase MailMessage, establecen propiedades como de, para, asunto y cuerpo. El método Save() toma el nombre del archivo como argumento. Además, los Mensajes de Outlook pueden ser creados con un cuerpo RTF comprimido usando las MapiConversionOptions. Para configurar, crea una nueva aplicación de Windows y añade una referencia al dll de Aspose.Email en el proyecto.

1. Crea una nueva instancia de la clase MailMessage y establece las propiedades De, Para, Asunto y Cuerpo.
1. Llama al método FromMailMessage de la clase MailMessage que acepta un objeto del tipo MailMessage. El método FromMailMessage() convierte el MailMessage en un MailMessage (MSG).
1. Llama al método MapiMessage.Save() para guardar el archivo MSG.

Escribe el siguiente código en el evento click del control de botón de la aplicación de Windows.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cpp" >}}

### **Creación de Archivos MSG Con Cuerpo RTF**
También puedes crear archivos de Mensajes de Outlook (MSG) con cuerpos de texto enriquecido (RTF) usando Aspose.Email. El cuerpo RTF soporta el formato de texto. Crea uno estableciendo la propiedad MailMessage.HtmlBody. Cuando conviertes una instancia de MailMessage en una instancia de MailMessage, el cuerpo HTML se convierte en RTF. De esta manera, se preserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un encabezado, formato negrita y subrayado aplicado en el cuerpo HTML. Este formato se mantiene cuando el HTML se convierte en RTF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cpp" >}}

### **Guardando Mensaje en Estado de Borrador**
Los correos electrónicos se guardan como borradores cuando alguien ha comenzado a editarlos pero quiere volver a ellos para completarlos más tarde. Aspose.Email soporta el guardado de mensajes de correo electrónico en estado de borrador configurando una bandera de mensaje. A continuación se muestra un código de ejemplo para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cpp" >}}

### **Implicaciones de la Compresión del Cuerpo**
El método de compresión de cuerpo RTF puede ser utilizado para generar un MSG de tamaño menor. Sin embargo, esto resulta en una velocidad más lenta. Para crear mensajes con velocidad mejorada, establece la bandera en falso. Esta bandera, a su vez, tiene efecto en los PST creados: archivos MSG más pequeños resultan en un PST más pequeño, y archivos MSG grandes devuelven una creación de PST más lenta.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetBodyCompression-SetBodyCompression.cpp" >}}