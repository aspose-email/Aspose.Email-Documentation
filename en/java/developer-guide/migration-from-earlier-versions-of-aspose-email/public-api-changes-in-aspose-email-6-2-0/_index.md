---
title: Public API Changes in Aspose.Email 6.2.0
type: docs
weight: 230
url: /java/public-api-changes-in-aspose-email-6-2-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.

Added APIs:
Class AppointmentCollection

Method AppointmentCollection.#ctor
Method AppointmentCollection.#ctor(IGenericEnumerable)

Method ExchangeClient.moveItems(String, boolean, /**params**/ String...)
Method ExchangeClient.moveMessage(String, boolean, String)
Method ExchangeClient.moveMessage(String, String)
Method ExchangeMessageInfoCollection.#ctor(IGenericEnumerable)
Method IEWSClient.getContact(ObjectIdentifier)
Method IEWSClient.getContact(ObjectIdentifier, ExchangeListContactsOptions)
Method IEWSClient.getContact(String)
Method IEWSClient.getContact(String, ExchangeListContactsOptions)
Method IEWSClient.listAppointments(MailQuery, int)
Method IEWSClient.listAppointments(MailQuery, int, int)
Method IEWSClient.listAppointments(int)
Method IEWSClient.listAppointments(int, int)
Method IEWSClient.listAppointments(String, MailQuery, int)
Method IEWSClient.listAppointments(String, MailQuery, int, int)
Method IEWSClient.listAppointments(String, int)
Method IEWSClient.listAppointments(String, int, int)
Method IEWSClient.listMessages(String, ExchangeMessageInfoCollection, int, int, ExchangeListMessagesOptions)
Method IEWSClient.listMessages(String, int, int, ExchangeListMessagesOptions)

Method ImapClient.beginListMessages(IConnection, int, int)
Method ImapClient.beginListMessages(IConnection, int, int, AsyncCallback)
Method ImapClient.beginListMessages(IConnection, int, int, AsyncCallback, Object)
Method ImapClient.beginListMessages(int, int)
Method ImapClient.beginListMessages(int, int, AsyncCallback)
Method ImapClient.beginListMessages(int, int, AsyncCallback, Object)
Method ImapClient.listMessages(IConnection, int, int)
Method ImapClient.listMessages(int, int)
Method ImapMessageInfoCollection.#ctor(IGenericEnumerable)
Method MapiAttachmentCollection.insert(int, String, MapiMessage)
Method MapiAttachmentCollection.replace(int, String, MapiMessage)
Method MapiContact.fromVCard(String, Encoding)
Method MapiObjectProperty.ToMapiMessage
Property AppointmentCollection.getLastItemOffset, setLastItemOffset
Property AppointmentCollection.getLastPage, setLastPage
Property AppointmentCollection.getTotalCount
Property ImapMessageInfoCollection.getLastItemOffset, setLastItemOffset
Property ImapMessageInfoCollection.getLastPage, setLastPage
Property ImapMessageInfoCollection.getTotalCount

Removed APIs:
Class MailMessageSaveOptions
Event SmtpClient.SendCompleted
Enum MailMessageSaveOptions.HideExtraPrintHeader
Enum MailMessageSaveOptions.NoEncodeCharactersToMht
Enum MailMessageSaveOptions.None
Enum MailMessageSaveOptions.WriteCompleteBccEmailAddressToMht
Enum MailMessageSaveOptions.WriteCompleteCcEmailAddressToMht
Enum MailMessageSaveOptions.WriteCompleteEmailAddressToMht
Enum MailMessageSaveOptions.WriteCompleteFromEmailAddressToMht
Enum MailMessageSaveOptions.WriteCompleteToEmailAddressToMht
Enum MailMessageSaveOptions.WriteHeaderToMht
Enum MailMessageSaveOptions.WriteOutlineAttachmentsToMht
Enum MhtFormatOptions.WriteCompleteEmailAddressToMht
Method ExchangeClient.moveItem(String, String)
Method IEWSClient.deleteContact(MapiContact, boolean)
Method IEWSClient.fetchMapiAttachments(IGenericEnumerable)
Method IEWSClient.listContacts(String, ExchangeListContactsOptions)
Method IEWSClient.loadContactPhoto(MapiContactPhoto)
Method IEWSClient.updateContact(MapiContact)
Method IMessage.save(Stream, MailMessageSaveType)
Method IMessage.save(String, MailMessageSaveType)
Method MailMessage.save(Stream, FileCompatibilityMode)
Method MailMessage.save(Stream, MailMessageSaveType)
Method MailMessage.save(Stream, MailMessageSaveType, MailMessageSaveOptions)
Method MailMessage.save(Stream, MessageFormat)
Method MailMessage.save(Stream, MessageFormat, MailMessageSaveOptions)
Method MailMessage.save(String, FileCompatibilityMode)
Method MailMessage.save(String, MailMessageSaveType)
Method MailMessage.save(String, MailMessageSaveType, MailMessageSaveOptions)
Method MailMessage.save(String, MessageFormat)
Method MailMessage.save(String, MessageFormat, MailMessageSaveOptions)
Method SmtpClient.sendAsyncCancel
Method HeaderCollection.add( imeHeader)
Method FollowUpManager.getFlag(MapiMessage)
Method FollowUpManager.setFlag(MapiMessage, FollowUpOptions)
Method MapiContactPhoto.#ctor(String, MapiContactPhotoImageFormat)
Method MapiContactPhoto.#ctor(String, byte[], MapiContactPhotoImageFormat)
Method MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat)
Method MapiMessage.fromMailMessage(MailMessage, OutlookMessageFormat, boolean)
Method PersonalStorage.changeDisplayName(String)
Property MailMessage.getPreserveOriginalBoundaries, setPreserveOriginalBoundaries
Property MailMessage.getPreserveOriginalDates, setPreserveOriginalDates
Property PersonalStorage.getDisplayName
Property PersonalStorage.MessageStoreProperties
