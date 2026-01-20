---
title: Working with TNEF Attachments in Aspose.Email for C++
ArticleTitle: Working with TNEF Attachments 
type: docs
weight: 50
url: /cpp/tnef-attachments-handling/
description: Read, preserve, and manage Transport Neutral Encapsulation Format (TNEF) attachments in Outlook messages using Aspose.Email for C++.
---


**Transport Neutral Encapsulation Format (TNEF)** is a proprietary email attachment format used by Microsoft Outlook and Exchange Server. These attachments often contain rich message data such as formatted text, embedded images, or meeting requests.

Aspose.Email for C++ provides full support for reading and preserving TNEF attachments when loading email messages. You can access and modify the contents of TNEF attachments and then save the message in its original or a different format while maintaining all embedded data.

## **Read Emails While Preserving TNEF Attachments**

To load an email message and preserve its TNEF attachments, use the [MsgLoadOptions](https://reference.aspose.com/email/cpp/class/aspose.email.msg_load_options/) class and set the [PreserveTnefAttachments](https://reference.aspose.com/email/cpp/class/aspose.email.msg_load_options#a0eca988feb7db20fa39e1f657bce1eee) property to `true`.

The following example demonstrates how to load and display attachment names from a message containing TNEF data.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}







