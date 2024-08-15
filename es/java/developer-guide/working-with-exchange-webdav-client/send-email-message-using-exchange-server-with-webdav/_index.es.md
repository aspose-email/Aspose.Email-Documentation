---
title: "Enviar un mensaje de correo electrónico mediante Exchange Server con WebDAV"
url: /es/java/send-email-message-using-exchange-server-with-webdav/
weight: 100
type: docs
---

Puede enviar mensajes de correo electrónico mediante un servidor de Exchange con la ayuda de las herramientas de com.aspose.email. El [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) el método acepta un [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) instancia como parámetro y envía el correo electrónico. En este artículo se explica cómo enviar mensajes de correo electrónico mediante un cliente de Exchange de la API.
## **Enviar mensajes de correo electrónico mediante Exchange WebDAV**
Para enviar correos electrónicos mediante un servidor Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Crea una instancia del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.
1. Especifique el origen, el destino, el asunto y otros [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) properties.
1. Llame al [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) método para enviar el correo electrónico.

El código de ejemplo que aparece a continuación envía mensajes de correo electrónico mediante Exchange Server.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}
