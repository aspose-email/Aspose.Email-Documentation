---
title: "Conectando ao Exchange Server"
url: /pt/java/conectando-ao-exchange-server/
weight: 10
type: docs
---


Para se conectar aos servidores Exchange 2007, 2010 e 2013 usando o Exchange Web Service, o Aspose.Email fornece a interface [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) que implementa a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). O método [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) cria e retorna um objeto [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) que é usado para realizar operações relacionadas a uma caixa de correio do Exchange e outras pastas. Este artigo mostra como instanciar objetos de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Conectando ao Exchange Server usando EWS**
O seguinte trecho de código mostra como se conectar usando o Exchange Web Service (EWS).

~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
## **Conectando ao Exchange Server usando IMAP**
O Microsoft Exchange Server suporta o protocolo IMAP para acessar itens em uma caixa de correio. Use a classe [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) do Aspose.Email para se conectar ao Exchange Server usando o protocolo IMAP. Para mais informações sobre a classe [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient). Primeiro, verifique se os serviços IMAP estão habilitados para o seu Exchange Server:

1. Abra o Painel de Controle.
1. Vá para Ferramentas Administrativas, depois Serviços.
1. Verifique o status do serviço Microsoft Exchange IMAP4.
1. Se não estiver em execução, habilite/inicie-o.

O seguinte trecho de código mostra como se conectar e listar mensagens da pasta Inbox do servidor Microsoft Exchange usando o protocolo IMAP.

~~~Java
// Conecte-se ao Exchange Server usando a classe ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Selecione a pasta Inbox
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Obtenha a lista de mensagens
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Desconecte-se do servidor
imapClient.dispose();
~~~

O seguinte trecho de código mostra como usar SSL.

~~~Java
public static void run() {
    // Conecte-se ao Exchange Server usando a classe ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Selecione a pasta Inbox
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Obtenha a lista de mensagens
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Desconecte-se do servidor
    imapClient.dispose();
}
~~~

Após conectar-se a um servidor Exchange usando IMAP e obter a [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), o seguinte trecho de código mostra como usar o número de sequência do objeto [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) para salvar uma mensagem específica.

~~~Java
// Selecione a pasta Inbox
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Obtenha a lista de mensagens
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Busque a mensagem da inbox usando seu SequenceNumber de msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Salve a mensagem em disco agora
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~