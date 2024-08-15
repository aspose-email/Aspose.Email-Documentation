---
title: "Obtención de información de buzones mediante el cliente WebDAV"
url: /es/java/getting-mailbox-information-using-webdav-client/
weight: 50
type: docs
---

{{% alert color="primary" %}}

The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) la clase tiene miembros que se pueden usar para obtener información de buzones de un servidor de Exchange llamando al [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) método. Devuelve una instancia de tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Obtenga información sobre los buzones de correo de propiedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) , y [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).

En este artículo se muestra cómo acceder a la información de los buzones directamente desde un servidor Exchange.

{{% /alert %}}
## **Obtenga información de buzones de correo de un servidor Exchange**
Para obtener la información del buzón de Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Especifique el servidor Exchange, el nombre de usuario, la contraseña y el dominio en el constructor ExchangeClient.
1. Llame al [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) método para obtener el tamaño del buzón.
1. Llame al [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) método para obtener una instancia del [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class.
1. Obtenga la información del buzón de correo mediante el [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) diferentes propiedades de la clase.

Los códigos de ejemplo que aparecen a continuación proporcionan información sobre los buzones de correo de Exchange.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}
