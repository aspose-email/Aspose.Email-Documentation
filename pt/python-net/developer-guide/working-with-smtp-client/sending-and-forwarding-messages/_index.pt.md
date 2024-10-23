---
title: "Enviando e Encaminhando Mensagens"
url: /pt/python-net/sending-and-forwarding-messages/
weight: 20
type: docs
---


A classe SmtpClient permite que aplicativos enviem e-mails usando o Protocolo Simples de Transferência de Correio (SMTP).

- A classe SmtpClient é a única entrada principal que os desenvolvedores usam para enviar mensagens de correio.
- A classe SmtpClient também fornece outros métodos comuns de entrega de e-mail, incluindo a escrita de mensagens de e-mail no sistema de arquivos, fila de mensagens, etc.
- A classe SmtpClient suporta totalmente esses dois modelos de programação:
  - Síncrono
- A classe SmtpClient também suporta o envio de mensagens como TNEF

Para enviar a mensagem de e-mail e bloquear enquanto aguarda a transmissão do e-mail para o servidor SMTP, use um dos métodos de envio síncronos. Para permitir que o thread principal do seu programa continue executando enquanto o e-mail é transmitido, use um dos métodos assíncronos SendAsync.
## **Enviando E-mails Sincronamente**
Uma mensagem de e-mail pode ser enviada de forma síncrona usando o método Send da classe SmtpClient. Ele envia a mensagem de e-mail especificada através de um servidor SMTP para entrega. O remetente da mensagem, destinatários, assunto e corpo da mensagem são especificados usando objetos String. Para enviar uma mensagem de e-mail de forma síncrona, siga os passos abaixo:

1. Crie uma instância da classe MailMessage e defina suas propriedades.
1. Crie uma instância da classe SmtpClient e especifique o Host, porta, nome de usuário e Senha.
1. Envie a Mensagem usando o método Send da classe SmtpClient e passe a instância MailMessage.

O seguinte trecho de código mostra como enviar e-mails de forma síncrona.

{{% alert color="primary" %}} 

O envio de e-mails de forma assíncrona não é suportado pela API.

{{% /alert %}} 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendEmailsSynchronously-SendEmailsSynchronously.py" >}}

## **Enviando Mensagens Armazenadas no Disco**

Se você precisar enviar programaticamente uma mensagem de e-mail pré-compondo, armazenada no formato EML, use a classe [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) para carregar o arquivo existente e mantê-lo antes do envio. Em seguida, envie-o usando a classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) especificando o nome do host do servidor SMTP, nome de usuário e senha para autenticação. O método 'send' da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) é usado para enviar a mensagem de e-mail. Todo o processo é mostrado no exemplo de código abaixo.

```py
import aspose.email as ae

message = ae.MailMessage.load("test.eml")

# Envie esta mensagem usando SmtpClient
client = ae.clients.SmtpClient("host", "username", "password")
client.send(message)
```

## **Enviando E-mail em Texto Simples**
Os exemplos de programação abaixo mostram como enviar uma mensagem de e-mail em texto simples. A propriedade Body, uma propriedade da classe MailMessage, é usada para especificar o conteúdo em texto simples do corpo da mensagem. Para enviar uma mensagem de e-mail em texto simples, siga estas etapas:

- Crie uma instância da classe MailMessage.
- Especifique os endereços de e-mail do remetente e do destinatário na instância de MailMessage.
- Especifique o conteúdo TextBody, usado para a mensagem em texto simples.
- Crie uma instância da classe SmtpClient e envie o e-mail.

O seguinte trecho de código mostra como enviar um e-mail em texto simples.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingPlainTextMessage-SendingPlainTextMessage.py" >}}
## **Enviando E-mail com corpo HTML**
Os exemplos de programação abaixo mostram como você pode enviar uma mensagem de e-mail HTML simples. O HtmlBody, uma propriedade da classe MailMessage, é usado para especificar o conteúdo HTML do corpo da mensagem. Para enviar um e-mail HTML simples, siga estas etapas:

- Crie uma instância da classe MailMessage.
- Especifique o endereço de e-mail do remetente e do destinatário na instância de MailMessage.
- Especifique o conteúdo HtmlBody.
- Crie uma instância da classe SmtpClient e envie o e-mail usando o método Send.

Para os propósitos deste artigo, o conteúdo HTML do e-mail é rudimentar: <html><body>Este é o corpo HTML</body></html> A maioria dos e-mails HTML será mais complexa. O seguinte trecho de código mostra como enviar e-mail com corpo HTML.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SettingHTMLBody-SettingHTMLBody.py" >}}
## **Enviando E-mail com Texto de Mensagem Alternativo**
Os exemplos de programação abaixo mostram como enviar uma mensagem de e-mail HTML simples com conteúdo alternativo. Use a classe AlternateView para especificar cópias de uma mensagem de e-mail em diferentes formatos. Por exemplo, se você enviar uma mensagem em HTML, talvez também queira fornecer uma versão em texto simples para destinatários que usam leitores de e-mail que não podem exibir conteúdo HTML. Ou, se você estiver enviando um boletim informativo, pode querer fornecer uma cópia em texto simples do texto para aqueles destinatários que escolheram receber uma versão em texto simples. Para enviar um e-mail com texto alternativo, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Especifique os endereços de e-mail do remetente e do destinatário na instância de MailMessage.
1. Crie uma instância da classe AlternateView.

Isso cria uma visualização alternativa para uma mensagem de e-mail usando o conteúdo especificado na string.

1. Adicione a instância da classe AlternateView ao objeto MailMessage.
1. Crie uma instância da classe SmtpClient e envie o e-mail usando o método Send.

O seguinte trecho de código mostra como enviar um e-mail com texto alternativo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SetAlternateText-SetAlternateText.py" >}}
## **Enviando E-mails em Lote**
Enviar e-mails em lote significa enviar um grupo de e-mails em uma única mensagem. Podemos enviar um lote de e-mails usando o método BulkSend da classe SmtpClient:

1. Crie uma instância da classe SmtpClient.
1. Especifique as propriedades da classe SmtpClient.
1. Crie uma instância da classe MailMessage.
1. Especifique o remetente, destinatário, assunto do e-mail e mensagem na instância da classe MailMessage.
1. Repita as duas etapas acima novamente, se você quiser enviar um e-mail para uma pessoa diferente.
1. Crie uma instância da classe MailMessageCollection.
1. Adicione a instância da classe MailMessage ao objeto da classe MailMessageCollection.
1. Agora envie seu e-mail usando o método BulkSend da classe SmtpClient passando a instância da classe MailMessageCollection.

O seguinte trecho de código mostra como enviar e-mails em lote.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingBulkEmails-SendingBulkEmails.py" >}}

## **Enviando E-mails com MultiConnection**

As seguintes propriedades da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) permitem que um cliente utilize várias conexões ao servidor para enviar e-mails. Isso pode ser benéfico em cenários onde o cliente precisa enviar um grande volume de e-mails e deseja distribuir a carga de trabalho entre várias conexões.

- A propriedade 'use_multi_connection' obtém ou define um valor que indica se o cliente deve usar várias conexões para operações com carga pesada.
- A propriedade 'connections_quantity' obtém ou define a quantidade de conexões no modo de múltiplas conexões.
```
Observe que o uso deste modo não levará necessariamente a um aumento de desempenho.
```
O seguinte exemplo de código mostra como implementar esse recurso em um projeto:
```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.send(messages)
```

## **Enviando Mensagem como TNEF**
E-mails TNEF têm formatação especial que pode ser perdida se enviados usando a API padrão. Aspose.Email fornece a capacidade de enviar e-mails como TNEF, preservando assim a formatação. A propriedade UseTnef da classe SmtpClient pode ser configurada para enviar o e-mail como TNEF. O seguinte trecho de código mostra como enviar uma mensagem como TNEF.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendMsgAsTNEF-SendMsgAsTNEF.py" >}}
## **Enviando Solicitações de Reunião**
O Microsoft Outlook oferece funções de calendário, além de gerenciamento de e-mails. Quando um usuário abre um e-mail com um convite para um evento, o Outlook solicita que ele aceite ou rejeite o convite. Aspose.Email permite que os desenvolvedores adicionem funções de calendário aos seus e-mails.
### **Enviando Solicitações por E-mail**
Para enviar solicitações de reunião via e-mail, siga estas etapas:

- Crie uma instância da classe MailMessage.
- Especifique os endereços do remetente e do destinatário usando uma instância da classe MailMessage.
- Inicialize uma instância da classe Appointment e passe os valores.
- Especifique o resumo e a descrição na instância de Calendário.
- Adicione o Calendário à instância de MailMessage e passe a instância de Appointment.

|**Solicitação de reunião iCalendar enviada por e-mail**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
O seguinte trecho de código mostra como enviar solicitações por e-mail.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingMeetingRequestsViaEmail-SendingMeetingRequestsViaEmail.py" >}}
### **Suporte iCalendar para IBM Lotus Notes**
O recurso de calendário do Aspose.Email.Mail é baseado no padrão iCalendar, um padrão para troca de dados de calendário (RFC 2445 ou Referência de Sintaxe RFC2445). Portanto, suporta não apenas o Microsoft Outlook, mas também o IBM Lotus Notes. Para enviar uma solicitação de reunião no Lotus Notes, siga os mesmos passos mencionados acima.
## **Encaminhando um E-mail usando o Cliente SMTP**
### **Encaminhando E-mail com cliente SMTP**
Encaminhar um e-mail é uma prática comum na comunicação digital do dia a dia. Um e-mail recebido pode ser encaminhado para destinatários específicos sem compartilhar com os remetentes originais. A API Aspose.Email's SmtpClient fornece a capacidade de encaminhar um e-mail para destinatários específicos. Seu método Forward pode ser usado para encaminhar um e-mail recebido ou salvo para os destinatários desejados, conforme mostrado neste artigo. O seguinte trecho de código mostra como encaminhar um e-mail usando o Cliente SMTP.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-ForwardEmail-ForwardEmail.py" >}}

### **Encaminhando E-mail sem usar MailMessage**

A API também suporta o encaminhamento de mensagens EML sem precisar primeiro carregá-las na [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class). Isso é útil em casos onde há recursos limitados em termos de memória do sistema.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient(host, smtp_port, username, password, ae.clients.SecurityOptions.AUTO)
file = open("test.eml", "rb")
client.forward(sender, recipients, file)
```