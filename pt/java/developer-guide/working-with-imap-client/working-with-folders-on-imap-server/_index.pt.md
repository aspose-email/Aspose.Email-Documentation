---
title: "Trabalhando com Pastas no Servidor IMAP"
url: /pt/java/trabalhando-com-pastas-no-servidor-imap/
weight: 60
type: docs
---

## **Obtendo Informações sobre Pastas**

Obter informações sobre pastas de um servidor IMAP é muito fácil com Aspose.Email. Chame o método [listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) da classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Ele retorna um objeto do tipo [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/). Percorra essa coleção e obtenha informações sobre pastas individuais em um loop. O método é sobrecarregado. Você pode passar um nome de pasta como parâmetro para obter uma lista de subpastas. O seguinte trecho de código mostra como obter informações de pastas de um servidor IMAP usando o método Aspose.Email descrito.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Obtenha todas as pastas na pasta atualmente inscrita
ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Percorra a coleção para obter informações da pasta uma a uma
for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoColl) {
    // Nome da pasta e obter novas mensagens na pasta
    System.out.println("O nome da pasta é " + folderInfo.getName());
    ImapFolderInfo folderExtInfo = client.getFolderInfo(folderInfo.getName());
    System.out.println("Contagem de novas mensagens: " + folderExtInfo.getNewMessageCount());
    System.out.println("É somente leitura? " + folderExtInfo.getReadOnly());
    System.out.println("Número total de mensagens " + folderExtInfo.getTotalMessageCount());
}
~~~

## **Excluindo e Renomeando Pastas**

Uma pasta em um servidor IMAP pode ser excluída ou renomeada em uma única linha com Aspose.Email:

- O método [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) aceita o nome da pasta como parâmetro.
- Para o método [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-), você precisa passar o nome atual da pasta e o novo nome da pasta.

O seguinte trecho de código mostra como remover uma pasta de um servidor IMAP e como renomear uma pasta. Cada operação é realizada em uma linha de código.

```java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Excluir uma pasta e renomear uma pasta
client.deleteFolder("nomeDaPasta");
client.renameFolder("nomeDaPasta", "novoNomeDaPasta");
```

## **Adicionando uma Nova Mensagem em uma Pasta**

Você pode adicionar uma nova mensagem à pasta usando as classes [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Primeiro, crie um objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) fornecendo os valores de assunto, para e de. Em seguida, inscreva-se em uma pasta e adicione a mensagem a ela. O seguinte trecho de código mostra como adicionar uma nova mensagem a uma pasta.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Criar uma mensagem
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "assunto", "mensagem");

// Inscreva-se na pasta Caixa de Entrada e anexe a mensagem recém-criada
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~ 

## **Adicionar Múltiplas Mensagens com Suporte a MultiConexão**

Você pode adicionar várias mensagens usando o método [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) fornecido pela classe [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). O método [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) aceita uma lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e adiciona-a à pasta atual se a pasta não for fornecida como um parâmetro. O ImapClient também suporta o modo MultiConexão para operações sobrecarregadas. O seguinte trecho de código mostra como adicionar várias mensagens usando o modo MultiConexão.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Mensagem de Teste - " + UUID.randomUUID().toString(), "Anexar em Grupo IMAP com MultiConexão");
    messages.add(message);
}

imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
imapClient.appendMessages(messages);
~~~ 

{{% alert color="primary" %}} 

Por favor, note que o uso do modo multi-conexão não garante aumento de desempenho.

{{% /alert %}} 

## **Mover Mensagens para Outra Pasta de Caixa de Correio**

Aspose.Email para Java permite mover uma mensagem de uma pasta de caixa de correio para outra usando a API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). O método [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) utiliza o id único da mensagem e o nome da pasta de destino para mover uma mensagem para a pasta de destino. O seguinte trecho de código mostra como mover mensagens para outra pasta de caixa de correio.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Este exemplo mostra como mover uma mensagem de uma pasta de uma caixa de correio para outra usando a API ImapClient do Aspose.Email para Java
// Disponível a partir do Aspose.Email para Java
// -------------- Membro da API de Sobrecarga Disponíveis --------------
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName)
// void ImapClient.moveMessage(int sequenceNumber, String folderName)
// void ImapClient.moveMessage(String uniqueId, String folderName)

final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    String folderName = "EMAILNET-35151";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35151 - " + UUID.randomUUID(),
                "EMAILNET-35151 ImapClient: Fornecer opção para Mover Mensagem");
        client.selectFolder(ImapFolderInfo.IN_BOX);
        // Anexar a nova mensagem à pasta da Caixa de Entrada
        String uniqueId = client.appendMessage(ImapFolderInfo.IN_BOX, message);
        ImapMessageInfoCollection messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Agora mova a mensagem para a pasta EMAILNET-35151
        client.moveMessage(uniqueId, folderName);
        client.commitDeletes();
        // Verifique se a mensagem foi movida para a nova pasta
        client.selectFolder(folderName);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Verifique se a mensagem foi movida da Caixa de Entrada
        client.selectFolder(ImapFolderInfo.IN_BOX);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~ 

## **Copiar Mensagens para Outra Pasta de Caixa de Correio**

A API Aspose.Email fornece a capacidade de copiar uma mensagem de uma pasta de caixa de correio para outra. Ela permite copiar uma única mensagem, bem como várias mensagens usando os métodos [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) e [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-). O método [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) proporciona a capacidade de copiar várias mensagens da pasta de origem de uma caixa de correio para a pasta de caixa de correio de destino. O seguinte trecho de código mostra como copiar mensagens para outra pasta de caixa de correio.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    // Criar a pasta de destino
    String folderName = "EMAILNET-35242";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        // Anexar algumas mensagens ao servidor
        MailMessage message1 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Melhoria do método de cópia. Adicionar capacidade de 'copiar' várias mensagens por invocação.");
        String uniqueId1 = client.appendMessage(message1);

        MailMessage message2 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Melhoria do método de cópia. Adicionar capacidade de 'copiar' várias mensagens por invocação.");
        String uniqueId2 = client.appendMessage(message2);

        // Verifique se as mensagens foram adicionadas à caixa de correio
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());

        // Copiar várias mensagens usando o comando CopyMessages e verificar se as mensagens são copiadas para a pasta de destino
        client.copyMessagesByUids(Arrays.asList(uniqueId1, uniqueId2), folderName);

        client.selectFolder(folderName);
        msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~ 

## **Trabalhando com Pastas de Caixa de Correio de Uso Especial**

Alguns armazenamentos de mensagem IMAP incluem caixas de correio de uso especial, como aquelas usadas para armazenar mensagens de rascunho ou mensagens enviadas. Muitos clientes de e-mail permitem que os usuários especifiquem onde as mensagens de rascunho ou enviadas devem ser colocadas, mas configurá-las requer que o usuário saiba quais caixas de correio o servidor reserva para esses fins. Aspose.Email pode identificar essas caixas de correio de uso especial usando a classe [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) para facilitar o trabalho com elas. O seguinte exemplo de código demonstra como acessar essas caixas de correio de uso especial usando a classe [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/).

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();
System.out.println(mailboxInfo.getInbox());
System.out.println(mailboxInfo.getDraftMessages());
System.out.println(mailboxInfo.getJunkMessages());
System.out.println(mailboxInfo.getSentMessages());
System.out.println(mailboxInfo.getTrash());
~~~