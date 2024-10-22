---
title: "Trabalhando com Mensagens em um Arquivo PST"
url: /pt/net/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---

## **Adicionando Mensagens a Arquivos PST**

O artigo [Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolderss) mostra como criar um arquivo PST e adicionar uma subpasta a ele. Com o Aspose.Email, você pode adicionar mensagens a subpastas de um arquivo PST que você criou ou carregou. Este artigo adiciona duas mensagens do disco à subpasta da Caixa de Entrada de um PST. Use as classes [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) para adicionar mensagens a arquivos PST. Para adicionar mensagens à pasta Caixa de Entrada de um arquivo PST:

1. Crie uma instância da classe FolderInfo e carregue-a com o conteúdo da pasta Caixa de Entrada.
2. Adicione mensagens de um disco à pasta Caixa de Entrada chamando o método [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage). A classe [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) expõe o método [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages) que permite adicionar um grande número de mensagens à pasta, reduzindo as operações de I/O no disco e melhorando o desempenho. Um exemplo completo pode ser encontrado abaixo, em [Adicionando Mensagens em Lote](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#adding-bulk-messages).

O trecho de código abaixo mostra como adicionar mensagens a uma subpasta de PST chamada Caixa de Entrada.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// Criar novo PST            
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Adicionar nova pasta "Caixa de Entrada"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Selecionar a pasta "Caixa de Entrada"
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Adicionar algumas mensagens à pasta "Caixa de Entrada"
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Adicionando Mensagens em Lote**

Adicionar mensagens individuais a um PST implica mais operações de I/O no disco e, portanto, pode desacelerar o desempenho. Para melhorar o desempenho, use o método AddMessages(IEnumerable<MapiMessage> messages) em vez do método AddMessage(MapiMessage message) para minimizar operações de I/O. Além disso, o evento MessageAdded ocorre quando uma mensagem é adicionada à pasta.

### **Carregando Mensagens do Disco**

O trecho de código abaixo mostra como carregar mensagens de um disco.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
private static void AddMessagesInBulkMode(string fileName, string msgFolderName)
{
    using (PersonalStorage personalStorage = PersonalStorage.FromFile(fileName))
    {
        FolderInfo folder = personalStorage.RootFolder.GetSubFolder("myInbox");
        folder.MessageAdded += OnMessageAdded;
        folder.AddMessages(new MapiMessageCollection(msgFolderName));
    }
}
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

### **Implementação de IEnumerable**

O trecho de código abaixo mostra como a Implementação de IEnumerable pode ser utilizada.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
public class MapiMessageCollection : IEnumerable<MapiMessage>
{
    private string path;

    public MapiMessageCollection(string path)
    {
        this.path = path;
    }

    public IEnumerator<MapiMessage> GetEnumerator()
    {
        return new MapiMessageEnumerator(path);
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}

public class MapiMessageEnumerator : IEnumerator<MapiMessage>
{
    private readonly string[] files;

    private int position = -1;

    public MapiMessageEnumerator(string path)
    {
        string path1 = RunExamples.GetDataDir_Outlook();
        files = Directory.GetFiles(path1);
    }

    public bool MoveNext()
    {
        position++;
        return (position < files.Length);
    }

    public void Reset()
    {
        position = -1;
    }

    object IEnumerator.Current
    {
        get
        {
            return Current;
        }
    }

    public MapiMessage Current
    {
        get
        {
            try
            {
                return MapiMessage.FromFile(files[position]);
            }
            catch (IndexOutOfRangeException)
            {
                throw new InvalidOperationException();
            }
        }
    }
    public void Dispose()
    {
    }
}
```

### **Adicionando Mensagens de Outro PST**

Para adicionar mensagens de outro PST, use o método [FolderInfo.EnumerateMapiMessages()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/#enumeratemapimessages) que retorna IEnumerable<MapiMessage>. O trecho de código abaixo mostra como adicionar mensagens de outro PST.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Obter a pasta pelo nome
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Obter a pasta pelo nome
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }

}

/// <summary>
/// Manipula o evento MessageAdded.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Obtenha Informações das Mensagens de um Arquivo PST do Outlook**

No artigo [Ler Arquivo PST do Outlook e Obter Informações de Pastas e Subpastas](https://docs.aspose.com/email/pt/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/) discutimos como carregar um arquivo PST do Outlook e navegar por suas pastas para obter os nomes das pastas e o número de mensagens nelas. Este artigo explica como ler todas as pastas e subpastas no arquivo PST e exibir informações sobre as mensagens, por exemplo, assunto, remetente e destinatários. O arquivo PST do Outlook pode conter pastas aninhadas. Para obter informações sobre as mensagens dessas, bem como das pastas de nível superior, use um método recursivo para ler todas as pastas. O trecho de código abaixo mostra como ler um arquivo PST do Outlook e exibir o conteúdo das pastas e mensagens de forma recursiva.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Carregar o arquivo do Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
       
        // Carregar o arquivo PST do Outlook
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Obter o Formato de Exibição do arquivo PST
        Console.WriteLine("Formato de Exibição: " + personalStorage.Format);

        // Obter informações sobre pastas e mensagens
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Chamar o método recursivo para exibir o conteúdo da pasta
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);               
    }            
}

/// <summary>
/// Este é um método recursivo para exibir o conteúdo de uma pasta
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Exibir o nome da pasta
    Console.WriteLine("Pasta: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Exibir informações sobre as mensagens dentro desta pasta
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Assunto: " + messageInfo.Subject);
        Console.WriteLine("Remetente: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Destinatários: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Chamar este método recursivamente para cada subpasta
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Extraindo Mensagens de Arquivos PST**

Este artigo mostra como ler arquivos PST do Microsoft Outlook e extrair mensagens. As mensagens são então salvas em um disco no formato MSG.

{{% alert %}}
**Experimente!**

Execute o projeto simples [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) e explore um uso interessante dos recursos do Aspose.Email para ler e-mails de PST e encontrar threads de conversação.
{{% /alert %}}

O trecho de código abaixo mostra como extrair mensagens de um arquivo PST: 
- Use um método recursivo para navegar por todas as pastas (incluindo quaisquer pastas aninhadas) e chame o método PersonalStorage.ExtractMessage() para obter mensagens do Outlook em uma instância da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). 
- Depois disso, chame o método MapiMessage.Save() para salvar a mensagem em um disco ou um stream no formato MSG.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // O caminho para o diretório de arquivos.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Carregar o arquivo do Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // carregar o arquivo PST do Outlook
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // obter o Formato de Exibição do arquivo PST
        Console.WriteLine("Formato de Exibição: " + pst.Format);

        // obter informações sobre pastas e mensagens
        FolderInfo folderInfo = pst.RootFolder;

        // Chamar o método recursivo para extrair arquivos msg de cada pasta
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }            
}

/// <summary>
/// Este é um método recursivo para exibir o conteúdo de uma pasta
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // exibir o nome da pasta
    Console.WriteLine("Pasta: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // percorrer todas as mensagens nesta pasta
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Salvando mensagem {0} ....", messageInfo.Subject);
        // obter a mensagem na instância MapiMessage
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // salvar essa mensagem em disco no formato msg
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // salvar essa mensagem em stream no formato msg
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Chamar este método recursivamente para cada subpasta
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Salvando Mensagens Diretamente de PST para Stream**

Para salvar mensagens de um arquivo PST diretamente em um stream, sem extrair o MsgInfo para mensagens, use o método SaveMessageToStream(). O trecho de código abaixo mostra como salvar mensagens diretamente de PST para um stream.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Outlook();

// Carregar o arquivo do Outlook
string path = dataDir + "PersonalStorage.pst";

// Salvar mensagem em MemoryStream
using (PersonalStorage personalStorage = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (MemoryStream memeorystream = new MemoryStream())
        {
            personalStorage.SaveMessageToStream(messageInfo.EntryIdString, memeorystream);
        }
    }
}

// Salvar mensagem em arquivo
using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (FileStream fs = File.OpenWrite(messageInfo.Subject + ".msg"))
        {
            pst.SaveMessageToStream(messageInfo.EntryIdString, fs);
        }
    }
}

using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    
    // Para enumerar entryId das mensagens você pode usar o método FolderInfo.EnumerateMessagesEntryId():
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}            
```

### **Extraindo n Número de Mensagens de um Arquivo PST**

O trecho de código abaixo mostra como extrair um número específico de mensagens de um PST. Basta fornecer o índice da primeira mensagem e o número total de mensagens a serem extraídas.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extrai mensagens começando do índice 10 do topo e extrai um total de 100 mensagens
MessageInfoCollection messages = inbox.GetContents(10, 100);
```
### **Obtendo Contagem Total de Itens de um Arquivo PST**

Aspose.Email fornece o método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) da propriedade [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property). Ele retorna o número total de itens de mensagem contidos no PST.

O seguinte exemplo de código mostra como recuperar a contagem total de itens (mensagens, compromissos, contatos, etc.) armazenados dentro do arquivo PST:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

## **Excluir Itens de Arquivos PST**

O artigo [Adicionar Mensagens a Arquivos PST](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#adding-messages-to-pst-files) mostra como adicionar mensagens a arquivos PST. É, claro, também possível excluir itens (conteúdos) de um arquivo PST, e pode ser desejável excluir mensagens em lote. Itens de um arquivo PST podem ser excluídos usando o método [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem). A API também fornece o método [FolderInfo.DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) para excluir itens em lote do arquivo PST.

### **Excluindo Mensagens de Arquivos PST**

Este artigo mostra como usar a classe [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) para acessar pastas específicas em um arquivo PST. Para excluir mensagens da subpasta Enviados de um arquivo PST previamente carregado ou criado:

1. Crie uma instância da classe [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) e carregue-a com o conteúdo da subpasta enviada.
1. Exclua mensagens da pasta Enviados chamando o método [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) e passando o [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) como parâmetro. O trecho de código a seguir mostra como excluir mensagens da subpasta Enviados de um arquivo PST.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Carregar o arquivo PST do Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Obter a pasta de itens enviados
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("some delete condition") == true)
    {
        // Excluir este item
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Mensagem excluída");
    }
}
```

### **Excluindo Pastas de Arquivos PST**

Você pode excluir uma pasta PST movendo-a para a pasta Itens Excluídos.

```csharp
using (PersonalStorage pst = PersonalStorage.FromFile(@"test.pst"))
{
    FolderInfo deletedItemsFolder = pst.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.RootFolder.GetSubFolder("Pasta Vazia");
	  FolderInfo someFolder = pst.RootFolder.GetSubFolder("Alguma Pasta");
    pst.MoveItem(emptyFolder, deletedItemsFolder);
	  pst.MoveItem(someFolder, deletedItemsFolder);
}
```

A vantagem desse método é que a pasta excluída pode ser facilmente recuperada.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Alguma Pasta");
pst.MoveItem(someFolder, pst.RootFolder);
```

Você também pode remover permanentemente uma pasta da pasta Itens Excluídos, se necessário.

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

O método [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) pode ser usado para qualquer pasta se você quiser excluir imediatamente e permanentemente uma subpasta, ignorando a pasta Itens Excluídos.

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Alguma Pasta");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```
### **Excluir Itens de PST**

Excluir itens (pastas ou mensagens) de uma Tabela de Armazenamento Pessoal (PST) usando o unique entryId associado ao item chamando o método DeleteItem(string entryId) da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).

O trecho de código a seguir pode ser usado para chamar o método DeleteItem e passar o entryId como parâmetro:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```
**Por Favor, Note:**

- Este método excluirá permanentemente o item do PST e não poderá ser desfeito. Exercite cautela ao usar este método para evitar perda acidental de dados.
- De acordo com as convenções padrão, assegure-se de que o entryId seja válido e corresponda a um item existente dentro do PST. 
- Caso contrário, uma exceção será lançada. É aconselhável ter um backup do PST ou implementar medidas adequadas para recuperar itens excluídos, se necessário.

### **Excluir Itens em Lote de um Arquivo PST**

A API Aspose.Email pode ser usada para excluir itens em lote de um arquivo PST. Isso é alcançado usando o método [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems) que aceita uma lista de itens de ID de entrada referindo-se aos itens a serem excluídos. O trecho de código a seguir mostra como excluir itens em lote de um arquivo PST.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Obter Subpasta Caixa de Entrada do arquivo do Outlook
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Criar uma instância do PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // excluir mensagens com From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Pesquisar Mensagens e Pastas em um PST por Critério**

Arquivos de Armazenamento Pessoal (PST) podem conter uma enorme quantidade de dados. Pesquisar dados que atendem a um critério específico em tais arquivos grandes precisa incluir múltiplos pontos de verificação no código para filtrar as informações. Com a classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) o Aspose.Email possibilita a busca por registros específicos em um PST com base em um critério de pesquisa especificado. Um PST pode ser pesquisado por mensagens com base em parâmetros de pesquisa, como remetente, receptor, assunto, importância da mensagem, presença de anexos, tamanho da mensagem e até mesmo ID da mensagem. A [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) também pode ser usada para pesquisar subpastas.

### **Pesquisando Mensagens e Pastas em PST**

O trecho de código abaixo mostra como usar a classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) para pesquisar conteúdos em um PST com base em diferentes critérios de pesquisa. Por exemplo, mostra como pesquisar um PST com base em:

- Importância da mensagem.
- Classe da mensagem.
- Presença de anexos.
- Tamanho da mensagem.
- Mensagens não lidas.
- Mensagens não lidas com anexos, e
- pastas com um nome de subpasta específico.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // Mensagens de alta importância
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensagens com Alta Imp:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensagens com IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensagens com anexos E alta importância
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensagens com anexos: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensagens com tamanho > 15 KB
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("mensagens tamanho > 15Kb:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensagens não lidas
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Não Lidas:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Mensagens não lidas com anexos
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Mensagens não lidas com anexos: " + messages.Count);

    // Pasta com o nome de 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Pasta contendo subpasta: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Pastas com subpastas
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```

### **Pesquisando uma String em PST com o Parâmetro Ignorar Caso**

O trecho de código abaixo mostra como pesquisar uma string em PST com o parâmetro ignorar caso.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase é Verdadeiro
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

### **Pesquisando Assuntos de Mensagens por Múltiplas Palavras-chave em um Arquivo PST**

Você pode usar o método [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) para encontrar mensagens com um assunto contendo pelo menos uma das palavras especificadas, conforme mostrado abaixo:

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' é a palavra-chave para a pesquisa

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' é também a palavra-chave para a pesquisa

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // os assuntos das mensagens devem conter as palavras 'Review' ou 'Error'

using (var storage = PersonalStorage.FromFile("example.pst"))
{
    var folderInfo = storage.RootFolder.GetSubFolder("Inbox");
    var messageInfos = folderInfo.GetContents(queryBuilder.GetQuery());

    foreach (var messageInfo in messageInfos)
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

## **Mover Itens para Outras Pastas do Arquivo PST**

Aspose.Email possibilita mover itens de uma pasta de origem para outra pasta no mesmo Arquivo de Armazenamento Pessoal (PST). Isso inclui:

- Mover uma pasta específica para uma nova pasta pai.
- Mover uma mensagem específica para uma nova pasta.
- Mover o conteúdo para uma nova pasta.
- Mover subpastas para uma nova pasta pai.

O trecho de código abaixo mostra como mover itens como mensagens e pastas de uma pasta de origem para outra pasta no mesmo arquivo PST.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Mover pasta e mensagem para a pasta Itens Excluídos
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Mover todas as subpastas da caixa de entrada e o conteúdo da subpasta para a pasta Itens Excluídos
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```
## **Mesclar e Dividir Arquivos PST**

O exemplo de código abaixo descreve o processo de divisão de um arquivo:

1. Primeiro, ele usa o método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) para especificar o nome do arquivo.

2. Em seguida, chama o delegado [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) para manipular um evento StorageProcessed.

3. A classe [StorageProcessingEventArgs]() fornece dados para o evento PersonalStorage.StorageProcessing. Sua propriedade [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventargs/filename/#storageprocessedeventargsfilename-property) permite que você recupere o nome do arquivo PST. Para o método [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) será o nome do PST atual a ser mesclado com o principal, e para o método [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) será o nome da parte atual.

4. Finalmente, o método sobrecarregado [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) lançará a divisão do armazenamento PST em partes de tamanho menor. Ele recebe os seguintes parâmetros:

- **chunkSize**: O tamanho aproximado de cada parte em bytes.
- **partFileNamePrefix**: O prefixo que será adicionado ao nome do arquivo de cada parte do PST. Se fornecido, o prefixo será adicionado ao início de cada nome de arquivo. Se não fornecido (nulo ou vazio), as partes do PST serão criadas sem um prefixo.
- **path**: O caminho da pasta onde as partes serão criadas.

O nome do arquivo de cada parte segue o modelo: {prefix}part{number}.pst, onde {prefix} representa o prefixo do nome do arquivo (se fornecido), e {number} representa o número do arquivo de parte.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Evento de processamento de armazenamento levantado para o arquivo: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

## **Atualizando Propriedades de Mensagens em um Arquivo PST**

Às vezes, é necessário atualizar certas propriedades de mensagens, como mudar o assunto, marcar a importância da mensagem e outras similares. Atualizar uma mensagem em um arquivo PST, com tais mudanças nas propriedades da mensagem, pode ser alcançado usando o método [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/) . Este artigo mostra como atualizar mensagens em lote em um arquivo PST para mudanças nas propriedades. O trecho de código a seguir mostra como atualizar propriedades de mensagens em modo em lote para várias mensagens em um arquivo PST.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Carregar o arquivo PST do Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
            
// Obter subpasta requerida 
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// encontrar mensagens com From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Obter Conteúdos da Consulta
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Salvar (MessageInfo,EntryIdString) na Lista
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Compor as novas propriedades
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("Novo Assunto")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// atualizar mensagens com From = "someuser@domain.com" com novas propriedades
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Atualizando Propriedades Personalizadas em um Arquivo PST**

Às vezes, é necessário marcar itens que foram processados dentro do arquivo PST. A API Aspose.Email permite alcançar isso usando o MapiProperty e MapiNamedProperty. Os seguintes métodos são úteis para alcançar isso.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- FolderInfo.ChangeMessages(MapiPropertyCollection updatedProperties) - muda todas as mensagens na pasta
- PersonalStorage.ChangeMessage(string entryId, MapiPropertyCollection updatedProperties) - muda propriedades da mensagem

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Carregar o arquivo do Outlook
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Criar a coleção de propriedades de mensagem para adicionar ou atualizar
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Propriedade normal, personalizada e PidLidLogFlags nomeada
		MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W,Encoding.Unicode.GetBytes("test_address@org.com"));
		MapiProperty namedProperty1 = new MapiNamedProperty(GenerateNamedPropertyTag(0, MapiPropertyType.PT_LONG),"ITEM_ID",Guid.NewGuid(),BitConverter.GetBytes(123));
		MapiProperty namedProperty2 = new MapiNamedProperty(GenerateNamedPropertyTag(1, MapiPropertyType.PT_LONG),0x0000870C,new Guid("0006200A-0000-0000-C000-000000000046"),BitConverter.GetBytes(0));
		newProperties.Add(namedProperty1.Tag, namedProperty1);
		newProperties.Add(namedProperty2.Tag, namedProperty2);
		newProperties.Add(property.Tag, property);
		testFolder.ChangeMessages(testFolder.EnumerateMessagesEntryId(), newProperties);
	}
}

private static long GenerateNamedPropertyTag(long index, MapiPropertyType dataType)
{
	return (((0x8000 | index) << 16) | (long)dataType) & 0x00000000FFFFFFFF;
}
```

## **Extraindo Anexos sem Extrair a Mensagem Completa**

A API Aspose.Email pode ser usada para extrair anexos de mensagens PST sem extrair a mensagem completa primeiro. O método ExtractAttachments da interface IEWSClient pode ser usado para isso. O seguinte trecho de código mostra como extrair anexos sem extrair uma mensagem completa.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalstorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalstorage.RootFolder.GetSubFolder("Inbox");

    foreach (var messageInfo in folder.EnumerateMessagesEntryId())
    {
        MapiAttachmentCollection attachments = personalstorage.ExtractAttachments(messageInfo);

        if (attachments.Count != 0)
        {
            foreach (var attachment in attachments)
            {
                if (!string.IsNullOrEmpty(attachment.LongFileName))
                {
                    if (attachment.LongFileName.Contains(".msg"))
                    {
                        continue;
                    }
                    else
                    {
                        attachment.Save(dataDir + @"\Attachments\" + attachment.LongFileName);
                    }
                }
            }
        }
    }
}
```

## **Adicionando Arquivos a PST**

A funcionalidade principal do Microsoft Outlook é gerenciar e-mails, calendários, tarefas, contatos e entradas de diário. Além disso, arquivos também podem ser adicionados a uma pasta PST e o PST resultante mantém um registro dos documentos adicionados. O Aspose.Email oferece a possibilidade de adicionar arquivos a uma pasta da mesma forma que adiciona mensagens, contatos, tarefas e entradas de diário ao PST. O trecho de código a seguir mostra como adicionar documentos a uma pasta PST usando o Aspose.Email.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Adicionar o arquivo Document.doc com a classe de mensagem "IPM.Document" por padrão.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```