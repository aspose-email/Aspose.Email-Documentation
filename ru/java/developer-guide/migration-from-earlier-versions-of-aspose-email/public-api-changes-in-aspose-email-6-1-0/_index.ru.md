---
title: "Изменения в публичном API Aspose.Email 6.1.0"
url: /ru/java/public-api-changes-in-aspose-email-6-1-0/
weight: 220
type: docs
---

Ниже приведен список изменений, внесенных в публичный API, таких как добавленные, переименованные, удаленные или устаревшие члены, а также любые изменения, несовместимые с предыдущими версиями, сделанные в Aspose.Email для Java. Если у вас есть сомнения по поводу любого из перечисленных изменений, пожалуйста, поднимите этот вопрос на форуме поддержки Aspose.Email.
## **Добавленные API**
- Класс `WebDavContactSaveOptions`
- Метод `WebDavContactSaveOptions.#ctor`
- Свойство `WebDavContactSaveOptions.getDefault`

- Класс `MapiContactSaveOptions`
- Метод `MapiContactSaveOptions.#ctor`
- Свойство `MapiContactSaveOptions.getDefault`

- Класс `PipeliningMode`
- Поле/Перечисление `PipeliningMode.Auto`
- Поле/Перечисление `PipeliningMode.Disabled`
- Поле/Перечисление `PipeliningMode.Enabled`

- Класс `PipeliningStatus`
- Метод `PipeliningStatus.to_PipeliningStatus(boolean mode)`
- Метод `PipeliningStatus.to_PipeliningStatus(int mode)`
- Метод `PipeliningStatus.to_Boolean(PipeliningStatus status)`
- Метод `PipeliningStatus.to_Boolean()`
- Метод `PipeliningStatus.toString`
- Свойство `PipeliningStatus.getClientMode, setClientMode`
- Свойство `PipeliningStatus.getPipeliningEnabled`
- Свойство `PipeliningStatus.getSupportedByServer, setSupportedByServer`

- Поле/Перечисление `PhoneNumberCategory.PrimaryValue`
- Поле/Перечисление `MapiPropertyTag.PidTagUrlName`

- Метод `IEWSClient.createFolder(String, String)`
- Свойство `IEWSClient.getUseSlashAsFolderSeparator, setUseSlashAsFolderSeparator`

- Метод `Contact.to_MapiContact(Contact contact)`
- Метод `Contact.to_Contact(MapiContact contact)`
- Метод `Contact.toString`

- Метод `MapiAttachmentCollection.remove(MapiAttachment)`

- Метод `PersonalStorage.extractAttachments( MessageInfo)`
- Метод `PersonalStorage.extractAttachments(String)`
- Метод `PersonalStorage.getParentFolder(byte[])`
- Метод `PersonalStorage.getParentFolder(SString)`

- Свойство `AssociatedPerson.getPrefered, setPrefered`
- Свойство `InstantMessengerAddress.getPrefered, setPrefered`
- Свойство `ObjectIdentifier.getWebDavId, setWebDavId`
- Свойство `PhoneNumberCategory.getPrimary, setPrimary`
- Свойство `Url.getPrefered, setPrefered`
- Свойство `UrlList.getFtp, setFtp`

- Метод `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage)`
- Метод `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback, Object)`
- Метод `SmtpClient.beginForward(IConnection, String, String, MailMessage)`
- Метод `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback, Object)`
- Метод `SmtpClient.beginForward(String, MailAddressCollection, MailMessage)`
- Метод `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback,
  Object)`
- Метод `SmtpClient.beginForward(String, String, MailMessage)`
- Метод `SmtpClient.beginForward(String, String, MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginForward(String, String, MailMessage, AsyncCallback, Object)`

- Метод `SmtpClient.beginNoop`
- Метод `SmtpClient.beginNoop(IConnection)`
- Метод `SmtpClient.beginNoop(IConnection, AsyncCallback)`
- Метод `SmtpClient.beginNoop(IConnection, AsyncCallback, Object)`
- Метод `SmtpClient.beginNoop(AsyncCallback)`
- Метод `SmtpClient.beginNoop(AsyncCallback, Object)`

- Метод `SmtpClient.beginSend(IConnection, MailMessage)`
- Метод `SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback, Object)`
- Метод `SmtpClient.beginSend(IConnection, MailMessage[])`
- Метод `SmtpClient.beginSend(IConnection, String, String, String, String)`
- Метод `SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback)`
- Метод `SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback, Object)`
- Метод `SmtpClient.beginSend(MailMessage)`
- Метод `SmtpClient.beginSend(MailMessage, AsyncCallback)`
- Метод `SmtpClient.beginSend(MailMessage, AsyncCallback, Object)`
- Метод `SmtpClient.beginSend(MailMessage[])`
- Метод `SmtpClient.beginSend(String, String, String, String)`
- Метод `SmtpClient.beginSend(String, String, String, String, AsyncCallback)`
- Метод `SmtpClient.beginSend(String, String, String, String, AsyncCallback, Object)`

- Метод `SmtpClient.endForward(IAsyncResult)`
- Метод `SmtpClient.endNoop(IAsyncResult)`
- Метод `SmtpClient.endSend(IAsyncResult)`

- Метод `SmtpClient.forward(IConnection, String, MailAddressCollection, MailMessage)`
- Метод `SmtpClient.forward(IConnection, String, String, MailMessage)`

- Метод `SmtpClient.noop`
- Метод `SmtpClient.noop(IConnection)`

- Метод `SmtpClient.send(IConnection, MailMessage)`
- Метод `SmtpClient.send(IConnection, MailMessage[])`
- Метод `SmtpClient.send(IConnection, MailMessageCollection)`
- Метод `SmtpClient.send(IConnection, IEnumerable)`
- Метод `SmtpClient.send(IConnection, String, String, String, String)`
- Метод `SmtpClient.send(MailMessage[])`
- Метод `SmtpClient.send(MailMessageCollection)`