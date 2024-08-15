---
title: "Работа с папками на сервере Exchange"
url: /ru/cpp/working-with-folders-on-exchange-server/
weight: 80
type: docs
---

## **Список всех папок с сервера**
Aspose.Email API предоставляет возможность подключиться к серверу Exchange и вывести список всех папок и подпапок. Вы также можете рекурсивно извлекать все подпапки из каждой папки. Он также предоставляет возможность перечислять папки с разбиением на страницы из клиента Exchange с помощью веб-службы Exchange (EWS). В этой статье показано, как извлечь все подпапки с сервера Exchange и извлечь папки с разбиением на страницы.

В следующем фрагменте кода показано, как вывести список папок с сервера Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Получите информацию о типе папки с помощью EWS**
The [ExchangeFolderType](https://apireference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f) счетчик, предоставленный [ExchangeFolderInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info) класс можно использовать для получения информации о типе папки. Это показано в примере кода ниже.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Перечисление папок с поддержкой пейджинга с помощью EWS**
В следующем фрагменте кода показано, как использовать поддержку пейджинга в EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Доступ к настраиваемым папкам или подпапкам почтового ящика**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) позволяет разработчикам получить доступ к любой настраиваемой папке или подпапке из почтового ящика. [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) возвращает URI указанной настраиваемой папки/подпапки, который затем можно использовать для доступа к целевой папке. В следующем примере открывается настраиваемая папка «TestInbox», созданная в папке INBOX, и отображаются все сообщения из этой настраиваемой папки. Для выполнения этой задачи выполняются следующие шаги:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) возразите, предоставив действительные учетные данные.
1. Получите доступ к почтовому ящику по умолчанию.
1. Откройте родительскую папку, которая в данном примере называется INBOX. Эта родительская папка также может быть пользовательской папкой.
1. Use [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) метод поиска в указанной настраиваемой подпапке, например «TestInbox». Он вернет URI «TestInbox».
1. Используйте этот URI для доступа ко всем сообщениям в этой настраиваемой папке.

В следующем фрагменте кода показано, как получить доступ к настраиваемым папкам или подпапкам почтового ящика с помощью EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Список общедоступных папок**
Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Синхронизация элементов папки**
API Aspose.Email [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) предоставляет возможность синхронизации содержимого папки Exchange. [SyncFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6) метод, представленный [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс можно использовать для синхронизации информации о папке в указанной папке. В следующем фрагменте кода показано, как синхронизировать информацию о папках Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Получение разрешений для папок Exchange**
Пользователям назначаются разрешения на доступ к общедоступным папкам на сервере Exchange, что ограничивает или определяет уровень доступа пользователя к этим папкам. *ExchangeFolderPermission* класс предоставляет набор свойств разрешений для папок Exchange, таких как *уровень разрешений*, могут ли они создавать элементы, удалять элементы и выполнять другие задачи, указанные в свойствах разрешений. Разрешения можно получить с помощью [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). В этой статье показано, как получить разрешения, примененные к общей папке, для всех пользователей, имеющих доступ к общим папкам.

Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Используйте [ListPublicFolders](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296) чтобы получить список всех общедоступных папок
1. Получите разрешения, связанные с папкой, с помощью [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) method

В следующем фрагменте кода показано, как использовать [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс для получения разрешений, примененных к папке.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Создание папок и подпапок**
Aspose.Email API предоставляет возможность создавать папки в почтовом ящике Exchange. [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) можно использовать для этой цели. Чтобы создать папку в почтовом ящике сервера Exchange, можно выполнить следующие шаги.

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Установите [set_UseSlashAsFolderSeparator](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) имущество по мере необходимости. Если установлено значение **true**, приложение будет считать «косую черту» разделителем папок, а вложенная папка будет создана после косой черты.
1. Используйте [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) метод создания папки.

В следующем фрагменте кода показано, как создавать папки и подпапки.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Резервное копирование папок Exchange в PST**
Часто бывает так, что пользователи могут захотеть сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность сделать резервную копию всех или указанных папок почтовых ящиков Exchange в PST. Чтобы сделать резервную копию папок сервера Exchange, можно выполнить следующие шаги.

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Добавьте информацию о нужной папке в [ExchangeFolderInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection)
1. Use [IEWSClient->Backup](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038) метод экспорта содержимого папки в PST

В следующем фрагменте кода показано, как создавать резервные копии папок Exchange в PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}
