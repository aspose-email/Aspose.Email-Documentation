---
title: "Trabajando con Zimbra"
url: /es/java/working-with-zimbra/
weight: 110
type: docs
---

## **Acerca de Zimbra**

Zimbra es una suite de correo electrónico, calendario y colaboración construida para la nube. Zimbra incluye correo electrónico completo, contactos, calendario, intercambio de archivos, tareas y mensajería/videoconferencia, todo accesible desde el Cliente Web de Zimbra desde cualquier dispositivo.

## **Leer todos los mensajes del almacenamiento TGZ de Zimbra**

Aspose.Email proporciona la clase [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) para leer archivos de almacenamiento TGZ de Zimbra. El siguiente código de muestra demuestra el uso de la clase [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) para leer todos los mensajes del archivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}

## **Guardar Mensajes y Estructura de Directorio**

También puede guardar todos los mensajes con la estructura de directorios del archivo de almacenamiento TGZ de Zimbra. Para esto, la clase [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) proporciona un método [ExportTo](<https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo(java.lang.String)>) que toma la ruta de salida como parámetro.

El siguiente fragmento de código demuestra el uso del método [TgzReader.ExportTo](<https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo(java.lang.String)>) para guardar todos los mensajes del archivo de almacenamiento TGZ de Zimbra.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Exportar elementos de calendario y contactos desde los archivos de respaldo de Zimbra**

Aspose.Email hace posible exportar el calendario y contactos de Zimbra a formatos iCalendar y VCard. El siguiente ejemplo de código muestra cómo implementar esta función en nuestro proyecto:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //los archivos de contactos se pueden encontrar en las subcarpetas Contactos y Contactos por Correo
    //los archivos de calendario se pueden encontrar en la subcarpeta Calendario
    reader.exportTo("out");
}
```

