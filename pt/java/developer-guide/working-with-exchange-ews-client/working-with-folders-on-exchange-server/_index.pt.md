---
title: "Trabalhando com Pastas no Exchange Server"
url: /pt/java/trabalhando-com-pastas-no-exchange-server/
weight: 80
type: docs
---

## **Listando todas as Pastas do Servidor**
A API Aspose.Email fornece a capacidade de se conectar ao Exchange Server e listar todas as pastas e subpastas. Você também pode recuperar todas as subpastas de cada pasta de forma recursiva. Ela também oferece a capacidade de enumerar pastas com paginação a partir do cliente Exchange usando o Exchange Web Service (EWS). Este artigo mostra como recuperar todas as subpastas do servidor Exchange e recuperar pastas com paginação.

O seguinte trecho de código mostra como listar pastas do Exchange Server.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    try {
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
        System.out.println("Baixando todas as mensagens da Caixa de Entrada....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI da Caixa de Correio: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Listar todas as pastas do servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Chama o método recursivo para ler mensagens e obter subpastas
            listSubFolders(client, folderInfo);
        }

        System.out.println("Todas as mensagens baixadas.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void listSubFolders(IEWSClient client, ExchangeFolderInfo folderInfo) {
    // Cria a pasta no disco (mesmo nome que no servidor IMAP)
    System.out.println(folderInfo.getDisplayName());
    try {
        // Se esta pasta tem subpastas, chama este método recursivamente para obter mensagens
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Obter Informações sobre o Tipo de Pasta usando EWS**
A propriedade [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)) fornecida pela classe [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo) pode ser utilizada para obter informações sobre o tipo da pasta. Isso é mostrado no exemplo de código abaixo.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeFolderInfoCollection folderInfoCol = client.listSubFolders(client.getMailboxInfo().getRootUri());
for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCol) {
    switch (folderInfo.getFolderType()) {
    case ExchangeFolderType.Appointment:
        // tratar Compromisso
        break;
    case ExchangeFolderType.Contact:
        // tratar Contato
        break;
    case ExchangeFolderType.Task:
        // tratar Tarefa
        break;
    case ExchangeFolderType.Note:
        // tratar mensagem de email
        break;
    case ExchangeFolderType.StickyNote:
        // tratar Nota Adesiva
        break;
    case ExchangeFolderType.Journal:
        // tratar Diário
        break;
    default:
        break;
    }
}
~~~
## **Enumerando Pastas com Suporte à Paginação usando EWS**
O seguinte trecho de código mostra como usar o suporte à paginação usando EWS.

~~~Java
// Criar instância da classe ExchangeWebServiceClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Chama o método ListMessages para listar informações das mensagens da Caixa de Entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());
int itemsPerPage = 5;
List<PageInfo> pages = new ArrayList<PageInfo>();
PageInfo pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
pages.add(pagedMessageInfoCol);
while (!pagedMessageInfoCol.getLastPage()) {
    pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
    pages.add(pagedMessageInfoCol);
}
pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
while (!pagedMessageInfoCol.getLastPage()) {
    client.listMessages(client.getMailboxInfo().getInboxUri());
}
~~~
## **Acessando Pastas Personalizadas ou Subpastas da Caixa de Correio**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite que os desenvolvedores acessem qualquer pasta personalizada ou subpasta da caixa de correio. A função [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) do [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) retorna a URI de uma pasta/pasta personalizada especificada, que pode ser usada então para acessar a pasta de destino. No exemplo a seguir, uma pasta personalizada chamada "TestInbox", que é criada sob a CAIXA DE ENTRADA, é acessada e todas as mensagens são exibidas desta pasta personalizada. Para realizar essa tarefa, os seguintes passos devem ser seguidos:

1. Inicializar o objeto IEWSClient fornecendo credenciais válidas.
1. Acessar a caixa de correio padrão.
1. Acessar a pasta pai, que é a CAIXA DE ENTRADA neste exemplo. Esta pasta pai também pode ser uma pasta personalizada.
1. Usar folderExists() para buscar a subpasta personalizada especificada, por exemplo "TestInbox". Isso retornará a URI de "TestInbox".
1. Usar esta Uri para acessar todas as mensagens nessa pasta personalizada.

O seguinte trecho de código mostra como acessar pastas personalizadas ou subpastas da caixa de correio com EWS.

~~~Java
// Criar instância da classe EWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Criar instância de ExchangeMailboxInfo, ExchangeMessageInfoCollection
ExchangeMailboxInfo mailbox = client.getMailboxInfo();
ExchangeMessageInfoCollection messages = null;
ExchangeFolderInfo subfolderInfo = new ExchangeFolderInfo();

// Verificar se a pasta personalizada especificada existe e obter todas as informações das mensagens da URI de destino
ExchangeFolderInfo[] referenceToSubfolderInfo = { subfolderInfo };
client.folderExists(mailbox.getInboxUri(), "TestInbox", /* out */ referenceToSubfolderInfo);
subfolderInfo = referenceToSubfolderInfo[0];

// se a pasta personalizada existir
if (subfolderInfo != null) {
    messages = client.listMessages(subfolderInfo.getUri());

    // Analisar todas as informações da coleção de mensagens
    for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) messages) {
        String strMessageURI = info.getUniqueUri();
        // agora obter os detalhes da mensagem usando FetchMessage()
        MailMessage msg = client.fetchMessage(strMessageURI);
        System.out.println("Assunto: " + msg.getSubject());
    }
} else {
    System.out.println("Nenhuma pasta com este nome encontrada.");
}
~~~
## **Listando Pastas Públicas**
O Microsoft Exchange Server permite que os usuários criem pastas públicas e postem mensagens nelas. Para fazer isso através de sua aplicação, use a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) da Aspose.Email para se conectar ao Exchange Server e ler e baixar mensagens e postagens de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas, e subpastas, listar e baixar quaisquer mensagens encontradas nessas pastas. Este exemplo só funciona com o Microsoft Exchange Server 2007 ou superior, pois apenas estes suportam EWS.

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
        System.out.println("Contagem de Subpastas: " + publicFolder.getChildFolderCount());
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

    // Chame esse método recursivamente para quaisquer subpastas
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Copiar uma Mensagem para Outra Pasta**
A API Aspose.Email permite copiar uma mensagem de uma pasta para outra usando o método [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). A versão sobrecarregada desse método retorna a URI Única da mensagem copiada, como mostrado neste artigo.

~~~Java
try {
    // Criar instância da classe EWSClient fornecendo credenciais
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copiar uma mensagem e obter referência ao novo item Copiado");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Sincronizando Itens da Pasta**
A API Aspose.Email for Java [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) fornece o recurso de sincronizar uma pasta Exchange para seus conteúdos. O método [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)) exposto pela classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) pode ser usado para realizar a sincronização das informações da pasta em uma pasta especificada. O seguinte trecho de código mostra como sincronizar informações da pasta Exchange.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sincronizar Itens da Pasta");
client.send(message1);

MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sincronizar Itens da Pasta");
client.send(message2);

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
SyncFolderResult result = client.syncFolder(client.getMailboxInfo().getInboxUri(), null);
System.out.println(result.getNewItems().size());
System.out.println(result.getChangedItems().size());
System.out.println(result.getReadFlagChanged().size());
System.out.println(result.getDeletedItems().length);
~~~
## **Recuperando Permissões para Pastas do Exchange**
Os usuários são atribuídos permissões a pastas públicas no Exchange Server, que limitam/determinam o nível de acesso que um usuário tem a essas pastas. A classe [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) fornece um conjunto de propriedades de permissão para pastas do Exchange, como o [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), se podem [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\)), e realizar outras tarefas conforme especificado pelas propriedades de permissão. As permissões podem ser recuperadas usando o método [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) da classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Este artigo mostra como recuperar as permissões aplicadas a uma pasta pública para todos os usuários que têm acesso às pastas compartilhadas.

Para realizar esta tarefa:

1. Inicializar o EWSClient.
1. Usar o listPublicFolders para obter uma lista de todas as pastas públicas.
1. Recuperar as permissões associadas a uma pasta usando o método getFolderPermissions().

O seguinte trecho de código mostra como usar a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para recuperar permissões aplicadas a uma pasta.

~~~Java
String folderName = "DesiredFolderName";

// Criar instância da classe EWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeFolderInfoCollection folders = client.listPublicFolders();
ExchangeFolderPermissionCollection permissions = new ExchangeFolderPermissionCollection();

ExchangeFolderInfo publicFolder = null;
try {
    for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folders)
        if (folderInfo.getDisplayName().equals(folderName))
            publicFolder = folderInfo;

    if (publicFolder == null)
        System.out.println("A pasta pública não foi criada na pasta pública raiz");

    ExchangePermissionCollection folderPermissionCol = client.getFolderPermissions(publicFolder.getUri());
    for (ExchangeBasePermission perm : (Iterable<ExchangeBasePermission>) folderPermissionCol) {
        if (perm instanceof ExchangeFolderPermission)
            System.out.println("A permissão é nula.");
        else {
            ExchangeFolderPermission permission = (ExchangeFolderPermission) perm;

            System.out.println("Endereço smtp primário do usuário: " + permission.getUserInfo().getPrimarySmtpAddress());
            System.out.println("Usuário pode criar Itens: " + permission.canCreateItems());
            System.out.println("Usuário pode deletar Itens: " + permission.getDeleteItems());
            System.out.println("A Pasta é Visível: " + permission.isFolderVisible());
            System.out.println("Usuário é proprietário desta pasta: " + permission.isFolderOwner());
            System.out.println("Usuário pode ler itens: " + permission.getReadItems());
        }
    }
    ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
    // Obter as permissões para a Pasta de Contatos e Calendário
    ExchangePermissionCollection contactsPermissionCol = client.getFolderPermissions(mailboxInfo.getContactsUri());
    ExchangePermissionCollection calendarPermissionCol = client.getFolderPermissions(mailboxInfo.getCalendarUri());
} finally {
    // Fazer o necessário
}
~~~
## **Criando Pastas e Sub-Pastas**
A API Aspose.Email fornece a capacidade de criar pastas em uma caixa de correio Exchange. O método [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) da classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) pode ser usado para esse propósito. Para criar uma pasta na caixa de correio do servidor Exchange, os seguintes passos podem ser seguidos.

1. Criar uma instância de IEWSClient.
1. Definir a propriedade UseSlashAsFolderSeparator conforme necessário. Se definida como **true**, a aplicação considerará o "Slash" como separador de pasta e a subpasta será criada após a barra.
1. Usar o método createFolder para criar a pasta.

O seguinte trecho de código mostra como criar pastas e subpastas.

~~~Java
// Criar instância da classe EWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String inbox = client.getMailboxInfo().getInboxUri();
String folderName1 = "EMAILNET-35054";
String subFolderName0 = "2015";
String folderName2 = folderName1 + "/" + subFolderName0;
String folderName3 = folderName1 + " / 2015";
ExchangeFolderInfo rootFolderInfo = null;
ExchangeFolderInfo folderInfo = null;

try {
    client.setUseSlashAsFolderSeparator(true);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName1);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName2);
} finally {
    ExchangeFolderInfo[] referenceToRootFolderInfo = { rootFolderInfo };
    boolean outRefCondition0 = client.folderExists(inbox, folderName1, /* out */ referenceToRootFolderInfo);
    rootFolderInfo = referenceToRootFolderInfo[0];
    if (outRefCondition0) {
        ExchangeFolderInfo[] referenceToFolderInfo = { folderInfo };
        boolean outRefCondition1 = client.folderExists(inbox, folderName2, /* out */ referenceToFolderInfo);
        folderInfo = referenceToFolderInfo[0];
        if (outRefCondition1)
            client.deleteFolder(folderInfo.getUri(), true);
        client.deleteFolder(rootFolderInfo.getUri(), true);
    }
}
~~~
## **Fazer Backup de Pastas do Exchange para PST**
Frequentemente, os usuários podem querer fazer um backup de todas ou algumas das pastas da caixa de correio. A Aspose.Email fornece a capacidade de fazer backup de todas ou pastas de caixa de correio Exchange especificadas para um PST. Este artigo descreve como fazer backup de pastas do Exchange para um PST com código de exemplo. Para fazer o backup das pastas do servidor Exchange, os seguintes passos podem ser seguidos.

1. Iniciar o IEWSClient com credenciais de usuário.
1. Adicionar as informações das pastas necessárias à ExchangeFolderInfoCollection.
1. Usar o método de backup do cliente para exportar o conteúdo da pasta para PST.

O seguinte trecho de código mostra como fazer backup de pastas do Exchange para PST.

~~~Java
String dataDir = "data/";
// Criar instância da classe IEWSClient fornecendo credenciais
final String mailboxUri = "https://ews.domain.com/ews/Exchange.asmx";
final String domain = "";
final String username = "username";
final String password = "password";
NetworkCredential credential = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

// Obter informações da caixa de correio Exchange de outra conta de email
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
ExchangeFolderInfo info = client.getFolderInfo(mailboxInfo.getInboxUri());
ExchangeFolderInfoCollection fc = new ExchangeFolderInfoCollection();
fc.addItem(info);
client.backup(fc, dataDir + "Backup_out.pst", BackupOptions.None);
~~~