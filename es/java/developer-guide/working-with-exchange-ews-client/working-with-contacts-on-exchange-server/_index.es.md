---
title: "Trabajar con contactos en Exchange Server"
url: /es/java/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [fetching](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [eliminar mensajes de correo electrónico](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) desde los servidores Exchange, Aspose.Email le permite trabajar con contactos. En este artículo se explica cómo recuperar la información de contacto mediante los servicios web de Exchange. Este artículo también muestra cómo puede enumerar los contactos de la carpeta Contactos o resolver los contactos en función del nombre del contacto. {{% /alert %}}
## **Cómo obtener contactos con EWS**
Aspose.Email proporciona la [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. Los fragmentos de código que aparecen a continuación utilizan los servicios web de Exchange para leer todos los contactos. El siguiente fragmento de código muestra cómo obtener contactos con EWS.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// List all the contacts
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    MapiContact mapiContact = Contact.to_MapiContact(contact);
    // Display name and email address
    System.out.println("Name: " + mapiContact.getNameInfo().getDisplayName() + "+ Email Address: " + mapiContact.getElectronicAddresses().getEmail1());
}
~~~
## **Resolver contactos usando el nombre del contacto**
El siguiente fragmento de código muestra cómo usar get contacts con EWS



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// List all the contacts
Contact[] contacts = client.resolveContacts("Changed Name", ExchangeListContactsOptions.FetchPhoto);
for (Contact c : contacts) {
    MapiContact contact = Contact.to_MapiContact(c);
    // Display name and email address
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + "+ Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
## **Determinación del formato de las notas de contacto**
El NotesFormat especifica el tipo de formato de texto de las notas de los contactos definido por el enumerador TextFormat.

## **Obtener un contacto usando el ID**
Un contacto concreto se puede recuperar del servidor mediante su identificador de contacto, tal y como se muestra en el siguiente ejemplo de código.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Agregar contactos**
The [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) class [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) el método se puede usar para agregar información de contacto a un servidor Exchange. El [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) el método toma un [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) objeto como parámetro de entrada.

Para agregar contactos a un servidor Exchange:

1. Inicialice el EWSClient con la dirección y las credenciales.
1. Inicialice el objeto Contact con las propiedades deseadas.
1. Llame al método CreateContact para agregar el contacto al servidor Exchange.

Aspose.Email proporciona la [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. Los fragmentos de código muestran cómo usar los servicios web de Exchange para agregar contactos a un servidor de Exchange.



~~~Java
// Set mailboxURI, Username, password, domain information
String mailboxUri = "https://ex2010/ews/exchange.asmx";
String username = "test.exchange";
String password = "pwd";
String domain = "ex2010.local";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Create New Contact
Contact contact = new Contact();

// Set general info
contact.setGender(Gender.Male);
contact.setDisplayName("Frank Lin");
contact.setCompanyName("ABC Co.");
contact.setJobTitle("Executive Manager");
PhoneNumber tmp0 = new PhoneNumber();
tmp0.setNumber("123456789");
tmp0.setCategory(PhoneNumberCategory.getHome());

// Add Phone numbers
contact.getPhoneNumbers().add(tmp0);
AssociatedPerson tmp1 = new AssociatedPerson();
tmp1.setName("Catherine");
tmp1.setCategory(AssociatedPersonCategory.getSpouse());

// contact's associated persons
contact.getAssociatedPersons().add(tmp1);
AssociatedPerson tmp2 = new AssociatedPerson();
tmp2.setName("Bob");
tmp2.setCategory(AssociatedPersonCategory.getChild());
contact.getAssociatedPersons().add(tmp2);
AssociatedPerson tmp3 = new AssociatedPerson();
tmp3.setName("Merry");
tmp3.setCategory(AssociatedPersonCategory.getSister());
contact.getAssociatedPersons().add(tmp3);
Url tmp4 = new Url();
tmp4.setHref("www.blog.com");
tmp4.setCategory(UrlCategory.getBlog());

// URLs
contact.getUrls().add(tmp4);
Url tmp5 = new Url();
tmp5.setHref("www.homepage.com");
tmp5.setCategory(UrlCategory.getHomePage());
contact.getUrls().add(tmp5);
EmailAddress tmp6 = new EmailAddress();
tmp6.setAddress("Frank.Lin@Abc.com");
tmp6.setDisplayName("Frank Lin");
tmp6.setCategory(EmailAddressCategory.getEmail1());

// Set contact's Email address
contact.getEmailAddresses().add(tmp6);

try {
    client.createContact(contact);
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Actualización de contactos**
La información de contacto se puede actualizar mediante Microsoft Outlook. Aspose.Email también puede actualizar la información de contacto en Exchange Server mediante el servicio web de Exchange (EWS). El [IEWSClient's](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) el método puede actualizar la información de contacto en Exchange Server.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// List all the contacts and Loop through all contacts
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Name: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Eliminar contactos**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) la clase proporciona la [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) para acceder a los contactos de la carpeta de contactos de un servidor Exchange y eliminarlos. Este método toma el identificador de contacto como parámetro de entrada.

Para eliminar contactos de un servidor Exchange:

1. Inicialice el ExchangeWebServiceClient con la dirección y las credenciales.
1. Elimina un contacto con su ID.

Los siguientes fragmentos de código muestran cómo eliminar contactos de un servidor de Exchange mediante el servicio web de Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String strContactToDelete = "John Teddy";
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    if (contact.getDisplayName().equals(strContactToDelete))
        client.deleteItem(contact.getId().getEWSId(), DeletionOptions.getDeletePermanently());

}
client.dispose();
~~~