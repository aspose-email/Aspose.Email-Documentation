---
title: "Trabajando con propiedades de MAPI"
url: /es/java/working-with-mapi-properties/
weight: 60
type: docs
---

## **Configuración y acceso a las propiedades de MAPI de Outlook**

Aspose.Email para Java proporciona la [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) clase que representa una propiedad MAPI:

- Nombre: el nombre de la propiedad.
- Etiqueta: la etiqueta de la propiedad.
- Datos: los datos de la propiedad.

En este tema también se explica cómo configurar y acceder a las propiedades MAPI de un archivo de mensajes de Outlook (MSG) mediante Aspose.Email para Java. Además, se proporciona un ejemplo de código sobre cómo eliminar propiedades de los mensajes y los archivos adjuntos.

### **Leer propiedades**

Para leer los datos de las propiedades MAPI de un archivo MSG:

1. Crea una instancia del [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase para cargar un archivo MSG usando el [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) método estático.
2. Establezca una referencia a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) método para obtener el [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Obtenga el [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) objeto del [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) por el [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) keys.
4. Obtenga los datos de la propiedad mediante un método getXXX () apropiado.
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Establecer propiedades adicionales**

El siguiente ejemplo de código se puede usar para establecer propiedades adicionales de un Outlook [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Eliminar propiedades**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Lectura de propiedades de Mapi con nombre en mensajes de correo electrónico**

Microsoft Outlook admite la adición de propiedades MAPI con nombre a un archivo MSG. Estas propiedades las agrega el usuario. Los desarrolladores pueden agregar una propiedad con nombre, por ejemplo, «MyProp», a un archivo MSG mediante Aspose.Email.

Este artículo ilustra Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) colección para leer las propiedades de MAPI con nombre de un archivo MSG.

### **Lea la propiedad MAPI con nombre**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Lea la propiedad con nombre de Mapi desde el archivo adjunto**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}
