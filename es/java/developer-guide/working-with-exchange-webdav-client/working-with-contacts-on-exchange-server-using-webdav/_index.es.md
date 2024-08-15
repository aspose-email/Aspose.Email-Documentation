---
title: "Trabajar con contactos en Exchange Server mediante WebDAV"
url: /es/java/working-with-contacts-on-exchange-server-using-webdav/
weight: 120
type: docs
---


{{% alert color="primary" %}}

En este artículo se explica cómo recuperar la información de contacto directamente de un servidor Exchange. En este artículo también se muestra cómo puede enumerar los contactos de la carpeta Contactos.

{{% /alert %}}
## **Obtener contactos de un servidor Exchange**
The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) class’ [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) este método se puede utilizar para obtener información de contacto de un servidor Exchange. [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) el método requiere el URI de la carpeta Contactos, que se puede obtener fácilmente con el [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)) property.

Para obtener contactos de un servidor Exchange:

1. Inicialice la clase ExchangeClient con la dirección y las credenciales.
1. Obtenga el URI de la carpeta Contactos con la propiedad ExchangeClient.getMailboxInfo () .getContactsUri ().
1. Llama al método listContacts (). Devuelve una matriz de MAPIContact.
1. Realice un bucle para cada uno de los bucles de la matriz MAPIContact para leer la información de contacto.

El siguiente fragmento de código muestra cómo usar [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) clase para leer todos los contactos de un servidor Exchange.


~~~Java
String mailboxURI = "http://ex2003/exchange/administrator"; // WebDAV
String username = "administrator";
String password = "pwd";
String domain = "domain.local";

// Credentials for connecting to Exchange Server
NetworkCredential credential = new NetworkCredential(username, password, domain);
ExchangeClient client = new ExchangeClient(mailboxURI, credential);

// List all the contacts
MapiContact[] contacts = client.listContacts(client.getMailboxInfo().getContactsUri());
for (MapiContact contact : contacts)
{
    // Display name and email address
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + ", Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
