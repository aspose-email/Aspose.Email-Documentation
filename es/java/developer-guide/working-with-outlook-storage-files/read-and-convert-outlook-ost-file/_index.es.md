---
title: "Lea y convierta el archivo OST de Outlook"
url: /es/java/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email proporciona una API para leer archivos OST de Microsoft Outlook. Puede cargar un archivo OST desde un disco o transmitirlo a una instancia del [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y obtenga información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar los correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite archivos de mayor tamaño que los archivos PST.

## **Lectura de archivos OST**

El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer archivos PST y OST: basta con proporcionar el nombre de archivo correcto al [PersonalStorage.fromFile()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-) método. El siguiente fragmento de código muestra cómo leer los archivos OST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}

## **Conversión de OST a PST**

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea de forma gratuita [**Aplicación de conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}
Aspose.Email permite convertir un archivo OST a PST con una sola línea de código. Del mismo modo, el archivo OST se puede crear a partir de un archivo PST utilizando la misma línea de código que el [FileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformat/) enumerador. En la actualidad, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código muestra cómo convertir OST a PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

Para realizar otras operaciones con archivos OST, consulte las páginas siguientes:

- [Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Obtener información de mensajes de un archivo PST de Outlook](/email/java/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extraiga los mensajes del archivo PST de Outlook y guárdelos en el disco o transmita en formato MSG](/email/java/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Acceda a la información de contacto desde el archivo PST de Outlook y guárdela en el disco en formato MSG](/email/java/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Conversión de PST a OST**

Aspose.Email no admite la conversión de PST a OST porque Outlook siempre crea OST cuando agrega una cuenta y se sincroniza con el servidor de correo.
La diferencia entre los archivos PST y OST es que el PST solo está disponible localmente. El contenido OST también está disponible en el servidor de correo electrónico.
Por lo tanto, no es necesario convertir PST a OST para uso local.
Pero puede importar PST a una cuenta existente utilizando el asistente de importación/exportación de Outlook.
