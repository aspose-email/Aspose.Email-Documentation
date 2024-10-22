---
title: "Trabajando con Contactos en Archivos PST"
url: /es/cpp/working-with-contacts-in-pst-file/
weight: 60
type: docs
---

## **Agregar Contacto a PST**
Con Aspose.Email, puedes agregar un MapiContact a la subcarpeta de Contactos de un archivo PST que hayas creado o cargado. A continuación se presentan los pasos para agregar MapiContact a un PST:

1. Crea un objeto MapiContact.
1. Establece las propiedades de MapiContact utilizando diferentes constructores y métodos.
1. Crea un PST utilizando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código te muestra cómo crear un MapiContact y luego agregarlo a la carpeta de contactos de un archivo PST recién creado.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cpp" >}}
## **Guardar información de contactos desde archivo PST en formato MSG**
Este artículo explica cómo acceder a la información de contacto desde un archivo PST de Outlook y guardar el contacto en el disco en formato MSG. Las clases PersonalStorage y MapiContact se utilizan para obtener y mostrar la información de contacto. Los pasos para obtener la información de contacto son:

1. Carga el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta de Contactos.
1. Obtén el contenido de la carpeta de Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llama al método PersonalStorage.ExtractContactInfo() para obtener la información de contacto en la clase MapiContact. Usa las propiedades de la clase MapiContact para acceder a la información de contacto.
1. Llama al método PersonalStorage.ExtractMessage() para obtener la información de contacto en la clase MapiMessage.
1. Llama al método MapiMessage.Save() para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código te muestra cómo recuperar toda la información de contacto del archivo PST y guardarla en el disco en formato MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AccessContactInformation-AccessContactInformation.cpp" >}}
## **Guardar información de Contactos desde archivo PST en formato VCF**
Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar el contacto en el disco en formato vCard (VCF). Utiliza las clases PersonalStorage y MapiContact para obtener información de contacto del archivo PST. Para obtener la información de contacto:

1. Carga el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta de Contactos.
1. Obtén el contenido de la carpeta de Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llama al método PersonalStorage.ExtractMessage() para obtener la información de contacto en la clase MapiContact.
1. Utiliza diferentes propiedades de la clase MapiContact para acceder a la información de contacto.

El programa a continuación carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden utilizar en cualquier otro programa que pueda cargar el archivo de contacto estándar vCard. Si abres cualquier archivo VCF en Microsoft Outlook, se verá como el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código te muestra cómo exportar contactos de Outlook PST a formato vCard (VCF).

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveContactInformation-SaveContactInformation.cpp" >}}
## **Trabajando con Listas de Distribución**
Es posible crear una lista de distribución utilizando la API de Aspose.Email que es una colección de múltiples contactos. Una lista de distribución se puede guardar en disco en formato MSG de Outlook y se puede ver/manipular abriéndola en MS Outlook.
### **Crear y Guardar una Lista de Distribución**
El siguiente fragmento de código te muestra cómo crear y guardar una lista de distribución.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cpp" >}}
### **Leer una Lista de Distribución desde un PST**
El siguiente fragmento de código te muestra cómo leer una lista de distribución desde un PST.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingDistributionListFromPST-ReadingDistributionListFromPST.cpp" >}}