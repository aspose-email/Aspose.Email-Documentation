---
title: "Leer y Convertir Archivos OST de Outlook"
url: /es/python-net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

Aspose.Email para .NET proporciona una API para leer archivos OST de Microsoft Outlook. Puedes cargar un archivo OST desde el disco o un flujo en una instancia de la clase Aspose.Email.Outlook.Pst.PersonalStorage y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite tamaños de archivo más grandes que los archivos PST.
## **Lectura de Archivos OST**
El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer archivos PST y OST: solo proporciona el nombre de archivo correcto al método PersonalStorage.FromFile(). El siguiente fragmento de código te muestra cómo leer archivos OST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Convertir OST a PST**
{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea con la gratuita [**Aplicación de Conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}
Aspose.Email hace posible convertir un archivo OST a PST con una sola línea de código. De manera similar, se puede crear un archivo OST a partir de un archivo PST utilizando la misma línea de código con el enumerador FileFormat. En la actualidad, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código te muestra cómo convertir OST a PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ConvertingOSTToPST-ConvertingOSTToPST.py" >}}

## **Convertir PST a OST**

La conversión de PST a OST no es compatible con Aspose.Email porque el OST siempre es creado por Outlook al agregar una cuenta y sincronizar con el servidor de correo. La diferencia entre los archivos PST y OST es que el PST está disponible solo localmente. El contenido de OST también está disponible en el servidor de correo electrónico. Por lo tanto, no es necesario convertir PST a OST para uso local. Pero puedes importar PST en una cuenta existente utilizando el asistente de Importación/Exportación en Outlook.

Para realizar otras operaciones con archivos OST, consulta las siguientes páginas:

- Leer archivo PST de Outlook y obtener información sobre carpetas y subcarpetas
- Obtener información de mensajes de un archivo PST de Outlook
- Extraer mensajes de un archivo PST de Outlook y guardarlos en disco o flujo en formato MSG
- Acceder a información de contacto desde un archivo PST de Outlook y guardarla en disco en formato MSG