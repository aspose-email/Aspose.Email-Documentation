---
title: "Lea y convierta el archivo OST de Outlook"
url: /es/cpp/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

## **Lea y convierta el archivo OST de Outlook**
Aspose.Email para C++ proporciona una API para leer los archivos OST de Microsoft Outlook. Puede cargar un archivo OST desde un disco o una transmisión a una instancia de la clase Aspose.Email.Outlook.pst.PersonalStorage y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. Microsoft Outlook crea un archivo PST para almacenar los correos electrónicos cuando se utilizan servidores de correo POP3 o IMAP para descargar mensajes. Crea un archivo OST cuando Microsoft Exchange es el servidor de correo. OST admite archivos de mayor tamaño que los archivos PST.
### **Lectura de archivos OST**
El proceso para leer un archivo OST con Aspose.Email es exactamente el mismo que para leer un archivo PST. El mismo código puede leer archivos PST y OST: basta con proporcionar el nombre de archivo correcto al método PersonalStorage.fromFile (). El siguiente fragmento de código muestra cómo leer los archivos OST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}
### **Conversión de OST a PST**
Aspose.Email permite convertir un archivo OST a PST con una sola línea de código. Del mismo modo, el archivo OST se puede crear a partir de un archivo PST utilizando la misma línea de código con el enumerador FileFormat. En la actualidad, la API admite la conversión de formatos OST a PST, excepto OST 2013/2016. El siguiente fragmento de código muestra cómo convertir OST a PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}



