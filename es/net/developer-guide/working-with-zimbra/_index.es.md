---
title: "Trabajando con Zimbra"
url: /es/net/working-with-zimbra/
weight: 120
type: docs
---


## **Acerca de Zimbra**

Zimbra es una suite de correo electrónico, calendario y colaboración creada para la nube. Zimbra incluye correo electrónico completo, contactos, calendario, intercambio de archivos, tareas y mensajería/videoconferencias, a los que se puede acceder desde el cliente web de Zimbra desde cualquier dispositivo.

## **Lea todos los mensajes del almacenamiento Zimbra TGZ**

Aspose.Email proporciona la clase TGZReader para leer los archivos de almacenamiento TGZ de Zimbra. El siguiente código de ejemplo demuestra el uso de la clase TGZReader para leer todos los mensajes del archivo. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}

## **Obtenga el recuento total de artículos de un archivo Tgz**

The [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) método del [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) la clase devolverá el número total de elementos de mensaje contenidos en el almacenamiento.

El siguiente ejemplo de código te mostrará cómo implementar este método en tu proyecto:

```cs
using (TgzReader reader = new TgzReader(fileName))
{
    int count = reader.GetTotalItemsCount();
}
```

## **Guardar mensajes y estructura de directorios**

También puede guardar todos los mensajes con la estructura de directorios del archivo de almacenamiento TGZ de Zimbra. Para ello, la clase TGZReader proporciona un método exportTo que toma la ruta de salida como parámetro.

El siguiente fragmento de código muestra el uso del método tgzReader.exportTo para guardar todos los mensajes del archivo de almacenamiento TGZ de Zimbra.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}

## **Exportar elementos de calendario y contactos desde archivos de respaldo de Zimbra**

Para exportar el calendario y los contactos de Zimbra y guardarlos en formatos iCalendar y vCard, puedes usar el siguiente fragmento de código:

```cs
using (var reader = new TgzReader(@"test2.tgz"))
{
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.ExportTo(@"out");
}
```