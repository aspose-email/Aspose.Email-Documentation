---
title: Sending and Forwarding Messages - Send Outlook Emails using C#
linktitle: Sending and Forwarding Messages
type: docs
weight: 20
url: /net/sending-and-forwarding-messages/
---


The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class allows applications to send email using the Simple Mail Transfer Protocol (SMTP).

- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class is the only major entry developers use to send mail messages.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class also provides other common email delivery methods, including writing email messages to the file system, message queue etc.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class fully supports these two programming models:
  - [Synchronous](https://docs.aspose.com/email/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Asynchronous](https://docs.aspose.com/email/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class also supports [sending messages as TNEF](https://docs.aspose.com/email/net/sending-and-forwarding-messages/#sending-message-as-tnef)

To send the email message and block while waiting for the email to be transmitted to the SMTP server, use one of the synchronous Send methods. To allow your program's main thread to continue executing while the email is transmitted, use the [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/) method.

## **Sending Emails Synchronously**

An email message can be sent synchronously using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method. It sends the specified email message through an SMTP server for delivery. The message sender, recipients, subject, and message body are specified using String objects. To send an email message synchronously, follow the steps given below:

1. Create an instance of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class and set its properties.
1. Create an instance of [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and specify the Host, port, username & Password.
1. Send the Message using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method and pass the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

The following C# code snippet shows you how to send outlook emails synchronously.

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

## **Sending Emails Asynchronously**

Sometimes, you may want to send mail asynchronously to let program continue executing other operations while the email is being sent in the background. Especially, if you are sending a lot of mail through your application, the synchronous approach might not work. 
Starting with .NET Framework 4.5, you can use asynchronous methods implemented according to [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) model. The C# code snippet below shows how to send outlook email messages using the task-based asynchronous pattern methods:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Sends the specified messages.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Allows applications to send messages by using the Simple Mail Transfer Protocol (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Creates a new instance of the Aspose.Email.Clients.Smtp.SmtpClient class

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Aspose.Email.Clients.Smtp.IAsyncSmtpClient.SendAsync(Aspose.Email.Clients.Smtp.Models.SmtpSend) method parameter set.

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - The Aspose.Email.Clients.Smtp.IAsyncSmtpClient.ForwardAsync(Aspose.Email.Clients.Smtp.Models.SmtpForward) arguments.

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

## **Sending Stored Messages from Disc**

EML files, (Outlook Express Electronic Mail files) contains an email's header, message body, and any attachments. Aspose.Email lets developers work with EML files in different ways. This article shows how to load EML files from disk and send them as emails with SMTP. You can load .eml files from disk or stream into the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class and send the email message using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class. The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class is the main class for creating new email messages, loading email message files from disk or stream and saving the messages. The following C# code snippet shows how to send stored messages from the disc.

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

## **Sending Plain Text Email**

The programming samples below show how to send a plain text email message. The [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) property, a property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, is used to specify the plain text content of the message body. To send a plain text email message, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Specify the sender and receiver email addresses in the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Specify the [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) content, used for the plain text message.
- Create an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and send the email.

The following code snippet shows you how to send a plain text email.

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

## **Sending Email with HTML body**

The programming samples below show how you can send a simple HTML email message. The [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), a property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, is used to specify the HTML content of the message body. To send a simple HTML email, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Specify sender and receiver email address in the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Specify the [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) content.
- Create an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and send the email using the [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

For the purposes of this article, the HTML content of the email is rudimentary: <html><body>This is the HTML body</body></html> Most HTML emails will be more complex. The following code snippet shows you how to send an email with HTML body.

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

## **Sending Email with Alternate Message Text**

The programming samples below show how to send a simple HTML email message with alternative content. Use the [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class to specify copies of an email message in different formats. For example, if you send a message in HTML, you might also want to provide a plain text version for recipients who use email readers that cannot display HTML content. Or, if you are sending a newsletter, you might want to provide a plain text copy of the text for those recipients who have chosen to receive a plain text version. To send an email with alternate text, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Specify sender and receiver email addresses in the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Create an instance of the [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class.

This creates an alternate view to an email message using the content specified in the string.

1. Add the instance of the [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object.
1. Create an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and send the email using the [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

The following code snippet shows you how to send an email with alternate text.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");
            
// Adding alternate text
message.AlternateViews.Add(alternate);
```

## **Sending Bulk Emails**

Sending emails in bulk means sending a batch of emails in one message. We can send a batch of emails using the  [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class of the [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method overload that accepts a [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Create an instance of [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class.
1. Specify the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class properties.
1. Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Specify sender, receiver, mail subject and message in the instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Repeat the above two steps again, if you want to send email to a different person.
1. Create an instance of [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Add an instance of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class in the object of the [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Now send your email using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method by passing the instance of [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class in it.

The following code snippet shows you how to send bulk emails.

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

### Getting information about bulk messages sent

When you send messages in bulk, you can get an information about the number of successfully sent messages and even get a list of these messages. A new [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending) event was added to [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) for this purpose.

Code sample:
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

## **Sending Emails with MultiConnection**

[SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) provides a [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). The following code snippet demonstrates the use of the multiconnection mode for sending multiple messages.

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

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 

## **Sending Message as TNEF**

TNEF emails have special formatting which may be lost if sent using the standard API. Aspose.Email provides the capability to send emails as TNEF, thus preserving the format. The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) property can be set to send the email as TNEF. The following code snippet shows you how to send a message as TNEF.

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

## **Sending Meeting Requests**

Microsoft Outlook offers calendar functions as well as email management. When a user opens an email with an invitation to an event, Outlook prompts them to accept or reject the invitation. Aspose.Email lets developers add calendar functions to your emails.

### **Sending Requests via Email**

To send meeting requests via email, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Specify sender and recipient addresses using an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Initialize an instance of the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) class and pass its values.
- Specify summary and description in the [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) instance.
- Add the [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance and pass it the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) instance.

|**iCalendar meeting request sent by email**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
The following code snippet shows you how to send requests via Email.

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

### **iCalendar supports for IBM Lotus Notes**

Aspose.Email calendar feature is based on the iCalendar standard, a standard for calendar data exchange (RFC 2445 or RFC2445 Syntax Reference). Therefore, it supports not only Microsoft Outlook but also IBM Lotus Notes. To send a meeting request in Lotus Notes, follow the same steps as mentioned above.

## **Forward an Email using SMTP Client**

### **Forwarding Email with SMTP client**

Forwarding an email is common practice in daily life digital communication. An email received can be forwarded to specific recipients without sharing with the original senders. Aspose.Email API's [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) provides the capability to forward an email to specific recipients. Its Forward method can be used to forward a received or saved email to desired recipients as shown in this article. The following code snippet shows you how to Forward an Email using SMTP Client.

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

### **Forwarding Email without using MailMessage**

The API also supports forwarding EML messages without first loading into [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). This is useful in cases where there are limited resources in terms of system memory.

```csharp

using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Forwarding Email without using MailMessage Asynchronously**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
	using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Performing Mail Merge**

Mail merges help you create and send a batch of similar email messages. The core of the emails are the same, but the content can be personalized. Typically, a recipient's contact details (first name, second name, company and so on) are used to personalize the email.

|**Illustration of how a mail merge works:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email lets developers set up mail merges that include data from a variety of data sources.

To perform a mail merge with Aspose.Email, take the following steps:

1. Create a function with the name signature
1. Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Specify the sender, receiver, subject, and body.
1. Create a signature for the end of the email.
1. Create an instance of the [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) class and pass it the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Take signature in the [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) instance.
1. Create an instance of the DataTable class.
1. Add the columns **Receipt**, **FirstName** and **LastName** as data sources in the DataTable class.
1. Create an instance of the DataRow class.
1. Specify the receipt address, first and last names in the DataRow object.
1. Create an instance of the [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class
1. Specify the [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/)  and DataTable instances in the [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) instance.
1. Create an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and specify the server, port, username, and password.
1. Send emails using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

In the sample below, #FirstName# indicates a DataTable column, whose value is set by the user. The following code snippet shows you how to perform Mail Merge.

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

## **Performing Row-Wise Mail Merge**

User can merge individual data row as well as to get a complete and prepared [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object. The [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) method can be used to perform a row-wise mail merge.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create message from the data in current row.
message = engine.Merge(currentRow);
```
