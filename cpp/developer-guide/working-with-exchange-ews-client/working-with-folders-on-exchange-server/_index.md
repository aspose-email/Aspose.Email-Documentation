---
title: Working with Folders on Exchange Server
type: docs
weight: 80
url: /cpp/working-with-folders-on-exchange-server/
---

## **Listing all Folders from Server**
Aspose.Email API provides the capability to connect to the Exchange Server and list all the folders and sub-folders. You can also retrieve all the sub-folders from each folder recursively. It also provides the capability to enumerate folders with paging from the Exchange client using Exchange Web Serice (EWS). This article shows how to retrieve all the sub-folders from the Exchange server and retrieve folders with pagination.

The following code snippet shows you how to List folders from Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Get Folder Type Information using EWS**
The [ExchangeFolderType](https://reference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f) enumerator provided by [ExchangeFolderInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info) class can be used to get information about the type of the folder. This is as shown in the code sample below.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Enumerating Folders with Paging Support using EWS**
The following code snippet shows you how to use paging support with EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Accessing Mailbox Custom Folders or Subfolders**
[IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) lets developers access any custom folder or subfolder from the mailbox. The [FolderExists()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) method of [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) returns the URI of a specified custom folder/sub-folder, which can be used then to access the target folder. In the following example, a custom folder named "TestInbox", which is created under INBOX is accessed and all the messages are displayed from this custom folder. To perform this task, the following steps are performed:

1. Initialize the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) object by providing valid credentials.
1. Access the default mailbox.
1. Access the parent folder, which is INBOX in this example. This parent folder can also be a custom folder itself.
1. Use [FolderExists()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) method to search the specified custom subfolder, for example, "TestInbox". It will return the URI of "TestInbox".
1. Use this URI to access all the messages in that custom folder.

The following code snippet shows you how to access mailbox custom folders or subfolders with EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Listing Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use the [EWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to reads all public folders and subfolders, and list and download any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Synching Folder Items**
Aspose.Email API's [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) provides the feature of syncing an Exchange folder for its contents. The [SyncFolder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6) method exposed by the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class can be used to sync folder information on a specified folder. The following code snippet shows you how to sync exchange folder information.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Retrieving Permissions for Exchange Folders**
Users are assigned permissions to public folders on Exchange Server, which limits/determine the level of access a user has to these folders. The *ExchangeFolderPermission* class provides a set of permission properties for Exchange folders such as the *permission level*, whether they can create items, deleting items, and perform other tasks as specified by the permission properties. Permissions can be retrieved using the [GetFolderPermissions()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) method of [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). This article shows how to retrieve the permissions applied to a public folder for all the users who have access to the shared folders.

To perform this task:

1. Initialize the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Use the [ListPublicFolders](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296) to get a list of all public folders
1. Retrieve the permissions associated with a folder using the [GetFolderPermissions()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) method

The following code snippet shows you how to use the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class to retrieve permissions applied to a folder.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Creating Folders and Sub-Folders**
Aspose.Email API provides the capability to create folders in an Exchange mailbox. The [CreateFolder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) method of [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) can be used for this purpose. In order to create a folder in the Exchange server mailbox, the following steps can be used.

1. Create an instance of [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Set the [set_UseSlashAsFolderSeparator](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) property as required. If set to **true**, the application will consider the "Slash" as folder separator and the subfolder will be created after the slash.
1. Use the [CreateFolder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) method to create the folder.

The following code snippet shows you how to create folders and sub-Folders.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Backup Exchange Folders to PST**
It often so happens that users may want to take a backup of all or some of the mailbox folders. Aspose.Email provides the capability to take a backup of all or specified Exchange mailbox folders to a PST. In order to take a backup of Exchange server folders, the following steps may be followed.

1. Create an instance of [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Add the required folder's info to [ExchangeFolderInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection)
1. Use [IEWSClient->Backup](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038) method to export the folder's contents to PST

The following code snippet shows you how to backup exchange folders to PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}
