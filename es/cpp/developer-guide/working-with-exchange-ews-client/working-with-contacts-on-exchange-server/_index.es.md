---
title: "Trabajando con Contactos en Exchange Server"
url: /es/cpp/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} Las cuentas de Exchange Server contienen más que solo mensajes de correo electrónico. Además de recuperar, mover, enviar y eliminar mensajes de correo electrónico de los servidores de Exchange, Aspose.Email te permite trabajar con contactos. Este artículo explica cómo recuperar información de contacto utilizando Exchange Web Services. Este artículo también muestra cómo puedes listar contactos desde la carpeta de Contactos o resolver contactos en función del nombre del contacto. {{% /alert %}} 
## **Obteniendo Contactos con EWS**
Aspose.Email proporciona la [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase para conectarse a Microsoft Exchange Server utilizando Exchange Web Services. Los fragmentos de código que siguen utilizan Exchange Web Services para leer todos los contactos. El siguiente fragmento de código muestra cómo obtener Contactos con EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Resolver Contactos utilizando el Nombre del Contacto**
El siguiente fragmento de código muestra cómo obtener contactos utilizando el nombre del contacto.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Determinar el Formato de Notas del Contacto**
El [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) especifica el tipo de formato de texto de las notas de los contactos definido por el enumerador [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info).
## **Obtener Contacto utilizando el Id**
Un contacto específico se puede recuperar del servidor utilizando su id de contacto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Agregar Contactos**
El método [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) de la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) se puede utilizar para agregar información de contacto a un Exchange Server. El método [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) toma un objeto [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parámetro de entrada.

Para agregar contactos a un Exchange Server:

1. Inicializa el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) con la dirección y las credenciales.
1. Inicializa el [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) con las propiedades deseadas.
1. Llama al método [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) y pasa el contacto a agregar al Exchange Server.

El siguiente fragmento de código demuestra cómo agregar contactos al Exchange Server.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Actualizar Contactos**
La información del contacto se puede actualizar utilizando Microsoft Outlook. Aspose.Email también puede actualizar la información del contacto en el Exchange Server utilizando el Servicio Web de Exchange (EWS). El método [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) puede actualizar información del contacto en el Exchange Server.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Eliminar Contactos**
La clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) proporciona el [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para acceder y eliminar contactos de la carpeta de contactos de un Exchange Server. Este método toma el ID del contacto o [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parámetro de entrada.

Para eliminar contactos de un Exchange Server:

1. Inicializa el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) con la dirección y las credenciales.
1. Elimina un contacto usando su ID.
1. Elimina un contacto llamando al método [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) con [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parámetro de entrada.

El siguiente fragmento de código te muestra cómo eliminar contactos de un servidor de intercambio utilizando [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}