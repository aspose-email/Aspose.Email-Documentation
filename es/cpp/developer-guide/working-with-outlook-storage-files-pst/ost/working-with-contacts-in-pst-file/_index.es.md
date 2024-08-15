---
title: "Trabajar con contactos en un archivo PST"
url: /es/cpp/working-with-contacts-in-pst-file/
weight: 60
type: docs
---

## **Agregar un contacto a PST**
Con Aspose.Email puede agregar un MapiContact a la subcarpeta Contactos de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiContact a un PST:

1. Cree un objeto MapiContact.
1. Establezca las propiedades de MapiContact con diferentes constructores y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiContact y, a continuación, añadirlo a la carpeta de contactos de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cpp" >}}
## **Guarde la información de contactos del archivo PST en formato MSG**
En este artículo se explica cómo acceder a la información de contacto desde un archivo PST de Outlook y guardar el contacto en el disco en formato MSG. Las clases PersonalStorage y MapiContact para obtener y mostrar la información de contacto. Los pasos para obtener la información de contacto son:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al método PersonalStorage.extractContactInfo () para obtener la información de contacto de la clase MAPIContact. Utilice las propiedades de la clase MAPIContact para acceder a la información de contacto
1. Llame al método PersonalStorage.extractMessage () para obtener la información de contacto de la clase MAPIMessage.
1. Llame al método mapiMessage.save () para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código muestra cómo recuperar toda la información de contacto del archivo PST y guardarla en el disco en formato MSG.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AccessContactInformation-AccessContactInformation.cpp" >}}
## **Guarde la información de contactos del archivo PST en formato VCF**
Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar el contacto en un disco en formato vCard (VCF). Utilice las clases PersonalStorage y MapiContact para obtener la información de contacto del archivo PST. Para obtener la información de contacto:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al método PersonalStorage.extractMessage () para obtener la información de contacto de la clase MAPIContact.
1. Utilice las diferentes propiedades de la clase MapiContact para acceder a la información de contacto.

El siguiente programa carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de contactos vCard estándar. Si abres cualquier archivo VCF en Microsoft Outlook, tendrá el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar contactos del formato PST de Outlook al formato vCard (VCF).



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveContactInformation-SaveContactInformation.cpp" >}}
## **Trabajando con listas de distribución**
Es posible crear una lista de distribución utilizando la API Aspose.Email que es una colección de varios contactos. Una lista de distribución se puede guardar en un disco en formato MSG de Outlook y se puede ver o manipular abriéndola en MS Outlook.
### **Creación y almacenamiento de una lista de distribución**
El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cpp" >}}
### **Lectura de una lista de distribución desde un PST**
El siguiente fragmento de código muestra cómo leer una lista de distribución desde un PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingDistributionListFromPST-ReadingDistributionListFromPST.cpp" >}}
