---
title: "Extraindo Conteúdos de Mensagens de E-mails"
url: /pt/net/extracting-message-contents-from-emails/
weight: 30
type: docs
---

# Extraindo Conteúdos de Mensagens de E-mails

## **Exibindo Informações do E-mail na Tela**

O [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) representa uma mensagem de e-mail e permite que desenvolvedores acessem propriedades da mensagem de e-mail. As informações do cabeçalho (discutidas em [Extraindo Cabeçalhos de E-mail](https://docs.aspose.com/email/pt/net/extracting-message-contents-from-emails/#extracting-email-headers)) podem ser extraídas e manipuladas de diferentes maneiras. Este artigo explica como exibir informações selecionadas do cabeçalho de e-mail e o corpo do e-mail na tela. Para Exibir Informações do E-mail na Tela, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Carregue uma mensagem de e-mail na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Exiba o conteúdo do e-mail na tela.

O seguinte trecho de código mostra como exibir informações do e-mail na tela.

```csharp
// Para exemplos completos e arquivos de dados, por favor, vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Email();

// Crie uma instância de MailMessage carregando um arquivo Eml
MailMessage message = MailMessage.Load(dataDir + "test.eml", new EmlLoadOptions());

// Obtém as informações do remetente, informações do destinatário, assunto, corpo html e corpo de texto
Console.Write("De:");
Console.WriteLine(message.From);
Console.Write("Para:");
Console.WriteLine(message.To);
Console.Write("Assunto:");
Console.WriteLine(message.Subject);
Console.WriteLine("HtmlBody:");
Console.WriteLine(message.HtmlBody);
Console.WriteLine("TextBody");
Console.WriteLine(message.Body);
```

## **Extraindo Cabeçalhos de E-mail**

O cabeçalho de e-mail representa um conjunto padrão de campos de cabeçalho definidos por Internet e RFC incluídos nas mensagens de e-mail da Internet. Um cabeçalho de e-mail pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Tipos comuns de cabeçalho são definidos na classe [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). É uma classe selada que funciona como uma enumeração normal. Para extrair cabeçalhos de um e-mail, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Carregue uma mensagem de e-mail na instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
3. Depois que uma mensagem de e-mail for carregada, obteremos seu conteúdo bruto.

A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) contém propriedades como De, Para, Cc, Assunto e assim por diante. Essas propriedades podem ser extraídas dos cabeçalhos.

O seguinte trecho de código mostra como extrair cabeçalhos de e-mail.

## **Obter Valores de Cabeçalho Decodificados**

O seguinte trecho de código mostra como obter valores de cabeçalho decodificados.

```csharp
// Para exemplos completos e arquivos de dados, por favor, vá para https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Obter corpo de texto simples**

A propriedade [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) retorna uma representação em texto simples do corpo de uma mensagem.

```csharp
string plainTextBody = mailMessage.Body;
```

Nota: Se a parte MIME text/plain estiver presente em uma mensagem, a propriedade retorna seus dados de texto. Caso contrário, retorna o conteúdo de texto separado da propriedade [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) sem marcação html.

## **Obter corpo HTML como texto simples**

A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) fornece o recurso para extrair o corpo HTML da mensagem como texto simples. A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) fornece um método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) que retorna o corpo HTML em texto simples. Este método analisa a propriedade [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) e retorna conteúdo separado em texto simples ignorando a marcação html. O método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) aceita um parâmetro booleano que indica se o corpo deve conter URLs ou não. Passar o parâmetro como verdadeiro indica que o corpo HTML deve conter URLs.

O seguinte trecho de código demonstra o uso do método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) para extrair o corpo HTML do e-mail como texto simples.

```csharp
// Para exemplos completos e arquivos de dados, por favor, vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
string dataDir = RunExamples.GetDataDir_Email();

MailMessage mail = MailMessage.Load(dataDir + "HtmlWithUrlSample.eml");

string body_with_url = mail.GetHtmlBodyText(true);// o corpo conterá URL
string body_without_url = mail.GetHtmlBodyText(false);// o corpo não conterá URL

Console.WriteLine("Corpo com URL: " + body_with_url);
Console.WriteLine("Corpo sem URL: " + body_without_url);
```