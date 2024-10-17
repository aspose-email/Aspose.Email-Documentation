---
title: "Soporte para Extensiones IMAP"
url: /es/python-net/support-for-imap-extensions/
weight: 110
type: docs
---


## **Soporte para Extensiones IMAP**

La API de Aspose.Email proporciona soporte para extensiones IMAP. Las siguientes extensiones IMAP son compatibles con la API en la actualidad. Estas extensiones IMAP no son compatibles con todos los servidores.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    # Establecer SecurityOptions
    client.security_options = ae.clients.SecurityOptions.AUTO
    print(client.id_supported)

    server_identification_info1 = client.introduce_client()
    server_identification_info2 = client.introduce_client(ae.clients.imap.ImapIdentificationInfo.default_value)

    # Mostrar propiedades de ImapIdentificationInfo
    print(server_identification_info1)
    print(server_identification_info2)
    print(server_identification_info1.name)
    print(server_identification_info1.vendor)
    print(server_identification_info1.support_url)
    print(server_identification_info1.version)
```

### **Comando de Lista Extendida IMAP4**

El siguiente fragmento de código muestra cómo usar el comando de lista extendida IMAP4.

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("imap.gmail.com", 993, "username", "password") as client:
    folder_info_col = client.list_folders("*")
    print("Lista Extendida Soportada:", client.extended_list_supported)

    for folder_info in folder_info_col:
        folder_name = folder_info.name

        if folder_name == "[Gmail]/Todos los correos":
            print("Tiene hijos:", folder_info.has_children)
        elif folder_name == "[Gmail]/Papelera":
            print("¿La papelera tiene hijos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Borradores":
            print("¿Los borradores tienen hijos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Importante":
            print("¿Importante tiene hijos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Correos enviados":
            print("¿Correos enviados tienen hijos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Spam":
            print("¿Spam tiene hijos?", folder_info.has_children)
        elif folder_name == "[Gmail]/Destacados":
            print("¿Destacados tienen hijos?", folder_info.has_children)
```