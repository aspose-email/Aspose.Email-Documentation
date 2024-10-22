---
title: "Envío y Reenvío de Mensajes - Enviar Correos de Outlook usando C#"
url: /es/net/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Envío y Reenvío de Mensajes"
---

La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite a las aplicaciones enviar correos electrónicos utilizando el Protocolo Simple de Transferencia de Correo (SMTP).

- La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) es la única entrada principal que los desarrolladores utilizan para enviar mensajes de correo.
- La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) también proporciona otros métodos comunes de entrega de correos electrónicos, incluyendo la escritura de mensajes de correo en el sistema de archivos, cola de mensajes, etc.
- La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) admite completamente estos dos modelos de programación:
  - [Sincrónico](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Asincrónico](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) también admite [el envío de mensajes como TNEF](https://docs.aspose.com/email/es/net/sending-and-forwarding-messages/#sending-message-as-tnef)

Para enviar el mensaje de correo y bloquear mientras se espera que el correo se transmita al servidor SMTP, utilice uno de los métodos de envío sincrónicos. Para permitir que el hilo principal de su programa continúe ejecutándose mientras se transmite el correo, utilice el método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/).

## **Envío de Correos Electrónicos Sincrónicamente**

Un mensaje de correo electrónico se puede enviar de forma sincrónica utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). Envía el mensaje de correo especificado a través de un servidor SMTP para su entrega. El remitente del mensaje, los destinatarios, el asunto y el cuerpo del mensaje se especifican mediante objetos String. Para enviar un mensaje de correo electrónico sincrónicamente, siga los pasos a continuación:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y establezca sus propiedades.
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y especifique el Host, el puerto, el nombre de usuario y la contraseña.
1. Envíe el mensaje utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y pase la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

El siguiente fragmento de código en C# muestra cómo enviar correos de Outlook de forma sincrónica.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare msg como instancia de MailMessage
MailMessage msg = new MailMessage();

// Cree una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Especifique su servidor de correo, nombre de usuario, contraseña, número de puerto y opción de seguridad
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;

try
{
    // Client.Send enviará este mensaje
    client.Send(msg);
    Console.WriteLine("Mensaje enviado");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

## **Envío de Correos Electrónicos Asincrónicamente**

A veces, puede desear enviar correos de forma asincrónica para permitir que el programa continúe ejecutando otras operaciones mientras el correo se envía en segundo plano. Especialmente si está enviando muchos correos a través de su aplicación, el enfoque sincrónico puede no funcionar. 
A partir del .NET Framework 4.5, puede utilizar métodos asincrónicos implementados según el modelo [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap). El siguiente fragmento de código en C# muestra cómo enviar mensajes de correo de Outlook utilizando los métodos de patrón asincrónico basado en tareas:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Envía los mensajes especificados.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Permite a las aplicaciones enviar mensajes mediante el Protocolo Simple de Transferencia de Correo (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Crea una nueva instancia de la clase Aspose.Email.Clients.Smtp.SmtpClient

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Parámetro del método Aspose.Email.Clients.Smtp.IAsyncSmtpClient.SendAsync(Aspose.Email.Clients.Smtp.Models.SmtpSend).

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - Los argumentos de Aspose.Email.Clients.Smtp.IAsyncSmtpClient.ForwardAsync(Aspose.Email.Clients.Smtp.Models.SmtpForward).

```csharp
// Autenticar al cliente para obtener los permisos necesarios
static readonly string tenantId = "YOUR_TENANT_ID";
static readonly string clientId = "YOUR_CLIENT_ID";
static readonly string redirectUri = "http://localhost";
static readonly string username = "username";
static readonly string[] scopes = { "https://outlook.office.com/SMTP.Send" };

// Usar el método SmtpAsync para operaciones asincrónicas
static async Task Main(string[] args)
{
    await SmtpAsync();
    Console.ReadLine();
}

static async Task SmtpAsync()
{
    // Crear proveedor de tokens y obtener token de acceso
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = SmtpClient.CreateAsync("outlook.office365.com", username, tokenProvider, 587).GetAwaiter().GetResult();
	
	// Crear un mensaje para enviar
    var eml = new MailMessage("from@domain.com", "to@domain.com", "test subj async", "test body async");
    
    // enviar mensaje
    var sendOptions = SmtpSend.Create();
    sendOptions.AddMessage(eml);
    await client.SendAsync(sendOptions);
    Console.WriteLine("mensaje fue enviado");

    // reenviar mensaje
    var fwdOptions = SmtpForward.Create();
    fwdOptions.SetMessage(eml);
    fwdOptions.AddRecipient("rec@domain.com");
    await client.ForwardAsync(fwdOptions);
    Console.WriteLine("mensaje fue reenviado");
}

// Implementación del proveedor de tokens
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
            Console.WriteLine($"Error al adquirir el token de acceso: {ex}");
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

## **Envío de Mensajes Almacenados desde el Disco**

Los archivos EML (Archivos de Correo Electrónico Electrónico de Outlook Express) contienen el encabezado de un correo electrónico, cuerpo del mensaje y cualquier archivo adjunto. Aspose.Email permite a los desarrolladores trabajar con archivos EML de diferentes maneras. Este artículo muestra cómo cargar archivos EML desde el disco y enviarlos como correos electrónicos con SMTP. Puede cargar archivos .eml desde el disco o un flujo en la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y enviar el mensaje de correo utilizando la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) es la clase principal para crear nuevos mensajes de correo electrónico, cargar archivos de mensajes de correo desde el disco o flujo y guardar los mensajes. El siguiente fragmento de código en C# muestra cómo enviar mensajes almacenados desde el disco.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Cargar un archivo EML en la clase MailMessage
MailMessage message = MailMessage.Load(dataDir + "test.eml");

// Enviar este mensaje usando SmtpClient
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

## **Envío de Correo Electrónico de Texto Plano**

Los ejemplos de programación a continuación muestran cómo enviar un mensaje de correo electrónico de texto plano. La propiedad [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), una propiedad de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), se utiliza para especificar el contenido de texto plano del cuerpo del mensaje. Para enviar un mensaje de correo electrónico de texto plano, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique las direcciones de correo del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique el contenido de [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), usado para el mensaje de texto plano.
- Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y envíe el correo.

El siguiente fragmento de código muestra cómo enviar un correo electrónico de texto plano.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
//Cree una instancia de la clase MailMessage
MailMessage message = new MailMessage();

// Establecer campo De, campo Para y cuerpo de texto plano
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Body = "Este es el cuerpo de texto plano";

// Cree una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Y especifique su servidor de correo, nombre de usuario, contraseña y puerto
client.Host = "smtp.server.com";
client.Username = "Username";
client.Password = "Password";
client.Port = 25;

try
{
    //Client.Send enviará este mensaje
    client.Send(message);
    Console.WriteLine("Mensaje enviado");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

## **Envío de Correo Electrónico con Cuerpo HTML**

Los ejemplos de programación a continuación muestran cómo puede enviar un mensaje de correo electrónico sencillo en HTML. La propiedad [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), una propiedad de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), se utiliza para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico HTML sencillo, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique las direcciones de correo del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique el contenido de [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/).
- Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y envíe el correo utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

Para los propósitos de este artículo, el contenido HTML del correo es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos HTML serán más complejos. El siguiente fragmento de código muestra cómo enviar un correo electrónico con cuerpo HTML.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // Declare msg como instancia de MailMessage
    MailMessage msg = new MailMessage();

    // Use propiedades de MailMessage como especificar remitente, destinatario, mensaje y HtmlBody
    msg.From = "newcustomeronnet@gmail.com";
    msg.To = "asposetest123@gmail.com";
    msg.Subject = "Asunto de prueba";
    msg.HtmlBody = "<html><body>Este es el cuerpo HTML</body></html>";
    SmtpClient client = GetSmtpClient();
    try
    {
        // Client enviará este mensaje
        client.Send(msg);
        Console.WriteLine("Mensaje enviado");
    }
    catch (Exception ex)
    {
        Trace.WriteLine(ex.ToString());
    }

    Console.WriteLine(Environment.NewLine + "Correo enviado con cuerpo HTML.");
}

private static SmtpClient GetSmtpClient()
{
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.SecurityOptions = SecurityOptions.Auto;
    return client;
}
```

## **Envío de Correo Electrónico con Texto Alternativo**

Los ejemplos de programación a continuación muestran cómo enviar un mensaje de correo electrónico sencillo en HTML con contenido alternativo. Use la clase [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) para especificar copias de un mensaje de correo en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, también puede querer proporcionar una versión de texto plano para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O, si está enviando un boletín, puede querer proporcionar una copia de texto plano para aquellos destinatarios que han elegido recibir una versión de texto plano. Para enviar un correo electrónico con texto alternativo, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique las direcciones de correo del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cree una instancia de la clase [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) que cree una vista alternativa a un mensaje de correo electrónico utilizando el contenido especificado en la cadena.

1. Agregue la instancia de la clase [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) al objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y envíe el correo utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

El siguiente fragmento de código muestra cómo enviar un correo electrónico con texto alternativo.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message como instancia de MailMessage
MailMessage message = new MailMessage();

// Crea una AlternateView para visualizar un mensaje de correo electrónico utilizando el contenido especificado en la cadena
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Texto Alternativo");
            
// Agregando texto alternativo
message.AlternateViews.Add(alternate);
```

## **Envío de Correos Electrónicos Masivos**

Enviar correos electrónicos en masa significa enviar un lote de correos electrónicos en un único mensaje. Podemos enviar un lote de correos electrónicos utilizando la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) que acepta una [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Especifique las propiedades de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique el remitente, el receptor, el asunto del correo y el mensaje en la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Repita los dos pasos anteriores si desea enviar correo a una persona diferente.
1. Cree una instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Agregue una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) en el objeto de la clase [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Ahora envíe su correo utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) pasando la instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) en ella.

El siguiente fragmento de código muestra cómo enviar correos electrónicos masivos.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear SmtpClient como cliente y especificar servidor, puerto, nombre de usuario y contraseña
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Crear instancias de la clase MailMessage y especificar Para, De, Asunto y Mensaje
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Asunto1", "mensaje1, ¿cómo estás?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Asunto2", "mensaje2, ¿cómo estás?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Asunto3", "mensaje3, ¿cómo estás?");

// Crear una instancia de la clase MailMessageCollection
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.Add(message1);
manyMsg.Add(message2);
manyMsg.Add(message3);

// Usar la función client.BulkSend para completar la tarea de envío masivo
try
{
    // Enviar Mensaje utilizando el método BulkSend
    client.Send(manyMsg);                
    Console.WriteLine("Mensaje enviado");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### Obtener información sobre mensajes masivos enviados

Cuando envía mensajes en masa, puede obtener información sobre el número de mensajes enviados correctamente e incluso obtener una lista de estos mensajes. Se añadió un nuevo evento [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending) a [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) para este propósito.

Código de ejemplo:
```csharp
using (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto))
{
    int messageCount = 0;

    client.SucceededSending += (sender, eventArgs) =>
    {
        Console.WriteLine("El mensaje '{0}' fue enviado exitosamente.", eventArgs.Message.Subject);
        messageCount++;
    };

    client.Send(messages);

    Console.WriteLine("{0} mensajes fueron enviados exitosamente.", messageCount);
}
```

## **Envío de Correos Electrónicos con MultiConexión**

[SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que se puede utilizar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se utilizarán durante el modo de multi-conexión utilizando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código demuestra el uso del modo de multi-conexión para enviar múltiples mensajes.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
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
        "<DIRECCIÓN DE CORREO>",
        "<DIRECCIÓN DE CORREO>",
        "Mensaje de Prueba - " + Guid.NewGuid().ToString(),
        "Enviar Mensajes SMTP con MultiConexión");
    messages.Add(message);
}

smtpClient.ConnectionsQuantity = 5;
smtpClient.UseMultiConnection = MultiConnectionMode.Enable;
smtpClient.Send(messages);
```

{{% alert color="primary" %}} 

Tenga en cuenta que el uso del modo de multi-conexión no garantiza un aumento de rendimiento.

{{% /alert %}} 

## **Envío de Mensajes como TNEF**

Los correos electrónicos TNEF tienen un formato especial que puede perderse si se envían utilizando la API estándar. Aspose.Email proporciona la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. La propiedad [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede establecer para enviar el correo como TNEF. El siguiente fragmento de código muestra cómo enviar un mensaje como TNEF.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
var emlFileName = RunExamples.GetDataDir_Email() + "Message.eml";     // Un correo TNEF

// Cargar desde eml
MailMessage eml1 = MailMessage.Load(emlFileName, new EmlLoadOptions());
eml1.From = "somename@gmail.com";
eml1.To.Clear();
eml1.To.Add(new MailAddress("first.last@test.com"));
eml1.Subject = "Con la opción PreserveTnef durante la carga";
eml1.Date = DateTime.Now;
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.SecurityOptions = SecurityOptions.Auto;
client.UseTnef = true;     // Use esta opción para enviar como TNEF
client.Send(eml1);
```

## **Envío de Solicitudes de Reunión**

Microsoft Outlook ofrece funciones de calendario así como gestión de correo electrónico. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le pide que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores agregar funciones de calendario a sus correos electrónicos.

### **Envío de Solicitudes por Correo Electrónico**

Para enviar solicitudes de reunión por correo electrónico, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique las direcciones del remitente y del destinatario utilizando una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Inicialice una instancia de la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) y pase sus valores.
- Especifique el resumen y la descripción en la instancia de [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/).
- Agregue [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y pase la instancia de [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/).

|**Solicitud de reunión iCalendar enviada por correo electrónico**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código muestra cómo enviar solicitudes por correo electrónico.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear una instancia de la clase MailMessage
MailMessage msg = new MailMessage();

// Establecer el remitente, el destinatario, quién recibirá la solicitud de reunión. Básicamente, el destinatario es el mismo que los asistentes a la reunión
msg.From = "newcustomeronnet@gmail.com";
msg.To = "person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com";

// Crear instancia de Appointment
Appointment app = new Appointment("Sala 112", new DateTime(2015, 7, 17, 13, 0, 0), new DateTime(2015, 7, 17, 14, 0, 0), msg.From, msg.To);
app.Summary = "Reunión de Lanzamiento";
app.Description = "Discutir sobre la próxima versión";

// Agregar la cita al mensaje y crear una instancia de la clase SmtpClient
msg.AddAlternateView(app.RequestApointment());
SmtpClient client = GetSmtpClient();

try
{
    // Client.Send enviará este mensaje
    client.Send(msg);
    Console.WriteLine("Mensaje enviado");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### **Soporte de iCalendar para IBM Lotus Notes**

La función de calendario de Aspose.Email se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (RFC 2445 o RFC2445 Syntax Reference). Por lo tanto, admite no solo Microsoft Outlook sino también IBM Lotus Notes. Para enviar una solicitud de reunión en Lotus Notes, siga los mismos pasos mencionados anteriormente.

## **Reenviar un Correo Electrónico utilizando el Cliente SMTP**

### **Reenviar Correo Electrónico con el cliente SMTP**

Reenviar un correo electrónico es una práctica común en la comunicación digital diaria. Un correo electrónico recibido puede ser reenviado a destinatarios específicos sin compartirlo con los remitentes originales. La API Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) proporciona la capacidad de reenviar un correo electrónico a destinatarios específicos. Su método Forward puede usarse para reenviar un correo electrónico recibido o guardado a los destinatarios deseados como se muestra en este artículo. El siguiente fragmento de código muestra cómo reenviar un correo electrónico utilizando el cliente SMTP.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
string dataDir = RunExamples.GetDataDir_SMTP();

//Crear una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Especifique su servidor de correo, nombre de usuario, contraseña, puerto y opciones de seguridad
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;
MailMessage message = MailMessage.Load(dataDir + "Message.eml");
client.Forward("Recipient1@domain.com", "Recipient2@domain.com", message);
```

### **Reenviar un Correo Electrónico sin usar MailMessage**

La API también admite reenviar mensajes EML sin primero cargar en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Esto es útil en casos en los que hay recursos limitados en términos de memoria del sistema.

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Reenviar un Correo Electrónico sin usar MailMessage Asincrónicamente**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
	using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Realizando una Combina de Correo**

Las combinaciones de correo lo ayudan a crear y enviar un lote de mensajes de correo electrónico similares. Los mensajes son esencialmente iguales, pero el contenido puede ser personalizado. Normalmente, se utilizan los detalles de contacto de un destinatario (nombre, apellido, empresa, etc.) para personalizar el correo.

|**Ilustración de cómo funciona una combinación de correo:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite a los desarrolladores configurar combinaciones de correo que incluyen datos de una variedad de fuentes de datos.

Para llevar a cabo una combinación de correo con Aspose.Email, siga estos pasos:

1. Cree una función con la firma de nombre.
1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique el remitente, receptor, asunto y cuerpo.
1. Cree una firma para el final del correo.
1. Cree una instancia de la clase [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) y pase la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Tome la firma en la instancia de [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/).
1. Cree una instancia de la clase DataTable.
1. Agregue las columnas **Receipt**, **FirstName** y **LastName** como fuentes de datos en la clase DataTable.
1. Cree una instancia de la clase DataRow.
1. Especifique la dirección de recibo, nombre y apellidos en el objeto DataRow.
1. Cree una instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Especifique las instancias [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) y DataTable en la instancia de [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) y especifique el servidor, puerto, username y password.
1. Envíe correos utilizando el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

En el ejemplo a continuación, #FirstName# indica una columna de DataTable, cuyo valor es establecido por el usuario. El siguiente fragmento de código muestra cómo realizar una combinación de correo.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // La ruta al directorio de archivos.
    string dataDir = RunExamples.GetDataDir_SMTP();
    string dstEmail = dataDir + "EmbeddedImage.msg";

    // Crear una nueva instancia de MailMessage
    MailMessage msg = new MailMessage();

    // Agregar asunto y dirección del remitente
    msg.Subject = "Hola, #FirstName#";
    msg.From = "sender@sender.com";

    // Agregar dirección de correo para enviar el correo también agregar campo de mensaje al cuerpo HTML
    msg.To.Add("your.email@gmail.com");
    msg.HtmlBody = "Su mensaje aquí";
    msg.HtmlBody += "Gracias por su interés en <STRONG>Aspose.Email</STRONG>.";

    // Usar GetSignment como la rutina de plantilla, que proporcionará la misma firma
    msg.HtmlBody += "<br><br>Diviértete con ello.<br><br>#GetSignature()#";

    // Crear una nueva instancia de TemplateEngine con el mensaje MSG, registrar la rutina GetSignature. Se utilizará en MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.RegisterRoutine("GetSignature", GetSignature);

    // Crear una instancia de DataTable y llenar una DataTable como fuente de datos
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
    dr["Receipt"] = "Tercer Destinatario<email.3@gmail.com>";
    dr["FirstName"] = "Tercer";
    dr["LastName"] = "Destinatario";
    dt.Rows.Add(dr);

    MailMessageCollection messages;
    try
    {
        // Crear mensajes de la mensaje y la fuente de datos.
        messages = engine.Instantiate(dt);

        // Crear una instancia de SmtpClient y especificar servidor, puerto, usuario y contraseña
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.SecurityOptions = SecurityOptions.Auto;

        // Enviar mensajes en masa
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

    Console.WriteLine(Environment.NewLine + "Mensaje enviado tras realizar la combinación de correo.");
}

// Rutina de plantilla para proporcionar la firma
static object GetSignature(object[] args)
{
    return "Equipo de Aspose.Email<br>Aspose Ltd.<br>" + DateTime.Now.ToShortDateString();
}
```

## **Realizando Combina de Correo Fila por Fila**

El usuario puede combinar una fila de datos individual, así como obtener un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) completamente preparado. El método [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) se puede utilizar para realizar una combinación de correo fila por fila.

```csharp
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear el mensaje a partir de los datos en la fila actual.
message = engine.Merge(currentRow);
```