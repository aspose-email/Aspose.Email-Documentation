---
title: "Trabajar con contactos en Exchange Server mediante WebDAV"
url: /es/net/working-with-contacts-on-exchange-server-using-webdav/
weight: 50
type: docs
---


{{% alert color="primary" %}}

Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [fetching](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [sending](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) and [eliminar mensajes de correo electrónico](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) desde los servidores Exchange, Aspose.Email le permite trabajar con contactos. En este artículo se explica cómo recuperar la información de contacto directamente de un servidor de Exchange. En este artículo también se muestra cómo puede enumerar los contactos de la carpeta Contactos.

{{% /alert %}}
## **Obtener contactos de un servidor Exchange**
The [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class’ [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) este método se puede utilizar para obtener información de contacto de un servidor Exchange. [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) el método requiere el URI de la carpeta Contactos, que se puede obtener fácilmente con el [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.

Para obtener contactos de un servidor Exchange:

1. Inicialice el [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) clase con dirección y credenciales.
1. Obtenga el URI de la carpeta Contactos con el [ExchangeClient.MailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.
1. Llame al [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) método. Devuelve una matriz de [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Haga un bucle para cada bucle en el [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact) matriz para leer la información de contacto.

El siguiente fragmento de código muestra cómo usar [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) clase para leer todos los contactos de un servidor Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}
