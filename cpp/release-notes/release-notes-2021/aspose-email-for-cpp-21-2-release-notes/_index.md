---
title: Aspose.Email for CPP 21.2 Release Notes
type: docs
weight: 2
url: /cpp/aspose-email-for-cpp-21-2-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for Aspose.Email for C++ 21.2.

{{% /alert %}} 

Aspose.Email for C++ 21.2 is based on [Aspose.Email for .NET 21.2](https://docs.aspose.com/email/net/aspose-email-for-net-21-2-release-notes/).

## **New Enhancements**

### **Getting Message Modified Date in OLM**
An **OlmMessageInfo.get_ModifiedDate()** method has been added to get the message modified date.

Code sample:
```cs
for (System::SharedPtr<OlmMessageInfo> messageInfo : System::IterateOver(inboxFolder->EnumerateMessages()))
{
    System::DateTime modifiedDate = messageInfo->get_ModifiedDate();
}
```

The full code of the example can be found at **[Aspose Email for C++ GitHub examples repository](https://github.com/aspose-email/Aspose.Email-for-C).**
