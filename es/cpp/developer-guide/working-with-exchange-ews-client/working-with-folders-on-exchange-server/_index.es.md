---
title: "Trabajando con Carpetas en Exchange Server"
url: /es/cpp/working-with-folders-on-exchange-server/
weight: 80
type: docs
---

## **Listando todas las Carpetas desde el Servidor**
La API Aspose.Email proporciona la capacidad de conectarse al Exchange Server y listar todas las carpetas y subcarpetas. También puedes recuperar todas las subcarpetas de cada carpeta de forma recursiva. También proporciona la capacidad de enumerar carpetas con paginación desde el cliente de Exchange utilizando Exchange Web Service (EWS). Este artículo muestra cómo recuperar todas las subcarpetas desde el servidor de Exchange y recuperar carpetas con paginación.

El siguiente fragmento de código muestra cómo listar carpetas desde Exchange Server.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Obtener Información del Tipo de Carpeta usando EWS**
El enumerador [ExchangeFolderType](https://apireference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f) proporcionado por la clase [ExchangeFolderInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info) se puede utilizar para obtener información sobre el tipo de carpeta. Esto se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Enumerando Carpetas con Soporte de Paginación usando EWS**
El siguiente fragmento de código muestra cómo usar el soporte de paginación con EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Accediendo a Carpetas Personalizadas o Subcarpetas del Buzón**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite a los desarrolladores acceder a cualquier carpeta personalizada o subcarpeta del buzón. El método [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) devuelve la URI de una carpeta/subcarpeta personalizada especificada, que puede usarse para acceder a la carpeta objetivo. En el siguiente ejemplo, se accede a una carpeta personalizada llamada "TestInbox", que se creó bajo INBOX, y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, se llevan a cabo los siguientes pasos:

1. Inicializa el objeto [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) proporcionando credenciales válidas.
1. Accede al buzón predeterminado.
1. Accede a la carpeta principal, que en este ejemplo es INBOX. Esta carpeta principal también puede ser una carpeta personalizada.
1. Utiliza el método [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) para buscar la subcarpeta personalizada especificada, por ejemplo, "TestInbox". Esto devolverá la URI de "TestInbox".
1. Utiliza esta URI para acceder a todos los mensajes en esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a carpetas personalizadas o subcarpetas del buzón con EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Listando Carpetas Públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacer esto a través de tu aplicación, utiliza la clase [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) para conectarte al Exchange Server y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código muestra cómo leer todas las carpetas y subcarpetas públicas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Sincronizando Elementos de Carpeta**
La API Aspose.Email de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) proporciona la característica de sincronizar una carpeta de Exchange para su contenido. El método [SyncFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6) expuesto por la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) se puede utilizar para sincronizar la información de la carpeta en una carpeta especificada. El siguiente fragmento de código muestra cómo sincronizar la información de la carpeta de Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Recuperando Permisos para Carpetas de Exchange**
Se asignan permisos a los usuarios para las carpetas públicas en Exchange Server, lo que limita/determina el nivel de acceso que un usuario tiene a estas carpetas. La clase *ExchangeFolderPermission* proporciona un conjunto de propiedades de permiso para las carpetas de Exchange, como el *nivel de permiso*, si pueden *crear* elementos, eliminar elementos, y realizar otras tareas según lo especificado por las propiedades de permiso. Los permisos se pueden recuperar usando el método [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Este artículo muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicializa el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Usa el [ListPublicFolders](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296) para obtener una lista de todas las carpetas públicas.
1. Recupera los permisos asociados con una carpeta usando el método [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601).

El siguiente fragmento de código muestra cómo usar la clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para recuperar los permisos aplicados a una carpeta.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Creando Carpetas y Subcarpetas**
La API Aspose.Email proporciona la capacidad de crear carpetas en un buzón de Exchange. El método [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) se puede utilizar para este propósito. Para crear una carpeta en el buzón del servidor Exchange, se pueden seguir los siguientes pasos.

1. Crea una instancia de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Establece la propiedad [set_UseSlashAsFolderSeparator](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) según sea necesario. Si se establece en **true**, la aplicación considerará la "Barra" como separador de carpetas y la subcarpeta se creará después de la barra.
1. Utiliza el método [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Respaldo de Carpetas de Exchange a PST**
A menudo sucede que los usuarios pueden querer hacer una copia de seguridad de todas o algunas de las carpetas del buzón. Aspose.Email proporciona la capacidad de hacer una copia de seguridad de todas o de las carpetas de buzón de Exchange especificadas a un PST. Para hacer una copia de seguridad de las carpetas del servidor Exchange, se pueden seguir los siguientes pasos.

1. Crea una instancia de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Agrega la información de las carpetas requeridas a [ExchangeFolderInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection).
1. Utiliza el método [IEWSClient->Backup](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038) para exportar el contenido de las carpetas a PST.

El siguiente fragmento de código muestra cómo hacer una copia de seguridad de las carpetas de Exchange a PST.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}