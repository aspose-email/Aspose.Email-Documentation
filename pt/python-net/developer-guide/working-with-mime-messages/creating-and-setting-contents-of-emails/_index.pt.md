---
title: "Criando e definindo o conteúdo de E-mails"
url: /pt/python-net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Criar Nova Mensagem de E-mail**
A classe MailMessage representa uma mensagem de e-mail e permite que os desenvolvedores criem novas mensagens de e-mail. Propriedades básicas de e-mail como De, Para, Assunto e corpo podem ser facilmente anexadas à nova mensagem de e-mail criada. Da mesma forma, podemos salvar a mensagem de e-mail em diferentes formatos como EML, MSG e MHTML.

- Crie uma instância da classe MailMessage.
- Defina as propriedades da mensagem de e-mail.
- Salve a mensagem de e-mail em formatos diferentes.

O seguinte trecho de código mostra como criar um novo e-mail com diferentes propriedades.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-CreateNewMailMesssage-CreateNewMailMesssage.py" >}}
## **Especificando Vários Destinatários**
O MailMessage representa uma mensagem de e-mail. Instâncias da classe MailMessage são usadas para construir mensagens de e-mail que são transmitidas a um servidor SMTP usando a classe SmtpClient. Este tópico demonstra como especificar mais de um endereço de e-mail. Endereços de e-mail podem ser especificados usando a classe MailMessage. Os endereços de e-mail usados na classe MailMessage são:

- **Para** - Endereços de destinatários podem ser especificados no campo 'Para'. Os destinatários do campo 'Para' são o público principal da mensagem. Pode haver mais de um endereço de destinatário.
- **Cc** - Cc significa "cópia carbono", ou "cópia de cortesia", e permite adicionar destinatários de e-mail que precisam ver o e-mail, mas que não necessariamente se espera que atuem sobre ele. Gerentes, por exemplo, ou membros de sua equipe que precisam estar cientes de uma conversa. Com Aspose.Email, endereços CC podem ser especificados em seu código. Dessa forma, e-mails automatizados, ou todos os e-mails para um endereço específico, podem ser copiados para o pessoal relevante.
- **Bcc** - Bcc, cópia carbono oculta, permite enviar um e-mail para um destinatário que é oculto de outros destinatários. Onde um CC aparece nas informações do e-mail que os principais destinatários veem, um Bcc não aparece. É destinado a notificações ocultas.

Para especificar vários endereços de e-mail em uma mensagem de e-mail, siga estas etapas:

1. Crie uma instância da classe MailMessage.
2. Especifique os endereços De e múltiplos Para, Cc e Bcc usando a instância MailMessage.
3. Crie uma instância da classe SmtpClient e envie o e-mail usando o método Send.

O exemplo de código abaixo mostra como podem ser especificados múltiplos endereços Para, Cc e Bcc.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SpecifyRecipientAddresses-SpecifyRecipientAddresses.py" >}}
## **Mudando endereços de e-mail para um nome amigável**
Os exemplos de programação abaixo demonstram como alterar endereços de e-mail para nomes amigáveis em uma mensagem de e-mail. Um nome amigável é um nome que é mais fácil de entender do que o endereço de e-mail, por exemplo, John Smith em vez de js346@domain.com. Ao enviar um e-mail, podemos associar um nome amigável a um endereço de e-mail no construtor da classe MailMessage.

Para mudar endereços de e-mail para nomes amigáveis em uma mensagem de e-mail, siga estas etapas:

- Crie uma instância da classe MailMessage e especifique endereços de e-mail nos campos **Para** e **De** junto com nomes amigáveis.
- Especifique os endereços de e-mail Cc e Bcc junto com nomes amigáveis chamando o construtor da classe MailMessage na instância MailMessage.
- Crie uma instância da classe SmtpClient e envie o e-mail usando o método Send.

O seguinte trecho de código mostra como exibir Nomes para endereços de e-mail.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ChangeEmailAddress-ChangeEmailAddress.py" >}}
## **Definir Corpo do E-mail**
A classe MailMessage representa uma mensagem de e-mail. Instâncias da classe MailMessage são usadas para construir mensagens de e-mail que são transmitidas a um servidor SMTP para entrega usando a classe SmtpClient. Um corpo de e-mail pode ser especificado usando a classe MailMessage. Um e-mail pode ter vários corpos. Existem dois tipos de corpos de e-mail na classe MailMessage:

- Corpo HTML
- Corpo de Texto

Além de HtmlBody e TextBody, Aspose.Email possui outras duas propriedades somente leitura relacionadas ao corpo do e-mail:

- IsBodyText: informa ao usuário se o corpo é texto.
- IsBodyHtml: informa ao usuário se o corpo é HTML ou texto simples.

Este artigo mostra como definir texto de corpo em texto simples ou HTML, definir texto alternativo e codificar o corpo do e-mail.
### **Definindo Corpo HTML**
HtmlBody é usado para especificar o conteúdo HTML de um corpo de mensagem. HtmlBody deve estar entre as tags <html> </html>. O seguinte trecho de código mostra como definir o corpo HTML.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SetHTMLBody-SetHTMLBody.py" >}}
### **Definindo Texto Alternativo**
Use a classe AlternateView para especificar cópias de uma mensagem de e-mail em diferentes formatos. Por exemplo, se você enviar uma mensagem em HTML, pode querer também fornecer uma versão em texto simples caso alguns dos destinatários usem leitores de e-mail que não conseguem exibir conteúdo HTML. Esta classe tem duas propriedades, LinkedResources e BaseUri, que são usadas para resolver URLs dentro do conteúdo do e-mail.

- LinkedResources é uma coleção de objetos LinkedResources. Quando renderizado, URLs dentro do conteúdo do e-mail são primeiro correspondidos com os URLs no Link de Conteúdo de cada objeto LinkedResources na coleção LinkedResources, e resolvidos.
- BaseUri é usado pelo leitor de e-mail para resolver URLs relativas dentro do corpo e também para resolver URLs de Link de Conteúdo relativas, na coleção LinkedResources.

O seguinte trecho de código mostra como definir texto alternativo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AlternateText-AlternateText.py" >}}
## **Recursos do MailMessage**
A classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) representa o conteúdo de uma mensagem de e-mail. Instâncias da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) são usadas para construir uma mensagem de e-mail que é transmitida a um servidor SMTP para entrega usando a classe [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient). Este artigo mostra como usar os recursos utilitários da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) para controlar os seguintes recursos do e-mail:

- **Data e hora** - Através da propriedade [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) Date obtemos ou definimos a data e hora de um e-mail.
- **Prioridade da mensagem** - A classe [MailPriority](https://apireference.aspose.com/email/net/aspose.email/mailpriority) especifica níveis de prioridade para o envio de uma mensagem de e-mail. Pode ser baixa, normal ou alta. A prioridade influencia a velocidade de transmissão e entrega.
- **Sensibilidade da mensagem** - A classe [MailSensitivity](https://apireference.aspose.com/email/net/aspose.email/mailsensitivity) especifica cinco níveis de sensibilidade.
- **Notificação de entrega** - Notificações de entrega permitem que os remetentes saibam que o e-mail que enviaram foi entregue na caixa de entrada do destinatário.

Por padrão, a data é a data real em que a mensagem foi enviada, e a hora é o horário em que foi enviada, conforme exibido pelo Microsoft Outlook. No entanto, o real horário de entrega do e-mail é adicionado pelo próprio servidor SMTP no cabeçalho do e-mail. Por exemplo, abaixo está um cabeçalho de e-mail comum, onde Date define o campo Date.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-DateAndTime-DateAndTime.py" >}}

O trecho de código abaixo ilustra como cada um dos recursos discutidos acima pode ser usado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-MailMessageFeatures-MailMessageFeatures.py" >}}
## **Solicitando um Recibo de Leitura**
Os exemplos de programação abaixo mostram como você pode solicitar um recibo de leitura. A classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) propriedade [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) enumera as opções de notificação de entrega para um e-mail. Para solicitar um recibo de leitura após enviar um e-mail, siga estas etapas:

1. Crie uma instância da [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) classe.
2. Especifique o remetente, destinatário e corpo HTML para o e-mail na instância [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
3. Especifique as [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) em outras instâncias [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
4. Crie uma instância da classe [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) e envie o e-mail usando o método Send.

Solicitações de recibo de leitura podem nem sempre ser atendidas porque:

- Um cliente de e-mail pode não implementar essa funcionalidade.
- O usuário final pode ter essa funcionalidade desativada.
- O usuário final pode optar por não enviar um.

O seguinte trecho de código mostra como solicitar um recibo de leitura.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-RequestReadReceipt-RequestReadReceipt.py" >}}
## **Definir Cabeçalhos de E-mail**
Os cabeçalhos de e-mail representam um padrão da Internet e a RFC define campos de cabeçalho que são incluídos em mensagens de e-mail na Internet. Um cabeçalho de e-mail pode ser especificado usando a classe MailMessage. Tipos comuns de cabeçalho são definidos na classe HeaderType. É uma classe selada que funciona como uma enumeração normal.

Normalmente, um cabeçalho de e-mail contém esses campos:

- Para: Endereços de destinatários podem ser especificados no campo **Para**. Os destinatários do campo **Para** são o público primário da mensagem. Pode haver mais de um endereço de destinatário.
- De: Este campo apresenta o endereço de e-mail do remetente da mensagem.
- Cc: Permite que os usuários enviem uma mensagem como "Cópia Carbono" ou "Cópia de Cortesia". Ou seja, espera-se que o receptor não responda ou atue. Normalmente, pessoal de supervisão é notificado com CC.
- Bcc: Significa Cópia Carbono Oculta, refere-se à prática de enviar uma mensagem para múltiplos destinatários de tal forma que o que eles recebem não contenha a lista completa de destinatários. É destinado a notificações ocultas.
- ReplyTo: Este campo de cabeçalho destina-se a indicar onde o remetente deseja que as respostas sejam enviadas.
- Assunto: Título, cabeçalho, assunto. Frequentemente usado como indicador de thread para mensagens que respondem ou comentam sobre outras mensagens.
- Data: Este cabeçalho especifica uma data (e hora). Normalmente, esta é a data em que a mensagem foi composta e enviada.
- XMailer: Informações sobre o software cliente do originador. Exemplo: X-Mailer: Aspose.Email. XMailer é usado por clientes de e-mail. Diferentes clientes de e-mail terão valores XMailer diferentes. O valor XMailer do MS Outlook é Microsoft Office Outlook, Build 11.0.5510. É ignorado pelo receptor de e-mail ou leitor de e-mail.

Normalmente, um cabeçalho de e-mail se parece com isto:

``` cs
 Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Para personalizar um cabeçalho de e-mail, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Especifique To, From, CC, Bcc, ReplyTo, Subject, Date e XMailer usando uma instância da [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Crie uma instância da classe [MimeHeader](https://apireference.aspose.com/email/net/aspose.email.mime/mimeheader) e especifique o cabeçalho secreto.
- Adicione o cabeçalho secreto à instância [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).

O seguinte trecho de código mostra como definir cabeçalhos de e-mail.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SetEmailHeaders-SetEmailHeaders.py" >}}

O trecho de código acima produz um cabeçalho de e-mail no seguinte formato. Isso pode ser observado abrindo o arquivo resultante "MsgHeaders.msg" no Microsoft Outlook e visualizando as Propriedades.

``` cs
 Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
secret-header: mystery
```
### **Inserir Cabeçalho em Localização Específica**
O método [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) da classe [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection) insere o cabeçalho no final da coleção. No entanto, às vezes pode ser necessário inserir um cabeçalho em uma localização específica. Nesse caso, o método [Add](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/add/methods/1) não será útil. Para conseguir isso, use o método [Insert](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/methods/insert) da [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection). Se a coleção contém cabeçalhos com o mesmo nome, este cabeçalho será inserido antes de outros cabeçalhos com o mesmo nome. O seguinte trecho de código mostra como inserir um cabeçalho em uma localização específica.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-InsertHeaderAtSpecificLocation-InsertHeaderAtSpecificLocation.py" >}}
### **Adicionando cabeçalhos personalizados ao e-mail**
Os exemplos de programação abaixo demonstram como especificar um cabeçalho personalizado em uma mensagem de e-mail. Um cabeçalho de e-mail pode ser especificado usando a classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Para especificar um cabeçalho personalizado em uma mensagem de e-mail, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
2. Especifique os valores de para, de e assunto usando a instância MailMessage.
3. Adicione o cabeçalho secreto à instância [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
4. Crie uma instância da classe SmtpClient e envie o e-mail usando o método Send.

O seguinte trecho de código mostra como adicionar cabeçalhos personalizados ao e-mail.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SpecifyCustomHeader-SpecifyCustomHeader.py" >}}