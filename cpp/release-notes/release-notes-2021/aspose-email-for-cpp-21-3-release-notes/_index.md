---
title: Aspose.Email for CPP 21.3 Release Notes
type: docs
weight: 2
url: /cpp/aspose-email-for-cpp-21-3-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for Aspose.Email for C++ 21.3.

{{% /alert %}} 

Aspose.Email for C++ 21.3 is based on [Aspose.Email for .NET 21.3](https://docs.aspose.com/email/net/aspose-email-for-net-21-3-release-notes/).

## **New Enhancements**

### **Getting information about bulk messages sent**
When you send messages in bulk, you can get an information about the number of successfully sent messages and moreover, it is possible to get a list of these messages. 
A new **SucceededSending** event was added to **SmtpClient** for this purpose.

Code sample:
```cpp
System::SharedPtr<SmtpClient> client = TestUtil::CreateSmtpClient(host, SecurityOptions::Auto);
int messageCount = 0;

auto eventHandler = [&](System::SharedPtr<System::Object> sender, System::SharedPtr<MailMessageEventArgs> evntArgs) -> void
{
    System::Console::WriteLine(u"The message '{0}' was successfully sent.", evntArgs->get_Message()->get_Subject());
    messageCount++;
};

client->SucceededSending_add(eventHandler);
client->Send(messages);
System::Console::Console::WriteLine(u"{0} messages were successfully sent.", messageCount);
```
### **LinkedResource.ContentDisposition property**

A **LinkedResource.ContentDisposition** property has been added to get Content-Disposition header.

Code sample:

```cpp
System::SharedPtr<MailMessage> eml = MailMessage::Load(fileName);
eml->get_LinkedResources()->idx_get(0)->get_ContentDisposition()->set_FileName(u"changed.png");
```

The full code of the example can be found at **[Aspose Email for C++ GitHub examples repository](https://github.com/aspose-email/Aspose.Email-for-C).**
