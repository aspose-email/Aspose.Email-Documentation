---
title: "Trabajando con Contactos en Exchange Server usando WebDav"
url: /es/net/working-with-contacts-on-exchange-server-using-webdav/
weight: 50
type: docs
---


{{% alert color="primary" %}} 

Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [recuperar](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [mover](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [enviar](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) y [eliminar mensajes de correo electrónico](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) de los servidores de Exchange, Aspose.Email te permite trabajar con contactos. Este artículo explica cómo recuperar información de contactos directamente desde un Exchange Server. Este artículo también muestra cómo puedes listar contactos de la carpeta de Contactos.

{{% /alert %}} 
## **Obteniendo Contactos de un Exchange Server**
El método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) de la clase [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) se puede usar para obtener información de contactos de un Exchange Server. El método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) requiere la URI de la carpeta de Contactos, que se puede obtener fácilmente con la propiedad [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).

Para obtener contactos de un Exchange Server:

1. Inicializa la clase [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) con la dirección y credenciales.
1. Obtén la URI de la carpeta de Contactos con la propiedad [ExchangeClient.MailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).
1. Llama al método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts). Devuelve un arreglo de [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Realiza un bucle foreach en el arreglo de [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact) para leer la información del contacto.

El siguiente fragmento de código te muestra cómo usar la clase [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) para leer todos los contactos de un Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}