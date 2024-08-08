---
title: Public API Changes in Aspose.Email 6.1.0
type: docs
weight: 220
url: /java/public-api-changes-in-aspose-email-6-1-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
Class WebDavContactSaveOptions
Method WebDavContactSaveOptions.#ctor
Property WebDavContactSaveOptions.getDefault

Class MapiContactSaveOptions
Method MapiContactSaveOptions.#ctor
Property MapiContactSaveOptions.getDefault

Class PipeliningMode
Field/Enum PipeliningMode.Auto
Field/Enum PipeliningMode.Disabled
Field/Enum PipeliningMode.Enabled

Class PipeliningStatus
Method PipeliningStatus.to_PipeliningStatus(boolean mode)
Method PipeliningStatus.to_PipeliningStatus(int mode)
Method PipeliningStatus.to_Boolean(PipeliningStatus status)
Method PipeliningStatus.to_Boolean()
Method PipeliningStatus.toString
Property PipeliningStatus.getClientMode, setClientMode
Property PipeliningStatus.getPipeliningEnabled
Property PipeliningStatus.getSupportedByServer, setSupportedByServer

Field/Enum PhoneNumberCategory.PrimaryValue
Field/Enum MapiPropertyTag.PidTagUrlName

Method IEWSClient.createFolder(String, String)
Property IEWSClient.getUseSlashAsFolderSeparator, setUseSlashAsFolderSeparator

Method Contact.to_MapiContact(Contact contact)
Method Contact.to_Contact(MapiContact contact)
Method Contact.toString

Method MapiAttachmentCollection.remove(MapiAttachment)

Method PersonalStorage.extractAttachments( MessageInfo)
Method PersonalStorage.extractAttachments(String)
Method PersonalStorage.getParentFolder(byte[])
Method PersonalStorage.getParentFolder(SString)

Property AssociatedPerson.getPrefered, setPrefered
Property InstantMessengerAddress.getPrefered, setPrefered
Property ObjectIdentifier.getWebDavId, setWebDavId
Property PhoneNumberCategory.getPrimary, setPrimary
Property Url.getPrefered, setPrefered
Property UrlList.getFtp, setFtp

Method SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage)
Method SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback)
Method SmtpClient.beginForward(IConnection, String, MailAddressCollection, MailMessage, AsyncCallback, Object)
Method SmtpClient.beginForward(IConnection, String, String, MailMessage)
Method SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback)
Method SmtpClient.beginForward(IConnection, String, String, MailMessage, AsyncCallback, Object)
Method SmtpClient.beginForward(String, MailAddressCollection, MailMessage)
Method SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback)
Method SmtpClient.beginForward(String, MailAddressCollection, MailMessage, AsyncCallback, Object)
Method SmtpClient.beginForward(String, String, MailMessage)
Method SmtpClient.beginForward(String, String, MailMessage, AsyncCallback)
Method SmtpClient.beginForward(String, String, MailMessage, AsyncCallback, Object)

Method SmtpClient.beginNoop
Method SmtpClient.beginNoop(IConnection)
Method SmtpClient.beginNoop(IConnection, AsyncCallback)
Method SmtpClient.beginNoop(IConnection, AsyncCallback, Object)
Method SmtpClient.beginNoop(AsyncCallback)
Method SmtpClient.beginNoop(AsyncCallback, Object)

Method SmtpClient.beginSend(IConnection, MailMessage)
Method SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback)
Method SmtpClient.beginSend(IConnection, MailMessage, AsyncCallback, Object)
Method SmtpClient.beginSend(IConnection, MailMessage[])
Method SmtpClient.beginSend(IConnection, String, String, String, String)
Method SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback)
Method SmtpClient.beginSend(IConnection, String, String, String, String, AsyncCallback, Object)
Method SmtpClient.beginSend(MailMessage)
Method SmtpClient.beginSend(MailMessage, AsyncCallback)
Method SmtpClient.beginSend(MailMessage, AsyncCallback, Object)
Method SmtpClient.beginSend(MailMessage[])
Method SmtpClient.beginSend(String, String, String, String)
Method SmtpClient.beginSend(String, String, String, String, AsyncCallback)
Method SmtpClient.beginSend(String, String, String, String, AsyncCallback, Object)

Method SmtpClient.endForward(IAsyncResult)
Method SmtpClient.endNoop(IAsyncResult)
Method SmtpClient.endSend(IAsyncResult)

Method SmtpClient.forward(IConnection, String, MailAddressCollection, MailMessage)
Method SmtpClient.forward(IConnection, String, String, MailMessage)

Method SmtpClient.noop
Method SmtpClient.noop(IConnection)

Method SmtpClient.send(IConnection, MailMessage)
Method SmtpClient.send(IConnection, MailMessage[])
Method SmtpClient.send(IConnection, MailMessageCollection)
Method SmtpClient.send(IConnection, IEnumerable)
Method SmtpClient.send(IConnection, String, String, String, String)
Method SmtpClient.send(MailMessage[])
Method SmtpClient.send(MailMessageCollection)
