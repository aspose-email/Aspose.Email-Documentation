---
title: "Obteniendo información de la bandeja de entrada utilizando el cliente WebDav"
url: /es/java/getting-mailbox-information-using-webdav-client/
weight: 50
type: docs
---

{{% alert color="primary" %}} 

La clase [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) tiene miembros que se pueden usar para obtener información de la bandeja de entrada desde un servidor Exchange llamando al método [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)). Devuelve una instancia del tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Obtenga información de la bandeja de entrada de propiedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) , y [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).

Este artículo muestra cómo acceder a la información de la bandeja de entrada directamente desde un servidor Exchange.

{{% /alert %}} 
## **Obtener información de la bandeja de entrada desde un servidor Exchange**
Para obtener la información de la bandeja de entrada de Exchange:

1. Cree una instancia de la [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Especifique el servidor Exchange, el nombre de usuario, la contraseña y el dominio en el constructor de ExchangeClient.
1. Llame al método [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) para obtener el tamaño de la bandeja de entrada.
1. Llame al método [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) para obtener una instancia de la [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class.
1. Obtenga la información de la bandeja de entrada utilizando las diferentes propiedades de la [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class.

Los códigos de muestra a continuación obtienen información de la bandeja de entrada de Exchange.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}