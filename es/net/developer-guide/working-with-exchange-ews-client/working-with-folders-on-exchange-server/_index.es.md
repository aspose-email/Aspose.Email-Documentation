---
title: "Trabajando con Carpetas en Exchange Server"
url: /es/net/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Listado de todas las Carpetas del Servidor**

Aspose.Email API proporciona la capacidad de conectarse al Exchange Server y listar todas las carpetas y subcarpetas. También puedes recuperar todas las subcarpetas de cada carpeta de manera recursiva. También ofrece la capacidad de enumerar carpetas con paginación desde el cliente de Exchange utilizando Exchange Web Service (EWS). Este artículo muestra cómo recuperar todas las subcarpetas del servidor Exchange y recuperar carpetas con paginación.

El siguiente fragmento de código muestra cómo listar carpetas desde el Exchange Server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}

## **Obtener Información del Tipo de Carpeta usando EWS**

La propiedad [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/foldertype/) proporcionada por la clase [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/) puede ser utilizada para obtener información sobre el tipo de carpeta. Se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}

## **Enumerando Carpetas con Soporte de Paginación usando EWS**

El siguiente fragmento de código muestra cómo usar el soporte de paginación utilizando EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}

## **Accediendo a Carpetas o Subcarpetas Personalizadas del Buzón**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite a los desarrolladores acceder a cualquier carpeta o subcarpeta personalizada del buzón. La función [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) devuelve el URI de una carpeta/subcarpeta personalizada especificada, que se puede usar para acceder a la carpeta de destino. En el siguiente ejemplo, se accede a una carpeta personalizada llamada "TestInbox", que se crea bajo INBOX, y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, sigue los siguientes pasos:

1. Inicializa el objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) proporcionando credenciales válidas.
1. Accede al buzón predeterminado.
1. Accede a la carpeta principal, que es INBOX en este ejemplo. Esta carpeta principal también puede ser una carpeta personalizada.
1. Usa [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) para buscar la subcarpeta personalizada especificada, por ejemplo "TestInbox". Esto devolverá el URI de "TestInbox".
1. Usa este URI para acceder a todos los mensajes en esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a carpetas o subcarpetas personalizadas del buzón con EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}

## **Listado de Carpetas Públicas**

Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de tu aplicación, utiliza la clase Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para conectarte al Exchange Server y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código muestra cómo leer todas las carpetas públicas y subcarpetas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos soportan EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}

## **Copiar un Mensaje a Otra Carpeta**

Aspose.Email API permite copiar un mensaje de una carpeta a otra carpeta utilizando el método [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/#copyitem). La versión sobrecargada de este método devuelve el URI Único del mensaje copiado como se muestra en este artículo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}

## **Sincronizando Elementos de Carpeta**

Aspose.Email para .NET API [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface proporciona la funcionalidad de sincronizar una carpeta de Exchange por su contenido. El método [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/syncfolder/#syncfolder/) expuesto por la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/) puede ser utilizado para realizar la sincronización de información de carpeta en una carpeta especificada. El siguiente fragmento de código muestra cómo sincronizar la información de la carpeta de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}

## **Recuperando Permisos para Carpetas de Exchange**

A los usuarios se les asignan permisos a carpetas públicas en Exchange Server, lo que limita/determina el nivel de acceso que un usuario tiene a estas carpetas. La clase [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/) proporciona un conjunto de propiedades de permisos para carpetas de Exchange tales como el [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/permissionlevel/), si pueden [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/cancreateitems/), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/deleteitems/), y realizar otras tareas según lo especificado por las propiedades de permiso. Los permisos pueden ser recuperados utilizando el método [GetFolderPermissions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/). Este artículo muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicializa el [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/ewsclient/).
1. Usa el [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/listpublicfolders/#listpublicfolders) para obtener una lista de todas las carpetas públicas.
1. Recupera los permisos asociados con una carpeta utilizando el método [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/getfolderpermissions/#getfolderpermissions).

El siguiente fragmento de código muestra cómo usar la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/ewsclient/) para recuperar los permisos aplicados a una carpeta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}

## **Creando Carpetas y Subcarpetas**

Aspose.Email API proporciona la capacidad de crear carpetas en un buzón de Exchange. El método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/) puede ser utilizado para este propósito. Para crear una carpeta en el buzón del servidor Exchange, se pueden seguir los siguientes pasos.

1. Crea una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Establece la propiedad [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/useslashasfolderseparator/) según sea necesario. Si se establece en **true**, la aplicación considerará la "Barra" como separador de carpetas y la subcarpeta se creará después de la barra.
1. Usa el método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}

## **Respaldar Carpetas de Exchange a PST**

A menudo sucede que los usuarios pueden querer hacer una copia de seguridad de todas o algunas de las carpetas del buzón. Aspose.Email proporciona la capacidad de hacer una copia de seguridad de todas o de las carpetas de buzón de Exchange especificadas a un PST. Este artículo describe cómo hacer una copia de seguridad de carpetas de Exchange a un PST con código de muestra. Para hacer la copia de seguridad de las carpetas del servidor Exchange, se pueden seguir los siguientes pasos.

1. Inicia el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) con las credenciales del usuario.
1. Agrega la información de la carpeta requerida a [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection/).
1. Usa el método [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/backup/#backup/) del cliente para exportar el contenido de la carpeta a PST.

El siguiente fragmento de código muestra cómo respaldar carpetas de Exchange a PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}