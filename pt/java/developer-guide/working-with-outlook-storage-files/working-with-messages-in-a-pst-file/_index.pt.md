---
title: "Trabalhando com Mensagens em um Arquivo PST"
url: /pt/java/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---

## **Adicionando Mensagens a Arquivos PST**

[Crie um Novo Arquivo PST e Adicione Subpastas](/email/java/create-new-pst-add-sub-folders-and-messages) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com o Aspose.Email, você pode adicionar mensagens a subpastas de um arquivo PST que você criou ou carregou. Este artigo adiciona duas mensagens do disco à subpasta Caixa de Entrada de um PST. Use as classes [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) para adicionar mensagens a arquivos PST. Para adicionar mensagens à pasta Caixa de Entrada de um arquivo PST:

1. Crie uma instância da classe **FolderInfo** e carregue-a com o conteúdo da pasta Caixa de Entrada.
1. Adicione mensagens do disco à pasta Caixa de Entrada chamando o método [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessage-com.aspose.email.MapiMessage-). A classe [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) expõe o método [addMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) que permite adicionar um grande número de mensagens à pasta, reduzindo as operações de I/O no disco e melhorando o desempenho. Um exemplo completo pode ser encontrado abaixo, em [Adicionando Mensagens em Lote](#adding-bulk-messages).

Os trechos de código abaixo mostram como adicionar mensagens a uma subpasta PST chamada Caixa de Entrada.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Criar novo PST
PersonalStorage personalStorage = PersonalStorage.create(dataDir, FileFormatVersion.Unicode);

// Adicionar nova pasta "Caixa de Entrada"
personalStorage.getRootFolder().addSubFolder("Inbox");

// Selecionar a pasta "Caixa de Entrada"
FolderInfo inboxFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

// Adicionar algumas mensagens à pasta "Caixa de Entrada"
inboxFolder.addMessage(MapiMessage.fromFile(dataDir + "MapiMsgWithPoll.msg"));
~~~

### **Adicionando Mensagens em Lote**

Adicionar mensagens individuais a um PST implica em mais operações de I/O no disco e, portanto, pode diminuir o desempenho. Para melhorar o desempenho, as mensagens podem ser adicionadas ao PST em modo de lote para minimizar as operações de I/O. O método [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) permite que você defina um intervalo de mensagens a serem adicionadas ao PST para melhorar o desempenho e pode ser usado nos seguintes cenários. Além disso, o evento MessageAdded ocorre quando uma mensagem é adicionada à pasta.

### **Carregando Mensagens do Disco**

O trecho de código abaixo mostra como carregar mensagens do disco.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
private static void addMessagesInBulkMode(String fileName, String msgFolderName) {
    try (PersonalStorage personalStorage = PersonalStorage.fromFile(fileName)) {
        FolderInfo folder = personalStorage.getRootFolder().getSubFolder("myInbox");
        folder.MessageAdded.add(new MessageAddedEventHandler() {
            public void invoke(Object sender, MessageAddedEventArgs e) {
                onMessageAdded(sender, e);
            }
        });
        folder.addMessages(new MapiMessageCollection(msgFolderName));
    }
}

static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

### **Implementação Iterable**

O trecho de código abaixo mostra como criar uma implementação Iterable.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public class MapiMessageCollection implements Iterable<MapiMessage> {

    private final File folder;

    public MapiMessageCollection(String folder) {
        this.folder = new File(folder);
    }

    public Iterator<MapiMessage> iterator() {
        return new MapiMessageIterator(folder.listFiles());
    }
}

public class MapiMessageIterator implements Iterator<MapiMessage> {

    private Queue<String> queue = new LinkedList<String>();

    public MapiMessageIterator(File[] listOfFiles) {
        for (File file : listOfFiles) {
            queue.offer(file.getAbsolutePath());
        }
    }

    public boolean hasNext() {
        return !queue.isEmpty();
    }

    public MapiMessage next() {
        return MapiMessage.fromFile(queue.poll());
    }
}
~~~

### **Adicionando Mensagens de Outro PST**

Para adicionar mensagens de outro PST, use o método [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) que retorna Iterable<MapiMessage>. O trecho de código abaixo mostra como adicionar mensagens de outros PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
private static void bulkAddFromAnotherPst(String source) {
    // O caminho para o diretório de arquivos.
    String dataDir = "data/";

    try (PersonalStorage pst = PersonalStorage.fromFile(source, false)) {
        try (PersonalStorage pstDest = PersonalStorage.fromFile(dataDir + "PersonalStorageFile1.pst")) {
            // Obter a pasta pelo nome
            FolderInfo folderInfo = pst.getRootFolder().getSubFolder("Contacts");
            MessageInfoCollection ms = folderInfo.getContents();

            // Obter a pasta pelo nome
            FolderInfo f = pstDest.getRootFolder().getSubFolder("myInbox");
            f.MessageAdded.add(new MessageAddedEventHandler() {
                public void invoke(Object sender, MessageAddedEventArgs e) {
                    onMessageAdded(sender, e);
                }
            });
            f.addMessages(folderInfo.enumerateMapiMessages());
            FolderInfo fi = pstDest.getRootFolder().getSubFolder("myInbox");
            MessageInfoCollection msgs = fi.getContents();
        }
    }
}

// Manipula o evento MessageAdded.
static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~ 

## **Obter Informações de Mensagens de um Arquivo PST do Outlook**

Em [Leia o Arquivo PST do Outlook e Obtenha Informações sobre Pastas e Subpastas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/), discutimos como carregar um arquivo PST do Outlook e navegar em suas pastas para obter os nomes das pastas e o número de mensagens nelas. Este artigo explica como ler todas as pastas e subpastas no arquivo PST e exibir informações sobre as mensagens, por exemplo, assunto, remetente e destinatários. O método [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--) é usado para exibir [informações breves sobre mensagens](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) como assunto, remetente, destinatários. Em termos de desempenho, esta é a opção mais adequada para obter informações primárias sobre mensagens. Para [extrair](#extracting-messages-form-pst-files) dados completos de mensagens, o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) é fornecido. O arquivo PST do Outlook pode conter pastas aninhadas. Para obter informações sobre mensagens dessas, bem como das pastas de nível superior, use um método recursivo para ler todas as pastas. O trecho de código abaixo mostra como ler um arquivo PST do Outlook e exibir o conteúdo da pasta e das mensagens recursivamente.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // O caminho para o diretório de arquivos.
    String dataDir = "data/";

    // Carregar o arquivo do Outlook
    String path = dataDir + "PersonalStorage.pst";

    try {

        // Carregar o arquivo PST do Outlook
        PersonalStorage personalStorage = PersonalStorage.fromFile(path);

        // Obter o formato de exibição do arquivo PST
        System.out.println("Formato de Exibição: " + personalStorage.getFormat());

        // Obter informações sobre pastas e mensagens
        FolderInfo folderInfo = personalStorage.getRootFolder();

        // Chamar o método recursivo para exibir o conteúdo da pasta
        displayFolderContents(folderInfo, personalStorage);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// Este é um método recursivo para exibir o conteúdo de uma pasta
private static void displayFolderContents(FolderInfo folderInfo, PersonalStorage pst) {
    // Exibir o nome da pasta
    System.out.println("Pasta: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // Exibir informações sobre mensagens dentro desta pasta
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Assunto: " + messageInfo.getSubject());
        System.out.println("Remetente: " + messageInfo.getSenderRepresentativeName());
        System.out.println("Destinatários: " + messageInfo.getDisplayTo());
        System.out.println("------------------------------");
    }

    // Chamar este método recursivamente para cada subpasta
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            displayFolderContents(subfolderInfo, pst);
        }
    }
}
~~~ 

## **Extraindo Mensagens de Arquivos PST**

Este artigo mostra como ler arquivos PST do Microsoft Outlook e [extrair mensagens](#extracting-messages-form-pst-files). As mensagens são então salvas no disco no formato MSG. O artigo também mostra como [extrair um número específico de mensagens](#extracting-n-number-of-messages-from-a-pst-file) de um arquivo PST. Use um método recursivo para navegar por todas as pastas (incluindo quaisquer pastas aninhadas) e chame o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obter mensagens do Outlook em uma instância da classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/). Depois disso, chame o método [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para salvar a mensagem no disco ou em um stream no formato MSG. O trecho de código abaixo mostra como extrair mensagens de um arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // O caminho para o diretório de arquivos.
    String dataDir = "data/";

    // Carregar o arquivo do Outlook
    String path = dataDir + "PersonalStorage.pst";

    try {
        // carregar o arquivo PST do Outlook
        PersonalStorage pst = PersonalStorage.fromFile(path);

        // obter o formato de exibição do arquivo PST
        System.out.println("Formato de Exibição: " + pst.getFormat());

        // obter informações sobre pastas e mensagens
        FolderInfo folderInfo = pst.getRootFolder();

        // Chamar o método recursivo para extrair arquivos msg de cada pasta
        extractMsgFiles(folderInfo, pst);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// Este é um método recursivo para exibir o conteúdo de uma pasta
private static void extractMsgFiles(FolderInfo folderInfo, PersonalStorage pst) {
    // exibir o nome da pasta
    System.out.println("Pasta: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // loop por todas as mensagens nesta pasta
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Salvando mensagem {0} ...." + messageInfo.getSubject());
        // obter a mensagem na instância MapiMessage
        MapiMessage message = pst.extractMessage(messageInfo);
        // salvar esta mensagem no disco no formato msg
        message.save(message.getSubject().replace(":", " ") + ".msg");
        // salvar esta mensagem em stream no formato msg
        ByteArrayOutputStream messageStream = new ByteArrayOutputStream();
        message.save(messageStream);
    }

    // Chamar este método recursivamente para cada subpasta
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            extractMsgFiles(subfolderInfo, pst);
        }
    }
}
~~~ 

### **Salvando Mensagens Diretamente de PST para Stream**

Para salvar mensagens de um arquivo PST diretamente em stream, sem extrair o MsgInfo para mensagens, use o método [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-). O trecho de código abaixo mostra como salvar mensagens diretamente de PST para stream.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";

// Carregar o arquivo do Outlook
String path = dataDir + "PersonalStorage.pst";

// Salvar mensagem em MemoryStream
try (PersonalStorage personalStorage = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (ByteArrayOutputStream memeorystream = new ByteArrayOutputStream()) {
            personalStorage.saveMessageToStream(messageInfo.getEntryIdString(), memeorystream);
        }
    }
}

// Salvar mensagem em arquivo
try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (FileOutputStream fs = new FileOutputStream(new File(dataDir + messageInfo.getSubject() + ".msg"))) {
            pst.saveMessageToStream(messageInfo.getEntryIdString(), fs);
        }
    }
}

try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");

    // Para enumerar o entryId das mensagens, você pode usar o método FolderInfo.EnumerateMessagesEntryId():
    for (String entryId : inbox.enumerateMessagesEntryId()) {
        try (ByteArrayOutputStream ms = new ByteArrayOutputStream()) {
            pst.saveMessageToStream(entryId, ms);
        }
    }
}
~~~ 

### **Extraindo n Número de Mensagens de um Arquivo PST**

O trecho de código abaixo mostra como extrair um número específico de mensagens de um PST. Basta fornecer o índice para a primeira mensagem e o total de mensagens a serem extraídas.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// Extrai mensagens começando do 10º índice e extrair um total de 100 mensagens
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~ 

### **Obter Número Total de Itens de um Arquivo PST**

Aspose.Email fornece o método [GetTotalItemsCount()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#getTotalItemsCount--) da propriedade [PersonalStorage.Store](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#getStore--). Ele retorna o número total de itens de mensagens contidos no PST.

O seguinte exemplo de código mostra como recuperar a contagem total de itens (mensagens, compromissos, contatos, etc.) armazenados no arquivo PST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    int count = pst.getStore().getTotalItemsCount();
}
``` 

## **Excluir Itens de Arquivos PST**

[Adicionar Mensagens a Arquivos PST](#adding-messages-to-pst-files) mostrou como adicionar mensagens a arquivos PST. É, claro, também possível excluir itens (conteúdos) de um arquivo PST e pode também ser desejável excluir mensagens em lote. Itens de um arquivo PST podem ser excluídos usando o método [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---). A API também fornece o método [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) para excluir itens em lote do arquivo PST.

### **Excluindo Mensagens de Arquivos PST**

Este artigo mostra como usar a classe [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) para acessar pastas específicas em um arquivo PST. Para excluir mensagens da subpasta Enviados de um arquivo PST carregado ou criado anteriormente:

1. Crie uma instância da classe [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) e carregue-a com o conteúdo da subpasta enviadas.
1. Exclua mensagens da pasta Enviados chamando o método [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) e passando o [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/#getEntryId--) como parâmetro. O trecho de código abaixo mostra como excluir mensagens de uma subpasta Enviados de um arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/" + "Sub.pst";

// Carregar o arquivo PST do Outlook
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Obter a pasta de itens Enviados
FolderInfo folderInfo = personalStorage.getPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.getContents();
for (MessageInfo msgInfo : msgInfoColl) {
    System.out.println(msgInfo.getSubject() + ": " + msgInfo.getEntryIdString());
    if (msgInfo.getSubject().equals("some delete condition")) {
        // Excluir este item
        folderInfo.deleteChildItem(msgInfo.getEntryId());
        System.out.println("Mensagem excluída");
    }
}
~~~ 

### **Excluindo Pastas de Arquivos PST**

Você pode excluir uma pasta PST movendo-a para a pasta Itens Excluídos.

~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Empty folder");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~ 
A vantagem deste método é que a pasta excluída pode ser facilmente recuperada.

~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Some folder");
pst.moveItem(someFolder, pst.getRootFolder());
~~~ 
Você também pode remover permanentemente uma pasta da pasta Itens Excluídos, se necessário.

~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~ 
O método [deleteChildItem()](https://apireference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) pode ser usado para qualquer pasta se você deseja excluir imediatamente e permanentemente uma subpasta, ignorando a pasta Itens Excluídos.

~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~ 

### **Excluir Itens em Lote de um Arquivo PST**

A API Aspose.Email pode ser usada para excluir itens em lote de um arquivo PST. Isso é realizado usando o método [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) que aceita uma lista de itens Entry ID referindo-se aos itens a serem excluídos. O trecho de código abaixo mostra como excluir itens em lote de um arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/" + "Sub.pst";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
    // Obter a subpasta Caixa de Entrada do arquivo do Outlook
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

    // Criar uma instância de PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.getFrom().contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());
    List<String> deleteList = new ArrayList<String>();
    for (MessageInfo messageInfo : messages) {
        deleteList.add(messageInfo.getEntryIdString());
    }

    // excluir mensagens com De = "someuser@domain.com"
    inbox.deleteChildItems(deleteList);
}
~~~ 

## **Buscar Mensagens e Pastas em um PST por Critério**

Os arquivos de Armazenamento Pessoal (PST) podem conter uma enorme quantidade de dados e buscar dados que atendem a um critério específico em arquivos tão grandes precisa incluir múltiplos pontos de verificação no código para filtrar as informações. Com a classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/), o Aspose.Email possibilita a busca de registros específicos em um PST com base em um critério de pesquisa especificado. Um PST pode ser pesquisado por mensagens com base em parâmetros de pesquisa, como remetente, destinatário, assunto, importância da mensagem, presença de anexos, tamanho da mensagem e até mesmo ID da mensagem. O [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) também pode ser usado para buscar subpastas.

### **Buscando Mensagens e Pastas em PST**

O trecho de código abaixo mostra como usar a classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) para buscar conteúdos em um PST com base em diferentes critérios de pesquisa. Por exemplo, mostra como buscar um PST com base em:

- Importância da mensagem.
- Classe da mensagem.
- Presença de anexos.
- Tamanho da mensagem.
- Data da mensagem.
- Mensagens não lidas.
- Mensagens não lidas com anexos, e
- pastas com um nome de subpasta específico.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalStorage.getRootFolder().getSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // Mensagens de alta importância
    builder.getImportance().equals((int) MapiImportance.High);
    MessageInfoCollection messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens com Alta Imp:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    builder.getMessageClass().equals("IPM.Note");
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens com IPM.Note:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensagens com anexos E alta importância
    builder.getImportance().equals((int) MapiImportance.High);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens com anexos: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensagens com tamanho > 15 KB
    builder.getMessageSize().greater(15000);
    messages = folder.getContents(builder.getQuery());
    System.out.println("mensagens tamanho > 15Kb:" + messages.size());

    java.util.Calendar c = java.util.Calendar.getInstance();

    builder = new PersonalStorageQueryBuilder();
    // Mensagens pela Data Atual
    // (Observe que consultas por data não são suportadas para Itens de Calendário na pasta Compromissos)
    builder.getSentDate().on(c.getTime(), DateComparisonType.ByDate);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens pela Data Atual: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensagens entre Datas
    // (Observe que consultas por data não são suportadas para Itens de Calendário na pasta Compromissos)
    c.set(2020,  0, 1, 0, 0, 0);
    builder.getSentDate().since(c.getTime());
    c.set(2021,  0, 1, 0, 0, 0);
    builder.getSentDate().before(c.getTime());
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens entre Datas: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensagens não lidas
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Não lidas:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Mensagens não lidas com anexos
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Mensagens não lidas com anexos: " + messages.size());

    // Pasta com o nome de 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.getFolderName().equals("SubInbox");
    FolderInfoCollection folders = folder.getSubFolders(builder.getQuery());
    System.out.println("Pasta com subpasta: " + folders.size());

    builder = new PersonalStorageQueryBuilder();
    // Pastas com subpastas
    builder.hasSubfolders();
    folders = folder.getSubFolders(builder.getQuery());
    System.out.println(folders.size());
}
~~~ 

### **Buscando uma String em PST com o Parâmetro Ignorar Maiúsculas**

O trecho de código abaixo mostra como buscar uma string em PST com o parâmetro ignorar maiúsculas.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CaseSensitivity.pst", FileFormatVersion.Unicode)) {
    FolderInfo folderinfo = personalStorage.createPredefinedFolder("Inbox", StandardIpmFolder.Inbox);
    folderinfo.addMessage(MapiMessage.fromMailMessage(MailMessage.load("Sample.eml")));
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // IgnorarMaiúsculas é Verdadeiro
    builder.getFrom().contains("automated", true);
    MailQuery query = builder.getQuery();
    MessageInfoCollection coll = folderinfo.getContents(query);
    System.out.println(coll.size());
}
~~~ 

### **Buscando Assuntos de Mensagens por Múltiplas Palavras-chave em um Arquivo PST**

Você pode usar o método [MailQueryBuilder.or](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) para encontrar mensagens com um assunto que contenha pelo menos uma das palavras especificadas, conforme mostrado abaixo:

~~~java
PersonalStorageQueryBuilder builder1 = new PersonalStorageQueryBuilder();
builder1.getSubject().contains("Review"); // 'Review' é a palavra-chave para a busca

PersonalStorageQueryBuilder builder2 = new PersonalStorageQueryBuilder();
builder2.getSubject().contains("Error"); // 'Error' também é a palavra-chave para a busca

PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.or(builder1.getQuery(), builder2.getQuery()); // os assuntos das mensagens devem conter as palavras 'Review' ou 'Error'

try (PersonalStorage storage = PersonalStorage.fromFile("example.pst"))
{
    FolderInfo folderInfo = storage.getRootFolder().getSubFolder("Inbox");
    MessageInfoCollection messageInfos = folderInfo.getContents(queryBuilder.getQuery());

    for (MessageInfo messageInfo : messageInfos)
    {
        System.out.println(messageInfo.getSubject());
    }
}
~~~ 

## **Mover Itens para Outras Pastas do Arquivo PST**

O Aspose.Email torna possível mover itens de uma pasta de origem para outra pasta no mesmo arquivo de Armazenamento Pessoal (PST). Isso inclui:

- Mover uma pasta especificada para uma nova pasta pai.
- Mover uma mensagem especificada para uma nova pasta.
- Mover o conteúdo para uma nova pasta.
- Mover subpastas para uma nova pasta pai.

O trecho de código abaixo mostra como mover itens, como mensagens e pastas, de uma pasta de origem para outra pasta no mesmo arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
try (PersonalStorage personalStorage = PersonalStorage.fromFile("test.pst")) {
    FolderInfo inbox = personalStorage.getPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.getSubFolder("Subfolder");

    // Mover pasta e mensagem para os Itens Excluídos
    personalStorage.moveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.getContents();
    personalStorage.moveItem(contents.get(0), deleted);

    // Mover todas as subpastas da caixa de entrada e conteúdos da subpasta para os Itens Excluídos
    inbox.moveSubfolders(deleted);
    subfolder.moveContents(deleted);
}
~~~ 

## **Atualizando Propriedades de Mensagem em um Arquivo PST**

Às vezes, é necessário atualizar certas propriedades de mensagens, como alterar o assunto, marcar a importância da mensagem e semelhantes. Atualizar uma mensagem em um arquivo PST, com tais alterações nas propriedades da mensagem, pode ser alcançado usando o método [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#changeMessages-com.aspose.email.MapiPropertyCollection-). Este artigo mostra como atualizar mensagens em lote em um arquivo PST para alterações nas propriedades. O trecho de código abaixo mostra como atualizar propriedades de mensagens em modo de lote para várias mensagens em um arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/" + "Sub.pst";

// Carregar o arquivo PST do Outlook
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Obter a subpasta necessária
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// encontrar mensagens com De = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.getFrom().contains("someuser@domain.com");

// Obter Conteúdos da Consulta
MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());

// Salvar (MessageInfo, EntryIdString) em uma Lista
List<String> changeList = new ArrayList<String>();
for (MessageInfo messageInfo : messages) {
    changeList.add(messageInfo.getEntryIdString());
}

// Compor as novas propriedades
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, "Novo Assunto".getBytes(Charset.forName("utf-16le"))));
updatedProperties.add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.getBytesInt64(2)));

// atualizar mensagens com De = "someuser@domain.com" com novas propriedades
inbox.changeMessages(changeList, updatedProperties);
~~~ 

## **Atualizando Propriedades Personalizadas em um Arquivo PST**

Às vezes, é necessário marcar itens que foram processados dentro do arquivo PST. A API Aspose.Email permite alcançar isso usando MapiProperty e MapiNamedProperty. Os seguintes métodos são úteis para alcançar isso.

- `constructor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `constructor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `FolderInfo.changeMessages(MapiPropertyCollection updatedProperties)` - altera todas as mensagens na pasta
- `PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties)` - altera as propriedades da mensagem

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // O caminho para o diretório de arquivos.
    String dataDir = "data/" + "Sub.pst";

    try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
        FolderInfo testFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

        // Criar a coleção de propriedades de mensagem para adicionar ou atualizar
        MapiPropertyCollection newProperties = new MapiPropertyCollection();

        // Propriedade nomeada normal, personalizada e PidLidLogFlags
        MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W, "test_address@org.com".getBytes(Charset.forName("utf-16le")));
        MapiProperty namedProperty1 = new MapiNamedProperty(generateNamedPropertyTag(0L, MapiPropertyType.PT_LONG), "ITEM_ID", UUID.randomUUID(),
                BitConverter.getBytesInt64(123));
        MapiProperty namedProperty2 = new MapiNamedProperty(generateNamedPropertyTag(1L, MapiPropertyType.PT_LONG), 0x0000870C,
                UUID.fromString("0006200A-0000-0000-C000-000000000046"), BitConverter.getBytesInt64(0));
        newProperties.add(namedProperty1.getTag(), namedProperty1);
        newProperties.add(namedProperty2.getTag(), namedProperty2);
        newProperties.add(property.getTag(), property);
        testFolder.changeMessages(testFolder.enumerateMessagesEntryId(), newProperties);
    }
}

private static long generateNamedPropertyTag(long index, int dataType) {
    return (((0x8000 | index) << 16) | (long) dataType) & 0x00000000FFFFFFFFL;
}
~~~ 

## **Extraindo Anexos sem Extrair a Mensagem Completa**

A API Aspose.Email pode ser usada para extrair anexos de mensagens PST sem extrair a mensagem completa primeiro. O método [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) da [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) pode ser usado para isso. O seguinte trecho de código mostra como extrair anexos sem extrair a mensagem completa.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";

try (PersonalStorage personalstorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalstorage.getRootFolder().getSubFolder("Inbox");

    for (String messageInfo : folder.enumerateMessagesEntryId()) {
        MapiAttachmentCollection attachments = personalstorage.extractAttachments(messageInfo);

        if (attachments.size() != 0) {
            for (MapiAttachment attachment : attachments) {
                if (attachment.getLongFileName() != null && !attachment.getLongFileName().isEmpty()) {
                    if (attachment.getLongFileName().contains(".msg")) {
                        continue;
                    } else {
                        attachment.save(dataDir + "Attachments/" + attachment.getLongFileName());
                    }
                }
            }
        }
    }
}
~~~ 

## **Adicionando Arquivos a PST**

A funcionalidade chave do Microsoft Outlook é gerenciar e-mails, calendários, tarefas, contatos e entradas de diário. Além disso, arquivos também podem ser adicionados a uma pasta PST e o PST resultante mantém registro dos documentos adicionados. O Aspose.Email fornece a facilidade de adicionar arquivos a uma pasta da mesma forma que adicionar mensagens, contatos, tarefas e entradas de diário a PST. O seguinte trecho de código mostra como adicionar documentos a uma pasta PST usando Aspose.Email.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode)) {
    FolderInfo folder = personalStorage.getRootFolder().addSubFolder("Files");

    // Adicionar o arquivo Document.doc com a classe de mensagem "IPM.Document" por padrão.
    folder.addFile(dataDir + "attachment_1.doc", null);
}
~~~