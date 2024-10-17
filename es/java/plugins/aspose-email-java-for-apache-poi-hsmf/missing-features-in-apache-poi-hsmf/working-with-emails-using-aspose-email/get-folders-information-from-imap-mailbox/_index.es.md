---
title: "Obtener Información de Carpetas desde el Buzón IMAP"
url: /es/java/get-folders-information-from-imap-mailbox/
weight: 10
type: docs
---

## **Aspose.Email - Obtener Información de Carpetas desde el Buzón IMAP**
Obtener información sobre las carpetas de un servidor IMAP es muy fácil con Aspose.Email. El método listFolders() de ImapClient devuelve un objeto de ImapFolderInfoCollection que contiene información sobre todas las carpetas del servidor. Itera a través de esta colección y obtén información sobre carpetas individuales en un bucle. El método está sobrecargado. Puedes pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas.

**Java**

``` java

 ImapClient client = new ImapClient();

client.setHost("--server--"); //imap.secureserver.net,

client.setPort(993);

client.setUsername("--username--");

client.setPassword("--password--");

client.setSecurityOptions(SecurityOptions.Auto);

ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Itera a través de la colección para obtener información de las carpetas una por una

for (ImapFolderInfo folderInfo:folderInfoColl)

{

	// Nombre de la carpeta

	System.out.println("El nombre de la carpeta es: " + folderInfo.getName());

	ImapFolderInfo folderExtInfo = client.listFolder(folderInfo.getName());

	// Nuevos mensajes en la carpeta

	System.out.println("Contador de nuevos mensajes: " + folderExtInfo.getNewMessageCount());

	// Verifica si es de solo lectura

	System.out.println("¿Es de solo lectura? " + folderExtInfo.getReadOnly());

	// Número total de mensajes

	System.out.println("Número total de mensajes: " + folderExtInfo.getTotalMessageCount());

}

```
## **Descargar Código en Ejecución**
Descargar **Obtener Información de Carpetas desde el Buzón IMAP** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)