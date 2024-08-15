---
title: "Carga, almacenamiento y conversión de diferentes formatos de mensajes de correo electrónico en C++"
description: "Con la biblioteca de analizadores de correo electrónico de C++, puede cargar, guardar, exportar y convertir diferentes formatos de mensajes de correo electrónico, por ejemplo, EML, MSG, MHTML."
url: /es/cpp/loading-and-saving-message/
weight: 30
type: docs
linktitle: "Cargar y guardar el mensaje"
---

## **Carga de un mensaje con opciones de carga**
El siguiente fragmento de código muestra cómo cargar un mensaje con opciones de carga.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Guardar y convertir mensajes**
Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, el código de este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base SaveOptions y las clases EMLSaveOptions, MsgSaveOptions, MhtSaveOptions, HtSaveOptions y HTMLSaveOptions, que proporcionan ajustes adicionales al guardar MailMessage, se pueden usar para guardar mensajes en otros formatos. En el artículo se muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Mensaje de Outlook.
- Formato MHTML.
- Formato HTML.
### **Cargar EML y guardar como EML**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco con el mismo formato.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Cargar EML y guardar como EML conservando los límites originales**
El siguiente fragmento de código muestra cómo cargar EML y guardar como EML conservando los límites originales.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Guardar como EML Preservar los archivos adjuntos TNEF**
El siguiente fragmento de código muestra cómo guardar como EML conservando los archivos adjuntos TNEF.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Cargar EML, guardar en MSG**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo en MSG mediante la opción adecuada de SaveOptions.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Guardar MailMessage como MHTML**
Se pueden usar diferentes opciones de MHTML para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) y lo convierte a MHTML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Exportación de correo electrónico a MHT con zona horaria personalizada**
La clase MailMessage proporciona la propiedad TimeZoneOffset para establecer una zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar un correo electrónico a MHT con una zona horaria personalizada.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Exportación de correo electrónico a EML**
El siguiente fragmento de código muestra cómo exportar el correo electrónico a eml.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}




