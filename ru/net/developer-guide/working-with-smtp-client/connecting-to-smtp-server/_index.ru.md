---
title: "Подключение к SMTP-серверу"
url: /ru/net/connecting-to-smtp-server/
weight: 10
type: docs
---

При работе с почтовыми клиентами выполнение некоторых операций может занять значительное время. Чтобы эти операции не выполнялись на неопределенный срок, пользователи могут использовать [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) имущество. Важно отметить, что значения, присвоенные этому свойству, должны иметь достаточно большие интервалы для выполнения длительных операций.

Однако использование только свойства Timeout может привести к тому, что установка соединения займет больше времени, чем ожидалось. Это может произойти, когда почтовый клиент использует автоматический режим для установления соединения. В этом режиме клиент циклически переключает различные параметры соединения до тех пор, пока соединение не будет установлено.

При подключении к серверам SMTP, IMAP и POP3 после успешного установления соединения клиенту отправляется строка приветствия. Серверы могут использовать неявное или явное (START TLS) инициирование соединения SSL/TLS. В случаях, когда режим соединения не совпадает (например, сервер ожидает неявного SSL-соединения, а клиент пытается установить незащищенное или явное SSL-соединение), сервер не отправит строку приветствия.

В результате пользователь может подождать истечения тайм-аута в течение длительного периода времени, а клиент переходит к следующему варианту подключения.

Чтобы решить эту проблему, [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) недвижимость была введена. Это свойство позволяет пользователям устанавливать тайм-аут для строки приветствия, сокращая время, необходимое для установки автоматического соединения. Внедряя **Свойство GreetingTimeout**, пользователи могут оптимизировать производительность своего почтового клиента и избежать длительного ожидания при установлении соединения.

В следующем примере кода показано, как установить [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) property:

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Подключение к серверу через прокси-сервер Socks**

Иногда мы используем прокси-серверы для связи с внешним миром. В таких случаях почтовые клиенты не могут общаться через Интернет без указания адреса прокси-сервера. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 прокси-протокола SOCKS. В этой статье представлен рабочий пример отправки электронной почты с помощью прокси-почтового сервера. Чтобы отправить электронное письмо через прокси-сервер, выполните следующие действия:

1. Инициализируйте прокси-сервер, указав необходимую информацию, например адрес прокси-сервера, порт и версию SOCKS.
1. Initialize [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) с адресом хоста, именем пользователя и паролем и любыми другими настройками.
1. Задайте свойству Proxy клиента значение [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) объект, созданный ранее.

В следующем фрагменте кода показано, как подключиться к серверу через прокси-сервер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Подключение к серверу через прокси-сервер HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Подключение к серверу с использованием поддерживаемого метода аутентификации**

Aspose.Email for .NET предлагает свойства, позволяющие проверить, какие методы аутентификации можно использовать для установления безопасного соединения с SMTP-сервером перед отправкой электронного письма:
- the [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) свойство возвращает список методов аутентификации, поддерживаемых SMTP-сервером.
- the [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) свойство возвращает список методов аутентификации, определенных пользователем.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Загрузка сведений об аутентификации SMTP из файла CONFIG**

The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс позволяет приложениям считывать аутентификационную информацию, такую как имя пользователя и пароль, а также адрес хоста и номер порта, непосредственно из файла конфигурации. Использование собственного тега конфигурации.NET, как показано ниже, позволяет [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс для чтения этой информации через Configuration Manager, также доступный в.NET framework. Чтобы Aspose.Email мог читать файл конфигурации, он должен быть в правильном формате. Ниже приведен пример XML-файла конфигурации, а затем код, который его читает. В следующем фрагменте кода показано, как загрузить информацию для аутентификации SMTP из файла CONFIG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

После определения параметров конфигурации загрузите эти настройки непосредственно в экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс, использующий один из перегруженных конструкторов. Следующий фрагмент кода демонстрирует чтение настроек конфигурации из файла конфигурации и их загрузку непосредственно в экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Привязать SMTP-клиент к определенному IP-адресу на хосте**

Нельзя исключать возможность наличия на хосте нескольких портов для отправки электронной почты. В таких случаях может возникнуть необходимость привязать клиент, отправляющий электронную почту, к определенному порту на хосте для отправки электронных писем. Это может быть достигнуто также с помощью API Aspose.Email, а также с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint) имущество. API [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно настроить использование определенного IP-адреса на хосте, указав конкретную конечную точку IP. В следующем фрагменте кода показано, как привязать SMTP-клиент к определенному IP-адресу на хосте.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Использование криптографических протоколов с SMTP-клиентом**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Для защиты обмена данными между приложением и почтовыми серверами можно включить криптографическое шифрование.

> **_NOTE:_**  Следует устанавливать только те версии протокола, которые поддерживаются платформе.NET Framework. Если некоторые версии криптографического протокола не поддерживаются текущей версией .NET Framework, они будут проигнорированы и пропущены. В этом случае исключения не будут созданы. Пожалуйста, используйте [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод, если вы хотите установить протоколы без каких-либо проверок совместимости.

В приведенном ниже примере кода показано, как установить TLS 1.3 для [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) экземпляр класса.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

В случае, если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении между [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) метод и [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) свойство следующее:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) используется свойство, почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) используется метод, почтовый клиент генерирует исключения.

##  **Использование механизма CRAM-MD5 для аутентификации**

Механизм аутентификации CRAM-MD5 в Aspose.Email for .NET обеспечивает дополнительный уровень безопасности при доступе к серверу. В следующем фрагменте кода показано, как внедрить эту функцию в свой проект:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```