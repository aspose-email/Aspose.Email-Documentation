---
title: "Ler arquivos PST/OST corrompidos"
url: /pt/net/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

Às vezes, pode não ser possível ler o PST/OST devido a alguns problemas. Por exemplo, alguns blocos de dados podem estar corrompidos. Nesses casos, exceções geralmente surgem ao chamar os métodos [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/), etc. Porém, mensagens ou pastas individuais podem permanecer intactas no armazenamento.

## **Métodos para encontrar os identificadores de itens**

Os seguintes métodos permitem encontrar identificadores de itens de maneira hierárquica.

- [FindMessages(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - encontra os identificadores de mensagens para a pasta.
- [FindSubfolders(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - encontra os identificadores de subpastas para a pasta.

Os identificadores obtidos usando os métodos podem ser usados para recuperar mensagens e pastas.

> **_NOTA:_** Deve-se notar que, apesar de suas vantagens, existem armazéns corrompidos que não podem ser lidos mesmo usando esses métodos.

## **Navegação em arquivos PST**

O seguinte exemplo de código mostra a navegação em um arquivo PST e a extração de pastas e mensagens. Para obter a lista de identificadores, use os métodos FindMessages e FindSubfolders. Em seguida, o identificador é passado para o método [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) ou [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) para extrair elementos.

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
            Console.WriteLine("Erro ao ler a mensagem. ID de entrada: " + messageId);
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
                Console.WriteLine("Erro ao ler a mensagem. ID de entrada: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```