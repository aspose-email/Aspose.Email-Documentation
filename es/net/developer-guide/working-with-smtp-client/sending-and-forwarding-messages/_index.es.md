---
title: "Envío y reenvío de mensajes: envíe correos electrónicos de Outlook con C#"
url: /es/net/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Envío y reenvío de mensajes"
---


The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) La clase permite a las aplicaciones enviar correos electrónicos mediante el Protocolo simple de transferencia de correo (SMTP).

- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class es la única entrada importante que utilizan los desarrolladores para enviar mensajes de correo.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) La clase también proporciona otros métodos comunes de entrega de correo electrónico, incluida la escritura de mensajes de correo electrónico en el sistema de archivos, la cola de mensajes, etc.
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class es totalmente compatible con estos dos modelos de programación:
  - [Synchronous](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Asynchronous](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) la clase también admite [enviar mensajes como TNEF](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-message-as-tnef)

Para enviar el mensaje de correo electrónico y bloquearlo mientras espera a que el correo electrónico se transmita al servidor SMTP, utilice uno de los métodos de envío sincrónico. Para permitir que el subproceso principal del programa continúe ejecutándose mientras se transmite el correo electrónico, utilice el [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/) method.

## **Envío sincrónico de correos electrónicos**

Se puede enviar un mensaje de correo electrónico de forma sincrónica mediante el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) método. Envía el mensaje de correo electrónico especificado a través de un servidor SMTP para su entrega. El remitente, los destinatarios, el asunto y el cuerpo del mensaje se especifican mediante objetos String. Para enviar un mensaje de correo electrónico de forma sincrónica, siga los pasos que se indican a continuación:

1. Crea una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase y establece sus propiedades.
1. Crea una instancia de [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase y especifique el host, el puerto, el nombre de usuario y la contraseña.
1. Envía el mensaje usando el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) método y pase el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

El siguiente fragmento de código de C# muestra cómo enviar correos electrónicos de Outlook de forma sincrónica.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Crea una instancia de SmtpClient class
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

## **Envío de correos electrónicos de forma asincrónica**

A veces, es posible que desee enviar correo de forma asincrónica para permitir que el programa continúe ejecutando otras operaciones mientras el correo electrónico se envía en segundo plano. Especialmente, si envías mucho correo a través de tu aplicación, es posible que el enfoque sincrónico no funcione.
A partir de .NET Framework 4.5, puede usar métodos asincrónicos implementados de acuerdo con [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) modelo. El siguiente fragmento de código de C# muestra cómo enviar mensajes de correo electrónico de Outlook mediante los métodos de patrón asincrónico basados en tareas:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Envía los mensajes especificados.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Permite que las aplicaciones envíen mensajes mediante el Protocolo simple de transferencia de correo (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Crea una nueva instancia de la clase Aspose.Email.Clients.Smtp.SmtpClient

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Conjunto de parámetros del método Aspose.Email.Clients.SMTP.IAsyncSMTPClient.SendAsync (Aspose.Email.Clients.Smtp.Models.SmtpSend).

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - Los argumentos aspose.email.clients.smtp.IAsyncSMTPClient.forwardAsync (aspose.email.clients.smtp.models.smtpForward).

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

## **Envío de mensajes almacenados desde un disco**

Los archivos EML (archivos de correo electrónico de Outlook Express) contienen el encabezado, el cuerpo del mensaje y los archivos adjuntos de un correo electrónico. Aspose.Email permite a los desarrolladores trabajar con los archivos EML de diferentes maneras. Este artículo muestra cómo cargar archivos EML desde el disco y enviarlos como correos electrónicos con SMTP. Puede cargar archivos.eml desde el disco o transmitirlos al [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase y enviar el mensaje de correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase. El [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class es la clase principal para crear nuevos mensajes de correo electrónico, cargar archivos de mensajes de correo electrónico desde un disco o transmisión y guardar los mensajes. El siguiente fragmento de código de C# muestra cómo enviar los mensajes almacenados desde el disco.

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

## **Envío de correo electrónico de texto sin formato**

Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico de texto sin formato. El [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) propiedad, una propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, se usa para especificar el contenido de texto sin formato del cuerpo del mensaje. Para enviar un mensaje de correo electrónico de texto sin formato, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Especifique las direcciones de correo electrónico del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Especifique el [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) contenido, usado para el mensaje de texto sin formato.
- Crea una instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase y envía el correo electrónico.

El siguiente fragmento de código muestra cómo enviar un correo electrónico de texto sin formato.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
//Crea una instancia del MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Body = "This is Plain Text Body";

// Crea una instancia del SmtpClient class
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

## **Envío de correo electrónico con cuerpo HTML**

Los ejemplos de programación que aparecen a continuación muestran cómo puede enviar un mensaje de correo electrónico HTML sencillo. El [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, se usa para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico HTML sencillo, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Especifique la dirección de correo electrónico del remitente y del destinatario en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Especifique el [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) content.
- Crea una instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase y envía el correo electrónico usando el [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

Para los fines de este artículo, el contenido HTML del correo electrónico es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos HTML serán más complejos. El siguiente fragmento de código muestra cómo enviar un correo electrónico con un cuerpo HTML.

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
    msg.HtmlBody = "<html><body>Este es el cuerpo HTML</body></html>";
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

## **Envío de correo electrónico con texto de mensaje alternativo**

Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico HTML sencillo con contenido alternativo. Utilice el [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) clase para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O bien, si va a enviar un boletín, puede que desee proporcionar una copia del texto sin formato para los destinatarios que hayan elegido recibir una versión en texto sin formato. Para enviar un correo electrónico con texto alternativo, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Especifique las direcciones de correo electrónico del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Crea una instancia del [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class.

Esto crea una vista alternativa a un mensaje de correo electrónico con el contenido especificado en la cadena.

1. Agregue la instancia del [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) clase a la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object.
1. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase y envía el correo electrónico usando el [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

El siguiente fragmento de código muestra cómo enviar un correo electrónico con texto alternativo.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");
           
// Adding alternate text
message.AlternateViews.Add(alternate);
```

## **Envío masivo de correos electrónicos**

Enviar correos electrónicos de forma masiva significa enviar un lote de correos electrónicos en un solo mensaje. Podemos enviar un lote de correos electrónicos mediante el  [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase del [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) sobrecarga de métodos que acepta un [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Crea una instancia de [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class.
1. Especifique el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) propiedades de clase.
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Especifique el remitente, el destinatario, el asunto del correo y el mensaje en la instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Repite los dos pasos anteriores de nuevo si quieres enviar un correo electrónico a otra persona.
1. Crea una instancia de [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Añadir una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase en el objeto del [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class.
1. Ahora envía tu correo electrónico usando el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) método pasando la instancia de [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) clase en él.

El siguiente fragmento de código muestra cómo enviar correos electrónicos masivos.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Subject1", "message1, how are you?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Subject2", "message2, how are you?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Subject3", "message3, how are you?");

// Crea una instancia de MailMessageCollection class
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

### Obtener información sobre los mensajes masivos enviados

Cuando envías mensajes de forma masiva, puedes obtener información sobre la cantidad de mensajes enviados correctamente e incluso obtener una lista de estos mensajes. Un nuevo [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending) el evento se agregó a [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) para este propósito.

Ejemplo de código:
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

## **Envío de correos electrónicos con MultiConnection**

[SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código muestra el uso del modo multiconexión para enviar varios mensajes.

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

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Enviar mensaje como TNEF**

Los correos electrónicos de TNEF tienen un formato especial que puede perderse si se envían mediante la API estándar. Aspose.Email ofrece la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. El [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) la propiedad se puede configurar para enviar el correo electrónico como TNEF. El siguiente fragmento de código muestra cómo enviar un mensaje como TNEF.

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

## **Envío de convocatorias de reunión**

Microsoft Outlook ofrece funciones de calendario y administración de correo electrónico. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le pide que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores añadir funciones de calendario a sus correos electrónicos.

### **Envío de solicitudes por correo electrónico**

Para enviar convocatorias de reunión por correo electrónico, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Especifique las direcciones del remitente y del destinatario mediante una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Inicialice una instancia del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) clasifique y apruebe sus valores.
- Especifique el resumen y la descripción en el [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) instance.
- Añada el [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) a la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia y pásala al [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) instance.

|**Solicitud de reunión de iCalendar enviada por correo electrónico**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código muestra cómo enviar solicitudes por correo electrónico.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Crea una instancia del MailMessage class
MailMessage msg = new MailMessage();

// Set the sender, recipient, who will receive the meeting request. Basically, the recipient is the same as the meeting attendees
msg.From = "newcustomeronnet@gmail.com";
msg.To = "person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com";

// Create Appointment instance
Appointment app = new Appointment("Room 112", new DateTime(2015, 7, 17, 13, 0, 0), new DateTime(2015, 7, 17, 14, 0, 0), msg.From, msg.To);
app.Summary = "Release Meetting";
app.Description = "Discuss for the next release";

// Add appointment a la message and Crea una instancia de SmtpClient class
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

### **iCalendar es compatible con IBM Lotus Notes**

La función de calendario Aspose.Email se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (referencia de sintaxis RFC 2445 o RFC2445). Por lo tanto, no solo es compatible con Microsoft Outlook, sino también con IBM Lotus Notes. Para enviar una convocatoria de reunión en Lotus Notes, siga los mismos pasos que se han mencionado anteriormente.

## **Reenviar un correo electrónico mediante un cliente SMTP**

### **Reenvío de correo electrónico con un cliente SMTP**

Reenviar un correo electrónico es una práctica común en la comunicación digital de la vida diaria. Un correo electrónico recibido se puede reenviar a destinatarios específicos sin compartirlo con los remitentes originales. API de Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) proporciona la capacidad de reenviar un correo electrónico a destinatarios específicos. Su método de reenvío se puede utilizar para reenviar un correo electrónico recibido o guardado a los destinatarios deseados, como se muestra en este artículo. El siguiente fragmento de código muestra cómo reenviar un correo electrónico mediante un cliente SMTP.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path a la File directory.
string dataDir = RunExamples.GetDataDir_SMTP();

//Crea una instancia de SmtpClient class
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

### **Reenviar correo electrónico sin usar MailMessage**

La API también admite el reenvío de mensajes EML sin cargarlos primero en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Esto es útil en los casos en que hay recursos limitados en términos de memoria del sistema.

```csharp

using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Reenviar correo electrónico sin usar MailMessage de forma asincrónica**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
	using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Realizar una combinación de correspondencia**

Las combinaciones de correspondencia le ayudan a crear y enviar un lote de mensajes de correo electrónico similares. El núcleo de los correos electrónicos es el mismo, pero el contenido se puede personalizar. Por lo general, los datos de contacto del destinatario (nombre, segundo nombre, empresa, etc.) se utilizan para personalizar el correo electrónico.

|**Ilustración de cómo funciona una combinación de correspondencia:**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite a los desarrolladores configurar combinaciones de correspondencia que incluyen datos de una variedad de fuentes de datos.

Para realizar una combinación de correspondencia con Aspose.Email, siga estos pasos:

1. Crea una función con la firma del nombre
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Especifique el remitente, el destinatario, el asunto y el cuerpo.
1. Crea una firma para el final del correo electrónico.
1. Crea una instancia del [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) clase y apruebalo el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Firme en el [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) instance.
1. Crea una instancia de la clase DataTable.
1. Agregue las columnas **Receipt**, **FirstName** and **LastName** como fuentes de datos en la clase DataTable.
1. Crea una instancia de la clase DataRow.
1. Especifique la dirección de recepción, el nombre y los apellidos en el objeto DataRow.
1. Crea una instancia del [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) class
1. Especifique el [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/)  e instancias de DataTable en [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) instance.
1. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase y especifique el servidor, el puerto, el nombre de usuario y la contraseña.
1. Envía correos electrónicos mediante el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) method.

En el ejemplo siguiente, #FirstName # indica una columna DataTable, cuyo valor lo establece el usuario. En el siguiente fragmento de código se muestra cómo combinar correspondencia.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // The path a la File directory.
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

    // Crea una instancia de DataTable and Fill a DataTable as data source
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

        // Crea una instancia de SmtpClient and specify server, port, username and password
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

## **Realización de una combinación de correspondencia por filas**

El usuario puede combinar una fila de datos individual, así como obtener una completa y preparada [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeto. El [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) este método se puede utilizar para realizar una combinación de correspondencia por filas.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create message from the data in current row.
message = engine.Merge(currentRow);
```
