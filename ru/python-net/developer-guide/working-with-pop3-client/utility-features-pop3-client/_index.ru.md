---
title: "Функции утилиты — клиент POP3"
url: /ru/python-net/utility-features-pop3-client/
weight: 30
type: docs
---

## **Подтвердить учетные данные почтового сервера**

Aspose.Email предоставляет метод validate_credentials () [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) класс для проверки учетных данных (имени пользователя и пароля), предоставленных пользователем для доступа к почтовому серверу POP3. Этот метод обеспечивает точность и действительность учетных данных пользователя, что позволяет ему успешно аутентифицироваться и получить доступ к своей учетной записи электронной почты по протоколу POP3. Если предоставленные учетные данные неверны, метод может вернуть ошибку или вызвать исключение, указывающее на сбой процесса входа в систему.

Приведенный ниже фрагмент кода демонстрирует метод проверки, предоставляемый API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```