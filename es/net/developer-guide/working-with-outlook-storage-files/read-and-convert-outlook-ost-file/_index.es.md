---
title: "Leer y Convertir Archivos OST de Outlook"
url: /es/net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email para .NET proporciona una API para leer archivos OST de Microsoft Outlook. Puedes cargar un archivo OST desde un disco o un flujo a una instancia de la clase [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite tamaños de archivo más grandes que los archivos PST.

## **Lectura de Archivos OST**

El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer tanto archivos PST como OST: solo proporciona el nombre de archivo correcto al método [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/). El siguiente fragmento de código muestra cómo leer archivos OST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

## **Convertir OST a PST**

{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea con la gratuita [**Aplicación de Conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}
Aspose.Email permite convertir un archivo OST a PST con una sola línea de código. De manera similar, el archivo OST puede ser creado a partir de un archivo PST utilizando la misma línea de código con el enumerador [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/). En la actualidad, la API admite la conversión de formatos OST a PST, excepto las versiones 2013/2016/2019/2021 y futuras. El siguiente fragmento de código muestra cómo convertir OST a PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

Para realizar otras operaciones con archivos OST, consulta las siguientes páginas:

- [Leer archivo PST de Outlook y obtener información sobre carpetas y subcarpetas](https://docs.aspose.com/email/es/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Obtener información de mensajes de un archivo PST de Outlook](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extraer mensajes de un archivo PST de Outlook y guardar en disco o flujo en formato MSG](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Acceder a información de contactos desde un archivo PST de Outlook y guardar en disco en formato MSG](https://docs.aspose.com/email/es/net/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Convertir PST a OST**

La conversión de PST a OST no es compatible con Aspose.Email porque el OST siempre es creado por Outlook al añadir una cuenta y sincronizar con el servidor de correo. 
La diferencia entre los archivos PST y OST es que el PST está disponible solo localmente. El contenido de OST también está disponible en el servidor de correo electrónico. 
Por lo tanto, no hay necesidad de convertir PST a OST para uso local. 
Pero puedes importar PST a una cuenta existente utilizando el asistente de Importación/Exportación en Outlook.