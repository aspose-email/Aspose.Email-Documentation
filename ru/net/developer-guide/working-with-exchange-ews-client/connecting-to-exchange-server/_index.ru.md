---
title: "Подключение к серверу Exchange"
url: /ru/net/connecting-to-exchange-server/
weight: 10
type: docs
---


Чтобы подключиться к серверам Exchange 2007, 2010 и 2013 с помощью веб-службы Exchange, Aspose.Email предоставляет [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) интерфейс, реализующий [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс. [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) метод создает экземпляр и возвращает [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) объект, который в дальнейшем используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. В этой статье показано, как создавать экземпляры объектов [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Подключение к серверу Exchange с помощью EWS**

В следующем фрагменте кода показано, как подключиться с помощью веб-службы Exchange (EWS).

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

## **Подключение к серверу Exchange с помощью протокола IMAP**

Microsoft Exchange Server поддерживает протокол IMAP для доступа к элементам в почтовом ящике. Используйте Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс для подключения к серверу Exchange по протоколу IMAP. Для получения дополнительной информации о [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс. Во-первых, убедитесь, что службы IMAP включены на вашем сервере Exchange:

1. Откройте панель управления.
1. Перейдите в раздел «Инструменты администратора», затем «Службы».
1. Проверьте состояние службы Microsoft Exchange IMAP4.
1. Если он еще не запущен, включите/запустите его.

В следующем фрагменте кода показано, как подключать и отображать сообщения из папки «Входящие» на сервере Microsoft Exchange с использованием протокола IMAP.

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

В следующем фрагменте кода показано, как использовать SSL.

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

После подключения к серверу Exchange по протоколу IMAP и получения [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), вы можете получить [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) объект. В следующем фрагменте кода показано, как использовать порядковый номер [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) объект для сохранения определенного сообщения.

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

### Настройка предпочтительной версии протокола шифрования

Для поддерживаемых операций EWS использует транспортный протокол HTTPS. Шифрование обеспечивается **SSL/TLS** протоколы. Эти протоколы реализованы фреймворком.NET и могут отличаться в зависимости от текущей версии платформы.NET.

Установить **SSL/TLS** версия использует следующий код:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
or

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Обратите внимание: если указанный EncryptionProtocol не поддерживается текущей версией платформы.NET, [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) свойство понижает протокол шифрования до поддерживаемого уровня, а [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод генерирует исключение.