---
title: "Trabajando con Contactos en Archivo PST"
url: /es/java/working-with-contacts-in-pst-file/
weight: 40
type: docs
---

## **Leyendo Múltiples Contactos en Formato VCard**

El siguiente ejemplo de código demuestra cómo leer un archivo VCF, verificar si contiene múltiples contactos, y si es así, cargar los contactos del archivo en una lista de objetos VCardContact. El código utiliza los siguientes métodos:

- [isMultiContacts(InputStream stream)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#isMultiContacts-java.io.InputStream-) - Verifica si la fuente de flujo contiene múltiples contactos.
- [loadAsMultiple(String filePath, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.lang.String-java.nio.charset.Charset-) - Carga la lista de contactos desde un archivo de múltiples contactos.
- [loadAsMultiple(InputStream stream, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.io.InputStream-java.nio.charset.Charset-) - Carga la lista de contactos desde un flujo de múltiples contactos.

```java
try (InputStream stream = new FileInputStream("test.vcf")) {
    if (VCardContact.isMultiContacts(stream)) {
        List<VCardContact> contacts = VCardContact.loadAsMultiple(stream, Charset.forName("utf-8"));
    }
}
```

## **Agregando Contacto a PST**

[Crear Nuevo PST, Agregar Subcarpetas y Mensajes](java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) a la subcarpeta de Contactos de un archivo PST que hayas creado o cargado. A continuación se detallan los pasos para agregar un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) a un PST:

1. Crear un objeto [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
2. Establecer las propiedades del [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) utilizando diferentes constructores y métodos.
3. Crear un PST usando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
4. Crear una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

El fragmento de código a continuación muestra cómo crear un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) y luego agregarlo a la carpeta de Contactos de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}

## **Guardar información de contactos desde archivo PST en formato MSG**

Este artículo muestra cómo acceder a la información de contactos desde un archivo PST de Microsoft Outlook y guardar los contactos en el disco en formato MSG. Para ello, utiliza las clases [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) y [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para obtener y mostrar la información de contacto.

Para obtener la información de un contacto:

1. Cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
2. Navegar por la carpeta de Contactos.
3. Obtener el contenido de la carpeta de Contactos para obtener la colección de mensajes.
4. Recorrer la colección de mensajes.
5. Llamar al método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) y luego al método [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMapiMessageItem--) para obtener la información de contacto en la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
6. Usar las propiedades de [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para acceder a la información de contacto.
7. Llamar al método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obtener la información de contacto en la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
8. Llamar al método [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para guardar el contacto en el disco en formato MSG.

A continuación se presenta un código de muestra que recupera toda la información de los contactos del archivo PST y la guarda en el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}

## **Guardar Información de Contactos desde Outlook PST en Disco en formato vCard**

Este artículo muestra cómo acceder a la información de contactos desde un archivo PST de Microsoft Outlook y guardar el contacto en disco en formato vCard (VCF). Utiliza las clases [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) y [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para obtener la información de contacto.

A continuación se detallan los pasos para obtener la información de los contactos:

1. Cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
2. Navegar por la carpeta de Contactos.
3. Obtener el contenido de la carpeta de Contactos para obtener la colección de mensajes.
4. Recorrer la colección de mensajes.
5. Llamar al método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obtener la información de contacto en la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
6. Usar las propiedades de la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para acceder a la información de contacto.

El programa a continuación carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF pueden ser utilizados en cualquier otro programa que pueda cargar el archivo de contacto estándar vCard. Si abres cualquier archivo VCF en Microsoft Outlook, se verá como el de la captura de pantalla a continuación.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
| :- |
|**Figura: Un vCard guardado con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}