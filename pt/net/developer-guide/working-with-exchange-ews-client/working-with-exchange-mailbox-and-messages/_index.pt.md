---
title: "Trabalhando com Caixas de Correio e Mensagens do Exchange - Ler Email do Servidor Exchange em C#"
url: /pt/net/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Trabalhando com Caixas de Correio e Mensagens do Exchange"
keywords: "c# ler email do servidor exchange"
---


## **Obter Informações da Caixa de Correio Usando EWS**

A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) possui membros que podem ser usados para obter informações da caixa de correio em um Servidor Exchange chamando o método [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/). Ele retorna uma instância do tipo [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Obtenha informações da caixa de correio a partir de propriedades como [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) e [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). Este artigo mostra como acessar informações da caixa de correio usando os Serviços Web do Exchange.

Se você deseja se conectar ao Servidor Exchange usando os Serviços Web do Exchange (EWS), use a classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) no namespace Aspose.Email.Exchange. Esta classe utiliza EWS para se conectar e gerenciar itens em um Servidor Exchange. O seguinte trecho de código C# mostra como obter informações da caixa de correio usando os serviços web do Exchange.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe EWSClient fornecendo as credenciais         
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha o tamanho da caixa de correio, informações da caixa de correio do exchange, URI da Caixa de Correio e da Caixa de Entrada
Console.WriteLine("Tamanho da caixa de correio: " + client.GetMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("URI da Caixa de Correio: " + mailboxInfo.MailboxUri);
Console.WriteLine("URI da Caixa de Entrada: " + mailboxInfo.InboxUri);
Console.WriteLine("URI de Itens Enviados: " + mailboxInfo.SentItemsUri);
Console.WriteLine("URI da Caixa de Projetos: " + mailboxInfo.DraftsUri);
```

## **Enviando Mensagens de Email**

Você pode enviar mensagens de email usando um Servidor Exchange com a ajuda das ferramentas em [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). O método [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) aceita uma instância de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) como parâmetro e envia o email. Este artigo explica como enviar mensagens de email usando os Serviços Web do Exchange.

Aspose.Email fornece a classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) para conectar-se ao Microsoft Exchange Server usando os Serviços Web do Exchange. O seguinte trecho de código C# mostra como usar EWS para enviar emails com o Microsoft Exchange Server. O seguinte trecho de código C# mostra como enviar mensagens de email usando EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crie uma instância do tipo MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@domain.com";
msg.Subject = "Enviando mensagem do servidor exchange";
msg.HtmlBody = "<h3>enviando mensagem do servidor exchange</h3>";

// Envie a mensagem
client.Send(msg);
```

## **Obtendo URI do Item Enviado**

Um Id de email enviado pode ser recuperado do servidor Exchange com o seguinte código de exemplo:

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Registre o manipulador de eventos
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "mensagem teste", "Esta é uma mensagem teste");

    client.Send(eml);
}
```

onde o método delegado é:

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Defina um método manipulador de eventos
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
    
    // Agora podemos obter um id do email enviado, que foi salvo na pasta Itens Enviados
    string id = e.SentFolderItemId;
}
```

## **Lendo Emails da Caixa de Correio de Outro Usuário**

Algumas contas em Servidores Exchange têm o direito de acessar várias caixas de correio, e alguns usuários têm várias contas de email no mesmo Servidor Exchange. Em ambos os casos, os usuários podem acessar as caixas de correio de outros usuários usando Aspose.Email para .NET. Esta API fornece um mecanismo para acessar pastas e emails de outras caixas de correio usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods). Essa funcionalidade pode ser alcançada usando o método sobrecarregado [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) e fornecendo o endereço de email do usuário como parâmetro.

O seguinte trecho de código C# mostra como ler emails usando a classe IEWSClient.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha informações da caixa de correio do outro usuário
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Listando Mensagens**

Uma lista das mensagens de email em uma caixa de correio Exchange pode ser obtida chamando o método [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). Obtenha as informações básicas sobre as mensagens, como assunto, de, para e ID da mensagem, usando o método ListMessage.

### **Listagem Simples de Mensagens**

Para listar as mensagens em uma caixa de correio Exchange:

1. Crie uma instância da interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) e crie uma coleção de mensagens.
1. Percorra a coleção e exiba as informações da mensagem.

O seguinte trecho de código C# mostra como conectar-se a um servidor Exchange usando EWS e listar mensagens da pasta de entrada.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Chame o método ListMessages para listar informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorra a coleção para exibir as informações básicas
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Assunto: " + msgInfo.Subject);
    Console.WriteLine("De: " + msgInfo.From.ToString());
    Console.WriteLine("Para: " + msgInfo.To.ToString());
    Console.WriteLine("ID da Mensagem: " + msgInfo.MessageId);
    Console.WriteLine("URI Único: " + msgInfo.UniqueUri);
}
```

### **Listando Mensagens de Pastas Diferentes**

[Os trechos de código acima](#simple-messages-listing) listam todas as mensagens na pasta da Caixa de Entrada. É possível obter a lista de mensagens de outras pastas também. O método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) aceita um URI de pasta como parâmetro. Desde que o URI da pasta seja válido, você pode obter a lista de mensagens daquela pasta. Use a propriedade [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties) para obter o URI de diferentes pastas. O restante do código é o mesmo para obter uma lista de mensagens. O seguinte trecho de código mostra como listar mensagens de pastas diferentes usando EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha o URI da pasta
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Obtenha a lista de mensagens da pasta especificada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **Listando Mensagens com Suporte a Paginação**

O seguinte trecho de código mostra como obter uma lista de mensagens com suporte a paginação.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Crie algumas mensagens de teste para serem adicionadas ao servidor para recuperação posterior
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Move parâmetros de paginação para uma classe separada");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Verifique se as mensagens foram adicionadas ao servidor
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// RECUPERANDO AS MENSAGENS USANDO SUPORTE A PAGINAÇÃO ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Total de Páginas
        Console.WriteLine(pageInfo.TotalCount);

        pages.Add(pageInfo);
        while (!pageInfo.LastPage)
        {
            pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage, pageInfo.PageOffset + 1);
            pages.Add(pageInfo);
        }
        int retrievedItems = 0;
        foreach (ExchangeMessagePageInfo pageCol in pages)
            retrievedItems += pageCol.Items.Count;
        // Verifique o total de mensagens usando paginação
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}          
```

### **Obtendo Informações do Tipo da Mensagem a partir de ExchangeMessageInfo**

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @""; 
const string username = @"username@ASE305.onmicrosoft.com";
const string password = @"password"; 
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```
### **Recuperando a Classe da Mensagem do Objeto ExchangeMessageInfo**

A classe da mensagem representa o tipo de um item no armazenamento do Exchange. Ao obter a classe da mensagem, você pode determinar o tipo da mensagem de email do Exchange e realizar operações específicas com base em sua classificação. 

Abaixo está um exemplo de obtenção da classe da mensagem usando a classe [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) do Aspose.Email para .NET:

**Exemplo de código**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Classe da Mensagem: {0}", messageInfo.MessageClass);
    }
}
```

## **Salvando Mensagens**

Este artigo mostra como obter mensagens de uma caixa de correio de um Servidor Exchange e salvá-las em disco nos formatos EML e MSG:

- Salvar como EML em disco.
- Salvar em um fluxo de memória.
- Salvar como MSG.
  
### **Salvando Mensagens em EML**

Para obter mensagens e salvar no formato EML:

1. Crie uma instância da interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Forneça o mailboxUri, nome de usuário, senha e domínio.
1. Chame o método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obter uma instância do [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/).
1. Percorra a [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/) para obter o URI único para cada mensagem.
1. Chame o método [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) e passe o URI único como um parâmetro.
1. Forneça ao método [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/savemessage/) o caminho para onde deseja salvar o arquivo.

O seguinte trecho de código mostra como usar EWS para se conectar ao Servidor Exchange e salvar mensagens como arquivos EML.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Crie uma instância da interface IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorra a coleção para obter o URI da Mensagem
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Agora salve a mensagem em disco
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Salvando Mensagens em um Fluxo de Memória**

Em vez de salvar arquivos EML em disco, é possível salvá-los em um fluxo de memória. Isso é útil quando você deseja salvar o fluxo em algum local de armazenamento, como um banco de dados. Uma vez que o fluxo tenha sido salvo em um banco de dados, você pode recarregar o arquivo EML na classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O seguinte trecho de código mostra como salvar mensagens de uma caixa de correio de um Servidor Exchange em um fluxo de memória usando EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
string datadir = RunExamples.GetDataDir_Exchange();
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorra a coleção para obter o URI da Mensagem
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Agora salve a mensagem em um fluxo de memória
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, datadir + stream);
}
```

### **Salvando Mensagens no Formato MSG**

O método [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) pode salvar diretamente a mensagem no formato EML. Para salvar as mensagens no formato MSG, primeiro chame o método [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) que retorna uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Em seguida, chame o método [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para salvar a mensagem como MSG. O seguinte trecho de código mostra como obter mensagens de uma caixa de correio de um Servidor Exchange e salvá-las no formato MSG usando EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Percorra a coleção para obter o URI da Mensagem
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
    
    // Obtenha os detalhes da mensagem usando FetchMessage() e salve a mensagem como Msg 
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Obtendo ExchangeMessageInfo a partir do URI da Mensagem**

Uma mensagem de email é representada por seu identificador único, URI, e é parte integral do objeto [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Caso somente o URI da mensagem esteja disponível, o objeto [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) também pode ser recuperado usando essa informação disponível. A versão sobrecarregada de [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) aceita uma lista de Ids para usar [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). O seguinte trecho de código mostra como obter [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) a partir do URI da mensagem.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Mensagens salvas da pasta Itens Enviados não contêm campo 'Para'");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Faça algo ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

## **Buscar Mensagens de uma Caixa de Correio do Servidor Exchange**

Para listar mensagens em um Servidor Exchange, o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) é utilizado para obter uma lista de mensagens de uma caixa de correio do Servidor Exchange. O método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) obterá informações básicas sobre as mensagens, por exemplo, o assunto, o ID da mensagem, o de e o para. Para obter os detalhes completos da mensagem, Aspose.Email.Exchange fornece o método [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/). Este método aceita o URI da mensagem como parâmetro e retorna uma instância da classe [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) fornece os detalhes da mensagem como corpo, cabeçalhos e anexos. Descubra mais sobre a API MailMessage ou descubra como gerenciar emails com a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Para buscar mensagens da caixa de correio do Servidor Exchange:

1. Crie uma instância do tipo [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Especifique o nome do servidor, nome de usuário, senha e domínio.
1. Chame [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obter a [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
1. Percorra a [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) para obter os valores de [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/).
1. Chame [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) e passe [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) como parâmetro.

O seguinte trecho de código mostra como se conectar à caixa de correio do Servidor Exchange e buscar todas as mensagens usando EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorra a coleção para obter o URI da Mensagem
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Agora obtenha os detalhes da mensagem usando FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);
 
    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Nome do Anexo: " + att.Name);
 }
}
```

### **Usando o método FetchItem para buscar uma mensagem**

{{% alert color="primary" %}}

Observe que o método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) retorna a mensagem sem anexos. Para buscar mensagens com anexos, use o método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) descrito na seção abaixo. 

{{% /alert %}}

O método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem) é mais preferido se você deseja buscar uma [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) e operar com propriedades MAPI. Você também pode usar este método para buscar qualquer item do Outlook, como um contato, um compromisso, uma tarefa, etc.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
// Chame o método ListMessages para listar as informações das mensagens da pasta de Contatos
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Percorra a coleção para obter o URI da Mensagem
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Agora obtenha a mensagem usando FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // Se necessário, você pode converter a MapiMessage para o tipo de item apropriado para simplificar o trabalho com suas propriedades.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Usando o método FetchItems**

O método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) descrito acima retorna a mensagem **sem anexos**, em uma tentativa de manter o desempenho.

Para buscar mensagens com anexos, use o mais poderoso método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) que permite passar as opções de [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/).

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

## **Buscando Itens com Anexos**

O método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)(EwsFetchItems options) do EwsClient recupera itens de email de um servidor Exchange. Aceita uma instância da classe [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) como parâmetro para definir várias opções para buscar os itens.

O seguinte código mostra como obter itens com anexos:

```cs
// Chame o método ListMessages para recuperar uma lista de mensagens da pasta da Caixa de Entrada
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Crie uma instância da classe EwsFetchItems e atribua-a à variável options
var options = EwsFetchItems.Create();

// Gere uma nova coleção de mensagens que será convertida em uma Lista.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Busque apenas mensagens contendo anexos
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

## **Pré-Buscar Tamanho da Mensagem**

A InterOp do Microsoft Outlook fornece o recurso de recuperar o tamanho da mensagem antes de realmente buscar a mensagem completa do servidor. No caso da API Aspose.Email, as informações resumidas recuperadas do servidor Exchange são representadas pela classe [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Ela fornece a mesma funcionalidade de recuperação do tamanho da mensagem usando a propriedade [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/). Para recuperar o tamanho da mensagem, a chamada padrão para [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) é usada, a qual recupera uma coleção de [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). O seguinte trecho de código mostra como exibir o tamanho da mensagem usando a classe [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/).

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorra a coleção para exibir as informações básicas
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Assunto: " + msgInfo.Subject);
    Console.WriteLine("De: " + msgInfo.From.ToString());
    Console.WriteLine("Para: " + msgInfo.To.ToString());
    Console.WriteLine("Tamanho da Mensagem: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

## **Baixando Mensagens Recursivamente**

O método [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) pode ser usado para obter mensagens de pastas e subpastas de uma caixa de correio do Servidor Exchange de forma recursiva. Isso requer o Exchange Server 2007 ou superior, pois utiliza EWS. O seguinte trecho de código mostra como baixar toda a caixa de correio (pastas e subpastas) de um Servidor Exchange. A estrutura de pastas é criada localmente e todas as mensagens são baixadas.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Registre o método de callback para o evento de validação do SSL
    ServicePointManager.ServerCertificateValidationCallback += RemoteCertificateValidationHandler;
    try
    {
        DownloadAllMessages();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void DownloadAllMessages()
{
    try
    {
        string rootFolder = domain + "-" + username;
        Directory.CreateDirectory(rootFolder);
        string inboxFolder = rootFolder + "\\Inbox";
        Directory.CreateDirectory(inboxFolder);

        Console.WriteLine("Baixando todas as mensagens da Caixa de Entrada....");
        // Crie uma instância da IEWSClient fornecendo as credenciais
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("URI da Caixa de Correio: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // Liste todas as pastas do servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Chame o método recursivo para ler mensagens e obter subpastas
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("Todas as mensagens baixadas.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Método recursivo para obter mensagens de pastas e subpastas
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Crie a pasta em disco (com o mesmo nome que no servidor IMAP)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // Liste as mensagens
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Listando mensagens....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Obtenha o assunto e outras propriedades da mensagem
        Console.WriteLine("Assunto: " + msgInfo.Subject);

        // Elimine caracteres como ? e :, que não devem ser incluídos no nome do arquivo
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
  
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // Se esta pasta tiver subpastas, chame este método recursivamente para obter mensagens
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        foreach (ExchangeFolderInfo subfolderInfo in folderInfoCollection)
        {
            ListMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    }
    catch (Exception)
    {
    }
}
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // Ignore as verificações e prossiga
}
```

## **Baixando Mensagens de Pastas Públicas**

O Microsoft Exchange Server permite que os usuários criem pastas públicas e postem mensagens nelas. Para fazer isso através de seu aplicativo, use a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) do Aspose.Email para se conectar ao Servidor Exchange e ler e baixar mensagens e postagens de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas, subpastas e listar e baixar quaisquer mensagens encontradas nessas pastas. Este exemplo funciona apenas com o Microsoft Exchange Server 2007 ou superior, pois apenas esses suportam EWS.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
public static string dataDir = RunExamples.GetDataDir_Exchange();
public static string mailboxUri = "https://exchange/ews/exchange.asmx"; // EWS
public static string username = "administrator";
public static string password = "pwd";
public static string domain = "ex2013.local";

public static void Run()
{
    try
    {
        ReadPublicFolders();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void ReadPublicFolders()
{
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.ListPublicFolders();
    foreach (ExchangeFolderInfo publicFolder in folders)
    {
        Console.WriteLine("Nome: " + publicFolder.DisplayName);
        Console.WriteLine("Contagem de Subpastas: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);
    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Nome da Pasta: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir +  msg.Subject + ".msg",  SaveOptions.DefaultMsgUnicode);
    }

    // Chame este método recursivamente para quaisquer subpastas
    if (publicFolder.ChildFolderCount > 0)
    {
        ExchangeFolderInfoCollection subfolders = client.ListSubFolders(publicFolder);
        foreach (ExchangeFolderInfo subfolder in subfolders)
        {
            ListMessagesFromSubFolder(subfolder, client);
        }
    }
}
```

## **Movendo Mensagens**

Você pode mover mensagens de email de uma pasta para outra com a ajuda da interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) usando o método [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/). Ele aceita os parâmetros:

- O URI único da mensagem que deve ser movida.
- O URI único da pasta de destino.
  
### **Movendo Mensagens entre Pastas**

O seguinte trecho de código mostra como mover uma mensagem em uma caixa de correio da pasta Caixa de Entrada para uma pasta chamada Processados. Neste exemplo, o aplicativo:

1. Lê mensagens da pasta Caixa de Entrada.
2. Processa algumas das mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
3. Move mensagens que atendem à condição especificada para a pasta processada.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Liste todas as mensagens da pasta Caixa de Entrada
Console.WriteLine("Listando todas as mensagens da Caixa de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Mover mensagem para a pasta "Processados", após processar certas mensagens com base em alguns critérios
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("processar esta mensagem") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Mensagem movida...." + msgInfo.Subject);
    }
    else
    {
        // Fazer outra coisa
    }
}
```

## **Deletando Mensagens**

Você pode deletar mensagens de email de uma pasta com a ajuda da classe [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/exchangeclient/) usando o método [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) que aceita um URI único de uma mensagem como parâmetro.

O seguinte trecho de código mostra como deletar uma mensagem da pasta Caixa de Entrada. Para o propósito deste exemplo, o código:

1. Lê mensagens da pasta Caixa de Entrada.
2. Processa mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
3. Deleta a mensagem.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
            
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Liste todas as mensagens da pasta Caixa de Entrada
Console.WriteLine("Listando todas as mensagens da Caixa de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Deletar mensagem com base em alguns critérios
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("deletar") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Mensagem deletada...." + msgInfo.Subject);
    }
    else
    {
        // Fazer outra coisa
    }
}
```

## **Copiando Mensagens**

A API Aspose.Email permite copiar uma mensagem de uma pasta para outra usando o método [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/). A versão sobrecarregada deste método retorna o URI Único da mensagem copiada, conforme mostrado neste artigo.

### **Copiando uma Mensagem para Outra Pasta**

O seguinte trecho de código mostra como copiar uma mensagem para outra pasta.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Crie uma instância da classe EWSClient fornecendo as credenciais
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Copie uma mensagem e obtenha referência ao novo item Copiado");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```