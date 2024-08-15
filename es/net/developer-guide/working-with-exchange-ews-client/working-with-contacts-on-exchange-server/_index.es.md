---
title: "Trabajar con contactos en Exchange Server"
url: /es/net/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de [fetching](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [eliminar mensajes de correo electrónico](https://docs.aspose.com/email/es/net/working-with-exchange-mailbox-and-messages/#deleting-messages) desde los servidores Exchange, Aspose.Email le permite trabajar con contactos. En este artículo se explica cómo recuperar la información de contacto mediante los servicios web de Exchange. Este artículo también muestra cómo puede enumerar los contactos de la carpeta Contactos o resolver los contactos en función del nombre del contacto. {{% /alert %}}

## **Cómo obtener contactos con EWS**

Aspose.Email proporciona la [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. Los fragmentos de código que aparecen a continuación utilizan los servicios web de Exchange para leer todos los contactos. El siguiente fragmento de código muestra cómo obtener contactos con EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Resolver contactos usando el nombre del contacto**

El siguiente fragmento de código muestra cómo usar get contacts con EWS

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Determinación del formato de las notas de contacto**

El Aspose.Email.Mail.Contact.NotesFormat especifica el tipo de formato de texto de las notas de contactos definido por el enumerador Aspose.Email.TextFormat.

## **Obtener un contacto usando el ID**

Un contacto concreto se puede recuperar del servidor mediante su identificador de contacto, tal y como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Agregar contactos**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) class [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) el método se puede usar para agregar información de contacto a un servidor Exchange. El [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) el método toma un objeto de contacto como parámetro de entrada.

Para agregar contactos a un servidor Exchange:

1. Inicialice el EWSClient con la dirección y las credenciales.
1. Inicialice el objeto Contact con las propiedades deseadas.
1. Llame al método CreateContact para agregar el contacto al servidor Exchange.

Aspose.Email proporciona la [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. Los fragmentos de código muestran cómo usar los servicios web de Exchange para agregar contactos a un servidor de Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Actualización de contactos**

La información de contacto se puede actualizar mediante Microsoft Outlook. Aspose.Email también puede actualizar la información de contacto en Exchange Server mediante el servicio web de Exchange (EWS). El cliente IEWS [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) el método puede actualizar la información de contacto en Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Eliminar contactos**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) la clase permite al DeleteContact acceder y eliminar contactos de una carpeta de contactos de Exchange Server. Este método toma el identificador de contacto o MapiContact como parámetro de entrada.

Para eliminar contactos de un servidor Exchange:

1. Inicialice el ExchangeWebServiceClient con la dirección y las credenciales.
1. Elimina un contacto con su ID.
1. Para eliminar un contacto, llame al [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) método con [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) como parámetro de entrada.

Los siguientes fragmentos de código muestran cómo eliminar contactos de un servidor de Exchange mediante el servicio web de Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Trabajar con las propiedades extendidas de los contactos en Exchange Server**

``` cs

 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

//The required extended properties must be added in order to create or read them from the Exchange Server

string[] extraFields = new string[] {{ "User Field 1", "User Field 2", "User Field 3", "User Field 4" }};

foreach (string extraField in extraFields)

    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Create a test contact on the Exchange Server

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)

    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//retrieve the contact back from the server after some time

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Parse the extended properties of contact

foreach (string extraField in extraFields)

    if (contact.ExtendedProperties.ContainsKey(extraField))

        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());

```
