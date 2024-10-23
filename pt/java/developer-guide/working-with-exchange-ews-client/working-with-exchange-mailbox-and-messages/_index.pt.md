---
title: "Trabalhando com Caixa de Correio do Exchange e Mensagens - Ler Email do Servidor Exchange em Java"
url: /pt/java/trabalhando-com-caixa-de-correio-do-exchange-e-mensagens/
weight: 20
type: docs
linktitle: "Trabalhando com Caixa de Correio do Exchange e Mensagens"
keywords: "java ler email do servidor exchange"
---


## **Obtendo Informações da Caixa de Correio Usando EWS**
A classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) possui membros que podem ser usados para obter informações da caixa de correio de um servidor Exchange chamando o método [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)). Ele retorna uma instância do tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Obtenha informações da caixa de correio a partir de propriedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) e [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). Este artigo mostra como acessar as informações da caixa de correio usando os Serviços Web do Exchange.

Se você deseja se conectar ao Servidor Exchange usando os Serviços Web do Exchange (EWS), use a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient). Esta classe usa EWS para se conectar e gerenciar itens em um servidor Exchange. O seguinte trecho de código Java mostra como obter informações da caixa de correio usando os serviços web de exchange.



~~~Java
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha o tamanho da caixa de correio, informações da caixa de correio do exchange, URI da Caixa de Correio e da Caixa de Entrada
System.out.println("Tamanho da caixa de correio: " + client.getMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("URI da caixa de correio: " + mailboxInfo.getMailboxUri());
System.out.println("URI da pasta de entrada: " + mailboxInfo.getInboxUri());
System.out.println("URI de itens enviados: " + mailboxInfo.getSentItemsUri());
System.out.println("URI da pasta de rascunhos: " + mailboxInfo.getDraftsUri());
~~~

## **Enviando Mensagens de Email**
Você pode enviar mensagens de email usando um servidor Exchange com a ajuda das ferramentas em [Aspose.Email.Exchange](#trabalhando-com-caixa-de-correio-do-exchange-e-mensagens). O método IEWSClient.Send() aceita uma instância [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) como parâmetro e envia o email. Este artigo explica como enviar mensagens de email usando os Serviços Web do Exchange.

Aspose.Email fornece a classe IEWSClient para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. O seguinte trecho de código mostra como usar EWS para enviar emails usando o Microsoft Exchange Server. O seguinte trecho de código Java mostra como enviar mensagens de email usando EWS.



~~~Java
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crie uma instância do tipo MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Enviando mensagem do servidor exchange");
msg.setHtmlBody("<h3>enviando mensagem do servidor exchange</h3>")

// Envie a mensagem
client.send(msg);
~~~

## **Obtendo a Classe da Mensagem**

O método [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) da classe [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) obtém uma string representando a classe da mensagem. O exemplo de código abaixo mostra como obter a classe da mensagem:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Classe da Mensagem: " + messageInfo.getMessageClass());
    }
}
```
## **Lendo Emails da Caixa de Correio de Outro Usuário**
Algumas contas em servidores Exchange têm o direito de acessar várias caixas de correio, e alguns usuários têm várias contas de email no mesmo servidor Exchange. Em ambos os casos, os usuários podem acessar as caixas de correio de outros usuários usando Aspose.Email para Java. Esta API fornece um mecanismo para acessar pastas e emails de outras caixas de correio usando a classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Essa funcionalidade pode ser alcançada usando o método sobrecarregado [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)) e fornecendo o endereço de email do usuário como parâmetro.

O seguinte trecho de código mostra como ler emails usando a classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha informações da caixa de correio do outro usuário
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~

## **Listando Mensagens**
Uma lista das mensagens de email em uma caixa de correio Exchange pode ser obtida chamando o método [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)). Obtenha informações básicas sobre as mensagens, como assunto, de, para e ID da mensagem, usando o método [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)).
### **Listagem Simples de Mensagens**
Para listar as mensagens em uma caixa de correio Exchange:

1. Crie uma instância da classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
1. Chame o método listMessages e crie uma coleção de mensagens.
1. Percorra a coleção e exiba as informações da mensagem.

O seguinte trecho de código Java mostra como se conectar a um servidor exchange usando EWS e lista as mensagens da pasta de entrada.



~~~Java
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para exibir as informações básicas
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Assunto: " + msgInfo.getSubject());
    System.out.println("De: " + msgInfo.getFrom().toString());
    System.out.println("Para: " + msgInfo.getTo().toString());
    System.out.println("ID da Mensagem: " + msgInfo.getMessageId());
    System.out.println("URI Único: " + msgInfo.getUniqueUri());
}
~~~
### **Listando Mensagens de Diferentes Pastas**
[Os trechos de código acima](#listagem-simples-de-mensagens), listam todas as mensagens da pasta de entrada. É possível obter a lista de mensagens de outras pastas também. O método [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) aceita um URI de pasta como parâmetro. Enquanto o URI da pasta for válido, você pode obter a lista de mensagens dessa pasta. Use a propriedade IEWSClient.getMailboxInfo().getXXXFolderUri para obter o URI de diferentes pastas. O restante do código é o mesmo para obter uma lista de mensagens. O seguinte trecho de código mostra como listar mensagens de diferentes pastas usando EWS.


~~~Java
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtenha o URI da pasta
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Obtenha a lista de mensagens da pasta especificada
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Listando Mensagens com Suporte a Paginação**
O seguinte trecho de código Java mostra como obter uma lista de mensagens com suporte a paginação.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Crie algumas mensagens de teste para serem adicionadas ao servidor para recuperação mais tarde
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Mover parâmetros de paginação para classe separada");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Verifique se as mensagens foram adicionadas ao servidor
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RECUPERANDO AS MENSAGENS USANDO SUPORTE A PAGINAÇÃO ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Contagem total de Páginas
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // Conversão de declarações foreach para while
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Verifique a contagem total de mensagens usando paginação
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    client.dispose();
}
~~~
### **Obtendo Informações do Tipo de Mensagem a partir de ExchangeMessageInfo**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.listMessages(client.getMailboxInfo().getDeletedItemsUri());
System.out.println(list.get_Item(0).getMessageInfoType()); // MessageInfoType
~~~
## **Salvando Mensagens**
Este artigo mostra como obter mensagens de uma caixa de correio de servidor Exchange e salvá-las em disco nos formatos EML e MSG:

- Salvar como EML no disco.
- Salvar em fluxo de memória.
- Salvar como MSG.
### **Salvando Mensagens em EML**
Para obter mensagens e salvar no formato EML:

1. Crie uma instância da classe IEWSClient.
2. Forneça o mailboxUri, nome de usuário, senha e domínio.
3. Chame o método IEWSClient.listMessages() para obter uma instância da coleção ExchangeMessagesInfoCollection.
4. Percorra a coleção ExchangeMessagesInfoCollection para obter o URI exclusivo de cada mensagem.
5. Chame o método IEWSClient.saveMessage() e passe o URI exclusivo como parâmetro.
6. Forneça o método saveMessage() com um caminho para onde você deseja salvar o arquivo.

O seguinte trecho de código mostra como usar EWS para se conectar ao Servidor Exchange e salvar mensagens como arquivos EML.



~~~Java
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para obter o URI da Mensagem
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Agora salve a mensagem em disco
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Salvando Mensagens em um Fluxo de Memória**
Em vez de salvar arquivos EML no disco, é possível salvá-los em um fluxo de memória. Isso é útil quando você deseja salvar o fluxo em algum local de armazenamento, como um banco de dados. Depois que o fluxo for salvo em um banco de dados, você pode recarregar o arquivo EML na classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). O seguinte trecho de código mostra como salvar mensagens de uma caixa de correio de servidor Exchange em um fluxo de memória usando EWS.



~~~Java
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para obter o URI da Mensagem
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Agora salve a mensagem em um fluxo de memória
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Salvando Mensagens no Formato MSG**
O método [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) pode salvar diretamente a mensagem no formato EML. Para salvar as mensagens no formato MSG, primeiro chame o método [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)) que retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Em seguida, chame o método [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)) para salvar a mensagem como MSG. O seguinte trecho de código mostra como obter mensagens de uma caixa de correio de servidor Exchange e salvá-las no formato MSG usando EWS.



~~~Java
// Crie uma instância da classe EWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Percorra a coleção para obter o URI da Mensagem
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Agora obtenha os detalhes da mensagem usando FetchMessage() e salve a mensagem como Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Obtendo ExchangeMessageInfo a partir do URI da Mensagem**
Uma mensagem de email é representada pelo seu identificador único, URI, e é parte integral do objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). No caso de apenas o URI da mensagem estar disponível, o objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) também pode ser recuperado usando essa informação disponível. A versão sobrecarregada do [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) aceita uma lista de IDs para usar [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). O seguinte trecho de código mostra como obter [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) a partir do URI da mensagem.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Mensagens salvas da pasta de Itens Enviados não contêm o campo 'Para'");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Fazer algo...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Buscar Mensagens de uma Caixa de Correio de Servidor Exchange**
Lista de Mensagens em um Servidor Exchange usou o método [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) para obter uma lista de mensagens de uma caixa de correio de servidor Exchange. O método [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) obtém informações básicas sobre as mensagens, por exemplo, o assunto, o ID da mensagem, de e para. Para obter os detalhes completos da mensagem, Aspose.Email.Exchange fornece o método IEWSClient.fetchMessage(). Este método aceita o URI da mensagem como um parâmetro e retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). A classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) então fornece detalhes da mensagem, como corpo, cabeçalhos e anexos. Descubra mais sobre a API [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage), ou descubra como gerenciar emails com a classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Para buscar mensagens da Caixa de Correio do Servidor Exchange:

1. Crie uma instância do tipo IEWSClient.
2. Especifique o nome do servidor, nome de usuário, senha e domínio.
3. Chame listMessages para obter a ExchangeMessageInfoCollection.
4. Percorra a coleção ExchangeMessageInfoCollection para obter os valores ExchangeMessageInfo.UniqueURI.
5. Chame IEWSClient.fetchMessage() e passe ExchangeMessageInfo.UniqueURI como parâmetro.

O seguinte trecho de código mostra como se conectar à caixa de correio do Servidor Exchange e buscar todas as mensagens usando EWS.



~~~Java
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para obter o URI da Mensagem
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Agora obtenha os detalhes da mensagem usando FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Nome do Anexo: " + att.getName());
    }
}
~~~

### **Usando o método FetchItem para buscar uma mensagem**

{{% alert color="primary" %}}

Nota, o método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) retorna a mensagem sem anexos. Para buscar mensagens com anexos, use o método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)), descrito na seção abaixo.

{{% /alert %}}

O método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) é mais preferido se você quiser buscar um [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) e operar com propriedades MAPI. Você também pode usar este método para buscar qualquer item do Outlook, como um contato, compromisso, tarefa, etc.

```java
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para obter o URI da Mensagem
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Agora obtenha a mensagem usando FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // Se necessário, você pode converter o MapiMessage para o tipo de item apropriado para simplificar o trabalho com suas propriedades.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Pré-Busca do Tamanho da Mensagem**
O Microsoft Outlook InterOp fornece a funcionalidade de recuperar o tamanho da mensagem antes de realmente buscar a mensagem completa do servidor. No caso da API Aspose.Email, a informação resumida recuperada do servidor Exchange é representada pela classe [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). Ela fornece o mesmo recurso de recuperar o tamanho da mensagem usando a propriedade Size. Para recuperar o tamanho da mensagem, a chamada padrão ao listMessages do IEWSClient é usada que recupera uma coleção de [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). O seguinte trecho de código mostra como exibir o tamanho da mensagem usando a classe [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo).



~~~Java
// Crie uma instância da classe ExchangeWebServiceClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Chame o método ListMessages para listar as informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Percorra a coleção para exibir as informações básicas
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Assunto: " + msgInfo.getSubject());
    System.out.println("De: " + msgInfo.getFrom().toString());
    System.out.println("Para: " + msgInfo.getTo().toString());
    System.out.println("Tamanho da Mensagem: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Baixando Mensagens Recursivamente**
O método [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) da classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) pode ser usado para obter mensagens de pastas e subpastas de uma caixa de correio de servidor Exchange de forma recursiva. Isso requer o Exchange Server 2007 ou superior, pois utiliza EWS. O seguinte trecho de código mostra como baixar toda a caixa de correio (pastas e subpastas) de um servidor Exchange. A estrutura da pasta é criada localmente e todas as mensagens são baixadas.



~~~Java
public static void run() {
    try {
        downloadAllMessages();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void downloadAllMessages() {
    try {
        String rootFolder = domain + "-" + username;
        new File(rootFolder).mkdirs();
        String inboxFolder = rootFolder + "\\Caixa de Entrada";
        new File(inboxFolder).mkdirs();

        System.out.println("Baixando todas as mensagens da Caixa de Entrada....");
        // Crie uma instância da classe IEWSClient fornecendo as credenciais
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI da caixa de correio: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Liste todas as pastas do servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Chame o método recursivo para ler mensagens e obter subpastas
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("Todas as mensagens baixadas.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Método recursivo para obter mensagens de pastas e subpastas
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Crie a pasta no disco (mesmo nome que no servidor IMAP)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // Liste as mensagens
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Listando mensagens....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Obtenha o assunto e outras propriedades da mensagem
        System.out.println("Assunto: " + msgInfo.getSubject());

        // Remova caracteres como ? e :, que não devem ser incluídos no nome do arquivo
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // Se esta pasta tem subpastas, chame este método recursivamente para obter mensagens
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Baixando Mensagens de Pastas Públicas**
O Microsoft Exchange Server permite que os usuários criem pastas públicas e publiquem mensagens nelas. Para fazer isso através de sua aplicação, use a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) da Aspose.Email para se conectar ao servidor Exchange e ler e baixar mensagens e publicações de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas e subpastas, e listar e baixar quaisquer mensagens encontradas nessas pastas. Este exemplo só funciona com Microsoft Exchange Server 2007 ou superior, já que apenas estes suportam EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Nome: " + publicFolder.getDisplayName());
        System.out.println("Contagem de subpastas: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Nome da Pasta: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Chame este método recursivamente para qualquer subpasta
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Movendo Mensagens**
Você pode mover mensagens de email de uma pasta para outra com a ajuda da classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) usando o método [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)). Ele aceita os parâmetros:

- O URI exclusivo da mensagem que deve ser movida.
- O URI exclusivo da pasta de destino.
### **Movendo Mensagens entre Pastas**
O seguinte trecho de código mostra como mover uma mensagem em uma caixa de correio da pasta Caixa de Entrada para uma pasta chamada Processada. Neste exemplo, a aplicação:

1. Lê mensagens da pasta Caixa de Entrada.
2. Processa algumas das mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
3. Move mensagens que atendem à condição dada para a pasta processada.

~~~Java
// Crie uma instância da classe IEWSClient fornecendo as credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Liste todas as mensagens da pasta Caixa de Entrada
System.out.println("Listando todas as mensagens da Caixa de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Mova a mensagem para a pasta "Processada", após processar certas mensagens com base em alguns critérios
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("processar esta mensagem")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Mensagem movida...." + msgInfo.getSubject());
    } else {
        // Fazer algo diferente
    }
}
~~~
## **Excluindo Mensagens**
Você pode excluir mensagens de email de uma pasta com a ajuda da classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) usando o método [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)). Ele aceita o URI exclusivo da mensagem como parâmetro.

O seguinte trecho de código mostra como excluir uma mensagem da pasta Caixa de Entrada. Para o propósito deste exemplo, o código:

1. Lê mensagens da pasta Caixa de Entrada.
2. Processa mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
3. Exclui a mensagem.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Liste todas as mensagens da pasta Caixa de Entrada
System.out.println("Listando todas as mensagens da Caixa de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Exclua a mensagem com base em alguns critérios
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("excluir") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Mensagem excluída...." + msgInfo.getSubject());
    } else {
        // Fazer algo diferente
    }
}
~~~
## **Copiando Mensagens**
A API Aspose.Email permite copiar uma mensagem de uma pasta para outra usando o método [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). A versão sobrecarregada deste método retorna o URI exclusivo da mensagem copiada, conforme mostrado neste artigo.
### **Copiando uma Mensagem para Outra Pasta**
O seguinte trecho de código mostra como copiar uma mensagem para outra pasta.



~~~Java
try {
    // Crie uma instância da classe EWSClient fornecendo as credenciais
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copiar uma mensagem e obter referência ao novo item Copiado");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~