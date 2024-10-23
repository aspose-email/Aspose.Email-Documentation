---
title: "Criar Novo PST, Adicionar Subpastas e Mensagens"
url: /pt/net/criar-novo-pst-adicionar-subpastas-e-mensagens/
weight: 10
type: docs
---

Assim como a análise de um arquivo PST existente, o Aspose.Email fornece os meios para criar um arquivo PST do zero. Este artigo demonstra como criar um arquivo PST do Outlook e adicionar uma subpasta a ele.

1. [Criando um novo arquivo PST](#criando-um-novo-arquivo-pst).
1. [Mudando a classe de Container de uma pasta](#mudando-a-classe-de-container-de-uma-pasta).
1. [Adicionar Mensagens em Lote com Desempenho Melhorado](#adicionar-mensagens-em-lote-com-desempenho-melhorado)

## **Criar um novo arquivo PST**

Use a classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) para criar um arquivo PST em algum local no disco local. Para criar um arquivo PST do zero:

1. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
1. Adicione uma subpasta na raiz do arquivo PST acessando a pasta Raiz e chamando o método [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/).

O seguinte trecho de código mostra como criar um arquivo PST e adicionar uma subpasta chamada Inbox.

```csharp
// Criar novo PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Adicionar nova pasta "Test"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Verificação de Correspondência da Classe de Container ao Adicionar uma Pasta ao PST**

Ao criar novas pastas ou adicionar itens a pastas existentes, é importante garantir que a classe de container do novo item ou pasta alinhe-se com a classe de container da pasta pai para manter a hierarquia organizacional dentro do arquivo de armazenamento PST. Para isso, o Aspose.Email possui a propriedade [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) da classe [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class). A propriedade especifica se deve ser feita a verificação da classe de container da pasta a ser adicionada em relação à classe de container da pasta pai. Se definido como 'true', uma exceção será lançada se as classes de container não corresponderem. O padrão é 'false'.

O seguinte exemplo de código demonstra o uso da propriedade [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) para controlar se uma exceção deve ser lançada ao adicionar pastas com classes de container incompatíveis:

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Criar uma pasta de Contatos padrão com a classe de container IPF.Contacts.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    
    // Uma exceção não ocorrerá. EnforceContainerClassMatching é falso por padrão.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
    
    // Uma exceção ocorrerá, pois a classe de container da subpasta sendo adicionada (IPF.Note) 
    // não corresponde à classe de container da pasta pai (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Nota: Certifique-se de fazer o tratamento adequado de exceções ao exigir correspondência da classe de container para evitar comportamentos inesperados durante a criação de pastas no PST.

## **Mudando a Classe de Container da Pasta**

Às vezes, é necessário mudar a classe de container da pasta. Um exemplo comum é quando mensagens de diferentes tipos (compromissos, mensagens, etc.) são adicionadas à mesma pasta. Nesses casos, a classe da pasta precisa ser alterada para que todos os elementos na pasta sejam exibidos corretamente. O seguinte trecho de código mostra como mudar a classe de container de uma pasta no PST para esse propósito.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst");
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Adicionar Mensagens em Lote com Desempenho Melhorado**

Adicionar mensagens individuais a um PST implica em mais operações de I/O no disco e pode diminuir o desempenho. Para melhorar o desempenho, as mensagens podem ser adicionadas ao PST em modo em lote para minimizar as operações de I/O. O método [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) permite adicionar mensagens em lote e pode ser usado nos seguintes cenários. Além disso, o evento [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) ocorre quando uma mensagem é adicionada à pasta.

### **Adicionar Mensagens de Outro PST**

Para adicionar mensagens de outro PST, use o método [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) que retorna `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Obtenha a pasta pelo nome
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());


// Manipula o evento MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Adicionado: {e.EntryId}");
}
```

### **Adicionar Mensagens de Diretório**

Para adicionar mensagens de um diretório, crie o método iterador nomeado `GetMessages(string pathToDir)` que retorna `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Método iterador nomeado para ler mensagens do diretório.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Manipula o evento MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Adicionado: {e.EntryId}");
}
```