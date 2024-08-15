---
title: "Ведение журнала активности IMapClient в Python"
url: /ru/python-net/imapclient-activity-logging/
weight: 40
type: docs
---


## **Включить ведение журнала активности**

Ведение журнала активности включает запись подключений к серверу, сведений о передаче отправленных и полученных сообщений, сообщений об ошибках во время обработки электронной почты и любых других действий, выполняемых клиентом или сервером. Чтобы отслеживать активность клиентов IMAP и взаимодействие с сервером, используйте следующий пример кода, в котором используется свойство log_file_name [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс для записи информации в указанный файл журнала:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```
