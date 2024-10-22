---
title: "Leer y Convertir Archivo OST de Outlook"
url: /es/cpp/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

## **Leer y Convertir Archivo OST de Outlook**
Aspose.Email para C++ proporciona una API para leer archivos OST de Microsoft Outlook. Puedes cargar un archivo OST desde el disco o un flujo en una instancia de la clase Aspose.Email.Outlook.Pst.PersonalStorage y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite tamaños de archivo más grandes que los archivos PST.
### **Leyendo Archivos OST**
El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer tanto archivos PST como OST: solo proporciona el nombre de archivo correcto al método PersonalStorage.FromFile(). El siguiente fragmento de código te muestra cómo leer archivos OST.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}
### **Convertir OST a PST**
Aspose.Email hace posible convertir un archivo OST a PST con una sola línea de código. De manera similar, se puede crear un archivo OST a partir de un archivo PST utilizando la misma línea de código con el enumerador FileFormat. En la actualidad, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código te muestra cómo convertir OST a PST.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}
