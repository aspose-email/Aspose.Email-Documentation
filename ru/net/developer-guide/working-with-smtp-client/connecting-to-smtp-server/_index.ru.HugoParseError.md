---
title: Подключение к SMTP-серверу
type: docs
weight: 10
url: /net/connecting-to-smtp-server/
---

При работе с почтовыми клиентами определенные операции могут занимать значительное время для выполнения. Чтобы предотвратить бесконечное выполнение этих операций, пользователи могут использовать свойство [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Важно отметить, что значения, назначенные этому свойству, должны иметь достаточные интервалы, чтобы учесть длительные операции.

Тем не менее, полагаться исключительно на свойство Timeout может привести к тому, что установление соединения займёт больше времени, чем ожидалось. Это может произойти, когда почтовый клиент использует автоматический режим для установки соединения. В этом режиме клиент перебирает различные параметры соединения, пока не будет установлено соединение.

При подключении к SMTP, IMAP и POP3 серверам строка приветствия отправляется клиенту после успешного установления соединения. Серверы могут использовать неявную или явную (START TLS) инициацию соединения SSL/TLS. В случаях, когда режим соединения не соответствует (например, сервер ожидает неявное SSL-соединение, в то время как клиент пытается установить незащищённое или явное SSL-соединение), сервер не отправит строку приветствия.

В результате пользователь может ожидать длительное время, пока не истечёт время ожидания, и клиент перейдёт к следующему варианту подключения.

Чтобы решить эту проблему, было введено свойство [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/). Это свойство позволяет пользователям установить тайм-аут для строки приветствия, сокращая время, необходимое для установления автоматического соединения. Реализуя свойство **GreetingTimeout**, пользователи могут оптимизировать производительность своего почтового клиента и избежать длительных ожиданий во время установления соединения.

Следующий пример кода показывает, как установить свойство [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/):

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Подключение к серверу через Socks-прокси**

Иногда мы используем прокси-серверы для связи с внешним миром. В таких случаях почтовые клиенты не могут общаться по Интернету, не указав адрес прокси. Aspose.Email поддерживает версии 4, 4a и 5 протокола прокси SOCKS. В этой статье представлен рабочий пример отправки электронного письма с использованием почтового прокси-сервера. Чтобы отправить электронное письмо через прокси-сервер:

1. Инициализируйте прокси с необходимой информацией, то есть адресом прокси, портом и версией SOCKS.
1. Инициализируйте [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) с адресом хоста, именем пользователя и паролем, а также любыми другими настройками.
1. Установите свойство Proxy клиента в объект [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/), созданный ранее.

Следующий фрагмент кода показывает, как подключиться к серверу через прокси-сервер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Подключение к серверу через HTTP-прокси**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Подключение к серверу с использованием поддерживаемого метода аутентификации**

Aspose.Email для .NET предлагает свойства, позволяющие проверить, какие методы аутентификации могут быть использованы для установления безопасного соединения с SMTP-сервером перед отправкой электронной почты:
- свойство [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) возвращает список методов аутентификации, поддерживаемых SMTP-сервером. 
- свойство [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) возвращает список методов аутентификации, определенных пользователем.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Загрузка информации для аутентификации SMTP из файла CONFIG**

Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) позволяет приложениям считывать информацию для аутентификации, такую как имя пользователя и пароль, а также адрес хоста и номер порта непосредственно из файла конфигурации. Использование родного тега конфигурации .NET, как показано ниже, позволяет классу [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) считывать эту информацию через Диспетчер конфигурации, также доступный в .NET Framework. Чтобы Aspose.Email мог считывать файл конфигурации, он должен быть в правильном формате. Ниже приведен пример XML-файла конфигурации, за которым следует код, который его считывает. Следующий фрагмент кода показывает, как загрузить информацию для аутентификации SMTP из файла CONFIG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

После определения конфигурационных настроек загрузите эти настройки непосредственно в экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) с использованием одного из его перегруженных конструкторов. Следующий фрагмент кода демонстрирует считывание конфигурационных настроек из файла конфигурации и загрузку их непосредственно в экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Привязка SMTP-клиента к конкретному IP-адресу на хосте**

Не исключается возможность, что у хоста есть несколько доступных портов для отправки электронных писем. В таких случаях может возникнуть необходимость привязать клиент для отправки электронной почты к конкретному порту на хосте. Это можно сделать с помощью API Aspose.Email, используя свойство [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint). API [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) может быть настроен для использования конкретного IP-адреса на хосте, указав конкретный IP-эндпоинт. Следующий фрагмент кода показывает, как привязать SMTP-клиент к конкретному IP-адресу на хосте.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от множества факторов (задержки сети, размер данных, производительность сервера и т. д.). Вы можете установить тайм-аут для всех почтовых операций. Пример кода ниже показывает, как это сделать, используя свойство [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Примечание: вы не должны устанавливать большие значения, чтобы избежать длительных ожиданий в вашем приложении.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 секунд

    // какой-то код...
}
```

## **Использование криптографических протоколов с SMTP-клиентом**

Aspose.Email поддерживает SSL (устаревший) и TLS криптографические протоколы для обеспечения безопасности связи. Вы можете включить криптографическое шифрование, чтобы защитить обмен данными между вашим приложением и почтовыми серверами.

> **_ПРИМЕЧАНИЕ:_**  Вы должны устанавливать только те версии протокола, которые поддерживаются .NET Framework. Если какие-то версии криптографического протокола не поддерживаются вашей текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут генерироваться. Пожалуйста, используйте метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), если вы хотите установить протоколы без проверок совместимости.

Пример кода ниже показывает, как установить TLS 1.3 для экземпляра класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // какой-то код...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, различие в поведении между методом [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) и свойством [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) следующее:
- Если используется свойство [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
- Если используется метод [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), почтовый клиент выбрасывает исключения.

##  **Использование механизма CRAM-MD5 для аутентификации**

Механизм аутентификации CRAM-MD5 в Aspose.Email для .NET предоставляет дополнительный уровень безопасности при доступе к серверу. Следующий фрагмент кода показывает, как реализовать эту функцию в вашем проекте:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```