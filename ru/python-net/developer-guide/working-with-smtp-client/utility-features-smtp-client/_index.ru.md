---
title: "Функции утилиты — SMTP-клиент"
url: /ru/python-net/utility-features-smtp-client/
weight: 30
type: docs
---


## **Список серверов расширений с использованием клиента Smtp**
Pop3Client от Aspose.Email позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. Метод getCapabilities () возвращает поддерживаемые типы расширений в виде строкового массива.
### **Получение серверных расширений**
В следующем фрагменте кода показано, как извлекать серверные расширения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Подтвердите учетные данные почтового сервера без отправки электронной почты**

Метод validate_credentials () [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) класс используется для проверки достоверности предоставленных учетных данных путем установления соединения с SMTP-сервером. Если учетные данные действительны и соединение установлено успешно, можно выполнить дальнейшие действия. Следующий пример кода можно использовать для проверки учетных данных, предоставленных для аутентификации на SMTP-сервере, без отправки электронного письма:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```
