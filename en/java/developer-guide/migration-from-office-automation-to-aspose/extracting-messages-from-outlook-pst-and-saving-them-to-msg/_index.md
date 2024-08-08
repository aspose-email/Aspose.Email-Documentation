---
title: Extracting Messages from Outlook PST and Saving them to MSG
type: docs
weight: 60
url: /java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
---


{{% alert color="primary" %}} 

This migration tip shows how to extract messages from an Outlook PST file and save them to disk as MSG files. It involves several steps:

1. Read the Outlook PST file,
1. extract messages and, finally,
1. save the extracted messages.

There are different ways to achieve the same result: this article compares using VSTO and Aspose.Email. First, are [code samples for using Microsoft Office Interop](#using-microsoft-office-interop) to extract messages from PST. After that example, [code samples show how to use Aspose.Email Outlook](#using-asposeemail), in Java, to perform the same task.

{{% /alert %}} 
## **Using Microsoft Office Interop**
To use Office Automation objects for Microsoft Outlook, add references to Microsoft Office Interop for Outlook libraries to the project. Microsoft Office Outlook must also be installed on the machine that the code runs on. The namespace used in the code sample that follows is Microsoft.Office.Interop.Outlook.
### **Programming Examples**
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
## **Using Aspose.Email**
The following code snippets do the same thing as [the code above](#using-microsoft-office-interop) but uses Aspose.Email. With Aspose.Email for Java installed Microsoft Outlook is no longer needed on the machine. Just reference the Aspose.Email to build and run the project successfully.
### **Programming Samples**

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