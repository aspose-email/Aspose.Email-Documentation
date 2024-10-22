---
title: "Cargar, guardar y convertir diferentes formatos de mensajes de correo electrónico en C++"
description: "Con la biblioteca de análisis de correo electrónico de C++, puedes cargar, guardar, exportar y convertir diferentes formatos de mensajes de correo electrónico, por ejemplo, EML, MSG, MHTML."
url: /es/cpp/loading-and-saving-message/
weight: 30
type: docs
linktitle: "Cargar y guardar mensajes"
---

## **Cargando un Mensaje con Opciones de Carga**
El siguiente fragmento de código te muestra cómo cargar un mensaje con opciones de carga.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Guardando y Convirtiendo Mensajes**
Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta característica, el código en este artículo carga tres tipos de mensajes desde el disco y los guarda de nuevo en otros formatos. La clase base SaveOptions y las clases EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions para configuraciones adicionales al guardar MailMessage se pueden utilizar para guardar mensajes en otros formatos. El artículo muestra cómo usar estas clases para guardar un correo electrónico de muestra como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
### **Cargando EML y Guardando como EML**
El siguiente fragmento de código te muestra cómo cargar un mensaje EML y guardarlo en el disco en el mismo formato.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Cargando EML y Guardando como EML Preservando los Limites Originales**
El siguiente fragmento de código te muestra cómo cargar EML y guardarlo como EML preservando los límites originales.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Guardando como EML Preservando los Archivos Adjuntos TNEF**
El siguiente fragmento de código te muestra cómo guardar como EML preservando los archivos adjuntos TNEF.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Cargando EML, Guardando como MSG**
El siguiente fragmento de código te muestra cómo cargar un mensaje EML y convertirlo a MSG utilizando la opción adecuada de SaveOptions.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Guardando MailMessage como MHTML**
Diferentes opciones de MHTML se pueden utilizar para obtener los resultados deseados. El siguiente fragmento de código te muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) y convertirlo a MHTML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Exportando Correo Electrónico a MHT con Zona Horaria Personalizada**
La clase MailMessage proporciona la propiedad TimeZoneOffset para establecer la zona horaria personalizada al exportar a MHT. El siguiente fragmento de código te muestra cómo exportar un correo electrónico a MHT con zona horaria personalizada.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Exportando Correo Electrónico a EML**
El siguiente fragmento de código te muestra cómo exportar correo electrónico a eml.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}

