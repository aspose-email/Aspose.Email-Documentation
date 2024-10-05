---
title: "Подключение к POP3 серверу"
url: /ru/net/connect-to-pop3-server/
weight: 10
type: docs
---

## Подключение к POP3 серверу

Класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) позволяет приложениям управлять почтовыми ящиками с использованием Протокола Почтового Офиса, версия 3 (POP3). Чтобы подключиться к серверу, используйте класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). Класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) является основным входом для разработчиков, которые хотят добавить управление POP3 в свои .NET приложения. Эта статья объясняет, как его использовать. Чтобы подключиться к POP3 серверу:

1. Создайте экземпляр класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Укажите хост, имя пользователя и пароль в экземпляре [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

Следующий фрагмент кода показывает, как подключиться к POP3 серверу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

## **Подключение к SSL серверу**

[Подключение к POP3 серверу](#connecting-to-a-pop3-server) описывает, как подключиться к POP3 серверу в два простых шага:

1. Создайте экземпляр класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Укажите хост, имя пользователя и пароль.

Процесс подключения к SSL-совместимому POP3 серверу похож, но требует установки еще нескольких свойств:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Порт

Чтобы подключиться к SSL-совместимому POP3 серверу, используйте класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) и установите свойства [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) и Port. Следующий фрагмент кода показывает, как подключиться к SSL-совместимому POP3 серверу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

## **Подключение с APOP сервером**

POP означает Протокол Почтового Офиса. APOP означает Аутентифицированный Протокол Почтового Офиса. APOP является расширенной версией настройки сервера POP3, которая шифрует ваше имя пользователя и пароль и использует механизм аутентификации, предназначенный для защиты пароля вашей учетной записи POP3 при проверке электронной почты. Аутентификация APOP не требует, чтобы пароль учетной записи отправлялся в открытом виде на почтовый сервер POP3.

## **Подключение к серверу через прокси**

Прокси-серверы очень распространены для общения с внешним миром. В таких случаях адреса прокси используются для почтовых клиентов для доступа к почтовым ящикам через Интернет. Aspose.Email поддерживает версии 4, 4a и 5 протокола SOCKS. Эта статья предоставляет рабочий пример получения электронной почты с использованием прокси-почтового сервера. Чтобы получить электронную почту через прокси-сервер:

1. Инициализируйте [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) с необходимой информацией, то есть адресом прокси, портом и версией SOCKS.
1. Инициализируйте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
1. Установите свойство Proxy клиента в созданный выше объект [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/).

Следующий фрагмент кода показывает, как получить электронную почту через прокси-сервер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

## **Подключение к серверу через HTTP-прокси**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

## **Подключение к серверу через механизм аутентификации CRAM-MD5**

Используя аутентификацию CRAM-MD5, Aspose.Email для .NET позволяет пользователям безопасно аутентифицироваться и получать доступ к почтовым серверам, поддерживающим этот метод аутентификации. Пример кода ниже показывает, как использовать механизм в вашем проекте:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (задержки сети, размер данных, производительность сервера и т.д.). Вы можете установить тайм-аут для всех почтовых операций. Пример кода ниже показывает, как это сделать с помощью свойства [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Примечание: не устанавливайте большие значения, чтобы избежать долгих ожиданий в вашем приложении.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 секунд

    // какой-то код...
}
```

## **Использование криптографических протоколов с POP3 клиентом**

Aspose.Email поддерживает SSL (устаревший) и TLS криптографические протоколы для обеспечения безопасности коммуникаций. Вы можете включить криптографическое шифрование для защиты обмена данными между вашим приложением и почтовыми серверами.

> **_ПРИМЕЧАНИЕ:_** Вы должны устанавливать только те версии протокола, которые поддерживаются .NET Framework. Если некоторые версии криптографического протокола не поддерживаются вашей текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут сгенерированы. Пожалуйста, используйте метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), если вы хотите установить протоколы без проверок совместимости.

Пример кода ниже показывает, как установить TLS 1.3 для экземпляра класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // какой-то код...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении между методом [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) и свойством [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) следующая:

- Если используется свойство [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
  
- Если используется метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), почтовый клиент выбрасывает исключения.