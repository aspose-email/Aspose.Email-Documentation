---
title: "Изменения публичного API в Aspose.Email 6.2.0"
url: /ru/java/public-api-changes-in-aspose-email-6-2-0/
weight: 230
type: docs
---

Следующий список включает все изменения, внесенные в публичный API, такие как добавленные, переименованные, удаленные или устаревшие элементы, а также любые изменения, не совместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть вопросы по любому из перечисленных изменений, пожалуйста, поднимите их на форуме поддержки Aspose.Email.

Добавленные API:
- Класс `AppointmentCollection`

- Метод `AppointmentCollection.#ctor`
- Метод `AppointmentCollection.#ctor(IGenericEnumerable)`

- Метод `ExchangeClient.moveItems(String, boolean, /**params**/ String...)`
- Метод `ExchangeClient.moveMessage(String, boolean, String)`
- Метод `ExchangeClient.moveMessage(String, String)`
- Метод `ExchangeMessageInfoCollection.#ctor(IGenericEnumerable)`
- Метод `IEWSClient.getContact(ObjectIdentifier)`
- Метод `IEWSClient.getContact(ObjectIdentifier, ExchangeListContactsOptions)`
- Метод `IEWSClient.getContact(String)`
- Метод `IEWSClient.getContact(String, ExchangeListContactsOptions)`
- Метод `IEWSClient.listAppointments(MailQuery, int)`
- Метод `IEWSClient.listAppointments(MailQuery, int, int)`
- Метод `IEWSClient.listAppointments(int)`
- Метод `IEWSClient.listAppointments(int, int)`
- Метод `IEWSClient.listAppointments(String, MailQuery, int)`
- Метод `IEWSClient.listAppointments(String, MailQuery, int, int)`
- Метод `IEWSClient.listAppointments(String, int)`
- Метод `IEWSClient.listAppointments(String, int, int)`
- Метод `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, int, int, ExchangeListMessagesOptions)`
- Метод `IEWSClient.listMessages(String, int, int, ExchangeListMessagesOptions)`

- Метод `ImapClient.beginListMessages(IConnection, int, int)`
- Метод `ImapClient.beginListMessages(IConnection, int, int, AsyncCallback)`
- Метод `ImapClient.beginListMessages(IConnection, int, int, AsyncCallback, Object)`
- Метод `ImapClient.beginListMessages(int, int)`
- Метод `ImapClient.beginListMessages(int, int, AsyncCallback)`
- Метод `ImapClient.beginListMessages(int, int, AsyncCallback, Object)`
- Метод `ImapClient.listMessages(IConnection, int, int)`
- Метод `ImapClient.listMessages(int, int)`
- Метод `ImapMessageInfoCollection.#ctor(IGenericEnumerable)`
- Метод `MapiAttachmentCollection.insert(int, String, MapiMessage)`
- Метод `MapiAttachmentCollection.replace(int, String, MapiMessage)`
- Метод `MapiContact.fromVCard(String, Encoding)`
- Метод `MapiObjectProperty.ToMapiMessage`
- Свойство `AppointmentCollection.getLastItemOffset, setLastItemOffset`
- Свойство `AppointmentCollection.getLastPage, setLastPage`
- Свойство `AppointmentCollection.getTotalCount`
- Свойство `ImapMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Свойство `ImapMessageInfoCollection.getLastPage, setLastPage`
- Свойство `ImapMessageInfoCollection.getTotalCount`

Удаленные API:
- Класс `MailMessageSaveOptions`
- Событие `SmtpClient.SendCompleted`
- Перечисление `MailMessageSaveOptions.HideExtraPrintHeader`
- Перечисление `MailMessageSaveOptions.NoEncodeCharactersToMht`
- Перечисление `MailMessageSaveOptions.None`
- Перечисление `MailMessageSaveOptions.WriteCompleteBccEmailAddressToMht`
- Перечисление `MailMessageSaveOptions.WriteCompleteCcEmailAddressToMht`
- Перечисление `MailMessageSaveOptions.WriteCompleteEmailAddressToMht`
- Перечисление `MailMessageSaveOptions.WriteCompleteFromEmailAddressToMht`
- Перечисление `MailMessageSaveOptions.WriteCompleteToEmailAddressToMht`
- Перечисление `MailMessageSaveOptions.WriteHeaderToMht`
- Перечисление `MailMessageSaveOptions.WriteOutlineAttachmentsToMht`
- Перечисление `MhtFormatOptions.WriteCompleteEmailAddressToMht`
- Метод `ExchangeClient.moveItem(String, String)`
- Метод `IEWSClient.deleteContact(MapiContact, boolean)`
- Метод `IEWSClient.fetchMapiAttachments(IGenericEnumerable)`
- Метод `IEWSClient.listContacts(String, ExchangeListContactsOptions)`
- Метод `IEWSClient.loadContactPhoto(MapiContactPhoto)`
- Метод `IEWSClient.updateContact(MapiContact)`
- Метод `IMessage.save(Stream, MailMessageSaveType)`
- Метод `IMessage.save(String, MailMessageSaveType)`
- Метод `MailMessage.save(Stream, FileCompatibilityMode)`
- Метод `MailMessage.save(Stream, MailMessageSaveType)`
- Метод `MailMessage.save(Stream, MailMessageSaveType, MailMessageSaveOptions)`
- Метод `MailMessage.save(Stream, MessageFormat)`
- Метод `MailMessage.save(Stream, MessageFormat, MailMessageSaveOptions)`
- Метод `MailMessage.save(String, FileCompatibilityMode)`
- Метод `MailMessage.save(String, MailMessageSaveType)`
- Метод `MailMessage.save(String, MailMessageSaveType, MailMessageSaveOptions)`
- Метод `MailMessage.save(String, MessageFormat)`
- Метод `MailMessage.save(String, MessageFormat, MailMessageSaveOptions)`
- Метод `SmtpClient.sendAsyncCancel`
- Метод `HeaderCollection.add(imeHeader)`
- Метод `FollowUpManager.getFlag(MapiMessage)`
- Метод `FollowUpManager.setFlag(MapiMessage, FollowUpOptions)`
- Метод `MapiContactPhoto.#ctor(String, MapiContactPhotoImageFormat)`
- Метод `MapiContactPhoto.#ctor(String, byte[], MapiContactPhotoImageFormat)`
- Метод `MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat)`
- Метод `MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat, boolean)`
- Метод `PersonalStorage.changeDisplayName(String)`
- Свойство `MailMessage.getPreserveOriginalBoundaries, setPreserveOriginalBoundaries`
- Свойство `MailMessage.getPreserveOriginalDates, setPreserveOriginalDates`
- Свойство `PersonalStorage.getDisplayName`
- Свойство `PersonalStorage.MessageStoreProperties`