---
title: "Работа с папками на Exchange Server"
url: /ru/cpp/working-with-folders-on-exchange-server/
weight: 80
type: docs
---

## **Список всех папок с сервера**
Aspose.Email API предоставляет возможность подключаться к Exchange Server и перечислять все папки и подпапки. Вы также можете рекурсивно получить все подпапки из каждой папки. Кроме того, предоставляется возможность перечисления папок с постраничной навигацией из клиента Exchange с использованием Exchange Web Service (EWS). В этой статье показано, как получить все подпапки с Exchange сервера и извлечь папки с постраничной навигацией.

Следующий фрагмент кода показывает, как перечислить папки с Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Получение информации о типе папки с использованием EWS**
Перечислитель [ExchangeFolderType](https://apireference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f), предоставленный классом [ExchangeFolderInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info), может быть использован для получения информации о типе папки. Это показано в приведенном ниже примере кода.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Перечисление папок с поддержкой постраничной навигации с использованием EWS**
Следующий фрагмент кода показывает, как использовать поддержку постраничной навигации с EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Доступ к пользовательским папкам или подпапкам почтового ящика**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) позволяет разработчикам получать доступ к любой пользовательской папке или подпапке из почтового ящика. Метод [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) возвращает URI заданной пользовательской папки/подпапки, который затем может быть использован для доступа к целевой папке. В следующем примере доступ к пользовательской папке с именем "TestInbox", которая создана в INBOX, осуществляется и все сообщения из этой пользовательской папки отображаются. Для выполнения этой задачи выполняются следующие шаги:

1. Инициализируйте объект [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), предоставив действительные учетные данные.
1. Получите доступ к почтовому ящику по умолчанию.
1. Получите доступ к родительской папке, которая является INBOX в данном примере. Эта родительская папка также может быть пользовательской папкой.
1. Используйте метод [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380), чтобы найти заданную пользовательскую подпапку, например, "TestInbox". Он вернет URI "TestInbox".
1. Используйте этот URI, чтобы получить доступ ко всем сообщениям в этой пользовательской папке.

Следующий фрагмент кода показывает, как получить доступ к пользовательским папкам или подпапкам почтового ящика с EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Список публичных папок**
Microsoft Exchange Server позволяет пользователям создавать публичные папки и отправлять сообщения в них. Для этого используйте класс [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) для подключения к Exchange Server и чтения и загрузки сообщений и публикаций из публичных папок. Следующий фрагмент кода показывает, как читать все публичные папки и подпапки, а также перечислять и загружать любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, так как только они поддерживают EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Синхронизация элементов папки**
Aspose.Email API [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) предоставляет возможность синхронизации папки Exchange для ее содержимого. Метод [SyncFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6), предоставляемый классом [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), может быть использован для синхронизации информации о папке в заданной папке. Следующий фрагмент кода показывает, как синхронизировать информацию о папке Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Получение прав для папок Exchange**
Пользователям назначаются права на публичные папки на Exchange Server, которые ограничивают/определяют уровень доступа пользователя к этим папкам. Класс *ExchangeFolderPermission* предоставляет набор свойств прав для папок Exchange, таких как *уровень прав*, возможность *создания* элементов, удаления элементов и выполнения других задач, определенных свойствами прав. Права можно получить с помощью метода [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Эта статья показывает, как получить права, применяемые к публичной папке для всех пользователей, имеющих доступ к общим папкам.

Чтобы выполнить эту задачу:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Используйте [ListPublicFolders](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296), чтобы получить список всех публичных папок.
1. Извлеките права, связанные с папкой, с помощью метода [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601).

Следующий фрагмент кода показывает, как использовать класс [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) для получения прав, применяемых к папке.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Создание папок и подпапок**
Aspose.Email API предоставляет возможность создавать папки в почтовом ящике Exchange. Метод [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) может быть использован для этой цели. Для создания папки в почтовом ящике Exchange можно использовать следующие шаги.

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Установите свойство [set_UseSlashAsFolderSeparator](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) по мере необходимости. Если установлено в **true**, приложение будет рассматривать "Слэш" как разделитель папок, и подпапка будет создана после слэша.
1. Используйте метод [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) для создания папки.

Следующий фрагмент кода показывает, как создать папки и подпапки.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Резервное копирование папок Exchange в PST**
Часто бывает так, что пользователи хотят сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность создать резервную копию всех или заданных папок почтового ящика Exchange в PST. Чтобы создать резервную копию папок Exchange, можно следовать следующим шагам.

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Добавьте информацию о необходимых папках в [ExchangeFolderInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection).
1. Используйте метод [IEWSClient->Backup](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038), чтобы экспортировать содержимое папки в PST.

Следующий фрагмент кода показывает, как создать резервную копию папок Exchange в PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}