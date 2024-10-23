---
title: "Enviando Solicitações de Reunião com Exchange Server usando WebDav"
url: /pt/java/sending-meeting-requests-with-exchange-server-using-webdav/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

Este artigo mostra como enviar uma solicitação de reunião para vários destinatários usando Microsoft Exchange Server e Aspose.Email. Ele também explica como ajustar o código para trabalhar com os Serviços Web do Exchange.

{{% /alert %}} 
## **Enviar Solicitações de Reunião usando Web Dav**
Para enviar uma solicitação de reunião:

1. Crie uma solicitação de reunião usando a [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment) classe e defina o local, horário e participantes.
1. Crie uma instância da [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) classe e defina a consulta usando o [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)) método.
1. Conecte-se ao Exchange Server e envie a solicitação de reunião usando o [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)) método.

Este exemplo usa a [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient) classe, que utiliza o [WebDAV](http://en.wikipedia.org/wiki/WebDAV) protocolo para se conectar ao Exchange Server e pode ser usado com qualquer versão do Exchange Server em que o WebDAV esteja habilitado, por exemplo, Exchange 2000, 2003 ou 2007.

Os trechos de código usados para enviar a solicitação de reunião estão dados abaixo:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}