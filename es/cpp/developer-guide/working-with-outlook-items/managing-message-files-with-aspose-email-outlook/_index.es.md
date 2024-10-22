---
title: "Gestión de Archivos de Mensajes de Outlook con la API de Analizador de Correo C++"
description: "La API de la Biblioteca de Analizador de Correo C++ es útil para leer, escribir archivos de plantilla de Outlook OFT, gestionar mensajes firmados digitalmente, configurar categorías de color y acceder a información de recibo de entrega."
url: /es/cpp/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
linktitle: "Gestión de Archivos de Mensajes con Aspose.Email.Outlook"
---

## **Lectura y Escritura de Archivos de Plantilla de Outlook (.OFT)**
Las plantillas de Outlook son muy útiles cuando deseas enviar un mensaje de correo electrónico similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, primero prepara el mensaje en Outlook y guárdalo como una plantilla de Outlook (OFT). Después de eso, cada vez que necesites enviar el mensaje, puedes crearlo desde la plantilla, ahorrando tiempo al escribir el mismo texto en el cuerpo o en la línea de asunto, configurando formato, etc. La clase MailMessage de Aspose.Email se puede usar para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez que la plantilla de Outlook está cargada en una instancia de la clase MailMessage, puedes actualizar el remitente, destinatario, cuerpo, asunto y otras propiedades. Después de actualizar las propiedades:

- Envía el correo electrónico utilizando la clase SmtpClient o
- Guarda el mensaje como MSG y realiza más actualizaciones/validaciones usando Microsoft Outlook.

En los ejemplos de código a continuación, nosotros:

1. Cargamos la plantilla utilizando la clase MailMessage.
1. Actualizamos algunas de las propiedades.
1. Guardamos el mensaje en formato MSG.

El siguiente fragmento de código te muestra cómo cargar el archivo OFT con la API de la Biblioteca de Analizador de Correo C++, actualizar el mensaje y guardarlo en formato MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cpp" >}}

## **Gestión de Mensajes Firmados Digitalmente**
Aspose.Email implementa el algoritmo completo del objeto de correo S/MIME. Esto le da a la API el poder completo para preservar las firmas digitales al convertir mensajes entre formatos.

### **Preservación de la Firma al Convertir de EML a MSG**
Al convertir de EML a MSG, establece el flag preserveSignature en true para preservar una firma. El siguiente fragmento de código te muestra cómo convertir de EML a MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cpp" >}}

### **Conversión de Mensajes S/MIME de MSG a EML**
Aspose.Email preserva la firma digital al convertir de MSG a EML como se muestra en el siguiente fragmento de código.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cpp" >}}

## **Configuración de Categoría de Color para Archivos MSG de Outlook**
Una categoría de color marca un mensaje de correo electrónico por algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de color para diferenciar los correos electrónicos. Para manejar la categoría de color, utiliza el FollowUpManager. Contiene funciones como AddCategory, RemoveCategory, ClearCategories y GetCategories.

- AddCategory toma MapiMessage y la cadena de categoría de color, por ejemplo "Categoría Púrpura" o "Categoría Roja" como argumentos.
- RemoveCategory toma MapiMessage y la cadena de categoría de color que se desea eliminar del mensaje.
- ClearCategories() se usa para eliminar todas las categorías de color del mensaje.
- GetCategories se utiliza para recuperar todas las categorías de color de un mensaje en particular.

El siguiente ejemplo realiza las tareas mencionadas a continuación:

1. Añadir una categoría de color.
1. Añadir otra categoría de color.
1. Recuperar la lista de todas las categorías.
1. Eliminar todas las categorías.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetColorCategories-SetColorCategories.cpp" >}}

## **Accediendo a Información de Seguimiento desde el Archivo MSG**
La API de Aspose.Email proporciona la capacidad de acceder a la información de seguimiento de un mensaje enviado o recibido. Puede recuperar la información de lectura, recibo de entrega y resultados de votación de un archivo de mensaje.

### **Recuperación de Información de Recibo de Lectura y Entrega**
El siguiente fragmento de código te muestra cómo recuperar la información de recibo de lectura y entrega.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cpp" >}}