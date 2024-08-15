---
title: "Extraer mensajes de Outlook PST y guardarlos en MSG"
url: /es/java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
weight: 60
type: docs
---


{{% alert color="primary" %}}

Este consejo de migración muestra cómo extraer mensajes de un archivo PST de Outlook y guardarlos en el disco como archivos MSG. Implica varios pasos:

1. Lea el archivo PST de Outlook,
1. extraer mensajes y, por último,
1. guarde los mensajes extraídos.

Hay diferentes maneras de lograr el mismo resultado: este artículo compara el uso de VSTO y Aspose.Email. En primer lugar, son [ejemplos de código para usar Microsoft Office Interop](#using-microsoft-office-interop) para extraer mensajes de PST. Tras ese ejemplo, [ejemplos de código muestran cómo usar Aspose.Email Outlook](#using-asposeemail), en Java, para realizar la misma tarea.

{{% /alert %}}
## **Uso de Microsoft Office Interop**
Para usar objetos de automatización de oficina para Microsoft Outlook, añada al proyecto referencias a las bibliotecas de Microsoft Office Interop para Outlook. Microsoft Office Outlook también debe estar instalado en la máquina en la que se ejecuta el código. El espacio de nombres utilizado en el ejemplo de código siguiente es Microsoft.Office.Interop.Outlook.
### **Ejemplos de programación**
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
## **Uso de Aspose.Email**
Los siguientes fragmentos de código hacen lo mismo que [el código de arriba](#using-microsoft-office-interop) pero usa Aspose.Email. Con Aspose.Email para Java instalado, Microsoft Outlook ya no es necesario en la máquina. Simplemente consulte el Aspose.Email para crear y ejecutar el proyecto correctamente.
### **Ejemplos de programación**

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