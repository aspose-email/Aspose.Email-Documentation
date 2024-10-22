---
title: "Leer archivos PST/OST corruptos"
url: /es/net/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

A veces puede no ser posible leer el PST/OST debido a algunos problemas. Por ejemplo, algunos bloques de datos pueden estar corruptos. En tales casos, generalmente surgen excepciones al llamar a los métodos [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/), etc. Pero mensajes o carpetas individuales pueden permanecer intactos en el almacenamiento.

## **Métodos para encontrar los identificadores de los elementos**

Los siguientes métodos permiten encontrar identificadores de elementos de manera jerárquica.

- [FindMessages(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - encuentra los identificadores de mensajes para la carpeta.
- [FindSubfolders(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - encuentra los identificadores de subcarpetas para la carpeta.

Los identificadores obtenidos mediante los métodos pueden ser utilizados para recuperar mensajes y carpetas.

> **_NOTA:_** Se debe tener en cuenta que a pesar de sus ventajas, existen almacenamientos corruptos que no se pueden leer incluso utilizando estos métodos.

## **Recorrido de archivos PST**

El siguiente ejemplo de código muestra el recorrido de un archivo PST y la extracción de carpetas y mensajes. Para obtener la lista de identificadores, utiliza los métodos FindMessages y FindSubfolders. Luego, el identificador se pasa al método [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) o [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) para extraer elementos.

```csharp
using (var pst = PersonalStorage.FromFile(fileName))
{
    ExploreCorruptedPst(pst, pst.RootFolder.EntryIdString);
}

public static void ExploreCorruptedPst(PersonalStorage pst, string rootFolderId)
{
    var messageIdList = pst.FindMessages(rootFolderId);

    foreach (var messageId in messageIdList)
    {
        try
        {
            var msg = pst.ExtractMessage(messageId);
            Console.WriteLine( "- " + msg.Subject);
        }
        catch
        {
            Console.WriteLine("Error al leer el mensaje. ID de entrada: " + messageId);
        }
    }

    var folderIdList = pst.FindSubfolders(rootFolderId);

    foreach (var subFolderId in folderIdList)
    {
        if (subFolderId != rootFolderId)
        {
            try
            {
                FolderInfo subfolder = pst.GetFolderById(subFolderId);
                Console.WriteLine(subfolder.DisplayName);
            }
            catch
            {
                Console.WriteLine("Error al leer el mensaje. ID de entrada: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```