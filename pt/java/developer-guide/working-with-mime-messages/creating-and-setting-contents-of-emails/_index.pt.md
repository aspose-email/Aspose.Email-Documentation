---
title: "Criando e Definindo Conteúdos de Emails"
url: /pt/java/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Criar Nova Mensagem de Email**

Aspose.Email para Java permite que desenvolvedores criem Mensagens MIME (Extensões de Correio da Internet de Múltiplos Propósitos) do zero. A classe principal para esse propósito na API Aspose.Email para Java é a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
Este tópico explica os passos necessários para criar mensagens de email nos formatos de arquivo EML, MSG e MTH usando Aspose.Email para Java.

Para criar uma mensagem de email do zero:

1. Crie uma instância da classe MailMessage.
2. Defina o assunto da mensagem usando o método [setSubject()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setSubject-java.lang.String-) .
3. Defina o corpo da mensagem usando o método [setHtmlBody()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) .
4. Defina o remetente do email usando o método [setFrom()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setFrom-com.aspose.email.MailAddress-) .
5. Defina o destinatário no campo **TO** usando o método [getTo().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
6. Defina o destinatário no campo **CC** usando o método [getCC().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
7. Chame o método [Save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.io.OutputStream-) para salvar o arquivo da mensagem em disco nos formatos MSG, EML e MHT.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-CreateNewEmail-.java" >}}

## **Especificando Vários Destinatários**

A [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa uma mensagem de email. Instâncias da classe MailMessage são usadas para construir mensagens de email que são transmitidas para um servidor SMTP usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este tópico demonstra como especificar mais de um endereço de email. Os endereços de email podem ser especificados usando a classe MailMessage. Os endereços de email usados na classe MailMessage são:

- **Para** - Os endereços dos destinatários podem ser especificados no campo 'Para'. Os destinatários do campo 'Para' são o público principal da mensagem. Pode haver mais de um endereço de destinatário.
- **Cc** - CC significa "cópia carbono", ou "cópia cortesia", e permite que você adicione destinatários de email que precisam ver o email, mas que não são necessariamente esperados para agir sobre ele. Gerentes, por exemplo, ou membros da sua equipe que precisam estar cientes de uma conversa. Com Aspose.Email, endereços CC podem ser especificados no seu código. Assim, emails automatizados, ou todos os emails para um endereço específico, podem ser copiados para o pessoal relevante.
- **Bcc** - Bcc, cópia carbono oculta, permite que você envie um email a um destinatário que está oculto de outros destinatários. Onde um CC aparece nas informações do email que os destinatários principais veem, um Bcc não aparece. É destinado a notificações ocultas.

Para especificar vários endereços de email em uma mensagem de email, siga estas etapas:

1. Crie uma instância da classe MailMessage.
2. Especifique o Remetente e vários endereços Para, Cc e Bcc usando a instância MailMessage.
3. Crie uma instância da classe SmtpClient e envie o email usando o método Send.

O exemplo de código abaixo mostra como vários endereços Para, CC e BCC podem ser especificados.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyRecipientAddresses-SpecifyRecipientAddresses.java" >}}

## **Mudando endereços de email para um nome amigável**

Os exemplos de programação abaixo demonstram como mudar endereços de email para nomes amigáveis em uma mensagem de email. Um nome amigável é um nome que é mais fácil de entender do que o endereço de email, por exemplo, John Smith em vez de js346@domain.com. Ao enviar um email, podemos associar um nome amigável a um endereço de email no construtor da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .

Para mudar endereços de email para nomes amigáveis em uma mensagem de email, siga estas etapas:

- Crie uma instância da classe MailMessage e especifique endereços de email nos campos **Para** e **De** junto com os nomes amigáveis.
- Especifique os endereços de email Cc e Bcc juntamente com nomes amigáveis chamando o construtor da classe MailMessage na instância MailMessage.
- Crie uma instância da classe SmtpClient e envie o email usando o método Send.

O seguinte trecho de código mostra como exibir Nomes para endereços de email.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ChangeEmailAddress-ChangeEmailAddress.java" >}}

## **Definir Corpo do Email**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa uma mensagem de email. Instâncias da classe MailMessage são usadas para construir mensagens de email que são transmitidas para um servidor SMTP para entrega usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Um corpo de email pode ser especificado usando a classe MailMessage. Um corpo de email pode ser especificado usando o método [setHtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) na MailMessage.

Além do [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), Aspose.Email tem outro método relacionado ao corpo do email:

- [isBodyHtml](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isBodyHtml--): informa ao usuário se o corpo é HTML ou texto simples.

Este tópico mostra como definir o texto do corpo HTML e definir texto alternativo.

### **Definindo Corpo HTML**

[HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) é usado para especificar o conteúdo HTML do corpo de uma mensagem. HtmlBody deve ser envolvido entre as tags <html> </html>. O seguinte trecho de código mostra como definir o corpo HTML.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetHTMLBody-SetHTMLBody.java" >}}

### **Definindo Texto Alternativo**

Use a classe [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) para especificar cópias de uma mensagem de email em diferentes formatos. Por exemplo, se você enviar uma mensagem em HTML, pode também querer fornecer uma versão em texto simples caso alguns dos destinatários usem leitores de email que não podem exibir conteúdo HTML. Esta classe possui duas propriedades, [LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getLinkedResources--) e [BaseUri](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getBaseUri--), que são usadas para resolver URLs dentro do conteúdo do email.

- LinkedResources é uma coleção de objetos LinkedResources. Quando renderizados, URLs dentro do conteúdo do email são primeiro correspondentes às URLs no Link de Conteúdo de cada objeto LinkedResources na coleção LinkedResources e resolvidos.
- BaseUri é usado pelo leitor de email para resolver URLs relativas dentro do corpo e também para resolver URLs relativas de Link de Conteúdo, na coleção LinkedResources.

O seguinte trecho de código mostra como definir texto alternativo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetAlternateText-SetAlternateText.java" >}}

## **Especificando Codificação do Corpo do Email**

O tipo de conteúdo define o formato de conteúdo do email: o conjunto de caracteres. Por exemplo, alguns conjuntos de caracteres comuns fornecidos em java.nio.Charset são:

- US-ASCII - ASCII de sete bits, também conhecido como ISO646-US, também conhecido como o bloco Latin Básico do conjunto de caracteres Unicode.
- ISO-8859-1 - Alfabeto Latino ISO No. 1, também conhecido como ISO-LATIN-1.
- UTF-8 - Formato de Transformação UCS de oito bits.
- UTF-16BE - Formato de Transformação UCS de dezesseis bits, ordem de bytes big-endian.
- UTF-16LE - Formato de Transformação UCS de dezesseis bits, ordem de bytes little-endian.
- UTF-16 - Formato de Transformação UCS de dezesseis bits, ordem de bytes identificada por uma marca de ordem de bytes opcional.

Aspose.Email usa a propriedade [BodyEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBodyEncoding--) da classe MailMessage para especificar a codificação do corpo do email. Para codificar o corpo de uma mensagem de email, siga os passos abaixo:

1. Crie uma instância da classe MailMessage.
1. Especifique o remetente, destinatário e corpo HTML do email na instância MailMessage.
1. Especifique o valor da propriedade BodyEncoding.
1. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e envie o email usando o método Send.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyMailBodyEncoding-SpecifyMailBodyEncoding.java" >}}

## **Características do MailMessage**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa o conteúdo de uma mensagem de email. Instâncias da classe MailMessage são usadas para construir uma mensagem de email que é transmitida para um servidor SMTP para entrega usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este artigo mostra como usar os recursos utilitários da classe MailMessage para controlar as seguintes características do email:

- **Data e hora** - Através do método [setDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setDate-java.util.Date-) da classe MailMessage, definimos a data e hora de um email.
- **Prioridade da mensagem** - A classe [MailPriority](https://reference.aspose.com/email/java/com.aspose.email/mailpriority/) especifica níveis de prioridade para enviar uma mensagem de email. Pode ser baixa, normal ou alta. A prioridade influencia a velocidade de transmissão e a entrega.
- **Sensibilidade da mensagem** - A classe [MailSensitivity](https://reference.aspose.com/email/java/com.aspose.email/mailsensitivity/) especifica cinco níveis de sensibilidade.
- **Notificação de entrega** - As notificações de entrega informam aos remetentes que o email que enviaram foi entregue na caixa de entrada do destinatário.

Por padrão, a data é a data atual em que a mensagem foi enviada, e a hora é a hora em que foi enviada, como exibido pelo Microsoft Outlook. No entanto, o tempo real de entrega do email é acrescentado pelo próprio servidor SMTP no cabeçalho do email. Por exemplo, abaixo está um cabeçalho de email comum, onde o campo Data foi configurado usando MailMessage.setDate.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-DateAndTime-DateAndTime.cs" >}}

O trecho de código abaixo ilustra como cada um dos recursos discutidos acima pode ser usado.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-UseMailMessageFeatures-MailMessageFeatures.java" >}}

## **Solicitando um Recebimento de Leitura**

Os exemplos de programação abaixo mostram como você pode solicitar um recibo de leitura. A propriedade de enumeração [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDeliveryNotificationOptions--) da classe MailMessage descreve as [opções de notificação de entrega](https://reference.aspose.com/email/java/com.aspose.email/deliverynotificationoptions/) para um email. Para solicitar um recibo de leitura após enviar um email, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Especifique o remetente, destinatário e corpo HTML para o email na instância MailMessage.
1. Especifique as DeliveryNotificationOptions em outras instâncias de MailMessage.
2. Crie uma instância da classe SmtpClient e envie o email usando o método Send.

Recibos de leitura podem nem sempre ser honrados porque:

- Um cliente de email pode não implementar essa funcionalidade.
- O usuário final pode ter essa funcionalidade desativada.
- O usuário final pode optar por não enviar um.

O seguinte trecho de código mostra como solicitar um recibo de leitura.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-RequestReadReceipt-RequestReadReceipt.java" >}}

## **Definir Cabeçalhos de Email**

Os cabeçalhos de email representam um padrão da Internet e o RFC define campos de cabeçalho que são incluídos nas mensagens de email da Internet. Um cabeçalho de email pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) . Tipos comuns de cabeçalho são definidos na classe [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) . É uma classe selada que funciona como uma enumeração normal.

Normalmente, um cabeçalho de email contém estes campos:

- Para: Os endereços dos destinatários podem ser especificados no campo **Para**. Os destinatários do campo **Para** são o público principal da mensagem. Pode haver mais de um endereço de destinatário.
- De: Este campo apresenta o endereço de email do remetente da mensagem.
- Cc: Permite que os usuários enviem uma mensagem como uma "Cópia Carbono" ou "Cópia Cortesia". Ou seja, espera-se que o destinatário não responda ou atue. Normalmente, pessoal supervisor é notificado com CC.
- Bcc: Significa Cópia Carbono Oculta, refere-se à prática de enviar uma mensagem para vários destinatários de tal forma que o que eles recebem não contém a lista completa de destinatários. Destina-se a notificações ocultas.
- ResponderPara: Este campo de cabeçalho é destinado a indicar onde o remetente deseja que as respostas sejam enviadas.
- Assunto: Título, cabeçalho, assunto. Frequentemente usado como indicador de tema para mensagens que respondem ou comentam sobre outras mensagens.
- Data: Este cabeçalho especifica uma data (e hora). Normalmente, esta é a data em que a mensagem foi composta e enviada.
- XMailer: Informações sobre o software cliente do originador. Exemplo: X-Mailer: Aspose.Email. XMailer é usado por clientes de email. Diferentes clientes de email terão diferentes valores de XMailer. O valor de XMailer do MS Outlook é Microsoft Office Outlook, Build 11.0.5510. É ignorado pelo receptor de email ou leitor de email.

Normalmente, um cabeçalho de email se parece com isto:

``` cs

 Responder-Para: reply@reply.com

De: sender@sender.com

Para: guangzhou@guangzhoo.com

Assunto: email de teste

Data: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

Para personalizar um cabeçalho de email, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
- Especifique Para, De, CC, Bcc, ResponderPara, Assunto, Data e XMailer usando uma instância da classe MailMessage.
- Crie uma instância da classe [MimeHeader](https://reference.aspose.com/email/java/com.aspose.email/mimeheader/) e especifique o cabeçalho secreto.
- Adicione o cabeçalho secreto à instância MailMessage.

No código abaixo, personalizamos um cabeçalho de email.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-SetEmailHeaders.java" >}}

O trecho de código acima produz um cabeçalho de email no seguinte formato. Isso pode ser observado abrindo o arquivo MsgHeaders.msg no Microsoft Outlook e depois visualizando suas propriedades.

``` cs

 Responder-Para: reply@reply.com

De: sender@sender.com

Para: receiver1@receiver.com

CC: receiver2@receiver.com

BCC: receiver3@receiver.com

Assunto: email de teste

Data: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

cabeçalho-secreto: mistério

```

### **Inserir Cabeçalho em Localização Específica**

O método [Add](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#add-com.aspose.email.HeaderCollection-) da Collection de Cabeçalhos insere o cabeçalho no final da coleção. No entanto, pode ser necessário inserir um cabeçalho em uma localização específica. Nesse caso, o método Add não será útil. Para conseguir isso, use o método [Insert](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#insert-java.lang.String-java.lang.String-) da Collection de Cabeçalhos. Se a coleção contiver cabeçalhos com o mesmo nome, este cabeçalho será inserido antes de outros cabeçalhos com o mesmo nome. A seguir está a assinatura do método Insert e um código de amostra para uso.

``` java

 Assinatura do Método

HeaderCollection.insert(String name, String value)

```

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-InsertHeaderAtSpecificLocation.java" >}}

### **Adicionando cabeçalhos personalizados ao email**

Os exemplos de programação abaixo demonstram como especificar um cabeçalho personalizado em uma mensagem de email. Um cabeçalho de email pode ser especificado usando a classe MailMessage. Para especificar um cabeçalho personalizado em uma mensagem de email, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Especifique os valores para, de e assunto usando a instância MailMessage.
1. Adicione o cabeçalho secreto à instância MailMessage.
1. Crie uma instância da classe SmtpClient e envie o email usando o método Send.

O seguinte trecho de código mostra como adicionar cabeçalhos personalizados ao email.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyCustomHeader-SpecifyCustomHeader.java" >}}

## **Assinar Emails com DKIM**

Aspose.Email permite assinar emails com DKIM (DomainKeys Identified Mail). Isso permite que uma organização assuma a responsabilidade por uma mensagem que está em trânsito ([sobre DKIM](https://www.dkim.org/)). DKIM adiciona uma assinatura digital aos cabeçalhos da mensagem de email que pode ser validada pelos destinatários. A chave pública do remetente permite que o receptor verifique se a assinatura corresponde ao conteúdo da mensagem. O método [dKIMSign](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#dKIMSign-com.aspose.ms.System.Security.Cryptography.RSACryptoServiceProvider-com.aspose.email.DKIMSignatureInfo-) da classe MailMessage é utilizado para definir as informações criptográficas e de assinatura para assinar a mensagem. O seguinte trecho de código mostra como assinar emails com DKIM.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SignEmailsWithDKIM-SignEmailsWithDKIM.java" >}}

## **Realizando Mala Direta**

Mala direta ajuda você a criar e enviar um lote de mensagens de email similares. O núcleo dos emails é o mesmo, mas o conteúdo pode ser personalizado. Tipicamente, os detalhes de contato de um destinatário (primeiro nome, sobrenome, empresa e assim por diante) são usados para personalizar o email.

|![todo:image_alt_text](https://i.imgur.com/D7WSp90.png)|
| :- |
|**Figura: Ilustração de como uma mala direta funciona**|

Para realizar uma mala direta com Aspose.Email, siga os seguintes passos:

1. Crie uma função com assinatura de nome
1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Especifique o remetente, destinatário, assunto e corpo.
1. Crie uma assinatura para o final do email.
1. Crie uma instância da classe [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) e passe a instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Obtenha a assinatura na instância [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) .
1. Crie uma instância da classe [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Adicione as colunas Receipt, FirstName e LastName como fontes de dados na classe DataTable.
1. Crie uma instância da classe [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Especifique o endereço de recebimento, primeiro e últimos nomes no objeto DataRow.
1. Crie uma instância da classe [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Especifique as instâncias [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) e DataTable na instância [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
2. Crie uma instância da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) e especifique o servidor, porta, nome de usuário e senha.
3. Envie emails usando o método BulkSendAsync da classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

O código abaixo envia um email para uma pessoa de três outros.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-PerformMailMerge-.java" >}}