---
title: "Trabalhando com Itens de Calendário no Exchange Server usando WebDav"
url: /pt/net/trabalhando-com-itens-de-calendario-no-exchange-server-usando-webdav/
weight: 40
type: docs
---


## **Enviando Solicitações de Reunião**
Este artigo mostra como enviar uma solicitação de reunião para múltiplos destinatários usando o Microsoft Exchange Server e o Aspose.Email.

1. Crie uma solicitação de reunião usando a classe [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) e defina o local, horário e participantes.
1. Crie uma instância da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) e defina o compromisso usando o método [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview).
1. Conecte-se ao Exchange Server e envie a solicitação de reunião usando o método Send(MailMessage).

Este exemplo usa a classe [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient), que utiliza o protocolo [WebDAV](https://en.wikipedia.org/wiki/WebDAV) para se conectar ao Exchange Server e pode ser usada com qualquer versão do Exchange Server em que o WebDAV esteja habilitado, por exemplo, Exchange 2000, 2003 ou 2007. O seguinte trecho de código mostra como enviar a solicitação de reunião.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}