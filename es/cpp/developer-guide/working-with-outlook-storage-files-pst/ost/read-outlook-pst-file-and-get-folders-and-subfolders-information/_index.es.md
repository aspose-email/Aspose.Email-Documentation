---
title: "Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas"
url: /es/cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

## **Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas**
Aspose.Email para C++ proporciona una API para leer archivos PST de Microsoft Outlook. Puede cargar un archivo PST desde un disco o una transmisión a una instancia de la clase PersonalStorage y obtener la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes. La API también ofrece la capacidad de incluir carpetas de búsqueda al buscar los mensajes de las carpetas PST.
### **Carga de un archivo PST**
Se puede cargar un archivo PST de Outlook en una instancia de la clase PersonalStorage. El siguiente fragmento de código muestra cómo cargar el archivo PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Visualización de la información de carpetas**
Tras cargar el archivo PST en la clase PersonalStorage, puede obtener la información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes. El siguiente fragmento de código muestra cómo mostrar el nombre del archivo PST, las carpetas y el número de mensajes de las carpetas.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Recuperar la información de la carpeta principal de MessageInfo**
En el siguiente fragmento de código, se muestra cómo recuperar la información de la carpeta principal de MessageInfo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}
