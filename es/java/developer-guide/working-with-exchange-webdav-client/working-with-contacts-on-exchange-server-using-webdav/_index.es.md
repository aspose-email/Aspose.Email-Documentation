---
title: "Trabajando con Contactos en Exchange Server usando WebDav"
url: /es/java/working-with-contacts-on-exchange-server-using-webdav/
weight: 120
type: docs
---


{{% alert color="primary" %}} 

Este artículo explica cómo recuperar información de contacto de un Exchange Server directamente. Este artículo también muestra cómo puedes listar contactos desde la carpeta de Contactos.

{{% /alert %}} 
## **Obteniendo Contactos de un Exchange Server**
El método [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) de la clase [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) se puede utilizar para obtener información de contacto de un Exchange Server. El método [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) requiere la URI de la carpeta de Contactos, que se puede obtener fácilmente con la propiedad [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)).

Para obtener contactos de un Exchange Server:

1. Inicializa la clase ExchangeClient con la dirección y las credenciales.
1. Obtén la URI de la carpeta de Contactos con la propiedad ExchangeClient.getMailboxInfo().getContactsUri().
1. Llama al método listContacts(). Este devuelve un array de MapiContact.
1. Realiza un bucle foreach en el array de MapiContact para leer la información de contacto.

El siguiente fragmento de código te muestra cómo usar la clase [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) para leer todos los contactos de un Exchange Server.


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
