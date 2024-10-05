---
title: "Поддержка расширений IMAP"
url: /ru/python-net/support-for-imap-extensions/
weight: 110
type: docs
---


## **Поддержка расширений IMAP**

Aspose.Email API предоставляет поддержку расширений IMAP. В настоящее время API поддерживает следующие расширения IMAP. Эти расширения IMAP не поддерживаются всеми серверами.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    # Установить SecurityOptions
    client.security_options = ae.clients.SecurityOptions.AUTO
    print(client.id_supported)

    server_identification_info1 = client.introduce_client()
    server_identification_info2 = client.introduce_client(ae.clients.imap.ImapIdentificationInfo.default_value)

    # Отобразить свойства ImapIdentificationInfo
    print(server_identification_info1)
    print(server_identification_info2)
    print(server_identification_info1.name)
    print(server_identification_info1.vendor)
    print(server_identification_info1.support_url)
    print(server_identification_info1.version)
```

### **Расширенная команда списка IMAP4**

Следующий фрагмент кода показывает, как использовать расширенную команду списка IMAP4.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    folder_info_col = client.list_folders("*")
    print("Расширенный список поддерживается:", client.extended_list_supported)

    for folder_info in folder_info_col:
        folder_name = folder_info.name

        if folder_name == "[Gmail]/Все письма":
            print("Есть вложения:", folder_info.has_children)
        elif folder_name == "[Gmail]/Корзина":
            print("В корзине есть вложения?", folder_info.has_children)
        elif folder_name == "[Gmail]/Черновики":
            print("В черновиках есть вложения?", folder_info.has_children)
        elif folder_name == "[Gmail]/Важно":
            print("Важно есть вложения?", folder_info.has_children)
        elif folder_name == "[Gmail]/Отправленные":
            print("В отправленных есть вложения?", folder_info.has_children)
        elif folder_name == "[Gmail]/Спам":
            print("В спаме есть вложения?", folder_info.has_children)
        elif folder_name == "[Gmail]/Звездные":
            print("В звездных есть вложения?", folder_info.has_children)
```