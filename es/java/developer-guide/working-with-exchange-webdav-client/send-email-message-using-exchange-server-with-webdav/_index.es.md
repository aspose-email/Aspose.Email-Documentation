---
title: "Enviar mensaje de correo electrónico utilizando Exchange Server con WebDav"
url: /es/java/send-email-message-using-exchange-server-with-webdav/
weight: 100
type: docs
---

Puedes enviar mensajes de correo electrónico utilizando un Exchange Server con la ayuda de las herramientas en com.aspose.email. El método [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) acepta una instancia de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) como parámetro y envía el correo electrónico. Este artículo explica cómo enviar mensajes de correo electrónico utilizando un cliente de Exchange de la API.
## **Enviar mensajes de correo electrónico utilizando Exchange WebDav**
Para enviar correos electrónicos utilizando un Exchange Server:

1. Crea una instancia de la clase [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Especifica el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Crea una instancia de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Especifica el de, para, asunto y otras propiedades de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Llama al método [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) para enviar el correo electrónico.

El código de muestra a continuación envía mensajes de correo electrónico utilizando Exchange Server.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}