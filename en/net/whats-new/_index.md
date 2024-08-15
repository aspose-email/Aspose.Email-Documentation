---
title: What's New in Aspose.Email for .NET
type: docs
weight: 5
url: /net/whats-new/
---


## [Aspose.Email for .NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Support for Contacts and Calendar in MS Graph** - IGraphClient interface methods allow you to access, manage, and interact with users’ contacts and calendar events:
  - Retrieve a collection of MAPI contacts.
  - Retrieve a specific contact.
  - Create a new contact.
  - Update an existing contact.
  - Retrieve a collection of calendar information.
  - Retrieve a collection of calendar items.
  - Retrieve a specific calendar item.
  - Create a new calendar item.
  - Updates an existing calendar item.

## [Aspose.Email for .NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Manipulate Outlook Item Categories** - Aspose.Email makes it possible to retrieve and utilize category colors associated with Outlook item categories stored in OLM files.

- **Container Class Matching** - a new [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) property was added to the [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) class which, when adding a folder to a PST file, allows you to ensure that the class of the folder matches the expected type or category of folders within the PST file.

## [Aspose.Email for .NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Setting Relative Path to Resources when Saving Email Message as HTML** - Aspose.Email introduces the ability to save email resources with relative paths when exporting messages to HTML format, offering enhanced flexibility for resource linking. Users can choose between absolute and relative paths, and define custom paths using the [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event) event, streamlining the sharing and display of emails across different systems.

## [Aspose.Email for .NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Validate Email Messages** - A set of components was added to enable users validate message files, supporting formats such as eml, emlx, mht, msg, and oft. By utilizing this functionality, users can validate messages and retrieve insights into the validation process, including format type and encountered errors.

- **Attach Digital Signatures to Email Messages** - The *AttachSignature* method in the [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) class was designed to easily add a digital signature to an email.

Once the signature is attached, users can verify the results through properties like 'IsSigned', 'MessageClass', and attachment details.

To customize the signature attachment process, users can utilize the [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class) class.

## [Aspose.Email for .NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Split Mbox Storage into Smaller Parts** - split large files into manageable parts and implement custom actions during the process:

  - Specify a custom prefix for the split Mbox file names.
  - Customize actions before and after an email is copied to a new Mbox file.
  - React when a new Mbox file is created.
  - Respond when a new Mbox file is filled with emails.

- **Get AlternateView Content by MediaType** - retrieve the content as a string from a specific AlternateView within an email message. The  [MailMessage.GetAlternateViewContent(string mediaType)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) method allows you to access the content from an AlternateView that matches the specified media type.

## [Aspose.Email for .NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Send Emails via Graph Client** - added the support for overloaded methods to the GraphClient class that accept a MailMessage object for sending emails:
  - [CreateMessage(string folderId, MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Send(MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Save Mapi Distribution List to a Single Multi Contact VCF File** - Save the Mapi Distribution List to a specified file name using the provided save options. You can provide the file name and an instance of the MapiDistributionListSaveOptions class as parameters.
  - void [Save(string fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) method has been added for this purpose.

## [Aspose.Email for .NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Delete Items from PST** - We have added a new method, [DeleteItem(string entryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), to the PersonalStorage class. This method provides a way to delete items (folders or messages) from a Personal Storage Table (PST) using the unique entryId associated with the item.
- **Event Handling and PST Splitting** - Improved Functionality in [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class:
  - [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) event occurs before the storage is processed, specifically before processing the current storage in MergeWith or SplitInto methods. This event provides an opportunity to execute custom logic or handle certain operations before the storage processing occurs.

  - [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) class provides data for the PersonalStorage.StorageProcessing event. 

  - [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) overload method allows the splitting of the PST storage into smaller-sized parts. 
- **Calendar Handling** - New properties and a method were added to the  CalendarReader class:
  - [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) property allows you to retrieve the number of Vevent components (events) present in the calendar, making it easier to track the total number of events.
  - [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) property determines whether the calendar contains multiple events.
  - [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) property obtains the iCalendar method type associated with the calendar object. It returns the method type, such as “REQUEST,” “PUBLISH,” or “CANCEL,” providing valuable insights into the purpose of the calendar.
  - [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) gets the Version of iCalendar.
  - [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) method enables the loading of a list of events from a calendar containing multiple events. It returns a list of Appointment objects, allowing easy access and processing of each event individually.

## [Aspose.Email for .NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Preserve or Remove Signature in MBOX to PST Conversion** - set the [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) property to 'true' to remove the signature.
- **Remove Signature when Loading EML Files** - set the [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) property to 'true' to remove the signature.
- **Email Signature Check**
  - Added a new [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) class for checking the signature of secure emails. You can now check the signature of MapiMessage and MailMessage objects.
  - Added a new [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) class to store the results of checking secure emails.

  Introduced methods of the SecureEmailManager:

  - [CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) 
  - [CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Aspose.Email for .NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Determine the Version of ICS/VCS Files** - Use the [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) property of the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class to retrieve the version of ICS/VCS files.
- **Customize Saving Options for VCard Files** - We added the new [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) class to our API with the following properties:
  - [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) enables users to specify the desired vCard version when saving contact items. By default, the class is set to use vCard version 2.1 (VCardVersion.V21).
  - [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - allows users to control whether extended fields can be used when saving vCard files. When set to true (default), extensions are permitted, providing compatibility with custom fields and additional contact information.
  - [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - the encoding to be used when saving vCard contact items.
- **Get Total Number of Message Items Contained in the Zimbra Storage** with the [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) method of the [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/) class.
- **Retrieve a PST subfolder by path** - Retrieve a subfolder with the specified name from the current PST folder using the [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) method overload.

## [Aspose.Email for .NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Add a Reference Attachment to a Message** - We have added a new [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) method to the [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) class with the following parameters:
  - `name` - the name of attachment
  - `sharedLink` - a fully qualified shared link to the attachment provided by web service manipulating the attachment
  - `url` - a file location
  - `providerName` - a name of reference attachment provider
- **Multiple VCard Contacts Check** - Check whether a source file contains multi contacts with the new [VCardContact.IsMultiContacts(string filePath)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1) method.
- **Convert Calendar ICS Format to Message Formats** - Convert appointments to message objects such as MapiMessage and MailMessage.  
- **Additional Options for Saving Messages in HTML and MHTML Formats**:
  - [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Gets or sets the current Priority of the Task object.
  - [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Defines whether there is a need to save all headers in output mhtml or not.
  - [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Indicates that the specific Task fields should be written in output html.
- **Set Timeout to Message Conversion and Loading Process** - Limit the time in milliseconds while converting and loading messages, ensuring that the process does not take longer than necessary. For this purpose, the following features have been introduced:
  - [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Limits the time in milliseconds while converting a message.
  - [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Raised if the time is out while converting to MailMessage.
  - [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limits the time in milliseconds while converting a message.
  - [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Raised if the time is out while converting to MailMessage.

## [Aspose.Email for .NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Get the Total Number of Message Items Contained in the OLM Storage** with the [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) method to [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.
- **Determine if MapiMessage is OFT or MSG** - Determine whether the MapiMessage was loaded from an OFT or MSG file with the new [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) property.
- **Detect a NSF File Format**

## [Aspose.Email for .NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

-**Retrieve message properties from MboxMessageInfo** - Get access to the information about individual messages stored in an mbox file, such as message size, message index, message headers, message flags, and other message-related metadata. We have added the following properties to [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class:

DateTime Date - Gets the date of message
MailAddress From - Gets the from address
string Subject - Gets the message subject
MailAddressCollection To - Gets the address collection that contains the recipients of message
MailAddressCollection CC - Gets the address collection that contains CC recipients
MailAddressCollection Bcc - Gets the address collection that contains BCC recipients of message

## [Aspose.Email for .NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Get the total number of message items contained in the PST** - We have added the [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) method to [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/) property.
- **Get a Standard RSS Feeds Folder in Personal Storage**, **Add a Standard RSS Feeds Folder in PST** - A new RssFeeds value has been added to StandardIpmFolder enum. Now the RSS Feeds Folder can be easily retrieved or added to the storage.
- **Decrypt an Email Message Stored in the MAPI Format** - We have added a Decrypt method to the MapiMessage class:
  - [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Gets a value indicating whether the message is encrypted.
  - [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Decrypts this message (method searches the current user and computer My stores for the appropriate certificate and private key).
  - [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Decrypts this message with certificate. 
- **Setting a Product ID when Saving MapiCalendar to ICS** - We have added [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) property to [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) class. 
- **Extract Messages by Identifiers from OLM and MBOX** - This is the efficient way to avoid traversing through the entire storage each time to find a specific message to extract.
- **Determine whether the Attachment is Inline or Regular** with the [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) property.

## [Aspose.Email for .NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Get a MAPI Item Type** - Avoid checking the MessageClass property value every time before message conversion.
- **Remove Signature from MapiMessage** - For better compatibility, the [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) method and [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) property were added.
- **Identifying Predefined Folders** - The new [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) method, [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/), has been introduced to determine if a folder is within a predefined folder by returning the StandardIpmFolder enum value based on the specified parameter value.
- **Verifying Attachment TNEF Format** - The [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) property indicates whether the message attachment is TNEF formatted message.

## [Aspose.Email for .NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Renaming an Attachment in MapiMessage** - Now it is possible to edit the [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) property value in MapiMessage attachments.

## [Aspose.Email for .NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **List Messages with Graph API** - The new [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) method allows you to control the ordering of the retrieved messages based on the criteria you specify.

## [Aspose.Email for .NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Reading Messages from MBOX** - We have introduced new features for configuring loading options:
  - [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) property - Gets or sets email load options when parsing an Mbox storage.
  - [MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1) method. EmlLoadOptions parameter specifies options when reading message from Mbox storage.

## [Aspose.Email for .NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Get Message Identification Info** such as UID or sequence number using the following features:
  - [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) class - Represents identification information about a message in a mailbox.
  - [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) property - The sequence number of a message.
  - [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) property - The unique id of a message.
  - [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) property - Represents identification information about a message in a mailbox.

## [Aspose.Email for .NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Preserving Original Timestamp in ICS Files** - Extract calendar items from PST files and save them in ICS format with the original timestamp using the following options:
  - [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Allows specifying additional options when saving MapiCalendar to ICS format.
  - [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Allows keeing the original DateTimeStamp value in the output file.

## [Aspose.Email for .NET 22.5](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-5-release-notes/)

- **Enumerate Messages with Paging Support via Graph Client** - The API provides the paging and filtering support for listing messages. This is very helpful where the mailbox has a large number of messages and requires a lot of time for retrieving the summary information about these.
- **Asynchronous Mode in Handling Mail Clients** - A new approach to the task includes the following API members:
  - [`IAsyncSmtpClient`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/) - Allows applications to send messages by using the Simple Mail Transfer Protocol (SMTP).
  - [`SmtpClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/#smtpclientcreateasync-method) - Creates a new instance of the `Aspose.Email.Clients.Smtp.SmtpClient` class.
  - [`IAsyncSmtpClient.SendAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpSend`) method parameter set.
  - [`IAsyncSmtpClient.ForwardAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpForward`) arguments.
  - [`IAsyncImapClient`](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Allows applications to access and manipulate messages by using the Internet Message Access Protocol (IMAP).
  - [`ImapClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Creates a new instance of the `Aspose.Email.Clients.Imap.ImapClient` class.

## [Aspose.Email for .NET 22.4](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-4-release-notes/)

- **Send Email with MailGun and SendGrid Delivery Services** -  We have created a unified API which you can use to initialize options depending on which service is going to be used for sending messages, call the required client instance using the builder, prepare and send an email message. There is also an asynchronous version of the Send method.
- **Set the X-ALT-DESC header in ICS file** - We introduced a new [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) property to set the X-ALT-DESC header.

## [Aspose.Email for .NET 22.3](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-3-release-notes/)

- **List Message Attachments using IMAP Client** - Get information about attachments such as name, size without fetching the attachment data. API members involved in the operation: 
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfo`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) - Represents an attachment information.
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfocollection/) - Represents a collection of ImapAttachmentInfo. 
  - [`Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/) - Gets an information for each attachment in message.
- **Fetch Items with Attachments via EWS Client** - We added the [`FetchItems(EwsFetchItems options)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method) method to [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#iewsclient-interface). It accepts an instance of [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) class as a parameter to control the behavior of the method.

## [Aspose.Email for .NET 22.2](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-2-release-notes/)

- **Adding Reference Attachments**
    Introduced API members:
  - [`Aspose.Email.ReferenceAttachment`](https://reference.aspose.com/email/net/aspose.email/referenceattachment/#referenceattachment-class) - represents a reference attachment.
  - [`Aspose.Email.AttachmentPermissionType`](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) - The permission type data associated with a web reference attachment.
  - [`Aspose.Email.AttachmentProviderType`](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) - The type of web service manipulating the attachment.
- **Retrieve message class** - We have added [MessageClass](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/messageclass/#exchangemessageinfomessageclass-propertyм) property to [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/#exchangemessageinfo-class) class to  retrieve the class of each message in the collection from a public folder, after establishing a connection to an EWS client.
