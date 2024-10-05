---
title: "Отправка и пересылка сообщений - Отправка email через Outlook с использованием C#"
url: /ru/net/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Отправка и пересылка сообщений"
---

Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) позволяет приложениям отправлять электронные письма с использованием протокола простой почты (SMTP).

- Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) является единственным основным интерфейсом, который разработчики используют для отправки почтовых сообщений.
- Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) также предоставляет другие распространенные методы доставки сообщений, включая запись электронных писем в файловую систему, в очередь сообщений и т. д.
- Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) полностью поддерживает эти две модели программирования:
  - [Синхронная](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Асинхронная](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- Класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) также поддерживает [отправку сообщений в формате TNEF](https://docs.aspose.com/email/ru/net/sending-and-forwarding-messages/#sending-message-as-tnef)

Чтобы отправить электронное сообщение и заблокировать выполнение программы во время ожидания передачи электронной почты на SMTP-сервер, используйте один из синхронных методов Send. Чтобы позволить основному потоку вашей программы продолжать выполнение во время передачи электронной почты, используйте метод [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/).

## **Отправка электронных писем синхронно**

Электронное сообщение можно отправить синхронно с использованием метода [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). Он отправляет указанное электронное сообщение через SMTP-сервер для доставки. Отправитель сообщения, получатели, тема и текст сообщения задаются с помощью объектов String. Чтобы отправить электронное сообщение синхронно, выполните следующие действия:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и задайте его свойства.
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и укажите хост, порт, имя пользователя и пароль.
1. Отправьте сообщение, используя метод [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и передайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Следующий пример кода C# показывает, как отправить электронные письма Outlook синхронно.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Create an instance of SmtpClient class
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

## **Отправка электронных писем асинхронно**

Иногда вам может понадобиться отправить почту асинхронно, чтобы позволить программе продолжить выполнение других операций, пока электронное письмо отправляется в фоновом режиме. Особенно, если вы отправляете много писем через ваше приложение, синхронный подход может не сработать. 
Начиная с .NET Framework 4.5, вы можете использовать асинхронные методы, реализованные в соответствии с моделью [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap). Пример кода C# ниже показывает, как отправить сообщения электронной почты Outlook, используя методы асинхронного паттерна на основе задач:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Отправляет указанные сообщения.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Позволяет приложениям отправлять сообщения с использованием протокола простой почты (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Создает новый экземпляр класса Aspose.Email.Clients.Smtp.SmtpClient.

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Параметры метода Aspose.Email.Clients.Smtp.IAsyncSmtpClient.SendAsync(Aspose.Email.Clients.Smtp.Models.SmtpSend).

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - Аргументы Aspose.Email.Clients.Smtp.IAsyncSmtpClient.ForwardAsync(Aspose.Email.Clients.Smtp.Models.SmtpForward).

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

Файлы EML (файлы электронной почты Outlook Express) содержат заголовок электронной почты, текст сообщения и любые вложения. Aspose.Email позволяет разработчикам работать с файлами EML различными способами. Эта статья показывает, как загрузить файлы EML с диска и отправить их как электронные письма через SMTP. Вы можете загрузить файлы .eml с диска или из потока в класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и отправить сообщение электронной почты с использованием класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) является основным классом для создания новых электронных сообщений, загрузки файлов сообщений электронной почты с диска или потока и сохранения сообщений. Следующий пример кода C# показывает, как отправить сохраненные сообщения с диска.

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

## **Отправка простого текстового сообщения**

Примеры программирования ниже показывают, как отправить простое текстовое сообщение. Свойство [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) используется для указания содержимого простого текстового тела сообщения. Чтобы отправить простое текстовое сообщение, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите содержимое [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), которое используется для простого текстового сообщения.
- Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и отправьте электронную почту.

Следующий фрагмент кода показывает, как отправить простое текстовое сообщение.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
//Create an instance of the MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Body = "This is Plain Text Body";

// Create an instance of the SmtpClient class
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

## **Отправка сообщения с HTML-телом**

Примеры программирования ниже показывают, как отправить простое HTML-сообщение. Свойство [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) используется для указания HTML-содержимого тела сообщения. Чтобы отправить простое HTML-сообщение, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите содержимое [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/).
- Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и отправьте электронное письмо с использованием метода [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

В целях этой статьи HTML-содержимое электронной почты является простым: <html><body>This is the HTML body</body></html> Большинство HTML-писем будет более сложным. Следующий код показывает, как отправить сообщение с HTML-телом.

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
    msg.HtmlBody = "<html><body>This is the HTML body</body></html>";
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

## **Отправка сообщения с альтернативным текстом**

Примеры программирования ниже показывают, как отправить простое HTML-сообщение с альтернативным содержимым. Используйте класс [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) для указания копий электронного сообщения в разных форматах. Например, если вы отправляете сообщение в HTML, вы также хотите предоставить просто текстовую версию для получателей, которые используют почтовые читатели, которые не могут отображать HTML-содержимое. Или, если вы отправляете информационный бюллетень, вы можете захотеть предоставить простую текстовую копию текста для тех получателей, которые выбрали получение простой текстовой версии. Чтобы отправить электронную почту с альтернативным текстом, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Создайте экземпляр класса [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) для создания альтернативного представления электронного сообщения с использованием содержания, указанного в строке.

1. Добавьте экземпляр класса [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) в объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и отправьте электронную почту с использованием метода [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

Следующий фрагмент кода показывает, как отправить электронную почту с альтернативным текстом.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");
            
// Adding alternate text
message.AlternateViews.Add(alternate);
```

## **Отправка массовых электронных писем**

Отправка электронных писем массово означает отправку партии электронных писем в одном сообщении. Мы можем отправить партию электронных писем, используя класс [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) с методом [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) с перегрузкой, которая принимает [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Укажите свойства класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Укажите отправителя, получателя, тему почты и сообщение в экземпляре класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Повторите два вышеуказанных шага, если хотите отправить электронное письмо другому человеку.
1. Создайте экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) .
1. Добавьте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) в объект класса [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Теперь отправьте свое электронное письмо, используя метод [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) передав экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) в него.

Следующий фрагмент кода показывает, как отправить массовые электронные письма.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Subject1", "message1, how are you?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Subject2", "message2, how are you?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Subject3", "message3, how are you?");

// Create an instance of MailMessageCollection class
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

### Получение информации о массовых сообщениях

Когда вы отправляете сообщения массово, вы можете получить информацию о числе успешно отправленных сообщений и даже получить список этих сообщений. Для этой цели в [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) было добавлено новое событие [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending).

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

## **Отправка электронных писем с MultiConnection**

[SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/), которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете установить количество соединений, которые будут использоваться в режиме многосоединений, с помощью [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). Следующий пример кода демонстрирует использование режима многосоединений для отправки нескольких сообщений.

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

Обратите внимание, что использование режима многосоединений не гарантирует повышения производительности.

{{% /alert %}} 

## **Отправка сообщения в формате TNEF**

Электронные письма TNEF имеют специальное форматирование, которое может быть утеряно, если отправить с помощью стандартного API. Aspose.Email предоставляет возможность отправлять электронные письма в формате TNEF, сохраняя тем самым формат. Свойство [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно установить, чтобы отправить электронное письмо в формате TNEF. Следующий код показывает, как отправить сообщение в формате TNEF.

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

## **Отправка приглашений на встречи**

Microsoft Outlook предлагает функции календаря, а также управление электронной почтой. Когда пользователь открывает электронное письмо с приглашением на событие, Outlook предлагает ему принять или отклонить приглашение. Aspose.Email позволяет разработчикам добавлять функции календаря в ваши электронные письма.

### **Отправка запросов по электронной почте**

Чтобы отправить запросы на встречу по электронной почте, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите адреса отправителя и получателя, используя экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Инициализируйте экземпляр класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) и передайте его значения.
- Укажите сводку и описание в экземпляре [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/).
- Добавьте [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и передайте ему экземпляр [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/).

|**Запрос iCalendar, отправленный по электронной почте**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
Следующий пример кода показывает, как отправить запросы по электронной почте.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create an instance of the MailMessage class
MailMessage msg = new MailMessage();

// Set the sender, recipient, who will receive the meeting request. Basically, the recipient is the same as the meeting attendees
msg.From = "newcustomeronnet@gmail.com";
msg.To = "person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com";

// Create Appointment instance
Appointment app = new Appointment("Room 112", new DateTime(2015, 7, 17, 13, 0, 0), new DateTime(2015, 7, 17, 14, 0, 0), msg.From, msg.To);
app.Summary = "Release Meetting";
app.Description = "Discuss for the next release";

// Add appointment to the message and Create an instance of SmtpClient class
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

### **Поддержка iCalendar для IBM Lotus Notes**

Функции календаря Aspose.Email основаны на стандарте iCalendar, стандарт для обмена данными о календаре (RFC 2445 или ссылка на синтаксис RFC2445). Поэтому он поддерживает не только Microsoft Outlook, но и IBM Lotus Notes. Чтобы отправить запрос на встречу в Lotus Notes, выполните те же шаги, что и выше.

## **Пересылка электронного письма с помощью SMTP-клиента**

### **Пересылка электронного письма с помощью SMTP-клиента**

Пересылка электронного письма является обычной практикой в повседневной цифровой коммуникации. Полученное электронное письмо можно переслать определенным получателям, не раскрывая при этом оригинальных отправителей. API Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) предоставляет возможность пересылать электронные письма конкретным получателям. Его метод Forward можно использовать для пересылки полученного или сохраненного электронного письма желаемым получателям, как показано в этой статье. Следующий пример кода показывает, как переслать электронное письмо с помощью SMTP-клиента.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_SMTP();

//Create an instance of SmtpClient class
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

API также поддерживает пересылку сообщений EML без предварительной загрузки в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Это полезно в случаях, когда имеются ограниченные ресурсы в терминах системной памяти.

```csharp

using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Пересылка электронной почты без использования MailMessage асинхронно**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
	using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Выполнение слияния почты**

Слияние почты помогает вам создавать и отправлять партию схожих сообщений электронной почты. Основная часть электронных писем одинакова, но содержимое может быть персонализировано. Обычно данные контакта получателя (имя, фамилия, компания и т. д.) используются для персонализации электронной почты.

|**Иллюстрация того, как работает слияние почты:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email позволяет разработчикам настраивать слияния почты, которые включают данные из различных источников данных.

Чтобы выполнить слияние почты с помощью Aspose.Email, выполните следующие шаги:

1. Создайте функцию с именем подписи.
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Укажите отправителя, получателя, тему и тело.
1. Создайте подпись в конце электронной почты.
1. Создайте экземпляр класса [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) и передайте ему экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Взять подпись в экземпляре [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/).
1. Создайте экземпляр класса DataTable.
1. Добавьте столбцы **Receipt**, **FirstName** и **LastName** в качестве источников данных в класс DataTable.
1. Создайте экземпляр класса DataRow.
1. Укажите адрес получения, имя и фамилию в объекте DataRow.
1. Создайте экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) .
1. Укажите экземпляры [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) и DataTable в экземпляре [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) и укажите сервер, порт, имя пользователя и пароль.
1. Отправьте письма с использованием метода [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

В следующем примере #FirstName# указывает столбец DataTable, значение которого задается пользователем. Следующий код показывает, как выполнить слияние почты.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // The path to the File directory.
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

    // Create an instance of DataTable and Fill a DataTable as data source
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

        // Create an instance of SmtpClient and specify server, port, username and password
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

## **Выполнение слияния по строкам**

Пользователь может объединить отдельную строку данных, а также получить полный и подготовленный объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Метод [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) можно использовать для выполнения слияния по строкам.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create message from the data in current row.
message = engine.Merge(currentRow);
```