---
title: "Ler Arquivo PST do Outlook e Obter Informações sobre Pastas e Subpastas"
url: /pt/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

Aspose.Email para .NET fornece uma API para ler arquivos PST do Microsoft Outlook. Você pode carregar um arquivo PST do disco ou transmiti-lo para uma instância da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens. A API também fornece a capacidade de incluir pastas de pesquisa ao percorrer as mensagens das pastas PST.

## **Carregando um Arquivo PST**

Um arquivo PST do Outlook pode ser carregado em uma instância da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/). O seguinte trecho de código mostra como carregar o arquivo PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

## **Exibindo Informações das Pastas**

Depois de carregar o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/), você pode obter informações sobre o nome de exibição do arquivo, a pasta raiz, subpastas e a contagem de mensagens. O seguinte trecho de código mostra como exibir o nome do arquivo PST, pastas e o número de mensagens nas pastas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

## **Obter apenas pastas definidas pelo usuário**

Arquivos PST/OST podem conter pastas que foram criadas por um usuário. Aspose.Email fornece a capacidade de acessar apenas pastas definidas pelo usuário usando a propriedade [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/). Você pode definir a propriedade [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) como **true** para obter apenas pastas definidas pelo usuário. O seguinte trecho de código demonstra o uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) para obter pastas definidas pelo usuário.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

## **Verificando se a pasta está em uma pasta pré-definida**

Ao abrir e inspecionar as pastas dentro de um arquivo PST (Tabela de Armazenamento Pessoal), você pode verificar se cada pasta é um tipo de pasta pré-definida ou uma subpasta de um tipo de pasta pré-definida e obter informações sobre cada pasta.

O método [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)(bool getForTopLevelParent) permite verificar se uma pasta é do [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). Se o parâmetro *getForTopLevelParent* for verdadeiro, o método retorna um valor enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) para a pasta pai de nível superior. Isso determina se a pasta atual é uma subpasta de uma pasta pré-definida. Se o parâmetro *getForTopLevelParent* for falso, ele retorna um valor enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) para a pasta atual.

O seguinte exemplo de código mostra como implementar esse recurso em seu projeto:

```cs
PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders();

            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Pasta: {folder.DisplayName}");
                Console.WriteLine($"É pré-definida: {folder.GetPredefinedType(false) != StandardIpmFolder.Unspecified}");
                Console.WriteLine("-----------------------------------");
            }
        }
    }
```
## **Obtendo e adicionando uma pasta padrão de RSS Feeds no PersonalStorage**

Aspose.Email possibilita recuperar uma referência à pasta pré-definida que contém feeds RSS. Isso pode ser útil se você quiser acessar e manipular programaticamente os feeds RSS armazenados em um arquivo PST do Outlook. Dê o valor de RssFeeds ao enum [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration).

O seguinte exemplo de código mostra como obter uma pasta de RSS Feeds.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

Para adicionar uma pasta de RSS Feeds, use o seguinte trecho de código:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Analisando Pastas Pesquisáveis**

Um PST/OST pode conter pastas pesquisáveis além do tipo normal de pastas. Aspose.Email fornece o enumerador [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) para especificar as mensagens de tais pastas de pesquisa com os métodos [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) e [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/). O seguinte trecho de código mostra como analisar pastas pesquisáveis.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Percorrer cada pasta para exibir o nome da pasta e o número de mensagens
            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Pasta: {folder.DisplayName}");

                FolderInfoCollection subFolders = folder.GetSubFolders(FolderKind.Search | FolderKind.Normal);
                foreach (FolderInfo subFolder in subFolders)
                {
                    Console.WriteLine($"Subpasta: {subFolder.DisplayName}");
                }
            }
        }
```

## **Recuperando Informações da Pasta Pai a partir de MessageInfo**

O seguinte trecho de código mostra como recuperar informações da pasta pai a partir de [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

## **Recuperar uma subpasta PST pelo caminho**

O método [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) sobrecarregado permitirá que você recupere uma subpasta com o nome especificado da pasta PST atual.

O método recebe os seguintes parâmetros:

- **name** - especifica o nome da subpasta a ser recuperada.
- **ignoreCase** - determina se a busca pelo nome da subpasta deve ser sensível ou não a maiúsculas e minúsculas. Se definido como *true*, a busca será insensível a maiúsculas e minúsculas; caso contrário, será sensível.
- **handlePathSeparator** - especifica se o nome da pasta especificado deve ser tratado como um caminho se contiver barras invertidas. Se definido como *true*, o método interpretará o nome da pasta como um caminho, tentando navegar até a subpasta usando o caminho. Se definido como *false*, o método tratará o nome da pasta como um nome simples, buscando uma subpasta com uma correspondência exata no nome.

O seguinte exemplo de código demonstra como implementar este método em seu projeto:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
Neste exemplo, o método retornará uma pasta chamada ‘Jan’ que está localizada no caminho Inbox\Reports\ em relação à pasta raiz.
```

## **API de Navegação de Arquivos PST**

A API de navegação permite extrair todos os itens PST na medida do possível, sem lançar exceções, mesmo que alguns dados do arquivo original estejam corrompidos. Os seguintes passos mostram como usar esta API.

Use o construtor [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e o método [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) em vez do método FromFile.

O construtor permite definir um método de retorno de chamada.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Código para tratamento de exceção. */ }))
```

Exceções ao carregar e navegar estarão disponíveis através do método de retorno de chamada.

O método [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) retorna 'true' se o arquivo foi carregado com sucesso e a navegação subsequente for possível. Se um arquivo estiver corrompido e a navegação não for possível, 'false' é retornado.

```csharp
if (currentPst.Load(inputStream))
```

Isso permite abrir e navegar até mesmo arquivos PST corrompidos sem lançar exceções. E exceções e itens corrompidos serão tratados pelo método de retorno de chamada.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Código para tratamento de exceção. */ }))
{
    if (pst.Load(@"test.pst"))
	{
		GetAllMessages(pst, pst.RootFolder);
	}
}

private static void GetAllMessages(PersonalStorage pst, FolderInfo folder)
{
    foreach (var messageEntryId in folder.EnumerateMessagesEntryId())
    {
        MapiMessage message = pst.ExtractMessage(messageEntryId);
    }
    foreach (var subFolder in folder.GetSubFolders())
    {
        GetAllMessages(pst, subFolder);
    }
}
```