---
title: "Trabajando con Contactos en Exchange Server"
url: /es/net/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [recuperar](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [mover](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#moving-messages), [enviar](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) y [eliminar mensajes de correo electrónico](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#deleting-messages) de los servidores de Exchange, Aspose.Email te permite trabajar con contactos. Este artículo explica cómo recuperar información de contacto usando Exchange Web Services. Este artículo también muestra cómo puedes listar contactos de la carpeta de Contactos o resolver contactos basados en el nombre del contacto. {{% /alert %}}

## **Obteniendo Contactos con EWS**

Aspose.Email proporciona la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para conectarse a Microsoft Exchange Server utilizando Exchange Web Services. Los fragmentos de código que siguen utilizan Exchange Web Services para leer todos los contactos. El siguiente fragmento de código te muestra cómo obtener contactos con EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Resolver Contactos usando el Nombre del Contacto**

El siguiente fragmento de código te muestra cómo obtener contactos con EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Determinar el Formato de Notas del Contacto**

El formato de notas de Aspose.Email.Mail.Contact.NotesFormat especifica el tipo de formato de texto de las notas de contacto definido por el enumerador Aspose.Email.TextFormat.

## **Recuperar Contacto usando Id**

Un contacto en particular puede ser recuperado del servidor usando su id de contacto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Agregar Contactos**

La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) puede utilizar el método [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) para agregar información de contacto a un Exchange Server. El método [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) recibe un objeto Contact como parámetro de entrada.

Para agregar contactos a un Exchange Server:

1. Inicializa el EWSClient con dirección y credenciales.
1. Inicializa el objeto Contact con las propiedades deseadas.
1. Llama al método CreateContact para agregar el contacto al Exchange Server.

Aspose.Email proporciona la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) para conectarse a Microsoft Exchange Server utilizando Exchange Web Services. Los fragmentos de código te muestran cómo utilizar Exchange Web Services para agregar contactos a un Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Actualizar Contactos**

La información del contacto puede ser actualizada usando Microsoft Outlook. Aspose.Email también puede actualizar la información del contacto en Exchange Server usando el servicio web de Exchange (EWS). El método IEWSClient [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) puede actualizar la información del contacto en Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Eliminar Contactos**

La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) permite que el método DeleteContact acceda y elimine contactos de la carpeta de contactos de un Exchange Server. Este método toma el ID del contacto o MapiContact como parámetro de entrada.

Para eliminar contactos de un Exchange Server:

1. Inicializa el ExchangeWebServiceClient con dirección y credenciales.
1. Elimina un contacto usando su ID.
1. Elimina un contacto llamando al método [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) con [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) como parámetro de entrada.

Los siguientes fragmentos de código te muestran cómo eliminar contactos de un servidor de intercambio utilizando el servicio web de intercambio.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Trabajando con Propiedades Extendidas de Contactos en Exchange Server**

``` cs
 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

//Las propiedades extendidas requeridas deben ser añadidas para poder crearlas o leerlas desde el Exchange Server

string[] extraFields = new string[] {{ "Campo de Usuario 1", "Campo de Usuario 2", "Campo de Usuario 3", "Campo de Usuario 4" }};

foreach (string extraField in extraFields)
    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Crear un contacto de prueba en el Exchange Server

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)
    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//recuperar el contacto de nuevo del servidor después de algún tiempo

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Parsear las propiedades extendidas del contacto

foreach (string extraField in extraFields)
    if (contact.ExtendedProperties.ContainsKey(extraField))
        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());
```