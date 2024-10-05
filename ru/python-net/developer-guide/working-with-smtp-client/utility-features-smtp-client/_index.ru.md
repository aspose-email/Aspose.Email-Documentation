---
title: "Утилитарные функции - SMTP клиент"
url: /ru/python-net/utility-features-smtp-client/
weight: 30
type: docs
---


## **Получение расширений сервера с использованием SMTP клиента**
Pop3Client от Aspose.Email позволяет получить расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для этой конкретной функции. Метод GetCapabilities() возвращает поддерживаемые типы расширений в виде массива строк.
### **Получение расширений сервера**
Следующий кодовый фрагмент показывает, как получить расширения сервера.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Проверка учетных данных почтового сервера без отправки электронной почты**

Метод 'validate_credentials()' класса [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) используется для проверки действительности предоставленных учетных данных путем установления соединения с SMTP сервером. Если учетные данные действительны и соединение успешно, можно выполнить дальнейшие действия. Следующий кодовый пример можно использовать для проверки учетных данных, предоставленных для аутентификации с SMTP сервером, без отправки электронной почты:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```