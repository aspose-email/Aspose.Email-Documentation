---
title: "Регистрация активности Pop3Client"
url: /ru/python-net/pop3client-activity-logging/
weight: 40
type: docs
---

## **Включение регистрации активности в коде программы**

Регистрация активности включает в себя мониторинг и запись взаимодействий и операций, выполняемых пользователями и почтовыми клиентами при получении и управлении электронной почтой с сервера POP3. Включенная регистрация активности позволяет диагностировать проблемы, связанные с электронной почтой, поддерживать безопасность и обеспечивать соблюдение норм хранения данных и конфиденциальности.

Следующий пример кода демонстрирует, как включить регистрацию активности с помощью Python API: 

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.Pop3.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```