---
title: "Alterações na API Pública no Aspose.Email 6.2.0"
url: /pt/java/public-api-changes-in-aspose-email-6-2-0/
weight: 230
type: docs
---

A seguir está uma lista de quaisquer alterações feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer alteração não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre qualquer alteração listada, por favor, levante-a no fórum de suporte da Aspose.Email.

APIs adicionadas:
- Classe `AppointmentCollection`

- Método `AppointmentCollection.#ctor`
- Método `AppointmentCollection.#ctor(IGenericEnumerable)`

- Método `ExchangeClient.moveItems(String, boolean, /**params**/ String...)`
- Método `ExchangeClient.moveMessage(String, boolean, String)`
- Método `ExchangeClient.moveMessage(String, String)`
- Método `ExchangeMessageInfoCollection.#ctor(IGenericEnumerable)`
- Método `IEWSClient.getContact(ObjectIdentifier)`
- Método `IEWSClient.getContact(ObjectIdentifier, ExchangeListContactsOptions)`
- Método `IEWSClient.getContact(String)`
- Método `IEWSClient.getContact(String, ExchangeListContactsOptions)`
- Método `IEWSClient.listAppointments(MailQuery, int)`
- Método `IEWSClient.listAppointments(MailQuery, int, int)`
- Método `IEWSClient.listAppointments(int)`
- Método `IEWSClient.listAppointments(int, int)`
- Método `IEWSClient.listAppointments(String, MailQuery, int)`
- Método `IEWSClient.listAppointments(String, MailQuery, int, int)`
- Método `IEWSClient.listAppointments(String, int)`
- Método `IEWSClient.listAppointments(String, int, int)`
- Método `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, int, int, ExchangeListMessagesOptions)`
- Método `IEWSClient.listMessages(String, int, int, ExchangeListMessagesOptions)`

- Método `ImapClient.beginListMessages(IConnection, int, int)`
- Método `ImapClient.beginListMessages(IConnection, int, int, AsyncCallback)`
- Método `ImapClient.beginListMessages(IConnection, int, int, AsyncCallback, Object)`
- Método `ImapClient.beginListMessages(int, int)`
- Método `ImapClient.beginListMessages(int, int, AsyncCallback)`
- Método `ImapClient.beginListMessages(int, int, AsyncCallback, Object)`
- Método `ImapClient.listMessages(IConnection, int, int)`
- Método `ImapClient.listMessages(int, int)`
- Método `ImapMessageInfoCollection.#ctor(IGenericEnumerable)`
- Método `MapiAttachmentCollection.insert(int, String, MapiMessage)`
- Método `MapiAttachmentCollection.replace(int, String, MapiMessage)`
- Método `MapiContact.fromVCard(String, Encoding)`
- Método `MapiObjectProperty.ToMapiMessage`
- Propriedade `AppointmentCollection.getLastItemOffset, setLastItemOffset`
- Propriedade `AppointmentCollection.getLastPage, setLastPage`
- Propriedade `AppointmentCollection.getTotalCount`
- Propriedade `ImapMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Propriedade `ImapMessageInfoCollection.getLastPage, setLastPage`
- Propriedade `ImapMessageInfoCollection.getTotalCount`

APIs removidas:
- Classe `MailMessageSaveOptions`
- Evento `SmtpClient.SendCompleted`
- Enumeração `MailMessageSaveOptions.HideExtraPrintHeader`
- Enumeração `MailMessageSaveOptions.NoEncodeCharactersToMht`
- Enumeração `MailMessageSaveOptions.None`
- Enumeração `MailMessageSaveOptions.WriteCompleteBccEmailAddressToMht`
- Enumeração `MailMessageSaveOptions.WriteCompleteCcEmailAddressToMht`
- Enumeração `MailMessageSaveOptions.WriteCompleteEmailAddressToMht`
- Enumeração `MailMessageSaveOptions.WriteCompleteFromEmailAddressToMht`
- Enumeração `MailMessageSaveOptions.WriteCompleteToEmailAddressToMht`
- Enumeração `MailMessageSaveOptions.WriteHeaderToMht`
- Enumeração `MailMessageSaveOptions.WriteOutlineAttachmentsToMht`
- Enumeração `MhtFormatOptions.WriteCompleteEmailAddressToMht`
- Método `ExchangeClient.moveItem(String, String)`
- Método `IEWSClient.deleteContact(MapiContact, boolean)`
- Método `IEWSClient.fetchMapiAttachments(IGenericEnumerable)`
- Método `IEWSClient.listContacts(String, ExchangeListContactsOptions)`
- Método `IEWSClient.loadContactPhoto(MapiContactPhoto)`
- Método `IEWSClient.updateContact(MapiContact)`
- Método `IMessage.save(Stream, MailMessageSaveType)`
- Método `IMessage.save(String, MailMessageSaveType)`
- Método `MailMessage.save(Stream, FileCompatibilityMode)`
- Método `MailMessage.save(Stream, MailMessageSaveType)`
- Método `MailMessage.save(Stream, MailMessageSaveType, MailMessageSaveOptions)`
- Método `MailMessage.save(Stream, MessageFormat)`
- Método `MailMessage.save(Stream, MessageFormat, MailMessageSaveOptions)`
- Método `MailMessage.save(String, FileCompatibilityMode)`
- Método `MailMessage.save(String, MailMessageSaveType)`
- Método `MailMessage.save(String, MailMessageSaveType, MailMessageSaveOptions)`
- Método `MailMessage.save(String, MessageFormat)`
- Método `MailMessage.save(String, MessageFormat, MailMessageSaveOptions)`
- Método `SmtpClient.sendAsyncCancel`
- Método `HeaderCollection.add(imeHeader)`
- Método `FollowUpManager.getFlag(MapiMessage)`
- Método `FollowUpManager.setFlag(MapiMessage, FollowUpOptions)`
- Método `MapiContactPhoto.#ctor(String, MapiContactPhotoImageFormat)`
- Método `MapiContactPhoto.#ctor(String, byte[], MapiContactPhotoImageFormat)`
- Método `MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat)`
- Método `MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat, boolean)`
- Método `PersonalStorage.changeDisplayName(String)`
- Propriedade `MailMessage.getPreserveOriginalBoundaries, setPreserveOriginalBoundaries`
- Propriedade `MailMessage.getPreserveOriginalDates, setPreserveOriginalDates`
- Propriedade `PersonalStorage.getDisplayName`
- Propriedade `PersonalStorage.MessageStoreProperties`