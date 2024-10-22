---
title: "Trabajando con Zimbra"
url: /es/net/working-with-zimbra/
weight: 120
type: docs
---


## **Acerca de Zimbra**

Zimbra es un conjunto de herramientas de correo electrónico, calendario y colaboración construido para la nube. Zimbra incluye correo electrónico completo, contactos, calendario, compartición de archivos, tareas y mensajería/videoconferencia, todo accesible desde el Cliente Web de Zimbra desde cualquier dispositivo.

## **Leer todos los mensajes desde el almacenamiento TGZ de Zimbra**

Aspose.Email proporciona la clase TgzReader para leer archivos de almacenamiento TGZ de Zimbra. El siguiente código de ejemplo demuestra el uso de la clase TgzReader para leer todos los mensajes del archivo.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}

## **Obtener el conteo total de elementos de un archivo Tgz**

El método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) de la clase [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) devolverá el número total de elementos de mensaje contenidos en el almacenamiento.

El siguiente ejemplo de código te mostrará cómo implementar este método en tu proyecto:

```cs
using (TgzReader reader = new TgzReader(fileName))
{
    int count = reader.GetTotalItemsCount();
}
```

## **Guardar mensajes y estructura de directorios**

También puedes guardar todos los mensajes con la estructura de directorios del archivo de almacenamiento TGZ de Zimbra. Para esto, la clase TgzReader proporciona un método ExportTo que toma la ruta de salida como parámetro.

El siguiente fragmento de código demuestra el uso del método TgzReader.ExportTo para guardar todos los mensajes del archivo de almacenamiento TGZ de Zimbra.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}

## **Exportar elementos de calendario y contactos desde archivos de respaldo de Zimbra**

Para exportar el calendario y los contactos de Zimbra y guardarlos en formatos iCalendar y VCard, puedes usar el siguiente fragmento de código:

```cs
using (var reader = new TgzReader(@"test2.tgz"))
{
    //los archivos de contactos se pueden encontrar en las subcarpetas Contactos y Contactos Enviados
    //los archivos de calendario se pueden encontrar en la subcarpeta Calendario
    reader.ExportTo(@"out");
}
```