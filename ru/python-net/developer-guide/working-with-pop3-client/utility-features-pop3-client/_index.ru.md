---
title: "Утилита Функции - POP3 Клиент"
url: /ru/python-net/utility-features-pop3-client/
weight: 30
type: docs
---

## **Проверка Учетных Данных Почтового Серверa**

Aspose.Email предоставляет метод 'validate_credentials()' класса [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) для проверки учетных данных (имя пользователя и пароль), предоставленных пользователем для доступа к почтовому серверу POP3. Этот метод гарантирует, что учетные данные пользователя точны и действительны, что позволяет успешно пройти аутентификацию и получить доступ к своей учетной записи электронной почты с использованием протокола POP3. Если предоставленные учетные данные неверны, метод может вернуть ошибку или выбросить исключение, указывая на то, что процесс входа в систему не удался.

Ниже приведен код, демонстрирующий метод проверки, предоставленный API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```