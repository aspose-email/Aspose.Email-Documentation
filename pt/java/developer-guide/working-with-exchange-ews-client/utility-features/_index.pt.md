---
title: "Recursos de Utilidade"
url: /pt/java/utility-features/
weight: 120
type: docs
---


## **Enviando uma Mensagem com Opção de Votação**
O Microsoft Outlook permite que os usuários criem uma enquete ao compor uma nova mensagem. Isso é feito incluindo opções de votação como Sim, Não, Talvez, etc. A classe FollowUpOptions oferecida pela Aspose.Email fornece a propriedade VotingButtons que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de como criar um MapiMessage com opções de votação para criar uma enquete e, em seguida, enviar a mensagem usando o cliente Exchange Web Service (EWS).
### **Criando e Enviando uma Mensagem com Opções de Votação**
O seguinte trecho de código mostra como criar uma nova mensagem e enviá-la com opções de votação.


~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Definir Botões FollowUpOptions
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Sim;Não;Talvez;Exatamente!");

client.send(message, options);
~~~
### **Métodos de Amostra Usados nos Exemplos**
O seguinte trecho de código mostra como usar os métodos usados no exemplo acima.


~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Mensagem Marcada",
            "Mantenha curto e simples, mas descritivo. A descrição pode aparecer nas páginas de resultados de pesquisa dos motores de busca...");

    return eml;
}
~~~
## **Criando mensagens RE e FW a partir de arquivos MSG**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite que os desenvolvedores criem mensagens RE (Responder/Responder a Todos) e FW (Encaminhar) a partir de uma mensagem de origem. A mensagem de origem é identificada selecionando uma [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) específica da [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) obtida por IEWSClient.listMessages(). O outro argumento é o [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) real a ser enviado como mensagem RE ou FW. O seguinte trecho de código mostra como criar uma conta de amostra que é usada para enviar uma mensagem e, em seguida, os recursos de Resposta e Encaminhamento são demonstrados contra essa mensagem de amostra. Para realizar esta tarefa:

1. Inicialize o objeto IEWSClient fornecendo credenciais válidas.
1. Envie algumas mensagens de amostra.
1. Chame as funções IEWSClient.reply(), IEWSClient.replyAll() e IEWSClient.forward() para enviar mensagens.


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar a capacidade de criar mensagens RE e FW a partir do arquivo MSG de origem");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 mensagem na Caixa de Entrada");
    else
        System.out.println("Erro! Nenhuma mensagem na Caixa de Entrada");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar a capacidade de criar mensagens RE e FW a partir do arquivo MSG de origem");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 mensagens na Caixa de Entrada");
    else
        System.out.println("Erro! Nenhuma nova mensagem na Caixa de Entrada");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar a capacidade de criar mensagens RE e FW a partir do arquivo MSG de origem");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Teste de anexo 1", "Nome do Anexo 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Teste de anexo 2", "Nome do Anexo 2"));

    // Responder, Responder a Todos e encaminhar Mensagem
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Erro no programa" + ex.getMessage());
}
~~~
## **Suporte ao OAuth para EWS com Office 365**
A API Aspose.Email fornece suporte para o Exchange Web Service (EWS) com Office 365. A interface [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) da API oferece um método sobrecarregado que fornece o [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) como entrada para acessar a conta Exchange via OAuth. O usuário precisa fornecer os parâmetros Authority, Client Id, Client App Uri e Resource para que isso funcione. O seguinte trecho de código mostra o suporte ao OAuth para EWS com Office 365.


~~~Java
// provedor de token
/*ITokenProvider provider = new ITokenProvider() {

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        return null;
    }
};

NetworkCredential credentials = new OAuthNetworkCredential(provider);*/

// accessToken
NetworkCredential credentials = new OAuthNetworkCredential("accessToken");

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", credentials);
client.listMessages();
~~~
## **Suporte para Registro em Clientes Exchange**
A API Aspose.Email fornece a capacidade de oferecer um recurso de registro do cliente Exchange Web Service.
### **Registro para Cliente EWS**


~~~Java
client.setLogFileName("logs/ews");
// OU
EWSClient.setCommonLogFileName("logs/ews");
~~~
## **Adicionando Cabeçalhos em Solicitações EWS**
A API Aspose.Email permite adicionar cabeçalhos às solicitações Exchange. Isso pode ser usado para adicionar cabeçalhos às solicitações EWS para diferentes cabeçalhos que podem ser usados para diferentes finalidades. Um exemplo pode ser adicionar o cabeçalho X-AnchorMailbox, que é usado para gerenciar problemas de limitação no servidor Exchange. O método addHeader da IEWSClient é usado para adicionar cabeçalhos às solicitações EWS, como mostrado no trecho de código a seguir.


~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~

## **Retornar o ID de Solicitação do Cliente no Cabeçalho**

O cabeçalho ```return-client-request-id``` é enviado na solicitação e usado pelo servidor para determinar se o cabeçalho ```client-request-id``` especificado pelo cliente deve ser retornado na resposta do servidor. Os seguintes métodos são usados nesta operação:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--) 
- [setReturnClientRequestId(boolean value)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Obter ou definir uma bandeira para indicar se o cliente requer que o servidor retorne o id da solicitação.

```java
try (IEWSClient client = createEWSClient())
{
    // O cliente criará um id aleatório e o passará para o servidor.
    // O servidor deve incluir esse id no cabeçalho de request-id de todas as respostas.
    client.setReturnClientRequestId(true);
    
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
```

## **Trabalhando com Mensagens Unificadas**
A Aspose.Email pode recuperar informações de mensagens unificadas do Exchange Server 2010. Mensagens unificadas, como obter informações de configuração, iniciar uma chamada de saída, recuperar informações de chamadas telefônicas por ID de chamada e desconectar uma chamada telefônica por ID, são suportadas no momento. O seguinte exemplo de código mostra como recuperar informações de configuração de mensagens unificadas do Microsoft Exchange Server 2010.


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~
## **Obtendo Dicas de Email**
O Microsoft Exchange Server adicionou vários novos recursos com o Exchange Server 2010 e 2013. Um deles permite que os usuários obtenham dicas de email ao compor uma mensagem de email. Essas dicas são muito úteis, pois fornecem informações antes que o email seja enviado. Por exemplo, se um endereço de email estiver errado na lista de destinatários, uma dica é exibida para informar que o endereço de email é inválido. As dicas de email também permitem que você veja respostas de ausência antes de enviar um email: o Exchange Server (2010 e 2013) envia a dica de email ao compor o email se um ou mais dos destinatários tiverem configurado respostas de ausência. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos demonstrados neste artigo. O seguinte trecho de código mostra como usar a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient), que utiliza serviços web do Exchange, disponível no Microsoft Exchange Server 2007 e versões posteriores.


~~~Java
// Criar uma instância da classe EWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Conectado ao servidor Exchange...");
// Fornecer opções de dicas de email
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Obter Dicas de Email
MailTips[] tips = client.getMailTips(options);

// Exibir informações sobre cada Dica de Email
for (MailTips tip : tips) {
    // Exibir mensagem de ausência, se presente
    if (tip.getOutOfOffice() != null) {
        System.out.println("Fora do escritório: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Exibir o endereço de email inválido no destinatário, se presente
    if (tip.getInvalidRecipient() == true) {
        System.out.println("O endereço de destinatário é inválido: " + tip.getRecipientAddress());
    }
}
~~~
## **Impersonação do Exchange**
A impersonação do Exchange permite que alguém impersonifique outra conta e execute tarefas e operações usando as permissões da conta impersonificada em vez de suas próprias. Onde a delegação permite que os usuários atuem em nome de outros usuários, a Impersonação permite que eles atuem como outros usuários. A Aspose.Email suporta a impersonação do Exchange. A classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) fornece os métodos ImpersonateUser e ResetImpersonation para facilitar esse recurso.

Para realizar esta tarefa:

1. Inicialize o ExchangeWebServiceClient para o usuário 1.
1. Inicialize o ExchangeWebServiceClient para o usuário 2.
1. Anexe mensagens de teste às contas.
1. Habilite a Impersonação.
1. Redefina a Impersonação.

O seguinte trecho de código mostra como usar a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para implementar o recurso de Impersonação.


~~~Java
// Criar instâncias da classe EWSClient fornecendo credenciais
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Rascunhos";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 Usuário Usuário1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 Usuário Usuário2";
        client2.appendMessage(folder, new MailMessage("User2@exchange.conholdate.local", "To@aspose.com", subj2, ""));

        ExchangeMessageInfoCollection messInfoColl = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl.Count);
        // Assert.AreEqual(subj1, messInfoColl[0].Subject);

        client1.impersonateUser(ItemChoice.PrimarySmtpAddress, "User2@exchange.conholdate.local");
        ExchangeMessageInfoCollection messInfoColl1 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl1.Count);
        // Assert.AreEqual(subj2, messInfoColl1[0].Subject);

        client1.resetImpersonation();
        ExchangeMessageInfoCollection messInfoColl2 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl2.Count);
        // Assert.AreEqual(subj1, messInfoColl2[0].Subject);
    } finally {
        try {
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
                client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
                client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        } catch (java.lang.RuntimeException e) {
        }
    }
}
~~~
## **Recurso de Descoberta Automática usando EWS**
A API Aspose.Email permite que você descubra as configurações do servidor Exchange usando o Cliente EWS. 


~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("URL EWS descoberta automaticamente: " + ewsUrl);
~~~
## **Abortar a Operação de Restauração PST para o Servidor Exchange**
A API Aspose.Email permite que você restaure um arquivo PST para o Servidor Exchange. No entanto, se a operação estiver demorando muito devido ao grande tamanho do arquivo PST, pode ser necessário especificar um critério para abortar a operação. Isso pode ser alcançado usando a API, conforme mostrado no seguinte código de amostra.


~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password");
try {
    final long startTime = System.currentTimeMillis();
    final AtomicInteger processedItems = new AtomicInteger(0);
    final long S15 = 15 * 1000;

    BeforeItemCallback callback = new BeforeItemCallback() {
        public void invoke(ItemCallbackArgs item) {
            if (System.currentTimeMillis() - startTime > S15) {
                throw new AbortRestoreException();
            }

            processedItems.incrementAndGet();
        }
    };

    try {
        // criar um pst de teste e adicionar algumas mensagens de teste a ele
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("Minha pasta de teste");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // agora restaure o PST com callback
        client.restore(pst, rs);
        System.out.println("Sucesso!");
    } catch (AbortRestoreException e) {
        System.out.println("Timeout! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~