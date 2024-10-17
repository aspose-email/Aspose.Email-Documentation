---
title: "Trabajando con Archivos In-Place"
url: /es/java/working-with-in-place-archive/
weight: 150
type: docs
---


## **Archivos In-Place en Office 365**
Los archivos In-Place en Office 365 proporcionan a los usuarios un espacio de almacenamiento adicional. Después de que los buzones de archivo se activan, los usuarios pueden acceder y almacenar mensajes en su Buzón de Archivo utilizando Microsoft Outlook y Outlook en la Web. Cuando el buzón con la activación In-Place habilitada se abre con Outlook, el buzón de archivo se muestra como un buzón separado.
## **Mover Elementos al Archivo In-Place**
La API de Aspose.Email se puede utilizar para mover elementos al buzón de archivo del usuario utilizando el [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) método. El método [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) ofrece cuatro sobrecargas que se enumeran a continuación.

- `archiveItem(String sourceFolderUri, Appointment appointment)`
- `archiveItem(String sourceFolderUri, ExchangeTask task)`
- `archiveItem(String sourceFolderUri, MapiMessageItemBase item)`
- `archiveItem(String sourceFolderUri, String uniqueId)`

El ejemplo de código dado a continuación demuestra el uso del [`IEWSClient.archiveItem`](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) método para mover un correo electrónico al Buzón de Archivo utilizando el UniqueUri.



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