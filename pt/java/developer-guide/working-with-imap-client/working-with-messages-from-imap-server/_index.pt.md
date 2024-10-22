---
title: "Trabalhando com Mensagens de Servidor IMAP"
url: /pt/java/trabalhando-com-mensagens-de-servidor-imap/
weight: 20
type: docs
---


## **Listando IDs de Mensagens MIME do Servidor**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) fornece o MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) para identificação de mensagens sem extrair a mensagem completa. O seguinte trecho de código mostra como listar o messageId MIME.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");

try {
    ImapMessageInfoCollection messageInfoCol = client.listMessages("Inbox");
    for (ImapMessageInfo info : messageInfoCol) {
        // Display MIME Message ID
        System.out.println("Message Id = " + info.getMessageId());
    }
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Listando Mensagens do Servidor**

Aspose.Email fornece uma variante sobrecarregada de 2 membros de [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) para recuperar um número especificado de mensagens com base em uma consulta. O seguinte trecho de código mostra como listar mensagens.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
ImapQueryBuilder builder = new ImapQueryBuilder();
MailQuery query = builder
        .or(builder.or(builder.or(builder.or(builder.getSubject().contains(" (1) "), builder.getSubject().contains(" (2) ")), builder.getSubject().contains(" (3) ")),
                builder.getSubject().contains(" (4) ")), builder.getSubject().contains(" (5) "));
ImapMessageInfoCollection messageInfoCol4 = client.listMessages(query, 4);
System.out.println((messageInfoCol4.size() == 4) ? "Success" : "Failure");
~~~

## **Listando Mensagens do Servidor Recursivamente**

O protocolo IMAP suporta a listagem de mensagens recursivamente de uma pasta de correio. Isso ajuda a listar mensagens de subpastas de uma pasta também. O seguinte trecho de código mostra como listar mensagens recursivamente.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");
ImapMessageInfoCollection msgsColl = client.listMessages(true);
System.out.println("Total Messages: " + msgsColl.size());
~~~

## **Listando Mensagens com MultiConnection**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de multiconexão usando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). O seguinte trecho de código demonstra o uso do modo de multiconexão para listar mensagens e compara seu desempenho com o modo de conexão única.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

imapClient.selectFolder("Inbox");
imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol1 = imapClient.listMessages(true);
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

imapClient.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol2 = imapClient.listMessages(true);
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~
{{% alert color="primary" %}} 

Por favor, note que o uso do modo de multiconexão não garante aumento de desempenho.

{{% /alert %}} 

## **Obter Mensagens em ordem decrescente**

Aspose.Email fornece o método [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) que lista mensagens com suporte a paginação. Algumas sobrecargas de [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) aceitam [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) como um parâmetro. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) fornece uma propriedade [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) que, quando definida como **false**, retorna emails em ordem decrescente.

O seguinte exemplo de código demonstra o uso da propriedade [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) da classe [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) para alterar a ordem dos emails.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

PageSettings pageSettings = new PageSettings();
pageSettings.setAscendingSorting(false);
ImapPageInfo pageInfo = imapClient.listMessagesByPage(5, pageSettings);
ImapMessageInfoCollection messages = pageInfo.getItems();

for (ImapMessageInfo message : messages) {
    System.out.println(message.getSubject() + " -> " + message.getDate().toString());
}
~~~

## **Buscar Mensagens do Servidor e Salvar no disco**

A classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) pode buscar mensagens de um servidor IMAP e salvar as mensagens no formato EML em um disco local. Os seguintes passos são necessários para salvar as mensagens no disco:

1. Crie uma instância da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especifique um nome de host, porta, nome de usuário e senha no [construtor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)) do ImapClient.
1. Selecione a pasta usando o método [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-).
1. Chame o método [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) para obter o objeto [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/).
1. Faça a iteração pela coleção [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/), chame o método [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) e forneça o caminho de saída e o nome do arquivo.

O seguinte trecho de código mostra como buscar mensagens de email de um servidor e salvá-las.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the EML file locally
    client.saveMessage(list.get_Item(i).getUniqueId(), dataDir + list.get_Item(i).getUniqueId() + ".eml");
}
~~~ 

## **Salvando Mensagens em Formato MSG**

[No exemplo acima](#fetch-messages-from-server-and-save-to-disc), os emails são salvos no formato EML. Para salvar emails em formato MSG, o método [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-) precisa ser chamado. Ele retorna a mensagem em uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). O método [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) pode então ser chamado para salvar a mensagem em MSG. O seguinte trecho de código mostra como salvar mensagens em Formato MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the file directory.
String dataDir = "data/";

// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the message in MSG format
    MailMessage message = client.fetchMessage(list.get_Item(i).getUniqueId());
    message.save(dataDir + list.get_Item(i).getUniqueId() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~ 

## **Busca de Mensagens em Grupo**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece um método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) que aceita iteráveis de números de sequência ou ID único e retorna uma lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). O seguinte trecho de código demonstra o uso do método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) para buscar mensagens por números de sequência e ID único.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (ImapMessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : imapClient.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : imapClient.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~ 

## **Threading de Email/Organizar Emails em Conversas**

Aspose.Email torna possível agrupar todos os encaminhamentos, respostas e mensagens de resposta de todos relacionadas à mesma conversa juntas de maneira hierárquica. Basicamente, o protocolo IMAP pode suportar a capacidade THREAD definida na RFC-5256. Além disso, há outra extensão IMAP fornecida pelo Gmail e descrita como X-GM-EXT-1.

Os seguintes recursos de threading de email estão disponíveis para uso:

- [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) método - Recebe threads de mensagem pelo [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - Obtém informações se a extensão Gmail X-GM-EXT-1 é suportada.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - Obtém informações se a extensão THREAD é suportada.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - Obtém algoritmos THREAD suportados.

Os seguintes exemplos de código mostram o uso desses recursos para obter as threads de email do Gmail:

```java
  ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password", SecurityOptions.SSLImplicit);

try {

    client.selectFolder(ImapFolderInfo.IN_BOX);

   // get a list of messages that we'll group by conversation

   ImapMessageInfoCollection messages = client.listMessages();

   // make sure the IMAP server supports X-GM-EXT-1 extension

   if (client.getGmExt1Supported()) {

       // gets unique conversationId for our example

       Set<String> conversationIds = new HashSet<String>();

       for (ImapMessageInfo messageInfo : messages) {

           if (messageInfo.getConversationId() != null)

                conversationIds.add(messageInfo.getConversationId());

       }

       for (String conversationId : conversationIds) {

           // create the necessary search conditions for a thread

           XGMThreadSearchConditions conditions = new XGMThreadSearchConditions();

            conditions.setConversationId(conversationId);

            conditions.setUseUId(true);

           // get results

           List<MessageThreadResult> conversation = client.getMessageThreads(conditions);

           // print the email conversation in hierarchically manner

           printConversaton("", conversation, messages);

            System.out.println("--------------------");

       }

   }

} finally {

    client.dispose();

}

/**

 * <p>

 * Prints the email conversation in hierarchically manner

 * </p>

 */

public static void printConversaton(String indent, Iterable<MessageThreadResult> conversation,

    Iterable<ImapMessageInfo> messages) {

   for (MessageThreadResult thread : conversation) {

       for (ImapMessageInfo messageInfo : messages) {

           if (thread.getUniqueId().equals(messageInfo.getUniqueId())) {

                System.out.println(indent + " (" + thread.getUniqueId() + ") " + messageInfo.getSubject());

               break;

           }

       }

       if (thread.getChildMessages().size() != 0) {

            printConversaton(indent += "-", thread.getChildMessages(), messages);

       }

   }

}
```
O código muda ligeiramente se o servidor IMAP suportar a capacidade THREAD:

Verifique se o servidor IMAP suporta a extensão THREAD:

```java
 if (client.getThreadSupported())
```
Crie as condições de pesquisa adequadas para uma thread:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
```

## **Listando Mensagens com Suporte a Paginação**

Em cenários onde o servidor de email contém um grande número de mensagens na caixa de correio, muitas vezes é desejável listar ou recuperar as mensagens com suporte a paginação. A API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) permite que você recupere as mensagens do servidor com suporte a paginação.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows the paging support of ImapClient for listing messages from the server
// Available in Aspose.Email for Java and onwards
final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    try {
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        // Create some test messages and append these to server's inbox
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157 - " + UUID.randomUUID(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        // List messages from inbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages();
        // Verify the number of messages added
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETRIEVE THE MESSAGES USING PAGING SUPPORT////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();
        PageSettings pageSettings = new PageSettings();
        ImapPageInfo pageInfo = client.listMessagesByPage(itemsPerPage, 0, pageSettings);
        System.out.println(pageInfo.getTotalCount());
        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(itemsPerPage, pageInfo.getNextPage().getPageOffset(), pageSettings);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;

        // foreach to while statements conversion
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~ 

## **Obtendo Pastas e Lendo Mensagens Recursivamente**

Neste artigo, a maioria dos recursos do [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) é usada para criar um aplicativo que lista todas as pastas e subpastas recursivamente de um servidor IMAP. Ele também salva as mensagens em cada pasta e subpasta no formato MSG em um disco local. Nos discos, as pastas e mensagens são criadas e salvas na mesma estrutura hierárquica que no servidor IMAP. O seguinte trecho de código mostra como obter as mensagens e informações de subpastas recursivamente.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Create an instance of the ImapClient class
    ImapClient client = new ImapClient();

    // Specify host, username, password, Port and SecurityOptions for your client
    client.setHost("imap.gmail.com");
    client.setUsername("your.username@gmail.com");
    client.setPassword("your.password");
    client.setPort(993);
    client.setSecurityOptions(SecurityOptions.Auto);
    try {
        // The root folder (which will be created on disk) consists of host and username
        String rootFolder = client.getHost() + "-" + client.getUsername();

        // Create the root folder and List all the folders from IMAP server
        new File(rootFolder).mkdirs();
        ImapFolderInfoCollection folderInfoCollection = client.listFolders();
        for (ImapFolderInfo folderInfo : folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listMessagesInFolder(folderInfo, rootFolder, client);
        }
        // Disconnect to the remote IMAP server
        client.dispose();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex);
    }

    System.out.println("Downloaded messages recursively from IMAP server.");
}

/// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(ImapFolderInfo folderInfo, String rootFolder, ImapClient client) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = "data/";
    new File(currentFolder).mkdirs();

    // Read the messages from the current folder, if it is selectable
    if (folderInfo.getSelectable()) {
        // Send status command to get folder info
        ImapFolderInfo folderInfoStatus = client.getFolderInfo(folderInfo.getName());
        System.out.println(folderInfoStatus.getName() + " folder selected. New messages: " + folderInfoStatus.getNewMessageCount() + ", Total messages: "
                + folderInfoStatus.getTotalMessageCount());

        // Select the current folder and List messages
        client.selectFolder(folderInfo.getName());
        ImapMessageInfoCollection msgInfoColl = client.listMessages();
        System.out.println("Listing messages....");
        for (ImapMessageInfo msgInfo : msgInfoColl) {
            // Get subject and other properties of the message
            System.out.println("Subject: " + msgInfo.getSubject());
            System.out.println("Read: " + msgInfo.isRead() + ", Recent: " + msgInfo.getRecent() + ", Answered: " + msgInfo.getAnswered());

            // Get rid of characters like ? and :, which should not be included in a file name and Save the message in MSG format
            String fileName = msgInfo.getSubject().replace(":", " ").replace("?", " ");
            MailMessage msg = client.fetchMessage(msgInfo.getSequenceNumber());
            msg.save(currentFolder + "\\" + fileName + "-" + msgInfo.getSequenceNumber() + ".msg", SaveOptions.getDefaultMsgUnicode());
        }
        System.out.println("============================\n");
    } else {
        System.out.println(folderInfo.getName() + " is not selectable.");
    }

    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ImapFolderInfoCollection folderInfoCollection = client.listFolders(folderInfo.getName());
        for (ImapFolderInfo subfolderInfo : folderInfoCollection) {
            listMessagesInFolder(subfolderInfo, rootFolder, client);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~ 

## **Obter UID ou Número de Sequência da Mensagem**

A API pública Aspose.Email fornece os seguintes recursos para obter as informações de identificação da mensagem, como UID ou número de sequência que podem ser necessárias ao processar mensagens recebidas do servidor:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) classe - Representa informações de identificação sobre uma mensagem em uma caixa de correio.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) método - Obtém o número de sequência de uma mensagem.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) método - Obtém o ID único de uma mensagem.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) classe - Representa uma mensagem de e-mail e permite o acesso às propriedades da mensagem, ex. assunto, corpo, remetente e endereços de destinatários, etc.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) método - Representa informações de identificação sobre uma mensagem em uma caixa de correio.

O exemplo de código abaixo demonstra como buscar e exibir os detalhes das mensagens da pasta "INBOX" em um servidor IMAP usando a classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
try (ImapClient client = new ImapClient(imapHost, port, emailAddress, password, securityOption)) {
    ImapMessageInfoCollection msgs = client.listMessages("INBOX");
    List<Integer> seqIds = new ArrayList<>();
    for (ImapMessageInfo msg : msgs) {
        seqIds.add(msg.getSequenceNumber());
    }
    Iterable<MailMessage> msgsViaFetch = client.fetchMessagesBySequences(seqIds);
    for (MailMessage thisMsg : msgsViaFetch) {
        System.out.println("Message ID: " + thisMsg.getItemId().getUniqueId()
                + " SequenceNumber: " + thisMsg.getItemId().getSequenceNumber()
                + " Subject: " + thisMsg.getSubject());
    }
}
```

## **Recuperando Parâmetros Extras como Informações Resumidas**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("host.domain.com", "username", "password");
try {
    MailMessage message = new MailMessage("from@domain.com", "to@doman.com", "EMAILNET-38466 - " + UUID.randomUUID().toString(),
            "EMAILNET-38466 Add extra parameters for UID FETCH command");

    // append the message to the server
    String uid = client.appendMessage(message);

    // wait for the message to be appended
    Thread.sleep(5000);

    // Define properties to be fetched from server along with the message
    List<String> messageExtraFields = Arrays.asList("X-GM-MSGID", "X-GM-THRID");

    // retreive the message summary information using it's UID
    ImapMessageInfo messageInfoUID = client.listMessage(uid, messageExtraFields);

    // retreive the message summary information using it's sequence number
    ImapMessageInfo messageInfoSeqNum = client.listMessage(1, messageExtraFields);

    // List messages in general from the server based on the defined properties
    ImapMessageInfoCollection messageInfoCol = client.listMessages(messageExtraFields);

    ImapMessageInfo messageInfoFromList = messageInfoCol.get_Item(0);

    // verify that the parameters are fetched in the summary information
    for (String paramName : messageExtraFields) {
        System.out.println(messageInfoFromList.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoUID.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoSeqNum.getExtraParameters().containsKey(paramName));
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~ 

## **Obtendo Informações de Cabeçalho List-Unsubscribe**

O cabeçalho List-Unsubscribe contém a URL para cancelar a assinatura de listas de email, como anúncios, boletins informativos, etc. Para obter o cabeçalho List-Unsubscribe, use a propriedade [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) da classe [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/). O seguinte exemplo mostra o uso da propriedade [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) para obter o cabeçalho List-Unsubscribe.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
for (ImapMessageInfo imapMessageInfo : messageInfoCol) {
    System.out.println("ListUnsubscribe Header: " + imapMessageInfo.getListUnsubscribe());
}
~~~