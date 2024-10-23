---
title: "Recursos de Utilidade para Cliente IMAP em Python"
url: /pt/python-net/utility-features-imap-client/
weight: 40
type: docs
---


## **Validar Credenciais do Servidor de Email**

Para estabelecer uma conexão segura com um servidor IMAP antes de realizar outras ações, as credenciais do usuário são verificadas e validadas. O método 'validate_credentials' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) ajuda a verificar se o nome de usuário e a senha fornecidos estão corretos. Se as credenciais forem realmente válidas, o cliente pode autenticar com sucesso no servidor IMAP. O seguinte exemplo de código mostra como implementar esse método em seu projeto:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```