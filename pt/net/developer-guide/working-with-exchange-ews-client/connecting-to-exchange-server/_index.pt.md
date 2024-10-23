---
title: "Conectando ao Exchange Server"
url: /pt/net/conectando-ao-exchange-server/
weight: 10
type: docs
---

Para conectar aos servidores Exchange 2007, 2010 e 2013 usando o Exchange Web Service, o Aspose.Email fornece a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) que implementa a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). O método [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) instancia e retorna um objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) que é usado para realizar operações relacionadas a uma caixa de correio Exchange e outras pastas. Este artigo mostra como instanciar objetos de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Conectando ao Exchange Server usando EWS**

O seguinte trecho de código mostra como conectar usando o Exchange Web Service (EWS).

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
private static IEWSClient GetExchangeEWSClient()
{
    const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    const string domain = @""; 
    const string username = @"username@ASE305.onmicrosoft.com"; 
    const string password = @"password"; 
    NetworkCredential credentials = new NetworkCredential(username, password, domain); 
    IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials); 
    return client; 
}
```

## **Conectando ao Exchange Server usando IMAP**

O Microsoft Exchange Server suporta o protocolo IMAP para acessar itens em uma caixa de correio. Use a classe Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para conectar ao Exchange Server usando o protocolo IMAP. Para mais informações sobre a classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Primeiro, certifique-se de que os serviços IMAP estão habilitados para seu Exchange Server:

1. Abra o Painel de Controle.
1. Vá para Ferramentas Administrativas, depois Serviços.
1. Verifique o status do serviço Microsoft Exchange IMAP4.
1. Se não estiver em execução, habilite/inicie-o.

O seguinte trecho de código mostra como conectar e listar mensagens da pasta Caixa de Entrada do servidor Microsoft Exchange usando o protocolo IMAP.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// Conecte-se ao Exchange Server usando a classe ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.SecurityOptions = SecurityOptions.Auto;

// Selecione a pasta Caixa de Entrada
imapClient.SelectFolder(ImapFolderInfo.InBox);

// Obtenha a lista de mensagens
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine(msgInfo.Subject);
}
// Desconecte do servidor
imapClient.Dispose();
```

O seguinte trecho de código mostra como usar SSL.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // Conecte-se ao Exchange Server usando a classe ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1", new RemoteCertificateValidationCallback(RemoteCertificateValidationHandler));
    imapClient.SecurityOptions = SecurityOptions.SSLExplicit;

    // Selecione a pasta Caixa de Entrada
    imapClient.SelectFolder(ImapFolderInfo.InBox);

    // Obtenha a lista de mensagens
    ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
    foreach (ImapMessageInfo msgInfo in msgCollection)
    {
        Console.WriteLine(msgInfo.Subject);
    }
    // Desconecte do servidor
    imapClient.Dispose();   
}

// Manipulador de verificação de certificado
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // ignora as verificações e continua
}
```

Após a conexão com um servidor Exchange usando IMAP e a obtenção da [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), você pode obter o objeto [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/). O seguinte trecho de código mostra como usar o número de sequência do objeto [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) para salvar uma mensagem específica.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// Selecione a pasta Caixa de Entrada
imapClient.SelectFolder(ImapFolderInfo.InBox);
// Obtenha a lista de mensagens
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    // Busque a mensagem da caixa de entrada usando seu SequenceNumber de msgInfo
    MailMessage message = imapClient.FetchMessage(msgInfo.SequenceNumber);

    // Salve a mensagem agora no disco
    message.Save(dataDir + msgInfo.SequenceNumber + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

### Definindo a versão preferencial do protocolo de criptografia

EWS usa o protocolo de transporte HTTPS para operações suportadas. A criptografia é fornecida pelos protocolos **SSL/TLS**. Esses protocolos são implementados pelo framework .NET e podem ser diferentes dependendo da versão atual do framework .NET.

Para definir a versão **SSL/TLS**, use o seguinte código:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
ou

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Observe que, se o protocolo de criptografia especificado não for suportado pela versão atual do framework .NET, a propriedade [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) atualiza o protocolo de criptografia para um nível suportado e o método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) lança uma exceção.