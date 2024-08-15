---
title: "Trabajar con carpetas en Exchange Server"
url: /es/cpp/working-with-folders-on-exchange-server/
weight: 80
type: docs
---

## **Listar todas las carpetas del servidor**
La API Aspose.Email ofrece la capacidad de conectarse al servidor Exchange y enumerar todas las carpetas y subcarpetas. También puede recuperar todas las subcarpetas de cada carpeta de forma recursiva. También ofrece la capacidad de enumerar carpetas con paginación desde el cliente de Exchange mediante el servicio web de Exchange (EWS). En este artículo se muestra cómo recuperar todas las subcarpetas del servidor de Exchange y cómo recuperar las carpetas con paginación.

El siguiente fragmento de código muestra cómo enumerar carpetas de Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Obtenga información sobre el tipo de carpeta mediante EWS**
The [ExchangeFolderType](https://apireference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f) enumerador proporcionado por [ExchangeFolderInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info) La clase se puede usar para obtener información sobre el tipo de carpeta. Esto es como se muestra en el ejemplo de código siguiente.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Enumeración de carpetas con soporte de paginación mediante EWS**
El siguiente fragmento de código muestra cómo usar la compatibilidad con la paginación con EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Acceso a las carpetas o subcarpetas personalizadas del buzón**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite a los desarrolladores acceder a cualquier carpeta o subcarpeta personalizada desde el buzón. El [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) método de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) devuelve el URI de una carpeta/subcarpeta personalizada especificada, que se puede usar entonces para acceder a la carpeta de destino. En el ejemplo siguiente, se accede a una carpeta personalizada denominada «TestInbox», que se crea en INBOX, y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, se llevan a cabo los siguientes pasos:

1. Inicialice el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) objetar proporcionando credenciales válidas.
1. Acceda al buzón predeterminado.
1. Acceda a la carpeta principal, que en este ejemplo es INBOX. Esta carpeta principal también puede ser una carpeta personalizada en sí misma.
1. Use [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) método para buscar en la subcarpeta personalizada especificada, por ejemplo, «TestInbox». Devolverá el URI de «TestInbox».
1. Usa este URI para acceder a todos los mensajes de esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a las carpetas o subcarpetas personalizadas de los buzones de correo con EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Listado de carpetas públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice el [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. En el siguiente fragmento de código se muestra cómo leer todas las carpetas y subcarpetas públicas, y cómo mostrar y descargar los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Sincronización de elementos de carpeta**
API de Aspose.Email [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) proporciona la función de sincronizar una carpeta de Exchange para su contenido. El [SyncFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6) método expuesto por el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) la clase se puede usar para sincronizar la información de la carpeta en una carpeta específica. El siguiente fragmento de código muestra cómo sincronizar la información de la carpeta de intercambio.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Recuperación de permisos para carpetas de Exchange**
A los usuarios se les asignan permisos para las carpetas públicas de Exchange Server, lo que limita o determina el nivel de acceso que un usuario tiene a estas carpetas. El *ExchangeFolderPermission* la clase proporciona un conjunto de propiedades de permisos para las carpetas de Exchange, como *nivel de permiso*, si pueden crear elementos, eliminar elementos y realizar otras tareas según lo especificado en las propiedades del permiso. Los permisos se pueden recuperar mediante el [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) método de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). En este artículo se muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicialice el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Usa el [ListPublicFolders](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296) para obtener una lista de todas las carpetas públicas
1. Recupere los permisos asociados a una carpeta mediante el [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) method

El siguiente fragmento de código muestra cómo usar el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) clase para recuperar los permisos aplicados a una carpeta.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Creación de carpetas y subcarpetas**
La API Aspose.Email ofrece la capacidad de crear carpetas en un buzón de Exchange. La [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) método de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) se puede utilizar para este propósito. Para crear una carpeta en el buzón del servidor Exchange, se pueden seguir los pasos siguientes.

1. Crea una instancia de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Configure el [set_UseSlashAsFolderSeparator](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) propiedad según sea necesario. Si se establece en **true**, la aplicación considerará la «barra» como separador de carpetas y la subcarpeta se creará después de la barra.
1. Usa el [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) método para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Haga copias de seguridad de las carpetas de Exchange en PST**
Suele ocurrir que los usuarios deseen realizar una copia de seguridad de todas o algunas de las carpetas del buzón. Aspose.Email ofrece la posibilidad de realizar una copia de seguridad de todas las carpetas de buzones de correo de Exchange o de las especificadas en un archivo PST. Para realizar una copia de seguridad de las carpetas del servidor Exchange, se pueden seguir los pasos siguientes.

1. Crea una instancia de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Agregue la información de la carpeta requerida a [ExchangeFolderInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection)
1. Use [IEWSClient->Backup](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038) método para exportar el contenido de la carpeta a PST

El siguiente fragmento de código muestra cómo hacer copias de seguridad de las carpetas de intercambio en PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}
