---
title: "Leer archivos PST/OST corruptos"
url: /es/net/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

A veces puede que no sea posible leer el PST/OST debido a algunos problemas. Por ejemplo, algunos bloques de datos pueden estar dañados. En tales casos, suelen surgir excepciones al llamar al [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/), etc. métodos. Sin embargo, es posible que los mensajes o carpetas individuales permanezcan intactos en el almacenamiento.

## **Métodos para encontrar los identificadores de los artículos**

Los siguientes métodos permiten encontrar los identificadores de los artículos de forma jerárquica.

- [FindMessages (cadena parentEntryID)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - busca los identificadores de los mensajes de la carpeta.
- [FindSubfolders (cadena ParentEntryID)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - busca los identificadores de las subcarpetas de la carpeta.

Los identificadores obtenidos mediante los métodos se pueden utilizar para recuperar mensajes y carpetas.

> **_NOTE:_** Cabe señalar que, a pesar de sus ventajas, existen almacenamientos corruptos que no se pueden leer ni siquiera con estos métodos.

## **Recorrido de archivos PST**

El siguiente ejemplo de código muestra cómo un archivo PST recorre y extrae carpetas y mensajes. Para obtener la lista de identificadores, utilice los métodos FindMessages y FindSubFolders. Luego, el identificador se pasa al [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) or [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) método para extraer elementos.

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
            Console.WriteLine("Message reading error. Entry id: " + messageId);
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
                Console.WriteLine("Message reading error. Entry id: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```
