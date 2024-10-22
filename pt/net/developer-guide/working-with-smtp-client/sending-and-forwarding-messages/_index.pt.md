---
title: "Enviando e Encaminhando Mensagens - Enviar E-mails do Outlook usando C#"
url: /pt/net/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Enviando e Encaminhando Mensagens"
---

A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite que aplicativos enviem e-mails usando o Protocolo Simples de Transferência de Correio (SMTP).

- A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) é a única entrada principal que os desenvolvedores usam para enviar mensagens de e-mail.
- A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) também fornece outros métodos comuns de entrega de e-mails, incluindo a gravação de mensagens de e-mail no sistema de arquivos, fila de mensagens etc.
- A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) suporta totalmente esses dois modelos de programação:
  - [Síncrono](https://docs.aspose.com/email/pt/net/sending-and-forwarding-messages/#sending-emails-synchronously)
  - [Assíncrono](https://docs.aspose.com/email/pt/net/sending-and-forwarding-messages/#sending-emails-asynchronously)
- A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) também suporta [envio de mensagens como TNEF](https://docs.aspose.com/email/pt/net/sending-and-forwarding-messages/#sending-message-as-tnef)

Para enviar a mensagem de e-mail e bloquear enquanto espera que o e-mail seja transmitido para o servidor SMTP, use um dos métodos de envio síncronos. Para permitir que o thread principal do seu programa continue executando enquanto o e-mail é transmitido, use o método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/sendasync/).

## **Enviando E-mails Síncronamente**

Uma mensagem de e-mail pode ser enviada de forma síncrona usando o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). Ele envia a mensagem de e-mail especificada através de um servidor SMTP para entrega. O remetente da mensagem, os destinatários, o assunto e o corpo da mensagem são especificados usando objetos String. Para enviar uma mensagem de e-mail de forma síncrona, siga os passos abaixo:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e defina suas propriedades.
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e especifique o Host, porta, nome de usuário e Senha.
1. Envie a mensagem usando o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e passe a instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

O seguinte trecho de código C# mostra como enviar e-mails do Outlook de forma síncrona.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare msg como instância de MailMessage
MailMessage msg = new MailMessage();

// Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// Especifique seu servidor de e-mail, Nome de usuário, Senha, Porta e Opção de Segurança
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;

try
{
    // Client.Send enviará esta mensagem
    client.Send(msg);
    Console.WriteLine("Mensagem enviada");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

## **Enviando E-mails Assincronamente**

Às vezes, você pode querer enviar e-mails de forma assíncrona para permitir que o programa continue executando outras operações enquanto o e-mail está sendo enviado em segundo plano. Especialmente se você estiver enviando muitos e-mails através do seu aplicativo, a abordagem síncrona pode não funcionar. 
A partir do .NET Framework 4.5, você pode usar métodos assíncronos implementados de acordo com o modelo [TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap). O código C# abaixo mostra como enviar mensagens de e-mail do Outlook usando os métodos do padrão assíncrono baseado em tarefas:

- [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)
Envia as mensagens especificadas.

- [IAsyncSmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/#iasyncsmtpclient-interface) - Permite que aplicativos enviem mensagens usando o Protocolo Simples de Transferência de Correio (SMTP).

- [SmtpClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/) - Cria uma nova instância da classe Aspose.Email.Clients.Smtp.SmtpClient

- [SmtpSend](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/) - Conjunto de parâmetros do método Aspose.Email.Clients.Smtp.IAsyncSmtpClient.SendAsync(Aspose.Email.Clients.Smtp.Models.SmtpSend).

- [SmtpForward](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/) - Os argumentos do Aspose.Email.Clients.Smtp.IAsyncSmtpClient.ForwardAsync(Aspose.Email.Clients.Smtp.Models.SmtpForward).

```csharp
// Autentique o cliente para obter as permissões necessárias
static readonly string tenantId = "SEU_ID_DE_TENANT";
static readonly string clientId = "SEU_ID_DE_CLIENTE";
static readonly string redirectUri = "http://localhost";
static readonly string username = "username";
static readonly string[] scopes = { "https://outlook.office.com/SMTP.Send" };

// Use o método SmtpAsync para operações assíncronas
static async Task Main(string[] args)
{
    await SmtpAsync();
    Console.ReadLine();
}

static async Task SmtpAsync()
{
    // Crie o provedor de token e obtenha o token de acesso
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = SmtpClient.CreateAsync("outlook.office365.com", username, tokenProvider, 587).GetAwaiter().GetResult();
	
	// Crie uma mensagem para enviar
    var eml = new MailMessage("from@domain.com", "to@domain.com", "assunto teste assíncrono", "corpo teste assíncrono");
    
    // enviar mensagem
    var sendOptions = SmtpSend.Create();
    sendOptions.AddMessage(eml);
    await client.SendAsync(sendOptions);
    Console.WriteLine("mensagem foi enviada");

    // encaminhar mensagem
    var fwdOptions = SmtpForward.Create();
    fwdOptions.SetMessage(eml);
    fwdOptions.AddRecipient("rec@domain.com");
    await client.ForwardAsync(fwdOptions);
    Console.WriteLine("mensagem foi encaminhada");
}

// Implementação do provedor de token
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
            Console.WriteLine($"Erro ao adquirir token de acesso: {ex}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Erro: {ex}");
        }

        return null;
    }

    public void Dispose()
    {

    }
}
```

## **Enviando Mensagens Armazenadas do Disco**

Os arquivos EML (arquivos de E-mail Eletrônico do Outlook Express) contêm o cabeçalho de um e-mail, corpo da mensagem e quaisquer anexos. Aspose.Email permite que desenvolvedores trabalhem com arquivos EML de diferentes maneiras. Este artigo mostra como carregar arquivos EML do disco e enviá-los como e-mails com SMTP. Você pode carregar arquivos .eml do disco ou stream na classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e enviar a mensagem de e-mail usando a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) é a classe principal para criar novas mensagens de e-mail, carregar arquivos de mensagens de e-mail do disco ou stream e salvar as mensagens. O seguinte trecho de código C# mostra como enviar mensagens armazenadas do disco.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Carregue um arquivo EML na classe MailMessage
MailMessage message = MailMessage.Load(dataDir + "teste.eml");

// Envie esta mensagem usando SmtpClient
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

## **Enviando E-mail em Texto Simples**

Os exemplos de programação abaixo mostram como enviar uma mensagem de e-mail em texto simples. A propriedade [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) é usada para especificar o conteúdo em texto simples do corpo da mensagem. Para enviar uma mensagem de e-mail em texto simples, siga estes passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique os endereços de e-mail do remetente e do receptor na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique o conteúdo do [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), usado para a mensagem em texto simples.
- Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e envie o e-mail.

O seguinte trecho de código mostra como enviar um e-mail em texto simples.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
//Crie uma instância da classe MailMessage
MailMessage message = new MailMessage();

// Defina o campo De, campo Para e o corpo em texto simples
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Body = "Este é o corpo em texto simples";

// Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// E especifique seu servidor de e-mail, Nome de usuário, Senha e Porta
client.Host = "smtp.server.com";
client.Username = "Username";
client.Password = "Password";
client.Port = 25;

try
{
    //Client.Send enviará esta mensagem
    client.Send(message);
    Console.WriteLine("Mensagem enviada");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

## **Enviando E-mail com corpo HTML**

Os exemplos de programação abaixo mostram como você pode enviar uma mensagem de e-mail HTML simples. A propriedade [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/), da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) é usada para especificar o conteúdo HTML do corpo da mensagem. Para enviar um e-mail HTML simples, siga esses passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique o endereço de e-mail do remetente e do receptor na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique o conteúdo do [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/).
- Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e envie o e-mail usando o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

Para fins deste artigo, o conteúdo HTML do e-mail é rudimentar: <html><body>Este é o corpo HTML</body></html> A maioria dos e-mails HTML será mais complexa. O seguinte trecho de código mostra como enviar um e-mail com corpo HTML.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // Declare msg como instância de MailMessage
    MailMessage msg = new MailMessage();

    // Use propriedades do MailMessage, como especificar remetente, destinatário, mensagem e HtmlBody
    msg.From = "newcustomeronnet@gmail.com";
    msg.To = "asposetest123@gmail.com";
    msg.Subject = "Assunto de teste";
    msg.HtmlBody = "<html><body>Este é o corpo HTML</body></html>";
    SmtpClient client = GetSmtpClient();
    try
    {
        // Client enviará esta mensagem
        client.Send(msg);
        Console.WriteLine("Mensagem enviada");
    }
    catch (Exception ex)
    {
        Trace.WriteLine(ex.ToString());
    }

    Console.WriteLine(Environment.NewLine + "E-mail enviado com corpo HTML.");
}

private static SmtpClient GetSmtpClient()
{
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.SecurityOptions = SecurityOptions.Auto;
    return client;
}
```

## **Enviando E-mail com Texto Alternativo da Mensagem**

Os exemplos de programação abaixo mostram como enviar uma mensagem de e-mail HTML simples com conteúdo alternativo. Use a classe [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) para especificar cópias de uma mensagem de e-mail em diferentes formatos. Por exemplo, se você enviar uma mensagem em HTML, pode também querer fornecer uma versão em texto simples para os destinatários que usam leitores de e-mail que não conseguem exibir conteúdo HTML. Ou, se você estiver enviando um boletim informativo, pode querer fornecer uma cópia em texto simples do texto para aqueles destinatários que optaram por receber uma versão em texto simples. Para enviar um e-mail com texto alternativo, siga estes passos:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique os endereços de e-mail do remetente e do receptor na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Crie uma instância da classe [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) .

Isso cria uma visualização alternativa para uma mensagem de e-mail usando o conteúdo especificado na string.

1. Adicione a instância da classe [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) ao objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e envie o e-mail usando o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/).

O seguinte trecho de código mostra como enviar um e-mail com texto alternativo.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Declare message como instância de MailMessage
MailMessage message = new MailMessage();

// Cria a AlternateView para visualizar uma mensagem de e-mail usando o conteúdo especificado na string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Texto Alternativo");
            
// Adicionando texto alternativo
message.AlternateViews.Add(alternate);
```

## **Enviando E-mails em Massa**

Enviar e-mails em massa significa enviar um lote de e-mails em uma única mensagem. Podemos enviar um lote de e-mails usando a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) através do método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) que aceita uma [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/):

1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Especifique as propriedades da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique o remetente, o destinatário, o assunto do e-mail e a mensagem na instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Repita as duas etapas acima novamente, se você quiser enviar e-mail para uma pessoa diferente.
1. Crie uma instância da classe [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Adicione uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) ao objeto da classe [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Agora envie seu e-mail usando a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) pelo método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) passando a instância da classe [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) para ela.

O seguinte trecho de código mostra como enviar e-mails em massa.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie SmtpClient como cliente e especifique servidor, porta, nome de usuário e senha
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Crie instâncias da classe MailMessage e especifique Para, De, Assunto e Mensagem
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Assunto1", "mensagem1, como você está?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Assunto2", "mensagem2, como você está?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Assunto3", "mensagem3, como você está?");

// Crie uma instância da classe MailMessageCollection
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.Add(message1);
manyMsg.Add(message2);
manyMsg.Add(message3);

// Use a função client.BulkSend para concluir a tarefa de envio em massa
try
{
    // Envie a mensagem usando o método BulkSend
    client.Send(manyMsg);                
    Console.WriteLine("Mensagem enviada");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### Obtendo informações sobre mensagens em massa enviadas

Quando você envia mensagens em massa, pode ter informações sobre o número de mensagens enviadas com sucesso e até mesmo obter uma lista dessas mensagens. Um novo evento [SucceededSending](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient//events/succeededsending) foi adicionado ao [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) para esse propósito.

Código de exemplo:
```csharp
using (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto))
{
    int messageCount = 0;

    client.SucceededSending += (sender, eventArgs) =>
    {
        Console.WriteLine("A mensagem '{0}' foi enviada com sucesso.", eventArgs.Message.Subject);
        messageCount++;
    };

    client.Send(messages);

    Console.WriteLine("{0} mensagens foram enviadas com sucesso.", messageCount);
}
```

## **Enviando E-mails com MultiConexão**

A classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de múltiplas conexões, usando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). O seguinte trecho de código demonstra o uso do modo de múltiplas conexões para enviar várias mensagens.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
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
        "<ENDEREÇO DE E-MAIL>",
        "<ENDEREÇO DE E-MAIL>",
        "Mensagem de Teste - " + Guid.NewGuid().ToString(),
        "Enviar Mensagens SMTP com MultiConexão");
    messages.Add(message);
}

smtpClient.ConnectionsQuantity = 5;
smtpClient.UseMultiConnection = MultiConnectionMode.Enable;
smtpClient.Send(messages);
```

{{% alert color="primary" %}} 

Por favor, note que o uso do modo de múltiplas conexões não garante aumento de desempenho.

{{% /alert %}} 

## **Enviando Mensagem como TNEF**

E-mails TNEF têm formatação especial que pode ser perdida se enviados usando a API padrão. Aspose.Email fornece a capacidade de enviar e-mails como TNEF, preservando assim a formatação. A propriedade [UseTnef](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/usetnef/) da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) pode ser definida para enviar o e-mail como TNEF. O seguinte trecho de código mostra como enviar uma mensagem como TNEF.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
var emlFileName = RunExamples.GetDataDir_Email() + "Message.eml";     // Um E-mail TNEF

// Carregue a partir de eml
MailMessage eml1 = MailMessage.Load(emlFileName, new EmlLoadOptions());
eml1.From = "somename@gmail.com";
eml1.To.Clear();
eml1.To.Add(new MailAddress("first.last@test.com"));
eml1.Subject = "Com a flag PreserveTnef durante o carregamento";
eml1.Date = DateTime.Now;
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.SecurityOptions = SecurityOptions.Auto;
client.UseTnef = true;     // Use essa flag para enviar como TNEF
client.Send(eml1);
```

## **Enviando Convites**

O Microsoft Outlook oferece funções de calendário, bem como gerenciamento de e-mails. Quando um usuário abre um e-mail com um convite para um evento, o Outlook o solicita para aceitar ou rejeitar o convite. Aspose.Email permite que desenvolvedores adicionem funções de calendário aos seus e-mails.

### **Enviando Convites via E-mail**

Para enviar convites de reunião via e-mail, siga estes passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique endereços do remetente e do destinatário usando uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Inicialize uma instância da classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) e passe seus valores.
- Especifique resumo e descrição na instância [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/).
- Adicione o [Calendar](https://reference.aspose.com/tasks/net/aspose.tasks/calendar/) à instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e passe a instância [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/).

|**Pedido de reunião iCalendar enviado por e-mail**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
O seguinte trecho de código mostra como enviar convites via e-mail.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie uma instância da classe MailMessage
MailMessage msg = new MailMessage();

// Defina o remetente, o destinatário, que receberá o convite para a reunião. Basicamente, o destinatário é o mesmo que os participantes da reunião
msg.From = "newcustomeronnet@gmail.com";
msg.To = "person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com";

// Crie uma instância de Appointment
Appointment app = new Appointment("Sala 112", new DateTime(2015, 7, 17, 13, 0, 0), new DateTime(2015, 7, 17, 14, 0, 0), msg.From, msg.To);
app.Summary = "Reunião de Lançamento";
app.Description = "Discutir sobre o próximo lançamento";

// Adicione o compromisso à mensagem e crie uma instância da classe SmtpClient
msg.AddAlternateView(app.RequestApointment());
SmtpClient client = GetSmtpClient();

try
{
    // Client.Send enviará esta mensagem
    client.Send(msg);
    Console.WriteLine("Mensagem enviada");
}
catch (Exception ex)
{
    Trace.WriteLine(ex.ToString());
}
```

### **Suporte a iCalendar para IBM Lotus Notes**

A função de calendário Aspose.Email é baseada no padrão iCalendar, um padrão para intercâmbio de dados de calendário (RFC 2445 ou Referência de Sintaxe RFC2445). Portanto, suporta não apenas o Microsoft Outlook, mas também o IBM Lotus Notes. Para enviar um convite de reunião no Lotus Notes, siga os mesmos passos mencionados acima.

## **Encaminhando um E-mail usando o Cliente SMTP**

### **Encaminhando E-mail com cliente SMTP**

Encaminhar um e-mail é uma prática comum na comunicação digital do dia a dia. Um e-mail recebido pode ser encaminhado para destinatários específicos sem compartilhar com os remetentes originais. A API Aspose.Email do [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) fornece a capacidade de encaminhar um e-mail para destinatários específicos. Seu método Forward pode ser usado para encaminhar um e-mail recebido ou salvo para os destinatários desejados, como mostrado neste artigo. O seguinte trecho de código mostra como encaminhar um e-mail usando o cliente SMTP.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_SMTP();

//Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// Especifique seu servidor de e-mail, Nome de usuário, Senha, Porta e SecurityOptions
client.Host = "mail.server.com";
client.Username = "username";
client.Password = "password";
client.Port = 587;
client.SecurityOptions = SecurityOptions.SSLExplicit;
MailMessage message = MailMessage.Load(dataDir + "Message.eml");
client.Forward("Recipient1@domain.com", "Recipient2@domain.com", message);
```

### **Encaminhando E-mail sem usar MailMessage**

A API também suporta o encaminhamento de mensagens EML sem primeiro carregá-las na [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Isso é útil em casos onde há recursos limitados em termos de memória do sistema.

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        client.Forward(sender, recipients, fs);
    }
}
```

### **Encaminhando E-mail sem usar MailMessage Assincronamente**

```csharp
using (var client = new SmtpClient(host, smtpPort, username, password))
{
    using (var fs = File.OpenRead(@"test.eml"))
    {
        await client.ForwardAsync(sender, recipients, fs);
    }
}
```

## **Realizando Mail Merge**

Mail merge ajuda a criar e enviar um lote de mensagens de e-mail semelhantes. O núcleo dos e-mails é o mesmo, mas o conteúdo pode ser personalizado. Normalmente, os detalhes de contato de um destinatário (primeiro nome, sobrenome, empresa e assim por diante) são usados para personalizar o e-mail.

|**Ilustração de como um mail merge funciona:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite que desenvolvedores configurem merges que incluem dados de uma variedade de fontes de dados.

Para realizar um mail merge com Aspose.Email, siga os seguintes passos:

1. Crie uma função com a assinatura do nome
1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique o remetente, receptor, assunto e corpo.
1. Crie uma assinatura para o final do e-mail.
1. Crie uma instância da classe [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) e passe a instância da [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Obtenha a assinatura na instância da [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/).
1. Crie uma instância da classe DataTable.
1. Adicione as colunas **Receipt**, **FirstName** e **LastName** como fontes de dados na classe DataTable.
1. Crie uma instância da classe DataRow.
1. Especifique o endereço de recebimento, primeiro e último nomes no objeto DataRow.
1. Crie uma instância da classe [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/) 
1. Especifique as instâncias de [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/)  e DataTable na instância de [MailMessageCollection](https://reference.aspose.com/email/net/aspose.email/mailmessagecollection/).
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) e especifique o servidor, porta, nome de usuário e senha.
1. Envie os e-mails usando o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send/) da classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

No exemplo abaixo, #FirstName# indica uma coluna DataTable, cujo valor é definido pelo usuário. O seguinte trecho de código mostra como realizar Mail Merge.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{
    // O caminho para o diretório de arquivos.
    string dataDir = RunExamples.GetDataDir_SMTP();
    string dstEmail = dataDir + "EmbeddedImage.msg";

    // Crie uma nova instância de MailMessage
    MailMessage msg = new MailMessage();

    // Adicione assunto e endereço de envio
    msg.Subject = "Olá, #FirstName#";
    msg.From = "sender@sender.com";

    // Adicione endereço de e-mail para enviar e também adicione campo de mensagem ao corpo HTML
    msg.To.Add("your.email@gmail.com");
    msg.HtmlBody = "Sua mensagem aqui";
    msg.HtmlBody += "Obrigado pelo seu interesse no <STRONG>Aspose.Email</STRONG>.";

    // Use GetSignment como a rotina do template, que fornecerá a mesma assinatura
    msg.HtmlBody += "<br><br>Divirta-se com isso.<br><br>#GetSignature()#";

    // Crie um novo TemplateEngine com a mensagem MSG, registre a rotina GetSignature. Ela será usada no MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.RegisterRoutine("GetSignature", GetSignature);

    // Crie uma instância de DataTable e preencha-a como fonte de dados
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
        // Crie mensagens a partir da mensagem e fonte de dados.
        messages = engine.Instantiate(dt);

        // Crie uma instância do SmtpClient e especifique servidor, porta, nome de usuário e senha
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.SecurityOptions = SecurityOptions.Auto;

        // Envie mensagens em massa
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

    Console.WriteLine(Environment.NewLine + "Mensagem enviada após realizar o mail merge.");
}

// Rotina do template para fornecer a assinatura
static object GetSignature(object[] args)
{
    return "Equipe Aspose.Email<br>Aspose Ltd.<br>" + DateTime.Now.ToShortDateString();
}
```

## **Realizando Mail Merge Linha a Linha**

O usuário pode mesclar linhas de dados individuais, bem como obter um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) completa e preparada. O método [TemplateEngine.Merge](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/merge/#merge/) pode ser usado para realizar um mail merge linha a linha.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET
// Crie mensagem a partir dos dados na linha atual.
message = engine.Merge(currentRow);
```