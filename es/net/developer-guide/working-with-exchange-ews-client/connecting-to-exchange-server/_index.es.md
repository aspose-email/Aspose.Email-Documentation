---
title: "Conexión a Exchange Server"
url: /es/net/connecting-to-exchange-server/
weight: 10
type: docs
---


Para conectarse a los servidores Exchange 2007, 2010 y 2013 mediante el servicio web de Exchange, Aspose.Email proporciona [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interfaz que implementa el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase. El [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) el método crea una instancia y devuelve un [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) objeto que se utiliza además para realizar operaciones relacionadas con un buzón de Exchange y otras carpetas. En este artículo se muestra cómo crear instancias de objetos de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Conexión a Exchange Server mediante EWS**

El siguiente fragmento de código muestra cómo conectarse mediante Exchange Web Service (EWS).

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
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

## **Conexión a Exchange Server mediante IMAP**

Microsoft Exchange Server admite el protocolo IMAP para acceder a los elementos de un buzón. Utilice Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) clase para conectarse al servidor Exchange mediante el protocolo IMAP. Para obtener más información acerca de [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) clase. En primer lugar, asegúrese de que los servicios IMAP estén habilitados para su servidor Exchange:

1. Abre el panel de control.
1. Vaya a Herramientas de administración y, a continuación, a Servicios.
1. Compruebe el estado del servicio IMAP4 de Microsoft Exchange.
1. Si aún no se está ejecutando, habilítelo o inícielo.

El siguiente fragmento de código muestra cómo conectar y enumerar los mensajes de la carpeta Bandeja de entrada del servidor Microsoft Exchange mediante el protocolo IMAP.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Connect to Exchange Server using ImapClient class
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.SecurityOptions = SecurityOptions.Auto;

// Select the Inbox folder
imapClient.SelectFolder(ImapFolderInfo.InBox);

// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine(msgInfo.Subject);
}
// Disconnect from the server
imapClient.Dispose();
```

El siguiente fragmento de código muestra cómo usar SSL.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{           
    // Connect to Exchange Server using ImapClient class
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1", new RemoteCertificateValidationCallback(RemoteCertificateValidationHandler));
    imapClient.SecurityOptions = SecurityOptions.SSLExplicit;

    // Select the Inbox folder
    imapClient.SelectFolder(ImapFolderInfo.InBox);

    // Get the list of messages
    ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
    foreach (ImapMessageInfo msgInfo in msgCollection)
    {
        Console.WriteLine(msgInfo.Subject);
    }
    // Disconnect from the server
    imapClient.Dispose();  
}

// Certificate verification handler
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // ignore the checks and go ahead
}
```

Tras conectarse a un servidor de Exchange mediante IMAP y obtener el [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), puedes obtener el [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) objeto. El siguiente fragmento de código muestra cómo usar el número de secuencia del [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) objeta para guardar un mensaje específico.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Select the Inbox folder
imapClient.SelectFolder(ImapFolderInfo.InBox);
// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    // Fetch the message from inbox using its SequenceNumber from msgInfo
    MailMessage message = imapClient.FetchMessage(msgInfo.SequenceNumber);

    // Save the message to disc now
    message.Save(dataDir + msgInfo.SequenceNumber + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

### Configuración de la versión preferida del protocolo de cifrado

EWS utiliza el protocolo de transporte HTTPS para las operaciones compatibles. El cifrado lo proporciona **SSL/TLS** protocolos. Estos protocolos los implementa el.NET Framework y pueden ser diferentes en función de la versión actual del.NET Framework.

Para configurar **SSL/TLS** versión usa el siguiente código:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
or

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Tenga en cuenta que si la versión actual de .NET Framework no admite el protocolo de cifrado especificado, [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) propiedad degrada el protocolo de cifrado a un nivel compatible y el [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) el método arroja una excepción.