---
title: Aspose.Email for CPP 21.5 Release Notes
type: docs
weight: 2
url: /cpp/aspose-email-for-cpp-21-6-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for Aspose.Email for C++ 21.6.

{{% /alert %}} 

Aspose.Email for C++ 21.6 is based on [Aspose.Email for .NET 21.6](https://docs.aspose.com/email/net/aspose-email-for-net-21-6-release-notes/).

## **New Enhancements**

### **Using a return-client-request-id HTTP header in the EWSClient**

The `return-client-request-id` header is sent in the request and used by the server to determine whether the `client-request-id` header specified by the client should be returned in the server response.

We have added the `get_ReturnClientRequestId` and `set_ReturnClientRequestId` methods to `EWSClient`:

```cpp
// Gets a flag to indicate whether the client requires the server side to return the  request id.
bool get_ReturnClientRequestId();
// Sets a flag to indicate whether the client requires the server side to return the  request id.
void set_ReturnClientRequestId(bool value);
```

**Code sample:**

```cpp
System::String user_email = u"xxx";
System::String user_password = u"xxx";
System::String server_url = u"xxx";

System::SharedPtr<System::Net::NetworkCredential> credentials = System::MakeObject<System::Net::NetworkCredential>(user_email, user_password);
System::SharedPtr<IEWSClient> client = EWSClient::GetEWSClient(server_url, credentials);
// Client will create random id and pass it to the server.
// The server should include this id in request-id header of all responses.
client->set_ReturnClientRequestId(true);

client->GetMailboxInfo();
```

The full code of the example can be found at **[Aspose Email for C++ GitHub examples repository](https://github.com/aspose-email/Aspose.Email-for-C).**

