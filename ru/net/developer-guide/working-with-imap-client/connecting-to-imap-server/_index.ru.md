---
title: "Подключение к серверу IMAP"
url: /ru/net/connecting-to-imap-server/
weight: 10
type: docs
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс позволяет приложениям управлять почтовыми ящиками IMAP с помощью протокола IMAP. [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс используется для подключения к почтовым серверам IMAP и управления электронной почтой в папках электронной почты IMAP. Для подключения к серверу IMAP

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Укажите имя хоста, имя пользователя и пароль в поле [Конструктор IMAP-клиентов](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Обратите внимание, что ограничения по паролям должны соответствовать требованиям сервера. Почтовый клиент не добавляет ограничений по паролям.**

Как только [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) экземпляр инициирован, следующий вызов любой операции с использованием этого экземпляра подключится к серверу. В следующем фрагменте кода показано, как подключиться к серверу IMAP, используя описанные выше шаги.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Подключение к серверу IMAP с поддержкой SSL**

[Подключение к серверу IMAP](/email/net/connecting-to-imap-server#connecting-with-imap-server) описал, как подключиться к серверу IMAP за четыре простых шага:

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Укажите имя хоста, имя пользователя и пароль.
1. Укажите порт.
1. Укажите параметры безопасности.

Процесс подключения к серверу IMAP с поддержкой SSL аналогичен, но требует установки еще нескольких свойств:

- Задайте для параметров безопасности значение SSLimplicit.

В следующем фрагменте кода показано, как

1. Задайте имя пользователя, пароль и порт.
1. Задайте параметр безопасности.


```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте экземпляр ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
           
// Set the security mode to implicit
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Подключение к серверу через прокси-сервер**

Прокси-серверы обычно используются для связи с внешним миром. В таких случаях почтовые клиенты не могут обмениваться данными через Интернет без указания адреса прокси-сервера. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. В этой статье представлен рабочий пример доступа к почтовому ящику с помощью прокси-почтового сервера. Чтобы получить доступ к почтовому ящику через прокси-сервер, выполните следующие действия:

1. Initialize [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) с необходимой информацией, то есть адресом прокси-сервера, портом и версией SOCKS.
1. Initialize [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
1. Установите значение клиента [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) собственность клиента в пользу [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) объект, созданный выше.

В следующем фрагменте кода показано, как получить почтовый ящик через прокси-сервер.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Connect and log in to IMAP and set SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
           
string proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Set the proxy
client.Proxy = proxy;
          
try
{
    client.SelectFolder("Inbox");
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

## **Подключение к серверу через HTTP-прокси-сервер**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Подключение к серверу в режиме «только для чтения»**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс предоставляет [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) свойство, для которого задано значение **true**, указывает на то, что не следует вносить никаких изменений в постоянное состояние почтового ящика. Следующий пример кода демонстрирует использование [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) имущество. Оно определяет количество непрочитанных сообщений, затем извлекает одно сообщение, а затем снова получает количество непрочитанных сообщений в режиме «только для чтения». Количество непрочитанных сообщений осталось прежним, что означает, что постоянное состояние почтового ящика не изменилось.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* get unread messages. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Initial Unread Count: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // This count will be equal to the initial count
    Console.WriteLine("Updated Unread Count: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("No unread messages found");
}
```
## **Подключение к серверу с использованием аутентификации CRAM-MD5**

Для безопасной аутентификации и доступа к почтовому серверу Aspose.Email for .NET предлагает метод аутентификации CRAM-MD5.
Следующий фрагмент кода покажет вам, как он работает с IMapClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Как ограничить тайм-аут приветствия**

Клиент IMAP может использовать автоматический режим для установления соединения. В этом режиме клиент IMAP проверяет все возможные параметры соединения до тех пор, пока соединение не будет установлено. Сервер IMAP в случае правильного соединения отправляет клиенту строку приветствия. Серверы могут использовать неявное или явное (START TLS) инициирование соединения SSL/TLS. Если режим соединения не совпадает (например, сервер ожидает неявного SSL-соединения, но клиент пытается установить незащищенное или явное SSL-соединение), сервер не отправит строку приветствия, а пользователь будет долго ждать, пока тайм-аут не достигнет строки приветствия, и клиент перейдет к следующему варианту подключения. Чтобы избежать этой проблемы, было введено свойство greetingTimeout. Это свойство позволяет установить тайм-аут для строки приветствия и сократить время автоматического установления соединения.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Использование криптографических протоколов с клиентом IMAP**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Для защиты обмена данными между приложением и почтовыми серверами можно включить криптографическое шифрование.

> **_NOTE:_**  Следует устанавливать только те версии протокола, которые поддерживаются платформе.NET Framework. Если некоторые версии криптографического протокола не поддерживаются текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут созданы. Пожалуйста, используйте [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод, если вы хотите установить протоколы без каких-либо проверок совместимости.

В приведенном ниже примере кода показано, как установить TLS 1.3 для [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) экземпляр класса.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении между [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод и [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) свойство следующее:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) используется свойство, почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) используется метод, почтовый клиент генерирует исключения.
