---
title: "Получение информации о папках из почтового ящика IMAP"
url: /ru/java/get-folders-information-from-imap-mailbox/
weight: 10
type: docs
---

## **Aspose.Email - получение информации о папках из почтового ящика IMAP**
С Aspose.Email очень просто получать информацию о папках с сервера IMAP. Метод listFolders () в IMapClient возвращает объект коллекции IMapFolderInfoCollection, содержащий информацию обо всех папках сервера. Просмотрите эту коллекцию и получайте информацию об отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок.

**Java**

``` java

 ImapClient client = new ImapClient();

client.setHost("--server--"); //imap.secureserver.net,

client.setPort(993);

client.setUsername("--username--");

client.setPassword("--password--");

client.setSecurityOptions(SecurityOptions.Auto);

ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Iterate through the collection to get folder info one by one

for (ImapFolderInfo folderInfo:folderInfoColl)

{

	// Folder name

	System.out.println("Folder name is: " + folderInfo.getName());

	ImapFolderInfo folderExtInfo = client.listFolder(folderInfo.getName());

	// New messages in the folder

	System.out.println("New message count: " + folderExtInfo.getNewMessageCount());

	// Check whether its read only

	System.out.println("Is it readonly? " + folderExtInfo.getReadOnly());

	// Total number of messages

	System.out.println("Total number of messages: " + folderExtInfo.getTotalMessageCount());

}

```
## **Загрузить рабочий код**
Download **Получение информации о папках из почтового ящика IMAP** с любого из нижеперечисленных сайтов социального программирования:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
