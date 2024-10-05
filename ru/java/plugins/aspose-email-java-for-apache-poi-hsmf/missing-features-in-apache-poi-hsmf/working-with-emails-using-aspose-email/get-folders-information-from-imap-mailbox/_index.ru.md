---
title: "Получение информации о папках из почтового ящика IMAP"
url: /ru/java/get-folders-information-from-imap-mailbox/
weight: 10
type: docs
---

## **Aspose.Email - Получение информации о папках из почтового ящика IMAP**
Получить информацию о папках с IMAP-сервера очень легко с помощью Aspose.Email. Метод listFolders() класса ImapClient возвращает объект ImapFolderInfoCollection, который содержит информацию обо всех папках сервера. Перебирайте эту коллекцию и получайте информацию о отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок.

**Java**

``` java

 ImapClient client = new ImapClient();

client.setHost("--server--"); //imap.secureserver.net,

client.setPort(993);

client.setUsername("--username--");

client.setPassword("--password--");

client.setSecurityOptions(SecurityOptions.Auto);

ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Перебираем коллекцию, чтобы получить информацию о папках одну за другой

for (ImapFolderInfo folderInfo:folderInfoColl)

{

	// Имя папки

	System.out.println("Имя папки: " + folderInfo.getName());

	ImapFolderInfo folderExtInfo = client.listFolder(folderInfo.getName());

	// Новые сообщения в папке

	System.out.println("Количество новых сообщений: " + folderExtInfo.getNewMessageCount());

	// Проверяем, является ли она только для чтения

	System.out.println("Это только для чтения? " + folderExtInfo.getReadOnly());

	// Общее количество сообщений

	System.out.println("Общее количество сообщений: " + folderExtInfo.getTotalMessageCount());

}

```
## **Скачать исполняющий код**
Скачайте **Получение информации о папках из почтового ящика IMAP** с любого из нижеупомянутых сайтов социального программирования:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)