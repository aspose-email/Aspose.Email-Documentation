---
title: "Ведение журнала активности Pop3Client"
url: /ru/python-net/pop3client-activity-logging/
weight: 40
type: docs
---

## **Включить ведение журнала активности в программном коде**

Ведение журнала активности включает мониторинг и запись взаимодействий и операций, выполняемых пользователями и почтовыми клиентами при доступе к электронной почте и управлении ею с сервера POP3. Включенное ведение журнала активности позволяет устранять проблемы, связанные с электронной почтой, обеспечивать безопасность и соблюдение правил хранения данных и конфиденциальности.

В следующем примере кода показано, как включить ведение журнала активности с помощью Python API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.Pop3.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```