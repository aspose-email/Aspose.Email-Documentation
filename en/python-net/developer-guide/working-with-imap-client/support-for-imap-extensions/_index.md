---
title: Support for IMAP Extensions
ArticleTitle: Support for IMAP Extensions
type: docs
weight: 110
url: /python-net/support-for-imap-extensions/
---


## **Support for IMAP Extensions**

Aspose.Email API provides support for IMAP extensions. The following IMAP extensions are supported by the API at present. These IMAP extensions are not supported by all servers.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    # Set SecurityOptions
    client.security_options = ae.clients.SecurityOptions.AUTO
    print(client.id_supported)

    server_identification_info1 = client.introduce_client()
    server_identification_info2 = client.introduce_client(ae.clients.imap.ImapIdentificationInfo.default_value)

    # Display ImapIdentificationInfo properties
    print(server_identification_info1)
    print(server_identification_info2)
    print(server_identification_info1.name)
    print(server_identification_info1.vendor)
    print(server_identification_info1.support_url)
    print(server_identification_info1.version)
```

### **IMAP4 Extended List Command**

The following code snippet shows you how to use IMAP4 extended list command.

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
