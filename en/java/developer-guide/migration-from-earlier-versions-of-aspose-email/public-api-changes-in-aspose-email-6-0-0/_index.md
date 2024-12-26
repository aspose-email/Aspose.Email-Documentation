---
title: Public API Changes in Aspose.Email 6.0.0
ArticleTitle: Public API Changes in Aspose.Email 6.0.0
type: docs
weight: 210
url: /java/public-api-changes-in-aspose-email-6-0-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for .NET. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
Class ExchangeDistributionList
Method ExchangeDistributionList.#ctor
Method ExchangeDistributionList.toMailAddress
Method IEWSClient.addToDistributionList(ExchangeDistributionList, MailAddressCollection)
Method IEWSClient.createDistributionList(ExchangeDistributionList, MailAddressCollection)
Method IEWSClient.deleteDistributionList( ExchangeDistributionList, boolean)
Method IEWSClient.deleteFromDistributionList( ExchangeDistributionList, MailAddressCollection)
Method IEWSClient.expandDistributionList(MailAddress)
Method IEWSClient.fetchDistributionList(ExchangeDistributionList)
Method IEWSClient.listDistributionLists
Property ExchangeDistributionList.getChangeKey(), setChangeKey(String)
Property ExchangeDistributionList.getDisplayName(), setDisplayName(String)
Property ExchangeDistributionList.getId(), setId(String)
Property MailAddress.Id

Class ForwardMessageBuilder
Class OriginalMessageAdditionMode
Class ReplyMessageBuilder
Class ResponseMessageBuilder
Enum OriginalMessageAdditionMode.Attachment
Enum OriginalMessageAdditionMode.None
Enum OriginalMessageAdditionMode.Textpart
Enum Outlook.MapiPropertyTag.PR_ATTACHMENT_HIDDEN
Method ForwardMessageBuilder.#ctor
Method ForwardMessageBuilder.buildResponse(MailMessage)
Method ForwardMessageBuilder.buildResponse(MapiMessage)
Method ReplyMessageBuilder.#ctor
Method ReplyMessageBuilder.buildResponse(MailMessage)
Method ReplyMessageBuilder.buildResponse(MapiMessage)
Method ResponseMessageBuilder.#ctor
Method ResponseMessageBuilder.buildResponse(MailMessage)
Method ResponseMessageBuilder.buildResponse(MapiMessage)
Property ReplyMessageBuilder.getReplyAll, setReplyAll(boolean)
Property ResponseMessageBuilder.getAdditionMode, setAdditionMode(int)
Property ResponseMessageBuilder.getResponseText, setResponseText(String)
Property ResponseMessageBuilder.getSender, setSender(MailAddress)

Enum MhtFormatOptions.SkipByteOrderMarkInBody

Class MailMessageEventArgs
Method MailMessageEventArgs.#ctor(MailMessage)
Property MailMessageEventArgs.getMessage
Method IEWSClient.listMessages(IGenericEnumerable<String>)

Method MapiAttachmentCollection.removeAt(int)
Method PersonalStorage.splitInto(long, String)
## **Removed APIs**
Method PersonalStorage.ыplitInto(int, String)
Property SmtpClientBulkSendEventArgs.getMessage
