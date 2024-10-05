---
title: Подключение к Exchange Server
type: docs
weight: 10
url: /net/подключение-к-exchange-server/
---


Для подключения к Exchange Server 2007, 2010 и 2013 с использованием Exchange Web Service Aspose.Email предоставляет интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/), который реализует класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Метод [EWSClient.GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) создает и возвращает объект [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/), который далее используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. В этой статье показано, как создавать объекты [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

## **Подключение к Exchange Server с использованием EWS**

Следующий фрагмент кода показывает, как подключиться с использованием Exchange Web Service (EWS).

```csharp
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-.NET
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

## **Подключение к Exchange Server с использованием IMAP**

Microsoft Exchange Server поддерживает протокол IMAP для доступа к элементам в почтовом ящике. Используйте класс Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) для подключения к Exchange Server с использованием протокола IMAP. Для получения дополнительной информации о классе [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) сначала убедитесь, что службы IMAP включены для вашего Exchange Server:

1. Откройте Панель управления.
1. Перейдите в Административные инструменты, затем в Службы.
1. Проверьте статус службы Microsoft Exchange IMAP4.
1. Если она еще не запущена, включите/запустите ее.

Следующий фрагмент кода показывает, как подключиться и получить список сообщений из папки "Входящие" Microsoft Exchange Server, используя протокол IMAP.

```csharp
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Подключение к Exchange Server с использованием класса ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.SecurityOptions = SecurityOptions.Auto;

// Выбор папки "Входящие"
imapClient.SelectFolder(ImapFolderInfo.InBox);

// Получение списка сообщений
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine(msgInfo.Subject);
}
// Отключение от сервера
imapClient.Dispose();
```

Следующий фрагмент кода показывает, как использовать SSL.

```csharp
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // Подключение к Exchange Server с использованием класса ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1", new RemoteCertificateValidationCallback(RemoteCertificateValidationHandler));
    imapClient.SecurityOptions = SecurityOptions.SSLExplicit;

    // Выбор папки "Входящие"
    imapClient.SelectFolder(ImapFolderInfo.InBox);

    // Получение списка сообщений
    ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
    foreach (ImapMessageInfo msgInfo in msgCollection)
    {
        Console.WriteLine(msgInfo.Subject);
    }
    // Отключение от сервера
    imapClient.Dispose();   
}

// Обработчик проверки сертификата
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // игнорировать проверки и продолжить
}
```

После подключения к Exchange Server с использованием IMAP и получения [IMapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) вы можете получить объект [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/). Следующий фрагмент кода показывает, как использовать номер последовательности объекта [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) для сохранения конкретного сообщения.

```csharp
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Выбор папки "Входящие"
imapClient.SelectFolder(ImapFolderInfo.InBox);
// Получение списка сообщений
ImapMessageInfoCollection msgCollection = imapClient.ListMessages();
foreach (ImapMessageInfo msgInfo in msgCollection)
{
    // Получение сообщения из входящих по его SequenceNumber из msgInfo
    MailMessage message = imapClient.FetchMessage(msgInfo.SequenceNumber);

    // Сохранение сообщения на диск
    message.Save(dataDir + msgInfo.SequenceNumber + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

### Установка предпочтительной версии протокола шифрования

EWS использует протокол передачи HTTPS для поддерживаемых операций. Шифрование обеспечивается протоколами **SSL/TLS**. Эти протоколы реализованы в .NET Framework и могут различаться в зависимости от текущей версии .NET Framework.

Чтобы установить версию **SSL/TLS**, используйте следующий код:

            var client = new ImapClient("some.host");
            client.SupportedEncryption = EncryptionProtocols.Tls13;
или

            var client = new ImapClient("some.host");
            client.SetSupportedEncryptionUnsafe(EncryptionProtocols.Tls13);

Обратите внимание, если указанный протокол шифрования не поддерживается текущей версией .NET Framework, свойство [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) понижает протокол шифрования до поддерживаемого уровня, а метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) вызывает исключение.