---
title: "Mudanças na API Pública no Aspose.Email 6.1.0"
url: /pt/java/public-api-changes-in-aspose-email-6-1-0/
weight: 220
type: docs
---

A seguir, uma lista de quaisquer alterações feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer mudança não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre qualquer alteração listada, por favor, levante a questão no fórum de suporte do Aspose.Email.
## **APIs Adicionadas**
- Classe `WebDavContactSaveOptions`
- Método `WebDavContactSaveOptions.#ctor`
- Propriedade `WebDavContactSaveOptions.getDefault`

- Classe `MapiContactSaveOptions`
- Método `MapiContactSaveOptions.#ctor`
- Propriedade `MapiContactSaveOptions.getDefault`

- Classe `PipeliningMode`
- Campo/Enum `PipeliningMode.Auto`
- Campo/Enum `PipeliningMode.Disabled`
- Campo/Enum `PipeliningMode.Enabled`

- Classe `PipeliningStatus`
- Método `PipeliningStatus.to_PipeliningStatus(boolean mode)`
- Método `PipeliningStatus.to_PipeliningStatus(int mode)`
- Método `PipeliningStatus.to_Boolean(PipeliningStatus status)`
- Método `PipeliningStatus.to_Boolean()`
- Método `PipeliningStatus.toString`
- Propriedade `PipeliningStatus.getClientMode, setClientMode`
- Propriedade `PipeliningStatus.getPipeliningEnabled`
- Propriedade `PipeliningStatus.getSupportedByServer, setSupportedByServer`

- Campo/Enum `PhoneNumberCategory.PrimaryValue`
- Campo/Enum `MapiPropertyTag.PidTagUrlName`

- Método `IEWSClient.createFolder(String, String)`
- Propriedade `IEWSClient.getUseSlashAsFolderSeparator, setUseSlashAsFolderSeparator`

- Método `Contact.to_MapiContact(Contact contact)`
- Método `Contact.to_Contact(MapiContact contact)`
- Método `Contact.toString`

- Método `MapiAttachmentCollection.remove(MapiAttachment)`

- Método `PersonalStorage.extractAttachments( MessageInfo)`
- Método `PersonalStorage.extractAttachments(String)`
- Método `PersonalStorage.getParentFolder(byte[])`
- Método `PersonalStorage.getParentFolder(SString)`

- Propriedade `AssociatedPerson.getPrefered, setPrefered`
- Propriedade `InstantMessengerAddress.getPrefered, setPrefered`
- Propriedade `ObjectIdentifier.getWebDavId, setWebDavId`
- Propriedade `PhoneNumberCategory.getPrimary, setPrimary`
- Propriedade `Url.getPrefered, setPrefered`
- Propriedade `UrlList.getFtp, setFtp`

- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage)`
- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback, Object)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback)`
- Método `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback, Object)`
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