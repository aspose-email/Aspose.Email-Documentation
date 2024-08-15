---
title: "Отправка и пересылка сообщений - отправка электронных писем Outlook с помощью C #"
url: /ru/net/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Отправка и пересылка сообщений"
---


The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс позволяет приложениям отправлять электронную почту с использованием простого протокола передачи почты (SMTP).

- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class — единственная крупная запись, которую разработчики используют для отправки почтовых сообщений.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс также предоставляет другие распространенные методы доставки электронной почты, включая запись сообщений электронной почты в файловую систему, очередь сообщений и т. д.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс полностью поддерживает эти две модели программирования:
  - [Synchronous](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Asynchronous](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс также поддерживает [отправка сообщений в формате TNEF](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-message-as-tnef)

Чтобы отправить сообщение электронной почты и заблокировать его в ожидании передачи на SMTP-сервер, используйте один из синхронных методов отправки. Чтобы основной поток программы продолжал выполняться во время передачи электронного письма, используйте [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/) method.

## **Синхронная отправка электронных писем**

Сообщение электронной почты можно отправить синхронно с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) метод. Он отправляет указанное сообщение электронной почты через SMTP-сервер для доставки. Отправитель, получатели, тема и тело сообщения указываются с помощью объектов String. Чтобы отправить сообщение электронной почты синхронно, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс и задайте его свойства.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс и укажите хост, порт, имя пользователя и пароль.
1. Отправьте сообщение, используя [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) метод и передайте [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

В следующем фрагменте кода C# показано, как синхронно отправлять электронные письма Outlook.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port # and Security option
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;

try
{
    // Client.Send will send this message
    client.Send(msg);
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

## **Асинхронная отправка электронных писем**

Иногда вы можете захотеть отправить почту асинхронно, чтобы программа продолжала выполнять другие операции, пока электронное письмо отправляется в фоновом режиме. В частности, если вы отправляете много почты через приложение, синхронный подход может не сработать.
Начиная с платформы.NET Framework 4.5 можно использовать асинхронные методы, реализованные в соответствии с [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) модель. В приведенном ниже фрагменте кода C# показано, как отправлять сообщения электронной почты Outlook с использованием методов асинхронных шаблонов, основанных на задачах:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Отправляет указанные сообщения.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Позволяет приложениям отправлять сообщения с использованием простого протокола передачи почты (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Создает новый экземпляр класса Aspose.Email.clients.smtpClient

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Набор параметров метода aspose.email.clients.smtp.iasyncSmtpClient.sendAsync (aSpose.email.clients.smtp.models.smtpSend).

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - Аргументы aspose.email.clients.smtp.iasyncSmtpClient.ForwardAsync (aspose.email.clients.smtp.models.smtpforward).

```csharp
// Authenticate the client to obtain necessary permissions
static readonly string tenantId = "YOU_TENANT_ID";
static readonly string clientId = "YOU_CLIENT_ID";
static readonly string redirectUri = "http://localhost";
static readonly string username = "username";
static readonly string[] scopes = { "https://outlook.office.com/SMTP.Send" };

// Use the SmtpAsync method for asynchronous operations
static async Task Main(string[] args)
{
    await SmtpAsync();
    Console.ReadLine();
}

static async Task SmtpAsync()
{
    // Create token provider and get access token
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = SmtpClient.CreateAsync("outlook.office365.com", username, tokenProvider, 587).GetAwaiter().GetResult();
	
	// Create a message to send
    var eml = new MailMessage("from@domain.com", "to@domain.com", "test subj async", "test body async");
   
    // send message
    var sendOptions = SmtpSend.Create();
    sendOptions.AddMessage(eml);
    await client.SendAsync(sendOptions);
    Console.WriteLine("message was sent");

    // forward message
    var fwdOptions = SmtpForward.Create();
    fwdOptions.SetMessage(eml);
    fwdOptions.AddRecipient("rec@domain.com");
    await client.ForwardAsync(fwdOptions);
    Console.WriteLine("message was forwarded");
}

// Token provider implementation
public class TokenProvider : IAsyncTokenProvider
{
    private readonly PublicClientApplicationOptions _pcaOptions;
    private readonly string[] _scopes;

    public TokenProvider(string clientId, string tenantId, string redirectUri, string[] scopes)
    {
        _pcaOptions = new PublicClientApplicationOptions
        {
            ClientId = clientId,
            TenantId = tenantId,
            RedirectUri = redirectUri
        };

        _scopes = scopes;
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false, CancellationToken cancellationToken = default)
    {

        var pca = PublicClientApplicationBuilder
            .CreateWithApplicationOptions(_pcaOptions).Build();

        try
        {
            var result = await pca.AcquireTokenInteractive(_scopes)
                .WithUseEmbeddedWebView(false)
                .ExecuteAsync(cancellationToken);

            return new OAuthToken(result.AccessToken);
        }
        catch (MsalException ex)
        {
            Console.WriteLine($"Error acquiring access token: {ex}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex}");
        }

        return null;
    }

    public void Dispose()
    {

    }
}
```

## **Отправка сохраненных сообщений с диска**

Файлы EML (файлы электронной почты Outlook Express) содержат заголовок, текст сообщения и все вложения. Aspose.Email позволяет разработчикам работать с файлами EML по-разному. В этой статье показано, как загружать файлы EML с диска и отправлять их по электронной почте с помощью SMTP. Вы можете загружать файлы.eml с диска или в потоковом режиме на [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс и отправьте сообщение электронной почты, используя [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс. [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class является основным классом для создания новых сообщений электронной почты, загрузки файлов сообщений электронной почты с диска или потока и сохранения сообщений. В следующем фрагменте кода C# показано, как отправлять сохраненные сообщения с диска.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Load an EML file in MailMessage class
MailMessage message = MailMessage.Load(dataDir + "test.eml");

// Send this message using SmtpClient
SmtpClient client = new SmtpClient("host", "username", "password");
           
try
{
    client.Send(message);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}           
```

## **Отправка электронного письма в виде обычного текста**

В приведенных ниже примерах программирования показано, как отправить текстовое сообщение по электронной почте. [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) имущество, собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, используется для указания текстового содержимого тела сообщения. Чтобы отправить сообщение электронной почты в виде обычного текста, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Укажите адреса электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Укажите [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) содержимое, используемое для текстового сообщения.
- Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс и отправьте электронное письмо.

В следующем фрагменте кода показано, как отправить электронное письмо в виде обычного текста.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
//Создайте экземпляр MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Body = "This is Plain Text Body";

// Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// And Specify your mailing host server, Username, Password and Port
client.Host = "smtp.server.com";
client.Username = "Username";
client.Password = "Password";
client.Port = 25;

try
{
    //Client.Send will send this message
    client.Send(message);
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

## **Отправка электронной почты с текстом HTML**

В приведенных ниже примерах программирования показано, как отправить простое HTML-сообщение по электронной почте. [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, используется для указания HTML-содержимого тела сообщения. Чтобы отправить простое электронное письмо в формате HTML, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Укажите адрес электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Укажите [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) content.
- Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс и отправьте электронное письмо, используя [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

Для целей этой статьи HTML-содержимое электронного письма является элементарным: <html><body>Это тело HTML</body></html> Большинство писем в формате HTML будут более сложными. В следующем фрагменте кода показано, как отправить электронное письмо с текстом HTML.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // Declare msg as MailMessage instance
    MailMessage msg = new MailMessage();

    // Use MailMessage properties like specify sender, recipient, message and HtmlBody
    msg.From = "newcustomeronnet@gmail.com";
    msg.To = "asposetest123@gmail.com";
    msg.Subject = "Test subject";
    msg.HtmlBody = "<html><body>Это тело HTML</body></html>";
    SmtpClient client = GetSmtpClient();
    try
    {
        // Client will send this message
        client.Send(msg);
        Console.WriteLine("Message sent");
    }
    catch (Exception ex)
    {
        Trace.WriteLine(ex.ToString());
    }

    Console.WriteLine(Environment.NewLine + "Email sent with HTML body.");
}

private static SmtpClient GetSmtpClient()
{
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.SecurityOptions = SecurityOptions.Auto;
    return client;
}
```

## **Отправка электронной почты с альтернативным текстом**

В приведенных ниже примерах программирования показано, как отправить простое HTML-сообщение электронной почты с альтернативным содержимым. Используйте [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) класс для указания копий сообщения электронной почты в разных форматах. Например, если вы отправляете сообщение в формате HTML, вы также можете захотеть предоставить текстовую версию для получателей, использующих программы чтения электронной почты, которые не могут отображать содержимое HTML. Или, если вы отправляете информационный бюллетень, вы можете предоставить копию текста в виде обычного текста тем получателям, которые решили получить текстовую версию. Чтобы отправить электронное письмо с альтернативным текстом, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Укажите адреса электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Создайте экземпляр [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class.

Это создает альтернативное представление сообщения электронной почты с использованием содержимого, указанного в строке.

1. Добавьте экземпляр [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) от класса до [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс и отправьте электронное письмо, используя [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

В следующем фрагменте кода показано, как отправить электронное письмо с альтернативным текстом.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");
           
// Adding alternate text
message.AlternateViews.Add(alternate);
```

## **Отправка массовых писем**

Массовая отправка электронных писем означает отправку пакета писем одним сообщением. Мы можем отправить партию электронных писем, используя  [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) перегрузка метода, который принимает [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class.
1. Укажите [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) свойства класса.
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Укажите отправителя, получателя, тему письма и сообщение в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Повторите два вышеуказанных шага еще раз, если вы хотите отправить электронное письмо другому человеку.
1. Создайте экземпляр [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Добавьте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс в объекте [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Теперь отправьте электронное письмо, используя [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) метод путем передачи экземпляра [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) класс в нем.

В следующем фрагменте кода показано, как отправлять массовые электронные письма.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Subject1", "message1, how are you?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Subject2", "message2, how are you?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Subject3", "message3, how are you?");

// Создайте экземпляр MailMessageCollection class
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.Add(message1);
manyMsg.Add(message2);
manyMsg.Add(message3);

// Use client.BulkSend function to complete the bulk send task
try
{
    // Send Message using BulkSend method
    client.Send(manyMsg);               
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### Получение информации об отправленных массовых сообщениях

При массовой отправке сообщений вы можете получить информацию о количестве успешно отправленных сообщений и даже получить список этих сообщений. Новое [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending) событие добавлено в [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) для этого.

Пример кода:
```csharp
using (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto))
{
    int messageCount = 0;

    client.SucceededSending += (sender, eventArgs) =>
    {
        Console.WriteLine("The message '{0}' was successfully sent.", eventArgs.Message.Subject);
        messageCount++;
    };

    client.Send(messages);

    Console.WriteLine("{0} messages were successfully sent.", messageCount);
}
```

## **Отправка электронных писем с помощью мультиподключения**

[SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). Следующий фрагмент кода демонстрирует использование режима нескольких подключений для отправки нескольких сообщений.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
SmtpClient smtpClient = new SmtpClient();
smtpClient.Host = "<HOST>";
smtpClient.Username = "<USERNAME>";
smtpClient.Password = "<PASSWORD>";
smtpClient.Port = 587;
smtpClient.SupportedEncryption = EncryptionProtocols.Tls;
smtpClient.SecurityOptions = SecurityOptions.SSLExplicit;

List<MailMessage> messages = new List<MailMessage>();
for (int i = 0; i < 20; i++)
{
    MailMessage message = new MailMessage(
        "<EMAIL ADDRESS>",
        "<EMAIL ADDRESS>",
        "Test Message - " + Guid.NewGuid().ToString(),
        "SMTP Send Messages with MultiConnection");
    messages.Add(message);
}

smtpClient.ConnectionsQuantity = 5;
smtpClient.UseMultiConnection = MultiConnectionMode.Enable;
smtpClient.Send(messages);
```

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Отправка сообщения как TNEF**

Письма в формате TNEF имеют специальное форматирование, которое может быть потеряно при отправке с использованием стандартного API. Aspose.Email предоставляет возможность отправлять электронные письма в формате TNEF, тем самым сохраняя формат. [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) свойство можно настроить для отправки электронного письма в формате TNEF. В следующем фрагменте кода показано, как отправить сообщение в формате TNEF.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
var emlFileName = RunExamples.GetDataDir_Email() + "Message.eml";     // A TNEF Email

// Load from eml
MailMessage eml1 = MailMessage.Load(emlFileName, new EmlLoadOptions());
eml1.From = "somename@gmail.com";
eml1.To.Clear();
eml1.To.Add(new MailAddress("first.last@test.com"));
eml1.Subject = "With PreserveTnef flag during loading";
eml1.Date = DateTime.Now;
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.SecurityOptions = SecurityOptions.Auto;
client.UseTnef = true;     // Use this flag to send as TNEF
client.Send(eml1);
```

## **Отправка приглашений на собрание**

Microsoft Outlook предлагает функции календаря, а также управление электронной почтой. Когда пользователь открывает электронное письмо с приглашением на мероприятие, Outlook предлагает ему принять или отклонить приглашение. Aspose.Email позволяет разработчикам добавлять функции календаря в ваши электронные письма.

### **Отправка запросов по электронной почте**

Чтобы отправить приглашения на собрание по электронной почте, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Укажите адреса отправителя и получателя, используя экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Инициализируйте экземпляр [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) класс и передайте его значения.
- Укажите краткое описание и описание в поле [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) instance.
- Добавьте [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) к [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр и передайте его [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) instance.

|**Запрос на собрание iCalendar отправлен по электронной почте**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
В следующем фрагменте кода показано, как отправлять запросы по электронной почте.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте экземпляр MailMessage class
MailMessage msg = new MailMessage();

// Set the sender, recipient, who will receive the meeting request. Basically, the recipient is the same as the meeting attendees
msg.From = "newcustomeronnet@gmail.com";
msg.To = "person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com";

// Create Appointment instance
Appointment app = new Appointment("Room 112", new DateTime(2015, 7, 17, 13, 0, 0), new DateTime(2015, 7, 17, 14, 0, 0), msg.From, msg.To);
app.Summary = "Release Meetting";
app.Description = "Discuss for the next release";

// Add appointment к message and Создайте экземпляр SmtpClient class
msg.AddAlternateView(app.RequestApointment());
SmtpClient client = GetSmtpClient();

try
{
    // Client.Send will send this message
    client.Send(msg);
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### **iCalendar поддерживает IBM Lotus Notes**

Функция календаря Aspose.Email основана на стандарте iCalendar, стандарте обмена календарными данными (справочник по синтаксису RFC 2445 или RFC2445). Таким образом, он поддерживает не только Microsoft Outlook, но и IBM Lotus Notes. Чтобы отправить приглашение на собрание в Lotus Notes, выполните те же действия, что и выше.

## **Пересылка электронной почты с помощью SMTP-клиента**

### **Пересылка электронной почты с помощью SMTP-клиента**

Пересылка электронной почты — обычная практика в повседневной цифровой коммуникации. Полученное электронное письмо можно переслать определенным получателям, не передавая его первоначальным отправителям. API Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) предоставляет возможность переслать электронное письмо определенным получателям. Метод «Переслать» можно использовать для пересылки полученного или сохраненного электронного письма нужным получателям, как показано в этой статье. В следующем фрагменте кода показано, как переслать электронное письмо с помощью SMTP-клиента.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path к File directory.
string dataDir = RunExamples.GetDataDir_SMTP();

//Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port and SecurityOptions
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;
MailMessage message = MailMessage.Load(dataDir + "Message.eml");
client.Forward("Recipient1@domain.com", "Recipient2@domain.com", message);
```

### **Пересылка электронной почты без использования MailMessage**

API также поддерживает пересылку сообщений EML без предварительной загрузки в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Это полезно в тех случаях, когда ресурсы системной памяти ограничены.

```csharp

using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Пересылка электронной почты без асинхронного использования MailMessage**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
	using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Выполнение слияния писем**

Объединение писем позволяет создавать и отправлять пакеты похожих сообщений электронной почты. Суть писем одна и та же, но их содержимое можно персонализировать. Как правило, контактные данные получателя (имя, отчество, компания и т. д.) используются для персонализации письма.

|**Иллюстрация того, как работает слияние писем:**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email позволяет разработчикам настраивать слияния писем, включающие данные из различных источников данных.

Чтобы выполнить слияние писем с помощью Aspose.Email, выполните следующие шаги:

1. Создайте функцию с подписью имени
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Укажите отправителя, получателя, тему и текст.
1. Создайте подпись в конце письма.
1. Создайте экземпляр [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) класс и сдайте его [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Сделайте подпись в [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) instance.
1. Создайте экземпляр класса DataTable.
1. Добавьте столбцы **Receipt**, **FirstName** and **LastName** в качестве источников данных в классе DataTable.
1. Создайте экземпляр класса DataRow.
1. Укажите адрес получения, имя и фамилию в объекте DataRow.
1. Создайте экземпляр [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class
1. Укажите [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/)  и экземпляры DataTable в [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) instance.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс и укажите сервер, порт, имя пользователя и пароль.
1. Отправляйте электронные письма с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

В приведенном ниже примере #FirstName # обозначает столбец DataTable, значение которого задается пользователем. В следующем фрагменте кода показано, как выполнить Mail Merge.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // The path к File directory.
    string dataDir = RunExamples.GetDataDir_SMTP();
    string dstEmail = dataDir + "EmbeddedImage.msg";

    // Create a new MailMessage instance
    MailMessage msg = new MailMessage();

    // Add subject and from address
    msg.Subject = "Hello, #FirstName#";
    msg.From = "sender@sender.com";

    // Add email address to send email also Add mesage field to HTML body
    msg.To.Add("your.email@gmail.com");
    msg.HtmlBody = "Your message here";
    msg.HtmlBody += "Thank you for your interest in <STRONG>Aspose.Email</STRONG>.";

    // Use GetSignment as the template routine, which will provide the same signature
    msg.HtmlBody += "<br><br>Have fun with it.<br><br>#GetSignature()#";

    // Create a new TemplateEngine with the MSG message,  Register GetSignature routine. It will be used in MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.RegisterRoutine("GetSignature", GetSignature);

    // Создайте экземпляр DataTable and Fill a DataTable as data source
    DataTable dt = new DataTable();
    dt.Columns.Add("Receipt", typeof(string));
    dt.Columns.Add("FirstName", typeof(string));
    dt.Columns.Add("LastName", typeof(string));

    DataRow dr = dt.NewRow();
    dr["Receipt"] = "abc<asposetest123@gmail.com>";
    dr["FirstName"] = "a";
    dr["LastName"] = "bc";
    dt.Rows.Add(dr);
    dr = dt.NewRow();
    dr["Receipt"] = "John<email.2@gmail.com>";
    dr["FirstName"] = "John";
    dr["LastName"] = "Doe";
    dt.Rows.Add(dr);
    dr = dt.NewRow();
    dr["Receipt"] = "Third Recipient<email.3@gmail.com>";
    dr["FirstName"] = "Third";
    dr["LastName"] = "Recipient";
    dt.Rows.Add(dr);

    MailMessageCollection messages;
    try
    {
        // Create messages from the message and datasource.
        messages = engine.Instantiate(dt);

        // Создайте экземпляр SmtpClient and specify server, port, username and password
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.SecurityOptions = SecurityOptions.Auto;

        // Send messages in bulk
        client.Send(messages);
    }
    catch (MailException ex)
    {
        Debug.WriteLine(ex.ToString());
    }

    catch (SmtpException ex)
    {
        Debug.WriteLine(ex.ToString());
    }

    Console.WriteLine(Environment.NewLine + "Message sent after performing mail merge.");
}

// Template routine to provide signature
static object GetSignature(object[] args)
{
    return "Aspose.Email Team<br>Aspose Ltd.<br>" + DateTime.Now.ToShortDateString();
}
```

## **Выполнение слияния писем по строкам**

Пользователь может объединить отдельные строки данных, а также получить полную и подготовленную [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект. [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) метод можно использовать для объединения писем по строкам.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create message from the data in current row.
message = engine.Merge(currentRow);
```
