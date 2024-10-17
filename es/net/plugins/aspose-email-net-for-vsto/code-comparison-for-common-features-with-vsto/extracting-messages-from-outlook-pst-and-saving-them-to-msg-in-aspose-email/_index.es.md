---
title: "Extrayendo Mensajes de Outlook PST y Guardándolos en MSG en Aspose.Email"
url: /es/net/extracting-messages-from-outlook-pst-and-saving-them-to-msg-in-aspose-email/
weight: 130
type: docs
---


## **VSTO**
``` cs

 string pstFilePath = "sample.pst";

Outlook.Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");
// Agregar archivo PST (Archivo de Datos de Outlook) al Perfil Predeterminado

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["sample"].GetRootFolder();

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

			// Recuperar el Objeto en MailItem

			MailItem mailItem = item as MailItem;

			Console.WriteLine("Guardando mensaje {0} ....", mailItem.Subject);

			// Guardar el mensaje en el disco en formato MSG

			// TODO: El nombre del archivo puede contener caracteres inválidos [\ / : * ? " < > |]

			mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg", OlSaveAsType.olMSG);

		}

	}

}

// Eliminar el archivo PST del Perfil Predeterminado

outlookNs.RemoveStore(rootFolder);

```
## **Aspose.Email**
``` cs

 string pstFilePath ="sample.pst";

// Crear una instancia de PersonalStorage y cargar el PST desde el archivo

using (PersonalStorage personalStorage = PersonalStorage.FromFile(pstFilePath))

{

	// Obtener la lista de subcarpetas en el archivo PST

	FolderInfoCollection folderInfoCollection = personalStorage.RootFolder.GetSubFolders();

	// Recorrer todas las carpetas en el archivo PST

	// TODO: Esto no es recursivo

	foreach (FolderInfo folderInfo in folderInfoCollection)

	{

		// Obtener todos los mensajes en esta carpeta

		MessageInfoCollection messageInfoCollection = folderInfo.GetContents();

		// Recorrer todos los mensajes en esta carpeta

		foreach (MessageInfo messageInfo in messageInfoCollection)

		{

			// Extraer el mensaje en la instancia MapiMessage

			MapiMessage message = personalStorage.ExtractMessage(messageInfo);

			Console.WriteLine("Guardando mensaje {0} ....", message.Subject);

			// Guardar el mensaje en el disco en formato MSG

			// TODO: El nombre del archivo puede contener caracteres inválidos [\ / : * ? " < > |]

			message.Save(@"\extracted\" + message.Subject + ".msg");

		}

```
## **Descargar Código de Ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772941)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Extract.Messages.from.PST.file.n.Save.in.MSG.Format.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip)