---
title: Manage Attachments in Outlook MSG Files Using Aspose.Email for C++
ArticleTitle: Manage Attachments in Outlook MSG Files 
linktitle: Working with Message Attachments
type: docs
weight: 70
url: /cpp/manage-outlook-msg-attachments/
description: Learn how to save, remove, and add attachments in Outlook MSG files using Aspose.Email for C++.
---

**Aspose.Email for C++** provides a rich API for accessing, saving, removing, and embedding attachments when working with Microsoft Outlook MSG files. Attachments are handled through the [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) class, using its `Attachments` property, which exposes a [MapiAttachmentCollection](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_attachment_collection).

## **Save Attachments from an MSG File**

To extract and save attachments from an MSG file:

1. Load the message using [MapiMessage::Load](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message#ad48c273564de4cc74907117bc62fd4ac).
2. Iterate through the [MapiAttachmentCollection](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_attachment_collection).
3. Save each attachment using the [MapiAttachment::Save()](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_attachment#a859598c4794757761e3b9b469e132805) method.

```cpp
// Create an instance of MapiMessage from file
System::SharedPtr<MapiMessage> message = MapiMessage::Load(fileName);
    
// Iterate through the attachments collection
    
{
    auto attachment_enumerator = (message->get_Attachments())->GetEnumerator();
    decltype(attachment_enumerator->get_Current()) attachment;
    while (attachment_enumerator->MoveNext() && (attachment = attachment_enumerator->get_Current(), true))
    {
        // Save the individual attachment
        attachment->Save(dataDir + attachment->get_FileName());
    }
}
```

## **Remove Attachments**

Aspose.Email for C++ offers two ways to remove attachments from MSG files:

- **Call the [RemoveAttachments()](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message#a15d2c8f06c732af9f8a941ba4670f4e7) method** 

It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object. This static helper method removes all attachments from a message file.

The following code snippet shows how to use this method.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

- **Call the [DestoryAttachment()](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message#a62f51f12ca13caefd6a7c11cfde1df14) method** 

It works faster because it removes attachments without fully parsing the MSG file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

## **Add MSG Attachments**

MSG files can contain other MSG files either as standard or embedded attachments. Use the overloaded `Add` methods in [MapiAttachmentCollection](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_attachment_collection/) to embed Outlook messages.

The following code sample demonstrates how to create a new MAPI message with specified sender, recipient, subject, and body, then attach an existing MSG file as an embedded message, and finally save the resulting message with the embedded attachment to a new MSG file.


```cpp
System::SharedPtr<MapiMessage> message = System::MakeObject<MapiMessage>(L"from@test.com", L"to@test.com", L"Subj", L"This is a message body");
System::SharedPtr<MapiMessage> attachMsg = MapiMessage::Load(L"Message.msg");
message->get_Attachments()->Add(L"Weekly report.msg", attachMsg);
message->Save(dataDir + L"WithEmbeddedMsg_out.msg");
```
