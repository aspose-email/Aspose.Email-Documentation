---
title: "Подключение к IMAP-серверу"
url: /ru/net/connecting-to-imap-server/
weight: 10
type: docs
---

Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) позволяет приложениям управлять почтовыми ящиками IMAP с использованием протокола IMAP. Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) используется для подключения к IMAP-почтовым серверам и управления электронной почтой в папках IMAP. Чтобы подключиться к IMAP-серверу

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Укажите имя хоста, имя пользователя и пароль в [конструкторе ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Примечание: ограничения на пароль должны соответствовать требованиям сервера. Почтовый клиент не добавляет ограничения на пароли.**

После инициализации экземпляра [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) следующий вызов любой операции с использованием этого экземпляра подключится к серверу. Следующий фрагмент кода показывает, как подключиться к IMAP-серверу, следуя вышеуказанным шагам.

```csharp
// Для получения полных примеров и файлов данных перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте imapclient с хостом, пользователем и паролем
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Подключение к IMAP-серверу с включённым SSL**

[Подключение к IMAP-серверу](/email/net/connecting-to-imap-server#connecting-with-imap-server) описывает, как подключиться к IMAP-серверу в четыре простых шага:

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Укажите имя хоста, имя пользователя и пароль.
1. Укажите порт.
1. Укажите параметры безопасности.

Процесс подключения к IMAP-серверу с включённым SSL аналогичен, но требует установки ещё нескольких свойств:

- Установите параметры безопасности на SSLImplicit.

Следующий фрагмент кода показывает, как

1. Установить имя пользователя, пароль и порт.
1. Установить параметры безопасности.

```csharp
// Для получения полных примеров и файлов данных перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте экземпляр класса ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
            
// Установите режим безопасности как implicit
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Подключение к серверу через прокси**

Прокси-серверы обычно используются для связи с внешним миром. В таких случаях почтовые клиенты не могут связываться через Интернет без указания адреса прокси. Aspose.Email поддерживает версии 4, 4a и 5 протокола SOCKS. Эта статья предоставляет рабочий пример доступа к почтовому ящику с использованием прокси-почтового сервера. Чтобы получить доступ к почтовому ящику через прокси-сервер:

1. Инициализируйте [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) с необходимой информацией, т.е. адресом прокси, портом и версией SOCKS.
1. Инициализируйте [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
1. Установите свойство клиента [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) клиента на созданный выше объект [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/).

Следующий фрагмент кода показывает, как получить почтовый ящик через прокси-сервер.

```csharp
// Для получения полных примеров и файлов данных перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Подключитесь и войдите в IMAP и установите SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
            
string proxyAddress = "192.168.203.142"; // адрес прокси
int proxyPort = 1080; // порт прокси
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Установите прокси
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

## **Подключение к серверу через HTTP-прокси**

```csharp
// Для получения полных примеров и файлов данных перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Подключение к серверу в режиме только для чтения**

Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет свойство [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/), которое при установке в **true** указывает на то, что изменения не должны вноситься в постоянное состояние почтового ящика. Следующий пример кода демонстрирует использование свойства [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/). Он получает количество непрочитанных сообщений, затем загружает одно сообщение и затем снова получает количество непрочитанных сообщений в режиме только для чтения. Количество непрочитанных сообщений остается прежним, что указывает на то, что постоянное состояние почтового ящика не было изменено.

```csharp
// Для получения полных примеров и файлов данных перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* получить непрочитанные сообщения. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Начальное количество непрочитанных: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // Это количество будет равно начальному количеству
    Console.WriteLine("Обновлённое количество непрочитанных: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("Непрочитанных сообщений не найдено");
}
```
## **Подключение к серверу с использованием аутентификации CRAM-MD5**

Для безопасной аутентификации и доступа к почтовому серверу Aspose.Email для .NET предлагает метод аутентификации CRAM-MD5.
Следующий фрагмент кода покажет, как это работает с ImapClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (задержки в сети, размер данных, производительность сервера и т. д.). Вы можете установить тайм-аут для всех почтовых операций. Пример кода ниже показывает, как это сделать, используя свойство [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Примечание: не устанавливайте большие значения, чтобы избежать длительного ожидания в вашем приложении.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 секунд

    // какой-то код...
}
```

## **Как ограничить тайм-аут приветствия**

IMAP-клиент может использовать автоматический режим для установления соединения. В этом режиме IMAP-клиент проходит через все возможные параметры соединения, пока соединение не будет установлено. IMAP-сервер в случае корректного подключения отправляет строку приветствия клиенту. Серверы могут использовать неявное или явное (START TLS) начало SSL/TLS-соединения. Если режим соединения несовпадает (например, сервер ожидает неявного SSL-соединения, но клиент пытается установить незащищённое или явное SSL-соединение), сервер не отправит строку приветствия, и пользователь будет долго ждать, пока тайм-аут не достигнет текста приветствия, и клиент перейдёт к следующему варианту соединения. Чтобы избежать этой проблемы, было введено свойство GreetingTimeout. Это свойство позволяет установить тайм-аут для строки приветствия и сократить время установления автоматического соединения.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Использование криптографических протоколов с IMAP-клиентом**

Aspose.Email поддерживает криптографические протоколы SSL (устаревший) и TLS для обеспечения безопасности связи. Вы можете включить криптографическое шифрование для защиты обмена данными между вашим приложением и почтовыми серверами.

> **_ПРИМЕЧАНИЕ:_** Вы должны настраивать только те версии протокола, которые поддерживаются .NET Framework. Если некоторые версии криптографического протокола не поддерживаются вашей текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут генерироваться. Пожалуйста, используйте метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), если хотите установить протоколы без проверки совместимости.

Пример кода ниже показывает, как установить TLS 1.3 для экземпляра класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // какой-то код...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении между методом [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) и свойством [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) следующая:
- Если используется свойство [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), почтовый клиент понижает уровень протокола шифрования до поддерживаемого.
- Если используется метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), почтовый клиент генерирует исключения.