---
title: "Trabajar con contactos en un archivo PST"
url: /es/java/working-with-contacts-in-pst-file/
weight: 40
type: docs
---

## **Lectura de varios contactos en formato vCard**

El ejemplo de código siguiente muestra cómo leer un archivo VCF, comprobar si contiene varios contactos y, de ser así, cargar los contactos del archivo en una lista de objetos vCardContact. El código usa los métodos siguientes:

- [isMultiContacts (flujo de entrada)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#isMultiContacts-java.io.InputStream-) - Comprueba si la transmisión fuente contiene contactos múltiples.
- [LoadAsMultiple (ruta de archivo de cadena, codificación de conjunto de caracteres)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.lang.String-java.nio.charset.Charset-) - Carga la lista de contactos del archivo de contactos múltiples.
- [LoadAsMultiple (flujo de entrada, codificación de conjunto de caracteres)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.io.InputStream-java.nio.charset.Charset-) - Carga la lista de contactos de un flujo de contactos múltiples.

```java
try (InputStream stream = new FileInputStream("test.vcf")) {
    if (VCardContact.isMultiContacts(stream)) {
        List<VCardContact> contacts = VCardContact.loadAsMultiple(stream, Charset.forName("utf-8"));
    }
}
```

## **Agregar un contacto a PST**

[Crear un nuevo PST, agregar subcarpetas y mensajes](java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) a la subcarpeta Contactos de un archivo PST que haya creado o cargado. A continuación se indican los pasos para añadirlo [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) a un PST:

1. Crea un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) object.
1. Configure el [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) propiedades que utilizan diferentes constructores y métodos.
1. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-) method.
1. Cree una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

El siguiente fragmento de código muestra cómo crear un [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) y, a continuación, agréguelo a la carpeta Contactos de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}

## **Guarde la información de contactos del archivo PST en formato MSG**

Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar los contactos en el disco en formato MSG. Para ello, utilice el [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) clases para obtener y mostrar la información de contacto.

Para obtener la información de un contacto:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Call [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) y luego [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMapiMessageItem--) método para obtener la información de contacto en el [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Use [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) propiedades para acceder a la información de contacto.
1. Llame al [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) método para obtener la información de contacto en el [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class.
1. Llame al [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) método para guardar el contacto en el disco en formato MSG.

A continuación se muestra un código de ejemplo que recupera toda la información de contactos del archivo PST y la guarda en el disco en formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}

## **Guardar la información de contactos de Outlook PST en el disco en formato vCard**

Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar el contacto en un disco en formato vCard (VCF). Utiliza el [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) clases para obtener la información de contacto.

A continuación se indican los pasos para obtener la información de los contactos:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) método para obtener la información de contacto en el [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Usa las propiedades del [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) clase para acceder a la información de contacto.

El siguiente programa carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de contactos vCard estándar. Si abres cualquier archivo VCF en Microsoft Outlook, tendrá el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
|: - |
|**Figura: Una vCard guardada con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}
