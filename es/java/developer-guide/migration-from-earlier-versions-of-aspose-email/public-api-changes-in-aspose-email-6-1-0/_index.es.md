---
title: "Cambios en la API pública de Aspose.Email 6.1.0"
url: /es/java/public-api-changes-in-aspose-email-6-1-0/
weight: 220
type: docs
---

La siguiente es una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible hacia atrás realizado en Aspose.Email para Java. Si tiene inquietudes sobre algún cambio listado, por favor, plantee su preocupación en el foro de soporte de Aspose.Email.
## **APIs Añadidas**
- Clase `WebDavContactSaveOptions`
- Método `WebDavContactSaveOptions.#ctor`
- Propiedad `WebDavContactSaveOptions.getDefault`

- Clase `MapiContactSaveOptions`
- Método `MapiContactSaveOptions.#ctor`
- Propiedad `MapiContactSaveOptions.getDefault`

- Clase `PipeliningMode`
- Campo/Enum `PipeliningMode.Auto`
- Campo/Enum `PipeliningMode.Disabled`
- Campo/Enum `PipeliningMode.Enabled`

- Clase `PipeliningStatus`
- Método `PipeliningStatus.to_PipeliningStatus(boolean mode)`
- Método `PipeliningStatus.to_PipeliningStatus(int mode)`
- Método `PipeliningStatus.to_Boolean(PipeliningStatus status)`
- Método `PipeliningStatus.to_Boolean()`
- Método `PipeliningStatus.toString`
- Propiedad `PipeliningStatus.getClientMode, setClientMode`
- Propiedad `PipeliningStatus.getPipeliningEnabled`
- Propiedad `PipeliningStatus.getSupportedByServer, setSupportedByServer`

- Campo/Enum `PhoneNumberCategory.PrimaryValue`
- Campo/Enum `MapiPropertyTag.PidTagUrlName`

- Método `IEWSClient.createFolder(String, String)`
- Propiedad `IEWSClient.getUseSlashAsFolderSeparator, setUseSlashAsFolderSeparator`

- Método `Contact.to_MapiContact(Contact contact)`
- Método `Contact.to_Contact(MapiContact contact)`
- Método `Contact.toString`

- Método `MapiAttachmentCollection.remove(MapiAttachment)`

- Método `PersonalStorage.extractAttachments( MessageInfo)`
- Método `PersonalStorage.extractAttachments(String)`
- Método `PersonalStorage.getParentFolder(byte[])`
- Método `PersonalStorage.getParentFolder(SString)`

- Propiedad `AssociatedPerson.getPrefered, setPrefered`
- Propiedad `InstantMessengerAddress.getPrefered, setPrefered`
- Propiedad `ObjectIdentifier.getWebDavId, setWebDavId`
- Propiedad `PhoneNumberCategory.getPrimary, setPrimary`
- Propiedad `Url.getPrefered, setPrefered`
- Propiedad `UrlList.getFtp, setFtp`

- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage)`
- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback,
  Object)`
- Método `SmtpClient.beginForward(String, String, MailMessage)`
- Método `SmtpClient.beginForward(String, String, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(String, String, MailMessage, AsyncCallback, Object)`

- Método `SmtpClient.beginNoop`
- Método `SmtpClient.beginNoop(IConnection)`
- Método `SmtpClient.beginNoop(IConnection, AsyncCallback)`
- Método `SmtpClient.beginNoop(IConnection, AsyncCallback, Object)`
- Método `SmtpClient.beginNoop(AsyncCallback)`
- Método `SmtpClient.beginNoop(AsyncCallback, Object)`

- Método `SmtpClient.beginSend(IConnection, MailMessage)`
- Método `SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginSend(IConnection, MailMessage[])`
- Método `SmtpClient.beginSend(IConnection, String, String, String, String)`
- Método `SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback)`
- Método `SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback, Object)`
- Método `SmtpClient.beginSend(MailMessage)`
- Método `SmtpClient.beginSend(MailMessage, AsyncCallback)`
- Método `SmtpClient.beginSend(MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginSend(MailMessage[])`
- Método `SmtpClient.beginSend(String, String, String, String)`
- Método `SmtpClient.beginSend(String, String, String, String, AsyncCallback)`
- Método `SmtpClient.beginSend(String, String, String, String, AsyncCallback, Object)`

- Método `SmtpClient.endForward(IAsyncResult)`
- Método `SmtpClient.endNoop(IAsyncResult)`
- Método `SmtpClient.endSend(IAsyncResult)`

- Método `SmtpClient.forward(IConnection, String, MailAddressCollection, MailMessage)`
- Método `SmtpClient.forward(IConnection, String, String, MailMessage)`

- Método `SmtpClient.noop`
- Método `SmtpClient.noop(IConnection)`

- Método `SmtpClient.send(IConnection, MailMessage)`
- Método `SmtpClient.send(IConnection, MailMessage[])`
- Método `SmtpClient.send(IConnection, MailMessageCollection)`
- Método `SmtpClient.send(IConnection, IEnumerable)`
- Método `SmtpClient.send(IConnection, String, String, String, String)`
- Método `SmtpClient.send(MailMessage[])`
- Método `SmtpClient.send(MailMessageCollection)`