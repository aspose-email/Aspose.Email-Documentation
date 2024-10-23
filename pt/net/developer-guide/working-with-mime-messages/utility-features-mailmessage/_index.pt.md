---
title: "Recursos de Utilidade - MailMessage"
url: /pt/net/utility-features-mailmessage/
weight: 50
type: docs
---

## **Criptografando e Descriptografando Mensagens**

Aspose.Email fornece a capacidade de criptografar e descriptografar mensagens de e-mail usando os X509Certificates. Este artigo mostra como uma mensagem existente ou nova pode ser carregada e criptografada usando [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Os métodos [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) e [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) retornam um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para os efeitos aplicados e precisam ser considerados ao criptografar/descriptografar mensagens. Criptografar e descriptografar mensagens envolve os seguintes passos:

1. Criar uma nova mensagem ou carregar uma existente
1. Carregar um certificado de criptografia usando o objeto X509Certificate
1. Criptografar a mensagem usando o certificado
1. Enviar a mensagem ou salvá-la
1. Descriptografar a mensagem conforme necessário

O seguinte trecho de código mostra como criptografar e descriptografar mensagens.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Verificar uma Mensagem para Criptografia**

A classe Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) permite verificar se uma mensagem está criptografada ou não. A propriedade [IsEncrypted](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/) da [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) permite verificar isso, conforme mostrado no seguinte exemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Mensagens de E-mail contendo anexos TNEF**

O Formato de Encapsulamento Neutro de Transporte (TNEF) é um formato proprietário de anexo de e-mail usado pelo Microsoft Outlook e pelo Microsoft Exchange Server. A API Aspose.Email permite ler mensagens de e-mail que possuem anexos TNEF e modificar o conteúdo do anexo. O e-mail pode então ser salvo como um e-mail normal ou no mesmo formato, preservando os anexos TNEF. Este artigo mostra diferentes exemplos de código para trabalhar com mensagens contendo anexos TNEF. Este artigo também mostra como criar arquivos EML TNEF a partir de arquivos MSG do Outlook.

### **Ler uma Mensagem Preservando Anexos TNEF**

O seguinte trecho de código mostra como ler uma mensagem preservando anexos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Ler uma Mensagem sem Preservar Anexos TNEF**

O seguinte trecho de código mostra como ler uma mensagem sem preservar anexos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Atualizando Recursos em um Anexo TNEF e Preservando o Formato TNEF**

O seguinte trecho de código mostra como atualizar recursos em um anexo TNEF e preservar o formato TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Adicionando Novos Anexos à Mensagem Principal Contendo TNEF**

O seguinte trecho de código mostra como adicionar novos anexos à mensagem principal contendo TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Criando TNEF EML a partir de MSG**

Os MSGs do Outlook às vezes contêm informações como tabelas e estilos de texto que podem ser perturbados se forem convertidos para EML. Criar mensagens TNEF a partir de arquivos MSG permite reter a formatação e até mesmo enviar tais mensagens via clientes de e-mail mantendo a formatação. A propriedade [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) é usada para conseguir isso. O seguinte trecho de código mostra como criar TNEF EML a partir de MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

Para criar o TNEF, o seguinte código de exemplo pode ser usado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Detectar se uma Mensagem é TNEF**

O seguinte trecho de código mostra como detectar se uma mensagem é TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Verificar se um Anexo está em formato TNEF**

A propriedade [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) permite detectar se o anexo da mensagem é uma mensagem formatada em TNEF.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"O Anexo é TNEF?: {attachment.IsTnef}");
}
```

## **Processando Mensagens Devolvidas**

É muito comum que uma mensagem enviada a um destinatário possa ser devolvida por qualquer motivo, como um endereço de destinatário inválido. A API Aspose.Email tem a capacidade de processar tal mensagem para verificar se é um e-mail devolvido ou uma mensagem de e-mail regular. O método [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) retorna um resultado válido se a mensagem de e-mail for um e-mail devolvido. Este artigo mostra o uso da classe [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/) que fornece a capacidade de verificar se uma mensagem é um e-mail devolvido. Ele fornece informações detalhadas sobre os destinatários, a ação tomada e o motivo da notificação. O seguinte trecho de código mostra como processar mensagens devolvidas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}

## **Analisador de Spam Bayesiano**

Aspose.Email fornece filtragem de e-mail usando um analisador de spam bayesiano. Ele fornece a classe [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) para esse propósito. Este artigo mostra como treinar o filtro para distinguir entre spam e e-mails regulares com base no banco de dados de palavras.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Obtendo preâmbulo e epílogo de mensagens em eml**

Uma mensagem de e-mail pode conter algumas informações ocultas como um texto simples antes do corpo da mensagem (ou seja, preâmbulo) ou após o corpo (ou seja, epílogo). Normalmente, é alguma informação adicional ou contexto para o destinatário antes ou depois que eles leem o conteúdo principal do e-mail. Você pode obter essas informações usando as propriedades [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) ou/and [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) respectivamente. 

O seguinte trecho de código mostra como obter os textos de preâmbulo e epílogo:

```cs
// Obtém ou define um texto de preâmbulo.
public string Preamble

// Obtém ou define um texto de epílogo.
public string Epilogue
```