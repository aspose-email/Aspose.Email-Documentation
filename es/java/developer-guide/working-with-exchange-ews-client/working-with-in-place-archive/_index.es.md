---
title: "Trabajando con In-Place Archive"
url: /es/java/working-with-in-place-archive/
weight: 150
type: docs
---


## **Archivos locales en Office 365**
Los archivos locales de Office 365 proporcionan a los usuarios espacio de almacenamiento adicional. Una vez activados los buzones de archivado, los usuarios pueden acceder a los mensajes y almacenarlos en su buzón de archivado mediante Microsoft Outlook y Outlook en la Web. Cuando el buzón con el archivado local habilitado se abre con Outlook, el buzón de archivo se muestra como un buzón independiente.
## **Mover elementos a un archivo local**
La API Aspose.Email se puede usar para mover elementos al buzón de archivo de los usuarios mediante el [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) method. [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) El método proporciona cuatro sobrecargas que se enumeran a continuación.

- `archiveItem(String sourceFolderUri, Appointment appointment)`
- `archiveItem(String sourceFolderUri, ExchangeTask task)`
- `archiveItem(String sourceFolderUri, MapiMessageItemBase item)`
- `archiveItem(String sourceFolderUri, String uniqueId)`

El ejemplo de código que se muestra a continuación demuestra el uso de [`IEWSClient.archiveItem`](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) método para mover un correo electrónico al buzón de archivo mediante el UniqueURI.



~~~Java
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject:" + msgInfo.getSubject());
    client.archiveItem(client.getMailboxInfo().getInboxUri(), msgInfo.getUniqueUri());
}
client.dispose();
~~~
