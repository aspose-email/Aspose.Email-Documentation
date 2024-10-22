---
title: "Conectarse al servidor de Exchange"
url: /es/net/conectarse-al-servidor-de-exchange/
weight: 10
type: docs
---

Para conectarse a servidores de Exchange 2007, 2010 y 2013 utilizando Exchange Web Service, Aspose.Email proporciona la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) que implementa la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). El método [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) instancia y devuelve un objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) que se utiliza posteriormente para realizar operaciones relacionadas con un buzón de Exchange y otras carpetas. Este artículo muestra cómo instanciar objetos de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Conectarse al servidor de Exchange utilizando EWS**

El siguiente fragmento de código muestra cómo conectarse utilizando Exchange Web Service (EWS).

```csharp
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
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

## **Conectarse al servidor de Exchange utilizando IMAP**

Microsoft Exchange Server soporta el protocolo IMAP para acceder a los elementos de un buzón. Utilice la clase Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para conectarse al servidor de Exchange utilizando el protocolo IMAP. Para obtener más información sobre la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Primero, asegúrese de que los servicios IMAP están habilitados para su servidor de Exchange:

1. Abra el Panel de control.
1. Vaya a Herramientas administrativas, luego Servicios.
1. Verifique el estado del servicio Microsoft Exchange IMAP4.
1. Si no está en ejecución, habilítelo/inícielo.

El siguiente fragmento de código muestra cómo conectarse y listar mensajes desde la carpeta de Bandeja de entrada del servidor de Microsoft Exchange utilizando el protocolo IMAP.

```csharp
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Conectar al servidor de Exchange utilizando la clase ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.SecurityOptions = SecurityOptions.Auto;

// Seleccionar la carpeta de Bandeja de entrada
imapClient.SelectFolder(ImapFolderInfo.InBox);

// Obtener la lista de mensajes
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine(msgInfo.Subject);
}
// Desconectarse del servidor
imapClient.Dispose();
```

El siguiente fragmento de código muestra cómo utilizar SSL.

```csharp
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // Conectar al servidor de Exchange utilizando la clase ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1", new RemoteCertificateValidationCallback(RemoteCertificateValidationHandler));
    imapClient.SecurityOptions = SecurityOptions.SSLExplicit;

    // Seleccionar la carpeta de Bandeja de entrada
    imapClient.SelectFolder(ImapFolderInfo.InBox);

    // Obtener la lista de mensajes
    ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
    foreach (ImapMessageInfo msgInfo in msgCollection)
    {
        Console.WriteLine(msgInfo.Subject);
    }
    // Desconectarse del servidor
    imapClient.Dispose();   
}

// Manejador de verificación de certificado
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // ignorar las verificaciones y continuar
}
```

Después de conectarse a un servidor de Exchange utilizando IMAP y obtener la [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), puede obtener el objeto [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/). El siguiente fragmento de código muestra cómo utilizar el número de secuencia del objeto [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) para guardar un mensaje específico.

```csharp
// Para ejemplos completos y archivos de datos, dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Seleccionar la carpeta de Bandeja de entrada
imapClient.SelectFolder(ImapFolderInfo.InBox);
// Obtener la lista de mensajes
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    // Recuperar el mensaje de la bandeja de entrada utilizando su SequenceNumber de msgInfo
    MailMessage message = imapClient.FetchMessage(msgInfo.SequenceNumber);

    // Guardar el mensaje en disco ahora
    message.Save(dataDir + msgInfo.SequenceNumber + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

### Establecer la versión preferida del protocolo de cifrado

EWS utiliza el protocolo de transporte HTTPS para las operaciones admitidas. El cifrado es proporcionado por los protocolos **SSL/TLS**. Estos protocolos están implementados por el marco .NET y pueden variar en dependencia de la versión actual del marco .NET.

Para establecer la versión **SSL/TLS**, use el siguiente código:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
o

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Tenga en cuenta que, si el EncryptionProtocol especificado no es compatible con la versión actual del marco .NET, la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) degrada el protocolo de cifrado a un nivel compatible y el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) lanza una excepción.