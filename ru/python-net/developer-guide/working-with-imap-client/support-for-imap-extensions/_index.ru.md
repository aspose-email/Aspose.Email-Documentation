---
title: "Поддержка расширений IMAP"
url: /ru/python-net/support-for-imap-extensions/
weight: 110
type: docs
---


## **Поддержка расширений IMAP**

API Aspose.Email обеспечивает поддержку расширений IMAP. В настоящее время API поддерживает следующие расширения IMAP. Эти расширения IMAP поддерживаются не всеми серверами.

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

### **Команда расширенного списка IMAP4**

В следующем фрагменте кода показано, как использовать команду IMAP4 extended list.

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
