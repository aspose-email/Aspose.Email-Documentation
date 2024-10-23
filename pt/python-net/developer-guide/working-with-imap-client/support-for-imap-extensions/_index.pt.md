---
title: "Suporte para Extensões IMAP"
url: /pt/python-net/support-for-imap-extensions/
weight: 110
type: docs
---


## **Suporte para Extensões IMAP**

A API Aspose.Email fornece suporte para extensões IMAP. As seguintes extensões IMAP são suportadas pela API atualmente. Essas extensões IMAP não são suportadas por todos os servidores.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    # Definir SecurityOptions
    client.security_options = ae.clients.SecurityOptions.AUTO
    print(client.id_supported)

    server_identification_info1 = client.introduce_client()
    server_identification_info2 = client.introduce_client(ae.clients.imap.ImapIdentificationInfo.default_value)

    # Exibir propriedades de ImapIdentificationInfo
    print(server_identification_info1)
    print(server_identification_info2)
    print(server_identification_info1.name)
    print(server_identification_info1.vendor)
    print(server_identification_info1.support_url)
    print(server_identification_info1.version)
```

### **Comando IMAP4 Lista Estendida**

O seguinte trecho de código mostra como usar o comando de lista estendida IMAP4.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    folder_info_col = client.list_folders("*")
    print("Lista Estendida Suportada:", client.extended_list_supported)

    for folder_info in folder_info_col:
        folder_name = folder_info.name

        if folder_name == "[Gmail]/Todos os e-mails":
            print("Tem Filhos:", folder_info.has_children)
        elif folder_name == "[Gmail]/Lixeira":
            print("A Lixeira tem filhos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Rascunhos":
            print("Rascunhos tem filhos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Importante":
            print("Importante tem Filhos?", folder_info.has_children)
        elif folder_name == "[Gmail]/E-mails Enviados":
            print("E-mails Enviados têm Filhos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Spam":
            print("Spam tem Filhos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Destacados":
            print("Destacados têm Filhos?", folder_info.has_children)
```