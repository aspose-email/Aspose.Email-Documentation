---
title: Извлечение сообщений из Outlook PST и сохранение их в MSG в Aspose.Email
type: docs
weight: 130
url: /net/extracting-messages-from-outlook-pst-and-saving-them-to-msg-in-aspose-email/
---


## **VSTO**
``` cs

 string pstFilePath = "sample.pst";

Outlook.Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Добавление PST файла (файла данных Outlook) в профиль по умолчанию

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["sample"].GetRootFolder();

// Проход по всем папкам в PST файле

// TODO: Это не рекурсивно

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

	Items items = folder.Items;

	foreach (object item in items)

	{

		if (item is MailItem)

		{

			// Получение объекта в MailItem

			MailItem mailItem = item as MailItem;

			Console.WriteLine("Сохранение сообщения {0} ....", mailItem.Subject);

			// Сохранение сообщения на диск в формате MSG

			// TODO: Имя файла может содержать недопустимые символы [\ / : * ? " < > |]

			mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg", OlSaveAsType.olMSG);

		}

	}

}

// Удаление PST файла из профиля по умолчанию

outlookNs.RemoveStore(rootFolder);

```
## **Aspose.Email**
``` cs

 string pstFilePath ="sample.pst";

// Создание экземпляра PersonalStorage и загрузка PST из файла

using (PersonalStorage personalStorage = PersonalStorage.FromFile(pstFilePath))

{

	// Получение списка подпапок в PST файле

	FolderInfoCollection folderInfoCollection = personalStorage.RootFolder.GetSubFolders();

	// Проход по всем папкам в PST файле

	// TODO: Это не рекурсивно

	foreach (FolderInfo folderInfo in folderInfoCollection)

	{

		// Получение всех сообщений в этой папке

		MessageInfoCollection messageInfoCollection = folderInfo.GetContents();

		// Цикл через все сообщения в этой папке

		foreach (MessageInfo messageInfo in messageInfoCollection)

		{

			// Извлечение сообщения в экземпляр MapiMessage

			MapiMessage message = personalStorage.ExtractMessage(messageInfo);

			Console.WriteLine("Сохранение сообщения {0} ....", message.Subject);

			// Сохранение сообщения на диск в формате MSG

			// TODO: Имя файла может содержать недопустимые символы [\ / : * ? " < > |]

			message.Save(@"\extracted\" + message.Subject + ".msg");

		}

```
## **Скачать пример кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772941)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Extract.Messages.from.PST.file.n.Save.in.MSG.Format.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip)
