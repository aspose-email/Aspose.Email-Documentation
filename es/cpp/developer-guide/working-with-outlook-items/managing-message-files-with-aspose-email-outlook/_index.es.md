---
title: "Administración de archivos de mensajes de Outlook con la API de analizador de correo electrónico de C++"
description: "La API de biblioteca de analizadores de correo electrónico de C++ es útil para leer, escribir un archivo OFT de plantillas de Outlook, administrar mensajes firmados digitalmente, establecer la categoría de color y acceder a la información del recibo de entrega."
url: /es/cpp/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
linktitle: "Administración de archivos de mensajes con Aspose.Email.Outlook"
---

## **Archivo de plantilla de Outlook para lectura y escritura (.OFT)**
Las plantillas de Outlook son muy útiles cuando quieres enviar un mensaje de correo similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, prepare primero el mensaje en Outlook y guárdelo como plantilla de Outlook (OFT). Después de eso, siempre que necesite enviar el mensaje, puede crearlo a partir de la plantilla, ahorrando tiempo al escribir el mismo texto en el cuerpo o en la línea de asunto, configurar el formato, etc. La clase MailMessage de Aspose.Email se puede usar para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez cargada la plantilla de Outlook en una instancia de la clase MailMessage, puede actualizar el remitente, el destinatario, el cuerpo, el asunto y otras propiedades. Tras actualizar las propiedades:

- Envíe el correo electrónico mediante la clase SmtpClient o
- Guarde el mensaje como MSG y realice más actualizaciones/validaciones con Microsoft Outlook.

En los ejemplos de código que aparecen a continuación, nosotros:

1. Carga la plantilla con la clase MailMessage.
1. Actualice algunas de las propiedades.
1. Guarda el mensaje en formato MSG.

El siguiente fragmento de código muestra cómo cargar el archivo OFT con la API de biblioteca de analizadores de correo electrónico de C++, actualizar el mensaje y guardarlo en formato MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cpp" >}}

## **Administración de mensajes firmados digitalmente**
Aspose.Email implementa el algoritmo completo de objetos de correo electrónico S/MIME. Esto le da a la API el poder total para preservar las firmas digitales mientras convierte los mensajes entre formatos.

### **Preservar la firma al convertir de EML a MSG**
Al convertir de EML a MSG, defina el indicador PreserveSignature en true para conservar la firma. El siguiente fragmento de código muestra cómo convertir de EML a MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cpp" >}}

### **Conversión de mensajes S/MIME de MSG a EML**
Aspose.Email conserva la firma digital al convertir de MSG a EML, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cpp" >}}

## **Configuración de la categoría de color para los archivos MSG de Outlook**
Una categoría de color marca un mensaje de correo electrónico con algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de colores para diferenciar los correos electrónicos. Para gestionar la categoría de color, utilice el FollowupManager. Contiene funciones como addCategory, removeCategory, clearCategories y getCategories.

- addCategory toma como argumentos MAPIMessage y la cadena de categoría de color, por ejemplo, «Categoría púrpura» o «Categoría roja».
- RemoveCategory toma MapiMessage y la cadena de categoría de color que se van a eliminar del mensaje.
- clearCategories () se usa para eliminar todas las categorías de colores del mensaje.
- GetCategories se usa para recuperar todas las categorías de color de un mensaje en particular.

El siguiente ejemplo realiza las tareas que se indican a continuación:

1. Añade una categoría de color.
1. Añade otra categoría de color.
1. Recupera la lista de todas las categorías.
1. Eliminar todas las categorías.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetColorCategories-SetColorCategories.cpp" >}}

## **Acceso a la información de seguimiento desde el archivo MSG**
La API Aspose.Email brinda la capacidad de acceder a la información de seguimiento de un mensaje enviado o recibido. Puede recuperar la información sobre la lectura, la entrega, la lectura, el recibo y los resultados de la votación de un archivo de mensajes.

### **Recuperación de la información de lectura y recibo de entrega**
El siguiente fragmento de código muestra cómo recuperar la información de los recibos de entrega y lectura.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cpp" >}}
