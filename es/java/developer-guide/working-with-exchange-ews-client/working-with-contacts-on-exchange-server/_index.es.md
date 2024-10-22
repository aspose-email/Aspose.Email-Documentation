---
title: "Trabajando con Contactos en Exchange Server"
url: /es/java/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [recuperar](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [mover](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [enviar](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) y [eliminar mensajes de correo electrónico](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) de Exchange Servers, Aspose.Email te permite trabajar con contactos. Este artículo explica cómo recuperar información de contactos utilizando Exchange Web Services. Este artículo también muestra cómo puedes listar contactos de la carpeta de Contactos o resolver contactos según el nombre del contacto. {{% /alert %}} 
## **Obteniendo Contactos con EWS**
Aspose.Email proporciona la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para conectarse a Microsoft Exchange Server utilizando Exchange Web Services. Los fragmentos de código que siguen utilizan Exchange Web Services para leer todos los contactos. El siguiente fragmento de código muestra cómo obtener Contactos con EWS.



~~~Java
// Crear instancia de la clase IEWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Listar todos los contactos
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    MapiContact mapiContact = Contact.to_MapiContact(contact);
    // Mostrar nombre y dirección de correo electrónico
    System.out.println("Nombre: " + mapiContact.getNameInfo().getDisplayName() + "+ Dirección de correo electrónico: " + mapiContact.getElectronicAddresses().getEmail1());
}
~~~
## **Resolver Contactos usando el Nombre del Contacto**
El siguiente fragmento de código muestra cómo usar obtener contactos con EWS



~~~Java
// Crear instancia de la clase IEWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Listar todos los contactos
Contact[] contacts = client.resolveContacts("Nombre Cambiado", ExchangeListContactsOptions.FetchPhoto);
for (Contact c : contacts) {
    MapiContact contact = Contact.to_MapiContact(c);
    // Mostrar nombre y dirección de correo electrónico
    System.out.println("Nombre: " + contact.getNameInfo().getDisplayName() + "+ Dirección de correo electrónico: " + contact.getElectronicAddresses().getEmail1());
}
~~~
## **Determinando el Formato de Notas de Contacto**
El NotesFormat especifica el tipo de formato del texto de notas de los contactos definido por el enumerador TextFormat.

## **Recuperar Contacto usando Id**
Un contacto en particular puede ser recuperado del servidor usando su ID de contacto, como se muestra en el siguiente ejemplo de código.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Añadiendo Contactos**
La clase [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) puede utilizar el método [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) para agregar información de Contacto a un Exchange Server. El método [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) toma un objeto [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) como parámetro de entrada.

Para agregar contactos a un Exchange Server:

1. Inicializa el EWSClient con dirección y credenciales.
1. Inicializa el objeto Contact con las propiedades deseadas.
1. Llama al método CreateContact para agregar el contacto al Exchange Server.

Aspose.Email proporciona la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para conectarse a Microsoft Exchange Server utilizando Exchange Web Services. Los fragmentos de código muestran cómo usar Exchange Web Services para agregar contactos a un Exchange Server.



~~~Java
// Establecer mailboxURI, Nombre de usuario, contraseña, información del dominio
String mailboxUri = "https://ex2010/ews/exchange.asmx";
String username = "test.exchange";
String password = "pwd";
String domain = "ex2010.local";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Crear Nuevo Contacto
Contact contact = new Contact();

// Establecer información general
contact.setGender(Gender.Male);
contact.setDisplayName("Frank Lin");
contact.setCompanyName("ABC Co.");
contact.setJobTitle("Gerente Ejecutivo");
PhoneNumber tmp0 = new PhoneNumber();
tmp0.setNumber("123456789");
tmp0.setCategory(PhoneNumberCategory.getHome());

// Agregar números de teléfono
contact.getPhoneNumbers().add(tmp0);
AssociatedPerson tmp1 = new AssociatedPerson();
tmp1.setName("Catherine");
tmp1.setCategory(AssociatedPersonCategory.getSpouse());

// personas asociadas al contacto
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

// Establecer la dirección de correo electrónico del contacto
contact.getEmailAddresses().add(tmp6);

try {
    client.createContact(contact);
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Actualizando Contactos**
La información de contacto puede actualizarse usando Microsoft Outlook. Aspose.Email también puede actualizar la información de contacto en Exchange Server utilizando los servicios web de Exchange (EWS). El método [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) de [IEWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) puede actualizar la información de contacto en Exchange Server.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Listar todos los contactos y recorrer todos los contactos
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Nombre: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Eliminando Contactos**
La clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) proporciona el método [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) para acceder y eliminar contactos de la carpeta de contactos de un Exchange Server. Este método toma el ID del contacto como parámetro de entrada.

Para eliminar contactos de un Exchange Server:

1. Inicializa el ExchangeWebServiceClient con dirección y credenciales.
1. Elimina un contacto usando su ID.

Los siguientes fragmentos de código te muestran cómo eliminar contactos de un servidor de exchange usando el servicio web de exchange.



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