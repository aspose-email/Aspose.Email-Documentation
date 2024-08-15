---
title: "Trabajando con Zimbra"
url: /es/java/working-with-zimbra/
weight: 110
type: docs
---

## **Acerca de Zimbra**
Zimbra es una suite de correo electrónico, calendario y colaboración creada para la nube. Zimbra incluye correo electrónico completo, contactos, calendario, intercambio de archivos, tareas y mensajería/videoconferencias, a los que se puede acceder desde el cliente web de Zimbra desde cualquier dispositivo.
## **Lea todos los mensajes del almacenamiento Zimbra TGZ**
Aspose.Email proporciona la [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) clase para leer los archivos de almacenamiento TGZ de Zimbra. El siguiente código de ejemplo demuestra el uso del [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) clase para leer todos los mensajes del archivo. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}
## **Guardar mensajes y estructura de directorios**
También puede guardar todos los mensajes con la estructura de directorios del archivo de almacenamiento TGZ de Zimbra. Para ello, el [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) la clase proporciona un método [ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) que toma la ruta de salida como parámetro.

El siguiente fragmento de código demuestra el uso del [TgzReader.ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) método para guardar todos los mensajes del archivo de almacenamiento TGZ de Zimbra.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Exportar elementos de calendario y contactos desde archivos de respaldo de Zimbra**

Aspose.Email permite exportar el calendario y los contactos de Zimbra a los formatos iCalendar y vCard. El siguiente ejemplo de código muestra cómo implementar esta función en nuestro proyecto:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.exportTo("out");
}
```