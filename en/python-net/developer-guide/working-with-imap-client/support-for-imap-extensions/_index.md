---
title: Enable IMAP Extensions using Python API
ArticleTitle: Enable IMAP Extensions
type: docs
weight: 110
url: /python-net/imap-extensions-support-python/
---


## **IMAP Extensions Support**

Aspose.Email API provides support for a range of IMAP protocol extensions. These extensions enable advanced operations such as identifying client applications and retrieving detailed mailbox metadata. While not all email servers support these features, many popular services like Gmail do.

This article demonstrates how to use the following IMAP extensions with the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/) class in Aspose.Email:

- **IMAP ID Command**

- **IMAP LIST-EXTENDED Command**

### **Using the IMAP ID Command**

This command provides feedback on whether the server supports the IMAP ID extension and returns structured identification details from the server.
This can be useful for logging, diagnostics, and server behavior customization.

The following code sample demonstrates how to use the Aspose.Email library to interact with an IMAP server, specifically to retrieve server identification information using the ID command:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:

    # Set security options
    client.security_options = ae.clients.SecurityOptions.AUTO

    # Check if ID command is supported
    print(client.id_supported)

    # Send identification info to the server
    server_identification_info1 = client.introduce_client()
    server_identification_info2 = client.introduce_client(ae.clients.imap.ImapIdentificationInfo.default_value)

    # Display server response
    print(server_identification_info1)
    print(server_identification_info2)
    print(server_identification_info1.name)
    print(server_identification_info1.vendor)
    print(server_identification_info1.support_url)
    print(server_identification_info1.version)
```

### **Using the IMAP LIST-EXTENDED Command**

The IMAP LIST-EXTENDED command (defined in RFC 5258) allows clients to retrieve detailed folder hierarchies and metadata, such as whether folders have child folders. This is especially useful for clients managing complex mailbox structures.

The following code sample demonstrates how to list folders in Gmail using the extended LIST command and verify which folders contain subfolders:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    folder_info_col = client.list_folders("*")
    print("Extended List Supported:", client.extended_list_supported)

    for folder_info in folder_info_col:
        folder_name = folder_info.name

        if folder_name == "[Gmail]/All Mail":
            print("Has Children:", folder_info.has_children)
        elif folder_name == "[Gmail]/Bin":
            print("Bin has children?", folder_info.has_children)
        elif folder_name == "[Gmail]/Drafts":
            print("Drafts has children?", folder_info.has_children)
        elif folder_name == "[Gmail]/Important":
            print("Important has Children?", folder_info.has_children)
        elif folder_name == "[Gmail]/Sent Mail":
            print("Sent Mail has Children?", folder_info.has_children)
        elif folder_name == "[Gmail]/Spam":
            print("Spam has Children?", folder_info.has_children)
        elif folder_name == "[Gmail]/Starred":
            print("Starred has Children?", folder_info.has_children)
```
