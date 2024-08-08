---
title: Utility Features - MailMessage
type: docs
weight: 40
url: /cpp/utility-features-mailmessage/
description: You can read email messages with TNEF attachments used by Microsoft Outlook and Exchange Server, and modify the contents of the attachment using the C++ Email Parser Library API.
---

## **MailMessages Containing TNEF attachments**
Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of the attachment. The email can then be saved as normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments. This article also shows working with creating TNEF EML files from Outlook MSG files.

### **Reading Message by Preserving TNEF Attachments**
The following code snippet shows you how to reading message by preserving TNEF attachments.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}

## **Check Bounced Messages**
It is very common that a message sent to a recipient may bounce for any reason such as invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The  MailMesage's CheckBounced method returns a valid result if the email message is a bounced email. This article shows the usage of BounceResult class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason about the notification. The following code snippet shows you how to process bounced messages.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}
