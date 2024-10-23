---
title: "Enviando e Encaminhando Mensagens - Enviar Mensagens de Email do Outlook usando Programa Java"
url: /pt/java/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Enviando e Encaminhando Mensagens"
---


A classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) permite que aplicações enviem emails usando o Protocolo Simples de Transferência de Email (SMTP).

- A classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) é a única entrada principal que os desenvolvedores usam para enviar mensagens de email.
- A classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) também fornece outros métodos comuns de entrega de email, incluindo escrever mensagens de email no sistema de arquivos, fila de mensagens, etc.
- A classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) suporta totalmente esses dois modelos de programação:
  - [Síncrono](#sending-emails-synchronously)
  - [Assíncrono](#sending-emails-asynchronously)
- A classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) também suporta [enviar mensagens como TNEF](#sending-message-as-tnef)

Para enviar a mensagem de email e bloquear enquanto aguarda a transmissão do email para o servidor SMTP, use um dos métodos Send síncronos. Para permitir que o thread principal do seu programa continue executando enquanto o email é transmitido, utilize o método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-).

## **Enviando Emails Síncronamente**

Uma mensagem de email pode ser enviada de forma síncrona usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Ele envia a mensagem de email especificada por meio de um servidor SMTP para entrega. O remetente da mensagem, os destinatários, o assunto e o corpo da mensagem são especificados usando objetos String. Para enviar uma mensagem de email de forma síncrona, siga os passos abaixo:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e defina suas propriedades.
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e especifique o Host, a porta, o nome de usuário e a senha.
1. Envie a mensagem usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e passe a instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

O seguinte trecho de código Java mostra como enviar emails do Outlook de forma síncrona.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Declare msg como instância MailMessage
MailMessage msg = new MailMessage();

// Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// Especifique seu servidor de correio, Nome de usuário, Senha, Número da Porta e Opção de Segurança
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);

try {
    // Client.Send enviará esta mensagem
    client.send(msg);
    System.out.println("Mensagem enviada");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Enviando Emails Assíncronamente**

Às vezes, você pode querer enviar emails de forma assíncrona. Por exemplo, se você estiver enviando muitos emails através de sua aplicação, a abordagem síncrona pode não funcionar. Nessa situação, você pode usar o [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). O método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) envia uma mensagem de email para um servidor SMTP para entrega. Este método não bloqueia o thread de chamada e permite que o chamador passe um objeto ao método que será invocado quando a operação for concluída. Para enviar uma mensagem de email do Outlook assim que o Java, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e use suas diferentes propriedades.
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e especifique o host, a porta, o nome de usuário e a senha.
1. Crie uma instância definida pelo usuário que será passada para o método e invocada quando a operação assíncrona for concluída.
1. Envie a mensagem usando o método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e passe a instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e a instância definida pelo usuário junto com uma função de retorno a ser chamada quando a operação for concluída.

Para receber uma notificação quando o email foi enviado ou a operação foi cancelada, a função de retorno passada ao método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) é chamada. Após chamar o método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/), não é necessário esperar que uma mensagem de email seja enviada completamente. Podemos chamar outro método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) ao mesmo tempo. Quando um email é enviado usando o método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-), o trecho de código imprime uma mensagem ("Mensagem Enviada"). O seguinte programa Java ou trecho de código mostra como enviar emails de forma assíncrona.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

public static void run() {
    sendMail();
}

static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient();
    client.setHost("mail.server.com");
    // Especifique seu Nome de usuário de correio, Senha, Número da Porta e opção de segurança
    client.setUsername("username");
    client.setPassword("password");
    client.setPort(587);
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    return client;
}

static void sendMail() {
    try {

        // Declare msg como instância MailMessage
        MailMessage msg = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Assunto de teste", "Corpo de teste");
        SmtpClient client = getSmtpClient();
        Object state = new Object();
        IAsyncResult ar = client.beginSend(msg, callback, state);
        // Se o usuário cancelou o envio, e o email ainda não foi enviado,
        client.cancelAsyncOperation(ar);

        msg.dispose();
        System.out.println("Adeus.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

static AsyncCallback callback = new AsyncCallback() {
    public void invoke(IAsyncResult ar) {
        IAsyncResultExt task = null;
        if (ar instanceof IAsyncResult)
            task = (IAsyncResultExt) ar;

        if (task != null && task.isCanceled()) {
            System.out.println("Envio cancelado.");
        }

        if (task != null && task.getErrorInfo() != null) {
            System.out.println(task.getErrorInfo());
        } else {
            System.out.println("Mensagem Enviada.");
        }
    }
};
~~~

## **Enviando Mensagens Armazenadas no Disco**

Arquivos EML (Arquivos Eletrônicos de Email do Outlook Express) contêm um cabeçalho de email, corpo da mensagem e quaisquer anexos. Aspose.Email permite que os desenvolvedores trabalhem com arquivos EML de diferentes maneiras. Este artigo mostra como carregar arquivos EML do disco e enviá-los como emails com SMTP. Você pode carregar arquivos .eml do disco ou de um stream na classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e enviar a mensagem de email usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) é a classe principal para criar novas mensagens de email, carregar arquivos de mensagem de email do disco ou de um stream e salvar as mensagens. O seguinte trecho de código Java mostra como enviar mensagens armazenadas do disco.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Carregue um arquivo EML na classe MailMessage
MailMessage message = MailMessage.load(dataDir + "test.eml");

// Envie esta mensagem usando SmtpClient
SmtpClient client = new SmtpClient("host", "username", "password");

try {
    client.send(message);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Enviando Email de Texto Simples**

Os exemplos de programação abaixo mostram como enviar uma mensagem de email em texto simples. A propriedade [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) é usada para especificar o conteúdo em texto simples do corpo da mensagem. Para enviar uma mensagem de email em texto simples, siga estes passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique os endereços de email do remetente e do destinatário na instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique o conteúdo do [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) usado para a mensagem em texto simples.
- Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e envie o email.

O seguinte trecho de código mostra como enviar um email em texto simples.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe MailMessage
MailMessage message = new MailMessage();

// Defina o campo De, o campo Para e o corpo em texto simples
message.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
message.getTo().add("receiver@receiver.com");
message.setBody("Este é o Corpo em Texto Simples");

// Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// E especifique seu servidor de correio, Nome de usuário, Senha e Porta
client.setHost("smtp.server.com");
client.setUsername("Username");
client.setPassword("Password");
client.setPort(25);

try {
    // Client.Send enviará esta mensagem
    client.send(message);
    System.out.println("Mensagem enviada");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Enviando Email com corpo HTML**

Os exemplos de programação abaixo mostram como você pode enviar uma mensagem de email HTML simples. A propriedade [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), uma propriedade da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), é usada para especificar o conteúdo HTML do corpo da mensagem. Para enviar um email HTML simples, siga estes passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique o endereço de email do remetente e do destinatário na instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique o conteúdo do [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--).
- Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e envie o email usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) da classe.

Para os propósitos deste artigo, o conteúdo HTML do email é rudimentar: <html><body>Este é o corpo HTML</body></html> A maioria dos emails HTML será mais complexa. O seguinte trecho de código Java mostra como enviar um email com corpo HTML.

~~~Java
public static void run() {
    // Declare msg como instância MailMessage
    MailMessage msg = new MailMessage();

    // Use as propriedades MailMessage para especificar remetente, destinatário, mensagem e HtmlBody
    msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("asposetest123@gmail.com"));
    msg.setSubject("Assunto de Teste");
    msg.setHtmlBody("<html><body>Este é o corpo HTML</body></html>");
    SmtpClient client = getSmtpClient();
    try {
        // Client enviará esta mensagem
        client.send(msg);
        System.out.println("Mensagem enviada");
    } catch (Exception ex) {
        System.err.println(ex);
    }

    System.out.println("Email enviado com corpo HTML.");
}

private static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.setSecurityOptions(SecurityOptions.Auto);
    return client;
}
~~~

## **Enviando Email com Texto Alternativo**

Os exemplos de programação abaixo mostram como enviar uma mensagem de email HTML simples com conteúdo alternativo. Use a classe [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) para especificar cópias de uma mensagem de email em diferentes formatos. Por exemplo, se você enviar uma mensagem em HTML, pode também querer fornecer uma versão em texto simples para destinatários que usam leitores de email que não podem exibir conteúdo HTML. Ou, se você está enviando um boletim informativo, pode querer fornecer uma cópia em texto simples do texto para aqueles destinatários que optaram por receber uma versão em texto simples. Para enviar um email com texto alternativo, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique os endereços de email do remetente e do destinatário na instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Crie uma instância da classe [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) que cria uma visualização alternativa de uma mensagem de email usando o conteúdo especificado na string.

1. Adicione a instância da classe [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) ao objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e envie o email usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) da classe.

O seguinte trecho de código mostra como enviar um email com texto alternativo.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Declare message como instância MailMessage
MailMessage message = new MailMessage();

// Cria AlternateView para visualizar uma mensagem de email usando o conteúdo especificado na String
AlternateView alternate = AlternateView.createAlternateViewFromString("Texto Alternativo");

// Adicionando texto alternativo
message.getAlternateViews().addItem(alternate);
~~~

## **Enviando Emails em Massa**

Enviar emails em massa significa enviar um lote de emails em uma única mensagem. Podemos enviar um lote de email usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) sobrecarregado da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) que aceita uma classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/):

1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).
1. Especifique as propriedades da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).
1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique o remetente, o destinatário, o assunto do email e a mensagem na instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Repita os dois passos acima se você quiser enviar um email para uma pessoa diferente.
1. Crie uma instância da classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Adicione uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) ao objeto da classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Agora envie seu email usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) passando a instância da classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) nela.

O seguinte trecho de código mostra como enviar emails em massa.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie SmtpClient como client e especifique servidor, porta, nome de usuário e senha
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Crie instâncias da classe MailMessage e especifique Para, De, Assunto e Mensagem
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Assunto1", "mensagem1, como você está?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Assunto2", "mensagem2, como você está?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Assunto3", "mensagem3, como você está?");

// Crie uma instância da classe MailMessageCollection
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.addItem(message1);
manyMsg.addItem(message2);
manyMsg.addItem(message3);

// Use a função client.BulkSend para completar a tarefa de envio em massa
try {
    // Envie a Mensagem usando o método BulkSend
    client.send(manyMsg);
    System.out.println("Mensagem enviada");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~
## **Obter Informações sobre Mensagens em Massa Enviadas**

Quando você envia mensagens em massa, pode obter informações sobre o número de mensagens enviadas com sucesso e a lista dessas mensagens. O evento [SucceededSending](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setSucceededSending-com.aspose.ms.System.EventHandler-com.aspose.email.MailMessageEventArgs--) é usado para esse propósito.

O exemplo de código abaixo mostra como obter informações sobre o número de mensagens enviadas com sucesso:

```java
try (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto)) {
    final AtomicInteger messageCount = new AtomicInteger(0);

    client.setSucceededSending(new EventHandler<MailMessageEventArgs>() {
        public void invoke(Object sender, MailMessageEventArgs eventArgs) {
            System.out.println("A mensagem " + eventArgs.getMessage().getSubject() + " foi enviada com sucesso.");
            messageCount.incrementAndGet();
        }
    });

    client.send(messages);

    System.out.println(messageCount + " mensagens foram enviadas com sucesso.");
}
```


## **Enviando Emails com MultiConnection**

O [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) fornece uma propriedade [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseMultiConnection-int-) que pode ser usada para criar várias conexões para operações pesadas. Você também pode definir o número de conexões a serem usadas durante o modo de multiconexão usando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setConnectionsQuantity-int-). O seguinte trecho de código demonstra o uso do modo de multiconexão para enviar várias mensagens.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient smtpClient = new SmtpClient();
smtpClient.setHost("<HOST>");
smtpClient.setUsername("<USERNAME>");
smtpClient.setPassword("<PASSWORD>");
smtpClient.setPort(587);
smtpClient.setSupportedEncryption(EncryptionProtocols.Tls);
smtpClient.setSecurityOptions(SecurityOptions.SSLExplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Mensagem de Teste - " + UUID.randomUUID().toString(),
            "SMTP Enviar Mensagens com MultiConnection");
    messages.add(message);
}

smtpClient.setConnectionsQuantity(5);
smtpClient.setUseMultiConnection(MultiConnectionMode.Enable);
smtpClient.send(messages);
~~~

{{% alert color="primary" %}} 

Por favor, note que o uso do modo de multiconexão não garante aumento de desempenho.

{{% /alert %}} 

## **Enviando uma Mensagem como TNEF**

Emails TNEF têm formatação especial que pode ser perdida se enviados usando a API padrão. Aspose.Email fornece a capacidade de enviar emails como TNEF, preservando assim o formato. A propriedade [UseTnef](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseTnef\(boolean\)) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) pode ser definida para enviar o email como TNEF. O seguinte trecho de código mostra como enviar uma mensagem como TNEF.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

String emlFileName = dataDir + "Message.eml"; // Um Email TNEF

// Carregar do eml
MailMessage eml1 = MailMessage.load(emlFileName, new EmlLoadOptions());
eml1.setFrom(MailAddress.to_MailAddress("somename@gmail.com"));
eml1.getTo().clear();
eml1.getTo().addItem(new MailAddress("first.last@test.com"));
eml1.setSubject("Com a bandeira PreserveTnef durante o carregamento");
eml1.setDate(new Date());
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setUseTnef(true); // Use esta bandeira para enviar como TNEF
client.send(eml1);
~~~

## **Enviando Convites para Reuniões**

O Microsoft Outlook oferece funções de calendário, além do gerenciamento de emails. Quando um usuário abre um email com um convite para um evento, o Outlook o solicita para aceitar ou rejeitar o convite. Aspose.Email permite que os desenvolvedores adicionem funções de calendário aos seus emails.

### **Enviando Convites por Email**

Para enviar convites para reuniões por email, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique os endereços do remetente e do destinatário usando uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Inicialize uma instância da classe [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) e passe seus valores.
- Especifique resumo e descrição na instância [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/).
- Adicione o [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) à instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e passe a instância [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).

|**Solicitação de reunião iCalendar enviada por email**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
O seguinte trecho de código mostra como enviar convites por Email.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe MailMessage
MailMessage msg = new MailMessage();

// Defina o remetente, destinatário, quem receberá o convite para a reunião. Basicamente, o destinatário é o mesmo que os participantes da reunião
msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com"));

// Crie instância de Appointment
Calendar cal = Calendar.getInstance();
cal.set(2015, Calendar.JULY, 17, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2015, Calendar.JULY, 17, 14, 0, 0);
Date endDate = cal.getTime();
Appointment app = new Appointment("Room 112", startDate, endDate, msg.getFrom(), msg.getTo());
app.setSummary("Reunião de Lançamento");
app.setDescription("Discutir sobre o próximo lançamento");

// Adicione o compromisso à mensagem e crie uma instância da classe SmtpClient
msg.addAlternateView(app.requestApointment());
SmtpClient client = getSmtpClient();

try {
    // Client.Send enviará esta mensagem
    client.send(msg);
    System.out.println("Mensagem enviada");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

### **Suporte a iCalendar para IBM Lotus Notes**

O recurso de calendário Aspose.Email é baseado no padrão iCalendar, um padrão para a troca de dados de calendário (RFC 2445 ou referência de sintaxe RFC2445). Portanto, ele suporta não apenas o Microsoft Outlook, mas também o IBM Lotus Notes. Para enviar um convite de reunião no Lotus Notes, siga as mesmas etapas mencionadas acima.

## **Encaminhando um Email usando o Cliente SMTP**

### **Encaminhando Email com o cliente SMTP**

Encaminhar um email é uma prática comum na comunicação digital do dia a dia. Um email recebido pode ser encaminhado para destinatários específicos sem compartilhar com os remetentes originais. A API Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) fornece a capacidade de encaminhar um email para destinatários específicos. Seu método [Forward](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#forward-java.lang.String-com.aspose.email.MailAddressCollection-com.aspose.email.MailMessage-) pode ser usado para encaminhar um email recebido ou salvo para os destinatários desejados, conforme mostrado neste artigo. O seguinte trecho de código mostra como encaminhar um email usando o Cliente SMTP.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

// Crie uma instância da classe SmtpClient
SmtpClient client = new SmtpClient();

// Especifique seu servidor de correio, Nome de usuário, Senha, Porta e SecurityOptions
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
MailMessage message = MailMessage.load(dataDir + "Message.eml");
client.forward("Recipient1@domain.com", "Recipient2@domain.com", message);
~~~

### **Encaminhando Email sem usar MailMessage**

A API também suporta o encaminhamento de mensagens EML sem primeiro carregá-las na [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Isso é útil em casos onde há recursos limitados em termos de memória do sistema.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java

String host = "mail.server.com";
String username = "username";
String password = "password";
int smtpPort = 587;
String sender = "Sender@domain.com";
MailAddressCollection recipients = new MailAddressCollection();
recipients.add("recepient1@domain.com, recepient2@domain.com");

try (SmtpClient client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto)) {
    String fileName = "test.eml";
    try (FileInputStream fs = new FileInputStream(new File(dataDir + fileName))) {
        client.forward(sender, recipients, fs);
    }
}
~~~

## **Realizando Mail Merge**

Mail merges ajudam você a criar e enviar um lote de mensagens de email semelhantes. O núcleo dos emails é o mesmo, mas o conteúdo pode ser personalizado. Normalmente, os detalhes de contato de um destinatário (primeiro nome, segundo nome, empresa etc.) são usados para personalizar o email.

|**Ilustração de como funciona um mail merge:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite que os desenvolvedores configurem mail merges que incluam dados de várias fontes de dados.

Para realizar um mail merge com Aspose.Email, siga estas etapas:

1. Crie uma função com a assinatura de nome
1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique o remetente, destinatário, assunto e corpo.
1. Crie uma assinatura para o final do email.
1. Crie uma instância da classe [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) e passe a instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Pegue a assinatura na instância [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/).
1. Crie uma instância da classe [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Adicione as colunas **Recebimento**, **PrimeiroNome** e **ÚltimoNome** como fontes de dados na classe [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Crie uma instância da classe [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Especifique o endereço de recebimento, primeiro e último nomes no objeto [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Crie uma instância da classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Especifique as instâncias [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) e [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) na instância [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e especifique o servidor, porta, nome de usuário e senha.
1. Envie emails usando o método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

No exemplo abaixo, #FirstName# indica uma coluna [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/), cujo valor é definido pelo usuário. O seguinte trecho de código mostra como realizar o Mail Merge.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // O caminho para o diretório do arquivo.
    String dstEmail = dataDir + "EmbeddedImage.msg";

    // Crie uma nova instância MailMessage
    MailMessage msg = new MailMessage();

    // Adicione assunto e endereço do remetente
    msg.setSubject("Olá, #FirstName#");
    msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));

    // Adicione endereço de email para enviar email também Adicione campo de mensagem ao corpo HTML
    msg.getTo().add("your.email@gmail.com");
    String htmlBody = "Sua mensagem aqui/r/n" + "Obrigado pelo seu interesse na <STRONG>Aspose.Email</STRONG>.";

    // Use GetSignment como a rotina de template, que fornecerá a mesma assinatura
    htmlBody += "<br><br>Divirta-se com isso.<br><br>#GetSignature()#";

    msg.setHtmlBody(htmlBody);

    // Crie uma nova TemplateEngine com a mensagem MSG, registre a rotina GetSignature. Ela será usada no MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.registerRoutine("GetSignature", new TemplateRoutine() {
        public Object invoke(Object[] args) {
            return getSignature(args);
        }
    });

    // Crie uma instância de DataTable e preencha um DataTable como fonte de dados
    DataTable dt = new DataTable();
    dt.getColumns().add("Recebimento");
    dt.getColumns().add("PrimeiroNome");
    dt.getColumns().add("ÚltimoNome");

    DataRow dr;
    dr = dt.newRow();
    dr.set("Recebimento", "Nancy&lt;Nancy@somedomain.com&gt;");
    dr.set("PrimeiroNome", "Nancy");
    dr.set("ÚltimoNome", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Recebimento", "Andrew&lt;Andrew@somedomain.com&gt;");
    dr.set("PrimeiroNome", "Andrew");
    dr.set("ÚltimoNome", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Recebimento", "Janet&lt;Janet@somedomain.com&gt;");
    dr.set("PrimeiroNome", "Janet");
    dr.set("ÚltimoNome", "Doe");
    dt.getRows().add(dr);

    MailMessageCollection messages;
    try {
        // Crie mensagens a partir da mensagem e da fonte de dados.
        messages = engine.instantiate(dt);

        // Crie uma instância de SmtpClient e especifique servidor, porta, nome de usuário e senha
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.setSecurityOptions(SecurityOptions.Auto);

        // Envie mensagens em massa
        client.send(messages);
    } catch (MailException ex) {
        System.err.println(ex);
    }

    catch (SmtpException ex) {
        System.err.println(ex);
    }

    System.out.println("Mensagem enviada após realizar o mail merge.");
}

// Rotina de template para fornecer assinatura
static Object getSignature(Object[] args) {
    return "Equipe Aspose.Email<br>Aspose Ltd.<br>" + new Date().toString();
}
~~~

## **Realizando Mail Merge Linha a Linha**

O usuário pode mesclar uma linha de dados individual também para obter um objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) completo e preparado. O método [TemplateEngine.merge](https://reference.aspose.com/email/java/com.aspose.email/templateengine/#merge-com.aspose.email.DataRow-) pode ser usado para realizar um mail merge linha a linha.

~~~Java
// Crie mensagem a partir dos dados na linha atual.
MailMessage message = engine.merge(currentRow);
~~~