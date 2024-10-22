---
title: "Leer y Convertir Archivos OST de Outlook"
url: /es/java/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

Aspose.Email proporciona una API para leer archivos OST de Microsoft Outlook. Puedes cargar un archivo OST desde el disco o transmitirlo en una instancia de la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite tamaños de archivo más grandes que los archivos PST.

## **Lectura de Archivos OST**

El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer tanto archivos PST como OST: simplemente proporciona el nombre de archivo correcto al método [PersonalStorage.fromFile()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-). El siguiente fragmento de código te muestra cómo leer archivos OST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}

## **Convertir OST a PST**

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea con la gratuita [**Aplicación de Conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}
Aspose.Email hace posible convertir un archivo OST a PST con una sola línea de código. De manera similar, el archivo OST se puede crear a partir de un archivo PST utilizando la misma línea de código con el enumerador [FileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformat/). Actualmente, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código te muestra cómo convertir OST a PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

Para realizar otras operaciones con archivos OST, consulta las siguientes páginas:

- [Leer Archivo PST de Outlook y Obtener Información de Carpetas y Subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Obtener Información de Mensajes de un Archivo PST de Outlook](/email/java/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extraer Mensajes de un Archivo PST de Outlook y Guardar en Disco o Transmitir en Formato MSG](/email/java/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Acceder a la Información de Contactos de un Archivo PST de Outlook y Guardar en Disco en Formato MSG](/email/java/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Convertir PST a OST**

La conversión de PST a OST no es compatible con Aspose.Email porque OST siempre es creado por Outlook al agregar una cuenta y sincronizarse con el servidor de correo. La diferencia entre los archivos PST y OST es que el PST está disponible solo localmente. El contenido de OST también está disponible en el servidor de correo electrónico. Por lo tanto, no hay necesidad de convertir PST a OST para uso local. Pero puedes importar PST en una cuenta existente utilizando el asistente de Importación/Exportación en Outlook.