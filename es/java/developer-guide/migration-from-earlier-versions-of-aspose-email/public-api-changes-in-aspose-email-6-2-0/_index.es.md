---
title: "Cambios en la API pública en Aspose.Email 6.2.0"
url: /es/java/public-api-changes-in-aspose-email-6-2-0/
weight: 230
type: docs
---

A continuación se presenta una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio que no sea compatible hacia atrás realizado en Aspose.Email para Java. Si tiene preocupaciones sobre algún cambio listado, por favor, hágalas en el foro de soporte de Aspose.Email.

APIs añadidas:
- Clase `AppointmentCollection`

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
- Propiedad `AppointmentCollection.getLastItemOffset, setLastItemOffset`
- Propiedad `AppointmentCollection.getLastPage, setLastPage`
- Propiedad `AppointmentCollection.getTotalCount`
- Propiedad `ImapMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Propiedad `ImapMessageInfoCollection.getLastPage, setLastPage`
- Propiedad `ImapMessageInfoCollection.getTotalCount`

APIs eliminadas:
- Clase `MailMessageSaveOptions`
- Evento `SmtpClient.SendCompleted`
- Enum `MailMessageSaveOptions.HideExtraPrintHeader`
- Enum `MailMessageSaveOptions.NoEncodeCharactersToMht`
- Enum `MailMessageSaveOptions.None`
- Enum `MailMessageSaveOptions.WriteCompleteBccEmailAddressToMht`
- Enum `MailMessageSaveOptions.WriteCompleteCcEmailAddressToMht`
- Enum `MailMessageSaveOptions.WriteCompleteEmailAddressToMht`
- Enum `MailMessageSaveOptions.WriteCompleteFromEmailAddressToMht`
- Enum `MailMessageSaveOptions.WriteCompleteToEmailAddressToMht`
- Enum `MailMessageSaveOptions.WriteHeaderToMht`
- Enum `MailMessageSaveOptions.WriteOutlineAttachmentsToMht`
- Enum `MhtFormatOptions.WriteCompleteEmailAddressToMht`
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
- Propiedad `MailMessage.getPreserveOriginalBoundaries, setPreserveOriginalBoundaries`
- Propiedad `MailMessage.getPreserveOriginalDates, setPreserveOriginalDates`
- Propiedad `PersonalStorage.getDisplayName`
- Propiedad `PersonalStorage.MessageStoreProperties`