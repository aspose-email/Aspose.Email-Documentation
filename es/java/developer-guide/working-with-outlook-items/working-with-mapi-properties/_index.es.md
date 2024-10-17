---
title: "Trabajando con Propiedades MAPI"
url: /es/java/working-with-mapi-properties/
weight: 60
type: docs
---

## **Configurando y Accediendo a Propiedades MAPI de Outlook**

Aspose.Email para Java proporciona la [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) clase que representa una propiedad MAPI:

- Nombre: el nombre de la propiedad.
- Etiqueta: la etiqueta de la propiedad.
- Datos: los datos de la propiedad.

Este tema también discute cómo configurar y acceder a las propiedades MAPI de un archivo de Mensaje de Outlook (MSG) utilizando Aspose.Email para Java. Además, se ha proporcionado un código de ejemplo sobre cómo eliminar propiedades de MSG y Adjuntos.

### **Leer Propiedades**

Para leer los datos de las propiedades MAPI de un archivo MSG:

1. Crear una instancia de la [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase para cargar un archivo MSG usando el [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) método estático.
2. Establecer una referencia al [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) objeto [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) método para obtener la [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Obtener el [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) objeto de la [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) por las [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) claves.
4. Obtener los datos de la propiedad utilizando un método adecuado getXXX() .

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Configurar Propiedades Adicionales**

El siguiente código de ejemplo puede ser utilizado para configurar propiedades adicionales de un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) de Outlook.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Eliminar Propiedades**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Lectura de Propiedades Mapi Nombradas desde Mensajes de Correo Electrónico**

Microsoft Outlook admite la adición de propiedades MAPI nombradas a un archivo MSG. Estas propiedades son añadidas por el usuario. Los desarrolladores pueden agregar una propiedad nombrada, por ejemplo “MyProp”, a un archivo MSG utilizando Aspose.Email.

Este artículo ilustra la colección [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) de Aspose.Email para leer propiedades MAPI nombradas de un archivo MSG.

### **Leer Propiedad MAPI Nombrada**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Leer Propiedad Mapi Nombrada desde un Adjunto**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}