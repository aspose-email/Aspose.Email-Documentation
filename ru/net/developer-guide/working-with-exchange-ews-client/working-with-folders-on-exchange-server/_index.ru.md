---
title: "Работа с папками на сервере Exchange"
url: /ru/net/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Список всех папок с сервера**

Aspose.Email API предоставляет возможность подключиться к серверу Exchange и вывести список всех папок и подпапок. Вы также можете рекурсивно извлекать все подпапки из каждой папки. Он также предоставляет возможность перечислять папки с разбиением на страницы из клиента Exchange с помощью веб-службы Exchange (EWS). В этой статье показано, как извлечь все подпапки с сервера Exchange и извлечь папки с разбиением на страницы.

В следующем фрагменте кода показано, как вывести список папок с сервера Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}

## **Получите информацию о типе папки с помощью EWS**

The [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/foldertype/) имущество, предоставленное [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/) класс можно использовать для получения информации о типе папки. Это показано в примере кода ниже.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}

## **Перечисление папок с поддержкой пейджинга с помощью EWS**

В следующем фрагменте кода показано, как использовать поддержку пейджинга в EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}

## **Доступ к настраиваемым папкам или подпапкам почтового ящика**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) позволяет разработчикам получить доступ к любой настраиваемой папке или подпапке из почтового ящика. [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) функция [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) возвращает URI указанной настраиваемой папки/подпапки, который затем можно использовать для доступа к целевой папке. В следующем примере открывается настраиваемая папка «TestInbox», созданная в папке INBOX, и отображаются все сообщения из этой настраиваемой папки. Для выполнения этой задачи выполните следующие шаги:

1. Инициализируйте [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) возразите, предоставив действительные учетные данные.
1. Получите доступ к почтовому ящику по умолчанию.
1. Откройте родительскую папку, которая в данном примере называется INBOX. Эта родительская папка также может быть пользовательской папкой.
1. Use [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) для поиска в указанной настраиваемой подпапке, например «TestInbox». Он вернет URI «TestInbox».
1. Используйте этот Uri для доступа ко всем сообщениям в этой настраиваемой папке.

В следующем фрагменте кода показано, как получить доступ к настраиваемым папкам или подпапкам почтового ящика с помощью EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}

## **Список общедоступных папок**

Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}

## **Скопируйте сообщение в другую папку**

Aspose.Email API позволяет копировать сообщение из одной папки в другую с помощью [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/#copyitem) метод. Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}

## **Синхронизация элементов папки**

Aspose.Электронная почта для API.NET [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) интерфейс предоставляет возможность синхронизации содержимого папки Exchange. [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/syncfolder/#syncfolder/) метод, представленный [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) класс можно использовать для синхронизации информации о папках в указанной папке. В следующем фрагменте кода показано, как синхронизировать информацию о папках Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}

## **Получение разрешений для папок Exchange**

Пользователям назначаются разрешения на доступ к общедоступным папкам на сервере Exchange, что ограничивает или определяет уровень доступа пользователя к этим папкам. [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/) класс предоставляет набор свойств разрешений для папок Exchange, таких как [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/permissionlevel/), могут ли они [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/cancreateitems/), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/deleteitems/), а также выполняйте другие задачи, указанные в свойствах разрешения. Разрешения можно получить с помощью [GetFolderPermissions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) метод [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). В этой статье показано, как получить разрешения, примененные к общей папке, для всех пользователей, имеющих доступ к общим папкам.

Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
1. Используйте [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listpublicfolders/#listpublicfolders) чтобы получить список всех общедоступных папок
1. Получите разрешения, связанные с папкой, с помощью [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) method

В следующем фрагменте кода показано, как использовать [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс для получения разрешений, примененных к папке.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}

## **Создание папок и подпапок**

Aspose.Email API предоставляет возможность создавать папки в почтовом ящике Exchange. [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) метод [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) можно использовать для этой цели. Чтобы создать папку в почтовом ящике сервера Exchange, можно выполнить следующие шаги.

1. Создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Установите [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/useslashasfolderseparator/) имущество по мере необходимости. Если установлено значение **true**, приложение будет считать «косую черту» разделителем папок, а вложенная папка будет создана после косой черты.
1. Используйте [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) метод создания папки.

В следующем фрагменте кода показано, как создавать папки и подпапки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}

## **Резервное копирование папок Exchange в PST**

Часто бывает так, что пользователи могут захотеть сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность сделать резервную копию всех или указанных папок почтовых ящиков Exchange в PST. В этой статье описывается резервное копирование папок Exchange в PST с образцом кода. Чтобы создать резервную копию папок сервера Exchange, можно выполнить следующие шаги.

1. Инициируйте [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) с учетными данными пользователя
1. Добавьте информацию о нужной папке в [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection/)
1. Пользователь — клиент [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/backup/#backup/) метод экспорта содержимого папки в PST

В следующем фрагменте кода показано, как создавать резервные копии папок Exchange в PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}
