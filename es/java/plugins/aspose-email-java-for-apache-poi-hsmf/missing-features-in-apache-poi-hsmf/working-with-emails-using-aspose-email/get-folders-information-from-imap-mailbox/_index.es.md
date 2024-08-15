---
title: "Obtenga información de carpetas del buzón IMAP"
url: /es/java/get-folders-information-from-imap-mailbox/
weight: 10
type: docs
---

## **Aspose.Email: obtenga información de carpetas del buzón IMAP**
Obtener información sobre las carpetas de un servidor IMAP es muy fácil con Aspose.Email. El método listFolders () de ImapClient devuelve un objeto de la colección IMAPFolderInfoCollection que contiene información sobre todas las carpetas del servidor. Recorra esta colección y obtenga información sobre las carpetas individuales de un bucle. El método está sobrecargado. Puede pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas.

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
## **Descargar Running Code**
Download **Obtenga información de carpetas del buzón IMAP** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
