---
title: "Extrayendo Mensajes de Outlook PST y Guardándolos como MSG"
url: /es/java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
weight: 60
type: docs
---


{{% alert color="primary" %}} 

Este consejo de migración muestra cómo extraer mensajes de un archivo PST de Outlook y guardarlos en disco como archivos MSG. Implica varios pasos:

1. Leer el archivo PST de Outlook,
1. extraer mensajes y, finalmente,
1. guardar los mensajes extraídos.

Hay diferentes maneras de lograr el mismo resultado: este artículo compara el uso de VSTO y Aspose.Email. Primero, hay [ejemplos de código para usar Microsoft Office Interop](#using-microsoft-office-interop) para extraer mensajes de PST. Después de ese ejemplo, [ejemplos de código muestran cómo usar Aspose.Email Outlook](#using-asposeemail), en Java, para realizar la misma tarea.

{{% /alert %}} 
## **Usando Microsoft Office Interop**
Para utilizar objetos de automatización de Office para Microsoft Outlook, agregue referencias a las bibliotecas de Microsoft Office Interop para Outlook al proyecto. Microsoft Office Outlook también debe estar instalado en la máquina donde se ejecuta el código. El espacio de nombres utilizado en el ejemplo de código que sigue es Microsoft.Office.Interop.Outlook.
### **Ejemplos de Programación**
**C#**

~~~cs

 string pstFilePath = @"C:\sample.pst";

Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Agregar el archivo PST (Archivo de Datos de Outlook) al Perfil Predeterminado

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["items"].GetRootFolder();

// Recorrer todas las carpetas en el archivo PST

// TODO: Esto no es recursivo

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

    Items items = folder.Items;

    foreach (object item in items)

    {

        if (item is MailItem)

        {

            // Recuperar el objeto en MailItem

            MailItem mailItem = item as MailItem;

            Console.WriteLine("Guardando mensaje {0} ....", mailItem.Subject);

            // Guardar el mensaje en disco en formato MSG

            // TODO: El nombre del archivo puede contener caracteres inválidos [\ / : * ? " < > |]

            mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg",OlSaveAsType.olMSG);

        }

    }

}

// Eliminar el archivo PST del Perfil Predeterminado

outlookNs.RemoveStore(rootFolder);

~~~
## **Usando Aspose.Email**
Los siguientes fragmentos de código hacen lo mismo que [el código anterior](#using-microsoft-office-interop) pero utilizan Aspose.Email. Con Aspose.Email para Java instalado, Microsoft Outlook ya no es necesario en la máquina. Simplemente haga referencia a Aspose.Email para compilar y ejecutar el proyecto con éxito.
### **Ejemplos de Programación**

~~~Java

String pstFilePath = "C:\\sample.pst";

// Crear una instancia de PersonalStorage y cargar el PST desde el archivo
try (PersonalStorage personalStorage = PersonalStorage.fromFile(pstFilePath)) {
    // Obtener la lista de subcarpetas en el archivo PST
    FolderInfoCollection folderInfoCollection = personalStorage.getRootFolder().getSubFolders();

    // Recorrer todas las carpetas en el archivo PST
    // Esto no es recursivo
    for (FolderInfo folderInfo : folderInfoCollection) {
        // Obtener todos los mensajes en esta carpeta
        MessageInfoCollection messageInfoCollection = folderInfo.getContents();

        // Recorrer todos los mensajes en esta carpeta
        for (MessageInfo messageInfo : messageInfoCollection) {
            // Extraer el mensaje en una instancia de MapiMessage
            MapiMessage message = personalStorage.extractMessage(messageInfo);

            System.out.println("Guardando mensaje " + message.getSubject() + " ...");

            // Guardar el mensaje en disco en formato MSG
            // TODO: El nombre del archivo puede contener caracteres inválidos [\ / : * ? " < > |]
            message.save("\\extracted\\" + message.getSubject() + ".msg");
        }
    }
}

~~~