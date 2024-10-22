---
title: "Criando e Definindo Conteúdos de Emails no .NET"
url: /pt/net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Criando e definindo conteúdos de Emails"
---

## **Criar Nova Mensagem de Email**

Para criar uma nova mensagem de email, você pode usar a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). A classe **MailMessage** também inicializa propriedades da mensagem de email criada, como o endereço de email do remetente, os endereços de email dos destinatários, o assunto do email e o conteúdo do corpo do email em formato HTML.

Considere o seguinte código, com etapas detalhadas, para criar uma nova mensagem de email e definir suas propriedades.

**Etapas do código:**

1. Crie uma nova instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Defina a propriedade [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) para o endereço de email do remetente.
3. Defina a propriedade [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) para uma lista de endereços de email dos destinatários, separados por vírgulas.
4. Defina a propriedade [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) para o assunto do email.
5. Defina a propriedade [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) para o conteúdo HTML do corpo do email.

**Exemplo de código:**
```cs
// Cria uma nova instância da classe MailMessage
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Nova mensagem",
    HtmlBody = @"<!DOCTYPE html>
    <html>
     <head>
      <style>
       h3{font-family:Verdana, sans-serif;color:#000000;background-color:#ffffff;}
       p {font-family:Verdana, sans-serif;font-size:14px;font-style:normal;
         font-weight:normal;color:#000000;background-color:#ffffff;}
      </style>
     </head>
     <body>
       <h3>Nova mensagem</h3>
       <p>Esta é uma nova mensagem criada pelo Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Especificando Múltiplos Destinatários**

Existem três maneiras de especificar os destinatários de uma mensagem de email: usando os campos **To**, **CC** ou **BCC**.

- O campo **To** é o destinatário principal da sua mensagem. Você pode inserir um ou mais endereços de email neste campo, separados por vírgulas. O campo To é obrigatório para cada mensagem de email.

- O campo **CC** significa cópia carbono. É usado para enviar uma cópia da sua mensagem para outras pessoas que estão interessadas ou envolvidas no tópico. O campo CC é opcional e também pode conter vários endereços de email. Os destinatários no campo CC podem ver quem mais recebeu a mensagem.

- O campo **BCC** significa cópia carbono oculta. É similar ao campo CC, mas os destinatários no campo BCC são ocultados dos outros destinatários. O campo BCC é útil quando você deseja proteger a privacidade de alguns destinatários ou evitar sobrecarregar suas caixas de entrada com respostas. O campo BCC também é opcional e pode ter vários endereços de email.

Considere o seguinte código, com etapas detalhadas, para especificar múltiplos destinatários para uma mensagem de email.

**Etapas do código:**

1. Crie uma nova instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Defina a propriedade [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) para o endereço de email do remetente.
3. Defina a propriedade [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) para um array de endereços de email dos destinatários principais.
4. Defina a propriedade [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) para um array de endereços de email dos destinatários que receberão uma cópia do email.
5. Defina a propriedade [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) para um array de endereços de email dos destinatários que receberão uma cópia carbono oculta do email.

**Exemplo de código:**

```cs
var eml = new MailMessage
{
    // Especifique o endereço From
    From = "sender@sender.com",
    //  Especifique os endereços de email dos destinatários
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Especifique os endereços CC
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Especifique os endereços BCC
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Adicionando nomes de exibição aos endereços de email**

Além de um endereço de email, um **nome de exibição** pode ser incluído para identificar o remetente ou o destinatário do email. Ele pode incluir o nome completo de uma pessoa, apelido ou outro identificador.

Quando uma mensagem de email é exibida em um cliente de email ou interface de webmail, o nome de exibição geralmente é mostrado ao lado do endereço de email, facilitando para o usuário identificar de quem é a mensagem ou para quem ela é endereçada. Por exemplo, um endereço de email pode ser "johndoe@example.com", mas o nome de exibição associado a ele pode ser "John Doe".

Para adicionar nomes de exibição aos endereços de email em uma mensagem de email, considere o seguinte código com etapas detalhadas:

**Etapas do código:**

1. Carregue a mensagem de email de um arquivo usando o método [MailMessage.Load]() .
2. Defina o remetente do email usando a propriedade [From]() do objeto eml, criando um novo objeto [MailAddress]() com o endereço de email e um nome de exibição do remetente.
3. Adicione um destinatário ao email usando a propriedade [To]() do objeto eml; se necessário, adicione a lista de CC (Cópia Carbono) usando a propriedade [CC](), a lista de BCC (Cópia Carbono Oculta) usando a propriedade [Bcc]() e chame o método [Add]() com um novo objeto [MailAddress]() que contém o endereço de email e um nome de exibição do destinatário.

**Exemplo de código:**

```cs
// Carregar eml de um arquivo
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// Um endereço To com um nome amigável também pode ser especificado assim
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Especifique o endereço Cc e Bcc junto com um nome amigável
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Guangzhou Team"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Exibindo os participantes opcionais na saída do cabeçalho mht**

O exemplo de código abaixo demonstra como usar o recurso *exibir participantes opcionais* ao salvar um msg em formato mhtml:

```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

//se você precisar ignorar OptionalAttendees no arquivo mhtml, pode limpar o modelo de formato para OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```

## **Definir Corpo de Email**

Neste artigo, você aprenderá como:

- [definir corpo de texto simples](#Set-Plain-Text-Body)
- [definir corpo HTML](#Setting-HTML-Body)
- [definir texto alternativo](#Setting-Alternate-Text)
- [especificar codificação do corpo do email](#Specifying-Mail-Body-Encoding)

### **Definindo Corpo de Texto Simples**

Um corpo de email pode ser especificado usando a propriedade [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Especifique o HtmlBody
    Body = "Este é um corpo de texto simples"
};
```

### **Definindo Corpo HTML**

Um corpo de email também pode ser especificado usando a propriedade [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). 

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Especifique o HtmlBody
    HtmlBody = "<html><body>Este é o corpo HTML</body></html>"
};
```

### **Definindo Texto Alternativo**

Uma exibição alternativa em um arquivo EML é uma representação adicional do conteúdo do email que pode ser usada para fornecer uma renderização diferente da mensagem de email. Por exemplo, se você enviar uma mensagem em HTML, pode também querer fornecer uma versão **texto simples** caso alguns dos destinatários usem leitores de email que não conseguem exibir conteúdo HTML. Para tal propósito, use a classe [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/). Esta classe possui duas propriedades, [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) e [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), que são usadas para resolver URLs dentro do conteúdo do email.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) é uma coleção de objetos [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/). Quando renderizado, URLs dentro do conteúdo do email são primeiro correspondidos contra os URLs no Link de Conteúdo de cada objeto [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) na coleção [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) e resolvidos.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) é usado pelo leitor de email para resolver URLs relativas dentro do corpo, e também para resolver URLs relativas do Link de Conteúdo, na coleção [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/).

Considere o seguinte código com etapas detalhadas para definir um texto alternativo.

**Etapas do código:**

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Crie uma [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) para visualizar uma mensagem de email usando o conteúdo especificado na string.
3. Adicione texto alternativo usando o método [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) da coleção [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/).

**Exemplo de código:**
```cs
// Declare message as MailMessage instance
var eml = new MailMessage();

// Cria uma AlternateView para visualizar uma mensagem de email usando o conteúdo especificado na string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Texto Alternativo");

// Adicionando texto alternativo
 eml.AlternateViews.Add(alternate);
```

### **Especificando Codificação do Corpo do Email**

Aspose.Email usa a propriedade [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para especificar a codificação do corpo do email. Por exemplo:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Definindo Propriedades Adicionais de MailMessage**

Com Aspose.Email, você pode usar propriedades adicionais da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) como:

- A propriedade [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) - define **data e hora** de um email. Por padrão, a data é a data real em que a mensagem foi enviada, e a hora é a hora em que foi enviada, como exibido pelo Microsoft Outlook. No entanto, o real horário de entrega do email é adicionado pelo servidor SMTP no cabeçalho do email. Por exemplo, abaixo está um cabeçalho de email comum, onde [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) define o campo Date.

   ```cs
   // Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-.NET
   
   // Adicionado pelo servidor SMTP na entrega dos emails
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
   
   // Adicionado pelo servidor SMTP na entrega dos emails
   Return-Path: <xyz@oikoscucine.it>
   
   // Adicionado pelo servidor SMTP na entrega dos emails
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: Para ABC
   
   // A data definirá o campo Date, o outlook mostrará isso como
   Date: Thu, 22 Feb 2007 20:58:51 +0300
   Message-ID: <01c756c4$41b554d0$6c822ecf@dishonestyinsufferably>
   MIME-Version: 1.0
   Content-Type: multipart/alternative;
   boundary="----=_NextPart_000_0006_01C7569A.58DF4CD0"
   X-Mailer: Microsoft Office Outlook, Build 11.0.5510
   X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2800.1106
   Thread-Index: Aca6Q:=ES0M(9-=(<.<1.<Q9@QE6CD==
   X-Read: 1
   ```

- A enumeração [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) - especifica níveis de prioridade para o envio de uma mensagem de email. Pode ser baixa, normal ou alta. A prioridade influencia a velocidade de transmissão e entrega.
- A enumeração [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) - especifica cinco níveis de sensibilidade.
- O [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/) - especifica o software que criou a mensagem de email.

O trecho de código abaixo ilustra como cada uma das propriedades discutidas acima pode ser usada.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Algum assunto", "Algum texto do corpo")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Solicitando um Aviso de Leitura**

Para solicitar um [aviso de leitura](https://en.wikipedia.org/wiki/Return_receipt), use a propriedade [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Essa propriedade contém os valores da enumeração [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration).

Considere o seguinte **exemplo de código**:

```cs
// Crie uma instância da classe MailMessage
var eml = new MailMessage
{
    // Especifique os campos From, To, HtmlBody, DeliveryNotificationOptions
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>Este é o corpo Html</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Crie uma instância da classe SmtpClient
var client = new SmtpClient
{
    // Especifique seu servidor de host de email, Nome de usuário, Senha e Porta
    Host = "smtp.server.com",
    Username = "NomeDeUsuario",
    Password = "Senha",
    Port = 25
};

try
{
    // Client.Send enviará esta mensagem
    client.Send(eml);
    // Exibir 'Mensagem Enviada', apenas se a mensagem for enviada com sucesso
    Console.WriteLine(@"Mensagem enviada");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Nota**: Solicitações de aviso de leitura podem nem sempre ser atendidas porque:

- Um cliente de email pode não implementar essa funcionalidade.
- O usuário final pode ter desativado essa funcionalidade.
- O usuário final pode optar por não enviar um.

## **Definir Cabeçalhos de Email**

Os cabeçalhos de email representam um padrão da Internet e a RFC define campos de cabeçalho que são incluídos em mensagens de email na Internet. Um cabeçalho de email pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Tipos comuns de cabeçalho são definidos na classe [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). É uma classe selada que funciona como uma enumeração normal.

Normalmente, um cabeçalho de email contém estes campos:

- **To**: endereços de destinatário podem ser especificados no campo To. Os destinatários do campo To são o público principal da mensagem. Pode haver mais de um endereço de destinatário.
- **From**: este campo apresenta o endereço de email do remetente da mensagem.
- **Cc**: permite que os usuários enviem uma mensagem como "Cópia Carbono" ou "Cópia de Cortesia". Ou seja, espera-se que o receptor não responda ou atue. Normalmente, o pessoal de supervisão é notificado com CC.
- **Bcc**: significa Cópia Carbono Oculta, o que permite enviar um email para um destinatário que está oculto de outros destinatários.
- **ReplyTo**: este campo de cabeçalho visa indicar para onde o remetente deseja que as respostas sejam enviadas.
- **Subject**: Título, cabeçalho, assunto. Usualmente usado como um indicador de thread para mensagens respondendo ou comentando sobre outras mensagens.
- **Date**: este cabeçalho especifica uma data (e hora). Normalmente, esta é a data em que a mensagem foi composta e enviada.
- **XMailer**: informações sobre o software cliente do originador. Exemplo: X-Mailer: Aspose.Email. O XMailer é usado pelos clientes de email. Diferentes clientes de email terão diferentes valores para XMailer. O valor do XMailer do MS Outlook é Microsoft Office Outlook, Build 11.0.5510. É ignorado pelo receptor de email ou leitor de email.

Normalmente, um cabeçalho de email se parece com isto:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: email de teste
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Para personalizar um cabeçalho de email, siga estas **etapas do código**:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifique To, From, Cc, Bcc, ReplyTo, Subject, Date e XMailer usando uma instância da [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Crie uma instância da classe [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) e especifique o cabeçalho personalizado.
- Adicione o cabeçalho personalizado à instância da [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

O seguinte **trecho de código** mostra como definir cabeçalhos de email.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "email de teste",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

O trecho de código acima produz um cabeçalho de email no seguinte formato:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: email de teste
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Inserir um Cabeçalho em um Local Específico**

O método [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) da classe [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) insere um cabeçalho no final da coleção. No entanto, pode ser necessário inserir um cabeçalho em um local específico. Nesse caso, o método [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) não será útil. Para conseguir isso, use o método [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) da [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). Se a coleção contiver cabeçalhos com o mesmo nome, esse cabeçalho será inserido antes de outros cabeçalhos com o mesmo nome. O seguinte trecho de código mostra como inserir um cabeçalho em um local específico.

```cs
eml.Headers.Insert("Received", "Value");
```

### **Salvar Todos os Cabeçalhos em MHTML**

A propriedade [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) da classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) define se há necessidade de salvar todos os cabeçalhos na saída mhtml ou não. O trecho de código a seguir mostra como salvar todos os cabeçalhos de um arquivo mhtml:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Adicionando Cabeçalhos Personalizados ao Email**

Um cabeçalho de email pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Para especificar um **cabeçalho personalizado** em uma mensagem de email, considere o seguinte exemplo de código:

```cs
eml.Headers.Add("secret-header", "mystery");
```

O trecho de código acima produz um cabeçalho de email no seguinte formato:

```cs
secret-header: mystery
```

## **Salvar um arquivo HTML com Campos de Tarefa em um Cabeçalho**

A enumeração [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) permite especificar que campos de tarefa devem ser incluídos no cabeçalho do arquivo HTML salvo. O trecho de código a seguir mostra como preservar campos de tarefa em um cabeçalho ao salvar um arquivo HTML:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Assinar Emails com DKIM**

> **_NOTA:_** O recurso está acessível apenas para as versões da biblioteca direcionadas ao .NET Framework. Versões direcionadas ao .NET Core não possuem esse recurso.

Aspose.Email permite assinar Emails com DKIM (DomainKeys Identified Mail). Isso permite que uma organização assuma a responsabilidade por uma mensagem que está em trânsito ([Mais informações](https://www.dkim.org/)). DKIM adiciona uma assinatura digital aos cabeçalhos da mensagem de email que pode ser validada pelos destinatários. A chave pública do remetente permite ao receptor verificar se a assinatura corresponde ao conteúdo da mensagem. O método [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) é usado para definir as informações criptográficas e de assinatura para assinar a mensagem. O trecho de código abaixo mostra como assinar emails com DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Algum assunto", "Algum texto do corpo");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```