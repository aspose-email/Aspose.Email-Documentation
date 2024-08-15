---
title: "Функции утилиты для клиента IMAP на Python"
url: /ru/python-net/utility-features-imap-client/
weight: 40
type: docs
---


## **Подтвердить учетные данные почтового сервера**

Чтобы установить безопасное соединение с сервером IMAP перед выполнением дальнейших действий, учетные данные пользователя проверяются и проверяются. Метод validate_credentials, используемый в [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс помогает проверить правильность введенных имени пользователя и пароля. Если учетные данные действительно действительны, клиент может успешно пройти аутентификацию на сервере IMAP. В следующем примере кода показано, как внедрить этот метод в свой проект:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```
