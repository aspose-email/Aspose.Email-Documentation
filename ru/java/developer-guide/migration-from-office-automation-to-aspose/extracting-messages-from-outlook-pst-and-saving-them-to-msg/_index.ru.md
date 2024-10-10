---
title: "Извлечение сообщений из Outlook PST и сохранение их в MSG"
url: /ru/java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
weight: 60
type: docs
---


{{% alert color="primary" %}} 

Этот совет по миграции показывает, как извлечь сообщения из файла PST Outlook и сохранить их на диске в виде файлов MSG. Это включает несколько этапов:

1. Прочитать файл PST Outlook,
1. извлечь сообщения и, наконец,
1. сохранить извлеченные сообщения.

Существует несколько способов достигнуть того же результата: эта статья сравнивает использование VSTO и Aspose.Email. Сначала идут [примеры кода для использования Microsoft Office Interop](#using-microsoft-office-interop) для извлечения сообщений из PST. После этого примера [примеры кода показывают, как использовать Aspose.Email Outlook](#using-asposeemail), на Java, для выполнения той же задачи.

{{% /alert %}} 
## **Использование Microsoft Office Interop**
Чтобы использовать объекты автоматизации Office для Microsoft Outlook, добавьте ссылки на библиотеки Microsoft Office Interop для Outlook в проект. Microsoft Office Outlook также должен быть установлен на машине, на которой выполняется код. Пространство имен, используемое в следующем примере кода, - Microsoft.Office.Interop.Outlook.
### **Примеры программирования**
**C#**

~~~cs

 string pstFilePath = @"C:\sample.pst";

Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Добавить файл PST (файл данных Outlook) в профиль по умолчанию

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["items"].GetRootFolder();

// Перебирать все папки в файле PST

// TODO: Это не рекурсивно

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

    Items items = folder.Items;

    foreach (object item in items)

    {

        if (item is MailItem)

        {

            // Извлечь объект в MailItem

            MailItem mailItem = item as MailItem;

            Console.WriteLine("Сохранение сообщения {0} ....", mailItem.Subject);

            // Сохранить сообщение на диск в формате MSG

            // TODO: Имя файла может содержать недопустимые символы [\ / : * ? " < > |]

            mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg",OlSaveAsType.olMSG);

        }

    }

}

// Удалить файл PST из профиля по умолчанию

outlookNs.RemoveStore(rootFolder);

~~~
## **Использование Aspose.Email**
Следующие фрагменты кода выполняют то же самое, что и [код выше](#using-microsoft-office-interop), но используют Aspose.Email. При установленном Aspose.Email для Java Microsoft Outlook больше не нужен на машине. Просто укажите Aspose.Email, чтобы успешно собрать и выполнить проект.
### **Примеры программирования**

~~~Java

String pstFilePath = "C:\\sample.pst";

// Создайте экземпляр PersonalStorage и загрузите PST из файла
try (PersonalStorage personalStorage = PersonalStorage.fromFile(pstFilePath)) {
    // Получите список подпапок в файле PST
    FolderInfoCollection folderInfoCollection = personalStorage.getRootFolder().getSubFolders();

    // Перебрать все папки в файле PST
    // Это не рекурсивно
    for (FolderInfo folderInfo : folderInfoCollection) {
        // Получить все сообщения в этой папке
        MessageInfoCollection messageInfoCollection = folderInfo.getContents();

        // Перебрать все сообщения в этой папке
        for (MessageInfo messageInfo : messageInfoCollection) {
            // Извлечь сообщение в экземпляр MapiMessage
            MapiMessage message = personalStorage.extractMessage(messageInfo);

            System.out.println("Сохранение сообщения " + message.getSubject() + " ...");

            // Сохранить сообщение на диск в формате MSG
            // TODO: Имя файла может содержать недопустимые символы [\ / : * ? " < > |]
            message.save("\\extracted\\" + message.getSubject() + ".msg");
        }
    }
}

~~~