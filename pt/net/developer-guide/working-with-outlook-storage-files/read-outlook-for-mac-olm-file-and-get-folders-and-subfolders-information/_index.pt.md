---
title: "Ler arquivo OLM do Outlook para Mac e obter informações sobre pastas e subpastas"
url: /pt/net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM é um formato de arquivo específico usado pelo Microsoft Outlook para armazenar dados locais, como e-mails, anexos, notas, dados de calendário, contatos, tarefas, histórico e mais. Os arquivos OLM são compatíveis apenas com o Outlook para Mac e não podem ser abertos ou acessados pelo Outlook para Windows, que usa o formato de arquivo PST em vez disso.

## **Abrindo arquivos no formato OLM**

Os arquivos no formato OLM podem ser abertos de duas maneiras:

- usando o construtor
- usando o método estático FromFile

Existem diferenças no comportamento entre esses métodos. Veja a seção abaixo.

### **Abrindo arquivos pelo construtor**

Para abrir um arquivo, chame o construtor da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) e passe o nome completo do arquivo ou o stream como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

### **Abrindo arquivos usando o método estático FromFile**

Para abrir um arquivo, use o método estático [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) e passe o nome completo do arquivo ou o stream como argumento:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

## **Obtendo pastas**

Para acessar a estrutura de diretórios de um arquivo OLM, crie uma instância da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) usando seu construtor e passe o caminho para o arquivo.
Uma vez que o arquivo esteja aberto, acesse sua estrutura de diretórios usando a propriedade [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/). Esta propriedade retorna uma lista de objetos [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/), cada um representando um diretório no arquivo OLM.
Para explorar ainda mais a estrutura de diretórios, acesse a propriedade [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) de cada objeto, que retorna uma lista de seus subdiretórios. Usando essas propriedades, você pode navegar por toda a hierarquia de diretórios do arquivo OLM e acessar todos os diretórios e subdiretórios que ele contém.

O exemplo abaixo exibe a lista de todas as pastas em ordem hierárquica:

```cs
using (var olm = new OlmStorage(fileName))
{
    PrintAllFolders(olm.FolderHierarchy, string.Empty);
}

private void PrintAllFolders(List<OlmFolder> folderHierarchy, string indent)
{
    foreach (var folder in folderHierarchy)
    {
        Console.WriteLine($"{indent}{folder.Name}");
        PrintAllFolders(folder.SubFolders, indent+"-");
    }
}
```

Ao usar o método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) para abrir um arquivo OLM, a propriedade [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) não será inicializada por padrão e retornará null. Neste caso, chame o método GetFolders explicitamente para inicializar a propriedade [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) e recuperar a lista de diretórios no arquivo OLM:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

Além disso, é possível obter qualquer pasta pelo nome:

1. Chame o método [GetFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/getfolder/).
2. Passe o nome da pasta como o primeiro argumento e um valor, que indica se deve ignorar a sensibilidade a maiúsculas e minúsculas ao procurar uma pasta, como o segundo parâmetro.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // obter a pasta de entrada pelo nome
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

## **Lista de e-mails**

A classe [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) que representa uma pasta, possui os seguintes métodos para obter a lista de e-mails:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) implementa a iteração de e-mails em uma pasta. Neste caso, cada iteração retorna um objeto [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) que fornece informações breves sobre o e-mail.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), também implementa a iteração de e-mails em uma pasta, mas neste caso, cada iteração retorna um objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que representa o próprio e-mail, com todas as propriedades.

### **Usando o método EnumerateMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);
    foreach (var messageInfo in folder.EnumerateMessages())
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

### **Usando o método EnumerateMapiMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var msg in folder.EnumerateMapiMessages())
    {
        // salvar mensagem no formato MSG
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Outras propriedades úteis**

As outras propriedades úteis da classe OlmFolder são: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) e [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) que retornam a presença de mensagens na pasta e sua contagem.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Contagem de mensagens: {folder.MessageCount}");
    }
}
```
### **Obter ou definir a data de modificação de uma mensagem**

A data de modificação representa a data e hora em que a mensagem OLM foi modificada pela última vez. Você pode usar a propriedade [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) para recuperar ou atualizar o valor da data de modificação de uma mensagem OLM.

Aqui está um exemplo que demonstra o uso da propriedade:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```
## **Extraindo e-mails**

A classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) possui o método [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/) que permite extrair e-mails. Este método recebe um objeto [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/).

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Extrai as mensagens de hoje da Caixa de entrada
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```
## **Extraindo todos os itens de um e-mail usando a API de percurso**

Você pode extrair todos os itens de um arquivo OLM do Outlook tanto quanto possível, sem lançar exceções, mesmo que alguns dados do arquivo original estejam corrompidos. Para fazer isso, use o construtor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) e o método [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) em vez do método FromFile. O construtor permite definir um método de callback.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de tratamento de exceções */ }))
```
O método de callback torna as exceções de carregamento e percurso disponíveis.

O método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) retorna 'true' se o arquivo foi carregado com sucesso e um percurso adicional é possível. Se um arquivo estiver corrompido e nenhum percurso for possível, 'false' é retornado.

```cs
if (olm.Load(fileName))
```

O seguinte trecho de código e os passos mostram como usar essa API:

1. Crie uma nova instância da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), passando um callback de tratamento de exceções para lidar com quaisquer exceções encontradas durante o processo.
2. Carregue o arquivo OLM chamando o método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) da instância OlmStorage. 
3. Se o arquivo OLM for carregado com sucesso, obtenha a hierarquia de pastas chamando o método [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) na instância OlmStorage. Isso retorna uma lista de objetos OlmFolder.
4. Chame o método ExtractItems, passando a instância OlmStorage e a lista de objetos OlmFolder.
5. No método ExtractItems, itere por cada pasta na lista de pastas.
6. Se a pasta contiver mensagens (e-mails), imprima o nome da pasta no console usando Console.WriteLine(folder).
7. Itere pelas mensagens na pasta atual chamando o método EnumerateMessages na instância OlmStorage, passando a pasta atual como argumento.
8. Imprima o assunto de cada mensagem no console usando Console.WriteLine(msg.Subject).
9. Se a pasta tiver subpastas, chame o método ExtractItems recursivamente, passando a instância OlmStorage e as subpastas da pasta atual.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de tratamento de exceções */ }))
{
    if (olm.Load(fileName))
    {
        var folderHierarchy = olm.GetFolders();
        ExtractItems(olm, folderHierarchy);
    }
}

private static void ExtractItems(OlmStorage olm, List<OlmFolder> folders)
{
    foreach (var folder in folders)
    {
        if (folder.HasMessages)
        {
            Console.WriteLine(folder);

            foreach (var msg in olm.EnumerateMessages(folder))
            {
                Console.WriteLine(msg.Subject);
            }
        }

        if (folder.SubFolders.Count > 0)
        {
            ExtractItems(olm, folder.SubFolders);
        }
    }
}
```
## **Extrair mensagens do OLM por identificadores**

O processo de extração de e-mails ficou mais fácil com a capacidade de extrair mensagens OLM selecionadas por identificadores. Isso é urgente para aplicativos que armazenam identificadores em um banco de dados. Extrair mensagens sob demanda é a maneira eficiente de evitar percorrer todo o armazenamento cada vez para encontrar uma mensagem específica a ser extraída. A propriedade [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) da classe [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) obtém o identificador de entrada da mensagem. O método sobrecarregado [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) obtém a mensagem do OLM. O seguinte trecho de código demonstra o uso dessas características:

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Obter caminho da pasta**

Você também pode obter o caminho das pastas no arquivo OML. O Aspose.Email fornece a propriedade [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) que retorna o caminho da pasta. O seguinte trecho de código demonstra o uso da propriedade [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) para obter os caminhos das pastas no arquivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // imprimir o caminho da pasta atual
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

## **Contar o número de itens na pasta**

Você também pode contar o número de itens na pasta. O Aspose.Email fornece a propriedade [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) que retorna o número de itens na pasta. O seguinte trecho de código demonstra o uso da propriedade [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) para obter o número de itens nas pastas do arquivo OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Contagem de mensagens [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Obter contagem total de itens do OlmStorage**

A classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) também possui o método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) que retorna o número total de itens de mensagens contidos no armazenamento OLM.

```cs
using (var olm = new OlmStorage("storage.olm"))
{
    var count = olm.GetTotalItemsCount();
}
```

### **Extrair mensagens do OLM por identificadores**

Às vezes, é necessário extrair mensagens selecionadas por identificadores. Por exemplo, seu aplicativo armazena identificadores em um banco de dados e extrai uma mensagem sob demanda. Esta é a maneira eficiente de evitar percorrer todo o armazenamento sempre que necessário para encontrar uma mensagem específica a ser extraída. Esse recurso está disponível para armazenamentos OLM.

O código abaixo mostra como extrair mensagens do OLM por identificadores.

O código realiza os seguintes passos:

1. Inicia um loop foreach para iterar por uma lista de objetos [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) . O loop utiliza o método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/) do objeto olmFolder para recuperar uma lista de todas as mensagens na pasta atual sendo iterada.
2. O loop extrai o objeto MapiMessage correspondente do armazenamento chamando o método [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) , passando o [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) da mensagem atual como parâmetro.

O objeto MapiMessage recuperado pode ser usado para acessar e manipular o conteúdo da mensagem. O loop continua até que todas as mensagens na pasta tenham sido processadas.

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Recuperação de Cores de Categorias do Outlook**

Para trabalhar com cores de categoria ou categorias de itens do Outlook armazenadas em arquivos OLM, o Aspose.Email oferece as seguintes soluções:

- A classe [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) - representa categorias de itens do Outlook que estão disponíveis pelo nome e cores associadas, representadas em formato hexadecimal.
- O método [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) - recupera a lista de categorias.

O seguinte exemplo de código demonstra como obter todas as categorias usadas do armazenamento OLM:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
    
    foreach (var category in categories)
    {
        Console.WriteLine($"Nome da categoria: {category.Name}");
        
        //A cor é representada como um valor hexadecimal: #rrggbb
        Console.WriteLine($"Cor da categoria: {category.Color}");
    }
}
```
O exemplo de código abaixo mostra como obter a cor de uma categoria de mensagem:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Nome da categoria: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Cor da categoria: {categoryColor}");
        }
    }
}
```