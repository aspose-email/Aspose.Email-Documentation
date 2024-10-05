---
title: "Работа с папками на Exchange Server"
url: /ru/net/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Список всех папок на сервере**

Aspose.Email API предоставляет возможность подключаться к Exchange Server и перечислять все папки и подпапки. Вы также можете рекурсивно получить все подпапки из каждой папки. Также предоставляется возможность перечислять папки с постраничной навигацией из клиента Exchange с использованием Exchange Web Service (EWS). В этой статье показано, как получить все подпапки с Exchange сервера и извлечь папки с постраничной навигацией.

Следующий фрагмент кода показывает, как перечислить папки с Exchange Server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}

## **Получение информации о типе папки с использованием EWS**

Свойство [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/foldertype/) класса [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/) может быть использовано для получения информации о типе папки. Это показано в приведенном ниже примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}

## **Перечисление папок с поддержкой постраничной навигации с использованием EWS**

Следующий фрагмент кода показывает, как использовать поддержку постраничной навигации с использованием EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}

## **Доступ к пользовательским папкам или подпапкам почтового ящика**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) позволяет разработчикам получать доступ к любой пользовательской папке или подпапке из почтового ящика. Функция [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) возвращает URI указанной пользовательской папки/подпапки, который затем может быть использован для доступа к целевой папке. В следующем примере доступ к пользовательской папке с названием "TestInbox", созданной в INBOX, и отображаются все сообщения из этой пользовательской папки. Для выполнения этой задачи выполните следующие шаги:

1. Инициализируйте объект [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) , предоставив действительные учетные данные.
1. Доступ к папке по умолчанию.
1. Доступ к родительской папке, которая в этом примере является INBOX. Эта родительская папка также может быть пользовательской папкой.
1. Используйте [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) для поиска указанной пользовательской подпапки, например "TestInbox". Это вернет URI "TestInbox".
1. Используйте этот URI для доступа ко всем сообщениям в этой пользовательской папке.

Следующий фрагмент кода показывает, как получить доступ к пользовательским папкам или подпапкам почтового ящика с EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}

## **Список открытых папок**

Microsoft Exchange Server позволяет пользователям создавать публичные папки и размещать сообщения в них. Для этого через ваше приложение используйте класс Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) для подключения к Exchange Server и чтения и загрузки сообщений и публикаций из публичных папок. Следующий фрагмент кода показывает, как прочитать все публичные папки и подпапки и перечислить и загрузить любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 и выше, так как только они поддерживают EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}

## **Копирование сообщения в другую папку**

Aspose.Email API позволяет копировать сообщение из одной папки в другую с использованием метода [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/#copyitem). Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}

## **Синхронизация элементов папки**

Aspose.Email for .NET API интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) предоставляет возможность синхронизации папки Exchange с ее содержимым. Метод [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/syncfolder/#syncfolder/) класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) может быть использован для выполнения синхронизации информации по указанной папке. Следующий фрагмент кода показывает, как синхронизировать информацию о папке Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}

## **Получение разрешений для папок Exchange**

Пользователям назначаются разрешения для публичных папок на Exchange Server, которые ограничивают/определяют уровень доступа пользователя к этим папкам. Класс [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/) предоставляет набор свойств разрешений для папок Exchange, таких как [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/permissionlevel/), могут ли они [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/cancreateitems/), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/deleteitems/), и выполнять другие задачи, как указано в свойствах разрешения. Разрешения могут быть получены с помощью метода [GetFolderPermissions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Эта статья показывает, как получить разрешения, примененные к публичной папке для всех пользователей, которые имеют доступ к общим папкам.

Чтобы выполнить эту задачу:

1. Инициализируйте [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
1. Используйте [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listpublicfolders/#listpublicfolders), чтобы получить список всех публичных папок
1. Извлеките разрешения, связанные с папкой, с помощью метода [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions)

Следующий фрагмент кода показывает, как использовать класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) для получения разрешений, примененных к папке.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}

## **Создание папок и подпапок**

Aspose.Email API предоставляет возможность создавать папки в почтовом ящике Exchange. Метод [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) можно использовать для этой цели. Для создания папки в почтовом ящике Exchange можно использовать следующие шаги.

1. Создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Установите свойство [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/useslashasfolderseparator/) по мере необходимости. Если установлено в **true**, приложение будет рассматривать "Slash" как разделитель папок, и подпапка будет создана после косой черты.
1. Используйте метод [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/), чтобы создать папку.

Следующий фрагмент кода показывает, как создавать папки и подпапки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}

## **Резервное копирование папок Exchange в PST**

Часто бывает так, что пользователи могут захотеть сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность резервного копирования всех или определенных папок почтового ящика Exchange в PST. Эта статья описывает резервное копирование папок Exchange в PST с примером кода. Чтобы сделать резервную копию папок Exchange сервера, можно следовать следующим шагам.

1. Инициализируйте [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) с учетными данными пользователя
1. Добавьте информацию о требуемой папке в [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection/)
1. Используйте метод [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/backup/#backup/) клиента для экспорта содержимого папки в PST

Следующий фрагмент кода показывает, как резервировать папки exchange в PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}