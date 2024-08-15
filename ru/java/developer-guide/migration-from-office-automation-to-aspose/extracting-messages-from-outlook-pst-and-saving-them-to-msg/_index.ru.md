---
title: "Извлечение сообщений из Outlook PST и сохранение их в формате MSG"
url: /ru/java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
weight: 60
type: docs
---


{{% alert color="primary" %}}

В этом совете по миграции показано, как извлечь сообщения из файла Outlook PST и сохранить их на диске в виде файлов MSG. Это включает в себя несколько этапов:

1. Прочитайте файл Outlook PST,
1. извлеките сообщения и, наконец,
1. сохраните извлеченные сообщения.

Существуют разные способы достижения одного и того же результата: в этой статье сравнивается использование VSTO и Aspose.Email. Во-первых, это [примеры кода для использования Microsoft Office Interop](#using-microsoft-office-interop) для извлечения сообщений из PST. После этого примера [примеры кода показывают, как использовать Aspose.Email Outlook](#using-asposeemail), на Java, для выполнения той же задачи.

{{% /alert %}}
## **Использование интерфейса Microsoft Office**
Чтобы использовать объекты автоматизации делопроизводства для Microsoft Outlook, добавьте в проект ссылки на библиотеки Microsoft Office Interop для Outlook. Microsoft Office Outlook также должен быть установлен на компьютере, на котором работает код. В приведенном ниже примере кода используется пространство имен Microsoft.Office.Interop.Outlook.
### **Примеры программирования**
**C#**

~~~cs

 string pstFilePath = @"C:\sample.pst";

Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Add PST file (Outlook Data File) to Default Profile

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["items"].GetRootFolder();

// Traverse through all folders in the PST file

// TODO: This is not recursive

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

    Items items = folder.Items;

    foreach (object item in items)

    {

        if (item is MailItem)

        {

            // Retrieve the Object into MailItem

            MailItem mailItem = item as MailItem;

            Console.WriteLine("Saving message {0} ....", mailItem.Subject);

            // Save the message to disk in MSG format

            // TODO: File name may contain invalid characters [\ / : * ? " < > |]

            mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg",OlSaveAsType.olMSG);

        }

    }

}

// Remove PST file from Default Profile

outlookNs.RemoveStore(rootFolder);

~~~
## **Использование Aspose.Email**
Следующие фрагменты кода делают то же самое, что и [приведенный выше код](#using-microsoft-office-interop) но использует Aspose.Email. После установки Aspose.Email для Java Microsoft Outlook больше не требуется на компьютере. Просто обратитесь к Aspose.Email, чтобы успешно создать и запустить проект.
### **Примеры программирования**

~~~Java

String pstFilePath = "C:\\sample.pst";

// Create an instance of PersonalStorage and load the PST from file
try (PersonalStorage personalStorage = PersonalStorage.fromFile(pstFilePath)) {
    // Get the list of subfolders in PST file
    FolderInfoCollection folderInfoCollection = personalStorage.getRootFolder().getSubFolders();

    // Traverse through all folders in the PST file
    // This is not recursive
    for (FolderInfo folderInfo : folderInfoCollection) {
        // Get all messages in this folder
        MessageInfoCollection messageInfoCollection = folderInfo.getContents();

        // Loop through all the messages in this folder
        for (MessageInfo messageInfo : messageInfoCollection) {
            // Extract the message in MapiMessage instance
            MapiMessage message = personalStorage.extractMessage(messageInfo);

            System.out.println("Saving message " + message.getSubject() + " ...");

            // Save the message to disk in MSG format
            // TODO: File name may contain invalid characters [\ / : * ? " < > |]
            message.save("\\extracted\\" + message.getSubject() + ".msg");
        }
    }
}

~~~