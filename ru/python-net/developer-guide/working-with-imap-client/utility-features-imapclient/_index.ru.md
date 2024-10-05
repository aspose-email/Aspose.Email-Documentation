---
title: "Утилитные функции для IMAP клиента на Python"
url: /ru/python-net/utility-features-imap-client/
weight: 40
type: docs
---


## **Проверка учетных данных почтового сервера**

Для установления безопасного соединения с IMAP сервером перед выполнением дальнейших действий проверяются и подтверждаются учетные данные пользователя. Метод 'validate_credentials' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) помогает проверить, являются ли указанные имя пользователя и пароль верными. Если учетные данные действительно действительны, клиент может успешно аутентифицироваться на IMAP сервере. Следующий пример кода показывает, как реализовать этот метод в вашем проекте:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```