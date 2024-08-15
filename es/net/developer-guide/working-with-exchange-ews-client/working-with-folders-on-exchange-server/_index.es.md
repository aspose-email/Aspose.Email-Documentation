---
title: "Trabajar con carpetas en Exchange Server"
url: /es/net/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Listar todas las carpetas del servidor**

La API Aspose.Email ofrece la capacidad de conectarse al servidor Exchange y enumerar todas las carpetas y subcarpetas. También puede recuperar todas las subcarpetas de cada carpeta de forma recursiva. También ofrece la capacidad de enumerar carpetas con paginación desde el cliente de Exchange mediante el servicio web de Exchange (EWS). En este artículo se muestra cómo recuperar todas las subcarpetas del servidor de Exchange y cómo recuperar las carpetas con paginación.

El siguiente fragmento de código muestra cómo enumerar carpetas de Exchange Server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}

## **Obtenga información sobre el tipo de carpeta mediante EWS**

The [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/foldertype/) propiedad proporcionada por [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/) La clase se puede usar para obtener información sobre el tipo de carpeta. Se muestra en el ejemplo de código que aparece a continuación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}

## **Enumeración de carpetas con soporte de paginación mediante EWS**

El siguiente fragmento de código muestra cómo utilizar el soporte de paginación mediante EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}

## **Acceso a las carpetas o subcarpetas personalizadas del buzón**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite a los desarrolladores acceder a cualquier carpeta o subcarpeta personalizada desde el buzón. El [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) función de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) devuelve el URI de una carpeta/subcarpeta personalizada especificada, que se puede usar entonces para acceder a la carpeta de destino. En el ejemplo siguiente, se accede a una carpeta personalizada denominada «TestInbox», que se crea en INBOX, y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, realice los siguientes pasos:

1. Inicialice el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) objetar proporcionando credenciales válidas.
1. Acceda al buzón predeterminado.
1. Acceda a la carpeta principal, que en este ejemplo es INBOX. Esta carpeta principal también puede ser una carpeta personalizada en sí misma.
1. Use [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) para buscar en la subcarpeta personalizada especificada, por ejemplo, «TestInbox». Devolverá el URI de «TestInbox».
1. Usa este Uri para acceder a todos los mensajes de esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a las carpetas o subcarpetas personalizadas de los buzones de correo con EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}

## **Listado de carpetas públicas**

Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. En el siguiente fragmento de código se muestra cómo leer todas las carpetas y subcarpetas públicas, y cómo mostrar y descargar los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}

## **Copiar un mensaje a otra carpeta**

La API Aspose.Email permite copiar un mensaje de una carpeta a otra mediante el [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/#copyitem) método. La versión sobrecargada de este método devuelve el URI único del mensaje copiado, como se muestra en este artículo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}

## **Sincronización de elementos de carpeta**

Aspose.Email para API.NET [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) La interfaz proporciona la función de sincronizar una carpeta de Exchange para su contenido. El [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/syncfolder/#syncfolder/) método expuesto por el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) la clase se puede usar para sincronizar la información de carpetas en una carpeta específica. El siguiente fragmento de código muestra cómo sincronizar la información de la carpeta de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}

## **Recuperación de permisos para carpetas de Exchange**

A los usuarios se les asignan permisos para las carpetas públicas de Exchange Server, lo que limita o determina el nivel de acceso que un usuario tiene a estas carpetas. El [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/) la clase proporciona un conjunto de propiedades de permisos para las carpetas de Exchange, como [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/permissionlevel/), si pueden [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/cancreateitems/), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/deleteitems/)y realizar otras tareas según lo especificado en las propiedades del permiso. Los permisos se pueden recuperar mediante el [GetFolderPermissions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) método de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). En este artículo se muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicialice el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
1. Usa el [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listpublicfolders/#listpublicfolders) para obtener una lista de todas las carpetas públicas
1. Recupere los permisos asociados a una carpeta mediante el [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) method

El siguiente fragmento de código muestra cómo usar el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase para recuperar los permisos aplicados a una carpeta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}

## **Creación de carpetas y subcarpetas**

La API Aspose.Email ofrece la capacidad de crear carpetas en un buzón de Exchange. La [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) método de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) se puede utilizar para este propósito. Para crear una carpeta en el buzón del servidor Exchange, se pueden seguir los pasos siguientes.

1. Crea una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Configure el [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/useslashasfolderseparator/) propiedad según sea necesario. Si se establece en **true**, la aplicación considerará la «barra» como separador de carpetas y la subcarpeta se creará después de la barra.
1. Usa el [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) método para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}

## **Haga copias de seguridad de las carpetas de Exchange en PST**

Suele ocurrir que los usuarios deseen realizar una copia de seguridad de todas o algunas de las carpetas del buzón. Aspose.Email ofrece la posibilidad de realizar una copia de seguridad de todas las carpetas de buzones de correo de Exchange o de las especificadas en un archivo PST. En este artículo se describe cómo realizar copias de seguridad de las carpetas de Exchange en un PST con código de ejemplo. Para realizar la copia de seguridad de las carpetas del servidor Exchange, se pueden seguir los pasos siguientes.

1. Inicie el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) con credenciales de usuario
1. Agregue la información de la carpeta requerida a [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection/)
1. Usuario del cliente [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/backup/#backup/) método para exportar el contenido de la carpeta a PST

El siguiente fragmento de código muestra cómo hacer copias de seguridad de las carpetas de intercambio en PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}
