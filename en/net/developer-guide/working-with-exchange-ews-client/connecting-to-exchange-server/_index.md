---
title: Connecting to Exchange Server
type: docs
weight: 10
url: /net/connecting-to-exchange-server/
---


In order to connect to Exchange servers 2007, 2010 and 2013 using Exchange Web Service, Aspose.Email provides the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface that implements the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class. The [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method instantiates and returns an [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) object that is further used to perform operations related to an Exchange mailbox and other folders. This article shows how to instantiate objects of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Connecting to Exchange Server using EWS**

The following code snippet shows you how to connect using Exchange Web Service (EWS).

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

## **Connecting to Exchange Server using IMAP**

Microsoft Exchange Server supports the IMAP protocol for accessing items in a mailbox. Use Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class to connect to the Exchange Server using the IMAP protocol. For more information about the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class. First, make sure that IMAP services are enabled for your Exchange Server:

1. Open the Control Panel.
1. Go to Administrator Tools, then Services.
1. Check the status of the Microsoft Exchange IMAP4 service.
1. If it is not already running, enable/start it.

The following code snippet shows you how to connect and list messages from the Inbox folder of Microsoft exchange server using IMAP protocol.

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

The following code snippet shows you how to use SSL.

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

After connecting to an Exchange server using IMAP and getting the [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), you can get the [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) object. The following code snippet shows you how to use the  sequence number of the [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) object to save a specific message.

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

### Setting the preferred version of the encryption protocol

EWS uses HTTPS transport protocol for supported operations. Encryption is provided by **SSL/TLS** protocols. These protocols are implemented by the .NET framework and may be different in dependence on the current version of the .NET framework.

To set **SSL/TLS** version use the following code:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
or

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Note, if the specified EncryptionProtocol isn't supported by the current version of the .NET framework, the [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property downgrades the encryption protocol to a supported level and the [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method throws an exception.