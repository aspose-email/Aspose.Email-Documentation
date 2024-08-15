---
title: "Lea y convierta el archivo OST de Outlook"
url: /es/python-net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email para.NET proporciona una API para leer archivos OST de Microsoft Outlook. Puede cargar un archivo OST desde un disco o una transmisión a una instancia de la clase Aspose.Email.Outlook.pst.PersonalStorage y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar los correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite archivos de mayor tamaño que los archivos PST.
## **Lectura de archivos OST**
El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer archivos PST y OST: basta con proporcionar el nombre de archivo correcto al método PersonalStorage.fromFile (). El siguiente fragmento de código muestra cómo leer los archivos OST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Conversión de OST a PST**
{{% alert %}}
**¡Pruébalo!**

Convierte correos electrónicos y archivos de mensajes en línea de forma gratuita [**Aplicación de conversión Aspose.Email**](https://products.aspose.app/email/es/Conversion).
{{% /alert %}}
Aspose.Email permite convertir un archivo OST a PST con una sola línea de código. Del mismo modo, el archivo OST se puede crear a partir de un archivo PST utilizando la misma línea de código con el enumerador FileFormat. En la actualidad, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código muestra cómo convertir OST a PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ConvertingOSTToPST-ConvertingOSTToPST.py" >}}

## **Convertir PST a OST**

Aspose.Email no admite la conversión de PST a OST porque Outlook siempre crea OST cuando agrega una cuenta y se sincroniza con el servidor de correo. La diferencia entre los archivos PST y OST es que el PST solo está disponible localmente. El contenido OST también está disponible en el servidor de correo electrónico. Por lo tanto, no es necesario convertir PST a OST para uso local. Pero puede importar PST a una cuenta existente utilizando el asistente de importación/exportación de Outlook.

Para realizar otras operaciones con archivos OST, consulte las páginas siguientes:

- Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas
- Obtener información de mensajes de un archivo PST de Outlook
- Extraiga los mensajes del archivo PST de Outlook y guárdelos en el disco o transmita en formato MSG
- Acceda a la información de contacto desde el archivo PST de Outlook y guárdela en el disco en formato MSG
