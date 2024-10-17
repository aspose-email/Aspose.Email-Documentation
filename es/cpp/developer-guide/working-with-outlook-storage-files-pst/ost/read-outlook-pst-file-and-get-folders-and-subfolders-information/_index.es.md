---
title: "Leer archivo PST de Outlook y obtener información de carpetas y subcarpetas"
url: /es/cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

## **Leer archivo PST de Outlook y obtener información de carpetas y subcarpetas**
Aspose.Email para C++ proporciona una API para leer archivos PST de Microsoft Outlook. Puedes cargar un archivo PST desde el disco o transmitirlo a una instancia de la clase PersonalStorage y obtener información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. La API también proporciona la capacidad de incluir carpetas de búsqueda mientras se realiza la búsqueda de mensajes en las carpetas PST.
### **Cargando un archivo PST**
Un archivo PST de Outlook puede cargarse en una instancia de la clase PersonalStorage. El siguiente fragmento de código muestra cómo cargar el archivo PST.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Mostrando información de carpetas**
Después de cargar el archivo PST en la clase PersonalStorage, puedes obtener información sobre el nombre de visualización del archivo, la carpeta raíz, subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes en las carpetas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Recuperando información de la carpeta padre desde MessageInfo**
El siguiente fragmento de código muestra cómo recuperar información de la carpeta padre desde MessageInfo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}