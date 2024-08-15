---
title: "Подключение к серверу POP3"
url: /ru/net/connect-to-pop3-server/
weight: 10
type: docs
---

## Подключение к серверу POP3

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс позволяет приложениям управлять почтовыми ящиками с использованием протокола Post Office Protocol версии 3 (POP3). Чтобы подключиться к серверу, используйте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс. [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class — основная статья для разработчиков, которые хотят добавить управление POP3 в свои приложения.NET. В этой статье объясняется, как его использовать. Чтобы подключиться к серверу POP3, выполните следующие действия:

1. Создайте экземпляр [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.
2. Укажите хост, имя пользователя и пароль в поле [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) instance.

В следующем фрагменте кода показано, как подключиться к серверу POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

## **Подключение к серверу SSL**

[Подключение к серверу POP3](#connecting-to-a-pop3-server) описал, как подключиться к серверу POP3 за два простых шага:

1. Создайте экземпляр [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.
1. Укажите хост, имя пользователя и пароль.

Процесс подключения к серверу POP3 с поддержкой SSL аналогичен, но требует установки еще нескольких свойств:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Port

Чтобы подключиться к серверу POP3 с поддержкой SSL, используйте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс и установите [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) и портовая недвижимость. В следующем фрагменте кода показано, как подключиться к серверу POP3 с поддержкой SSL.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

## **Подключение к серверу APOP**

POP означает Почтовый протокол. APOP означает аутентифицированный почтовый протокол. APOP — это расширенная версия настройки сервера POP3, которая шифрует ваше имя пользователя и пароль и использует механизм аутентификации, предназначенный для защиты пароля учетной записи POP3 при проверке электронной почты. Аутентификация APOP не требует отправки пароля учетной записи в виде обычного текста на почтовый сервер POP3.

## **Подключение к серверу через прокси-сервер**

Прокси-серверы очень распространены для связи с внешним миром. В таких случаях прокси-адреса используются почтовыми клиентами для доступа к почтовым ящикам через Интернет. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. В этой статье представлен рабочий пример получения электронной почты с помощью прокси-почтового сервера. Чтобы получить электронную почту через прокси-сервер, выполните следующие действия:

1. Initialize [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) с необходимой информацией, то есть адресом прокси-сервера, портом и версией SOCKS.
1. Initialize [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
1. Задайте свойству Proxy клиента значение [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) объект, созданный выше.

В следующем фрагменте кода показано, как получить электронную почту через прокси-сервер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

## **Подключение к серверу через HTTP-прокси-сервер**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

## **Подключение к серверу через механизм аутентификации CRAM-MD5**

Используя аутентификацию CRAM-MD5, Aspose.Email for .NET позволяет пользователям безопасно аутентифицироваться и получать доступ к серверам электронной почты, поддерживающим этот метод аутентификации. В приведенном ниже примере кода показано, как использовать этот механизм в вашем проекте:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Использование криптографических протоколов с клиентом POP3**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Для защиты обмена данными между приложением и почтовыми серверами можно включить криптографическое шифрование.

> **_NOTE:_**  Следует устанавливать только те версии протокола, которые поддерживаются платформе.NET Framework. Если некоторые версии криптографического протокола не поддерживаются текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут созданы. Пожалуйста, используйте [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод, если вы хотите установить протоколы без каких-либо проверок совместимости.

В приведенном ниже примере кода показано, как установить TLS 1.3 для [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) экземпляр класса.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении между [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод и [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) свойство следующее:

- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) используется свойство, почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
 
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) используется метод, почтовый клиент генерирует исключения.
