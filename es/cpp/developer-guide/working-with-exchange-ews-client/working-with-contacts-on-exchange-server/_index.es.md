---
title: "Trabajar con contactos en Exchange Server"
url: /es/cpp/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de buscar, mover, enviar y eliminar mensajes de correo electrónico de los servidores Exchange, Aspose.Email te permite trabajar con contactos. En este artículo se explica cómo recuperar la información de contacto mediante los servicios web de Exchange. En este artículo también se muestra cómo puede enumerar los contactos de la carpeta Contactos o resolver los contactos en función del nombre del contacto. {{% /alert %}}
## **Cómo obtener contactos con EWS**
Aspose.Email proporciona la [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. Los fragmentos de código que aparecen a continuación utilizan los servicios web de Exchange para leer todos los contactos. El siguiente fragmento de código muestra cómo obtener contactos con EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Resolver contactos usando el nombre del contacto**
El siguiente fragmento de código muestra cómo obtener contactos con el nombre del contacto.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Determinación del formato de las notas de contacto**
The [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) especifica el tipo de formato de texto de las notas de los contactos definido por [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info) enumerator.
## **Obtener un contacto usando el ID**
Un contacto concreto se puede recuperar del servidor mediante su identificador de contacto, tal y como se muestra en el siguiente ejemplo de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Agregar contactos**
The [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método del [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) la clase se puede usar para agregar información de contacto a un servidor Exchange. El [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) el método toma un [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) objeto como parámetro de entrada.

Para agregar contactos a un servidor Exchange:

1. Inicialice el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) con dirección y credenciales.
1. Inicialice el [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) objeto con las propiedades deseadas.
1. Llame al [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método y pase el contacto para agregarlo al servidor Exchange.

El siguiente fragmento de código muestra cómo agregar contactos al servidor Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Actualización de contactos**
La información de contacto se puede actualizar mediante Microsoft Outlook. Aspose.Email también puede actualizar la información de contacto en Exchange Server mediante el servicio web de Exchange (EWS). El [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) el método puede actualizar la información de contacto en Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Eliminar contactos**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) la clase proporciona la [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para acceder a los contactos de la carpeta de contactos de un servidor Exchange y eliminarlos. Este método toma el identificador de contacto o [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parámetro de entrada.

Para eliminar contactos de un servidor Exchange:

1. Inicialice el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) con dirección y credenciales.
1. Elimina un contacto con su ID.
1. Para eliminar un contacto, llame al [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método con [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parámetro de entrada.

El siguiente fragmento de código muestra cómo eliminar contactos de un servidor de Exchange mediante [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}
