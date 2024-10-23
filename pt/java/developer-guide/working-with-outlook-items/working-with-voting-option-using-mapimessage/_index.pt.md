---
title: "Trabalhando com Opção de Votação Usando MapiMessage"
url: /pt/java/trabalhando-com-opcao-de-votacao-usando-mapimessage/
weight: 40
type: docs
---


## **Criando Opção de Votação Usando MapiMessage**

O Microsoft Outlook permite que os usuários criem uma pesquisa ao compor uma nova mensagem. Ele permite incluir opções de votação, como Sim, Não, Talvez, etc. O Aspose.Email permite o mesmo ao criar uma nova mensagem do Outlook. A classe [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/) fornece a propriedade [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/#getVotingButtons--) que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de como criar um [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) com opções de votação para criar uma pesquisa.

### **Criando uma Pesquisa usando MapiMessage**

O seguinte trecho de código mostra como criar uma pesquisa, a classe [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) pode ser usada conforme mostrado no seguinte trecho de código.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
String address = "firstname.lastname@aspose.com";
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Definir Botões FollowUpOptions
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Sim;Não;Talvez;Exatamente!");
client.send(message, options);
~~~ 

### **Lendo Opções de Votação de um MapiMessage**

O seguinte trecho de código mostra como ler opções de votação de um [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);

// Este método pode ser útil quando, além dos botões de votação, é necessário obter outros parâmetros (ex. uma categoria)
FollowUpOptions options = FollowUpManager.getOptions(message);

// Os botões de votação serão apresentados como uma string com ponto e vírgula como separador
String votingButtons = options.getVotingButtons();
~~~ 

### **Lendo Apenas os Botões de Votação**

O seguinte trecho de código mostra como ler apenas os botões de votação.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// Este método pode ser útil quando é necessário ler apenas os botões de votação
// Os botões de votação serão apresentados como uma coleção de valores de string
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~ 

### **Adicionando um botão de votação a uma Mensagem Existente**

O seguinte trecho de código mostra como adicionar um botão de votação a uma mensagem existente.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "De fato!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~ 

### **Excluindo um botão de votação de uma Mensagem**

O seguinte trecho de código mostra como excluir um botão de voto de uma mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Criar Nova Mensagem e definir propriedades FollowUpOptions, FollowUpManager
MapiMessage msg = createTestMessage(false);

FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Sim;Não;Talvez;Exatamente!");
FollowUpManager.setOptions(msg, options);
msg.save(dataDir + "MapiMsgWithPoll.msg");
FollowUpManager.removeVotingButton(msg, "Exatamente!"); // Excluindo um único botão OU
FollowUpManager.clearVotingButtons(msg); // Excluindo todos os botões de um MapiMessage
msg.save(dataDir + "MapiMsgWithPoll.msg");
~~~ 

### **Ler as Informações dos Resultados da Votação**

O seguinte trecho de código mostra como ler as informações dos resultados da votação.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "AddVotingButtonToExistingMessage.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Destinatário: " + recipient.getDisplayName());

    // Obter a propriedade PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE
    System.out.println("Resposta: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE).getString());

    // Obter a propriedade PR_RECIPIENT_TRACKSTATUS_TIME
    System.out.println("Hora da resposta: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME).getDateTime());

    System.out.println();
}
~~~ 

### **Métodos Exemplo Usados nos Exemplos**

O seguinte trecho de código mostra como criar uma mensagem de exemplo usada nos exemplos.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static MapiMessage createTestMessage(boolean draft) {
    MapiMessage msg = new MapiMessage("from@test.com", "to@test.com", "Mensagem marcada",
            "Faça-a bonita e curta, mas descritiva. A descrição pode aparecer nas páginas de resultados de busca de mecanismos de busca...");

    if (!draft) {
        msg.setMessageFlags(msg.getFlags() ^ MapiMessageFlags.MSGFLAG_UNSENT);
    }
    return msg;
}
~~~