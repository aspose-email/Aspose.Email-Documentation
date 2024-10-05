---
title: "Журналирование активности ImapClient в Python"
url: /ru/python-net/imapclient-activity-logging/
weight: 40
type: docs
---


## **Включить журналирование активности**

Журналирование активности включает запись соединений с сервером, детали передачи сообщений, отправленных и полученных, сообщения об ошибках во время обработки электронной почты и любые другие действия, выполняемые клиентом или сервером. Чтобы отслеживать активность IMAP-клиента и взаимодействия с сервером, используйте следующий пример кода, который использует свойство 'log_file_name' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) для записи информации в указанный файл журнала:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Установите путь к файлу журнала с помощью свойства LogFileName.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Установите свойство UseDateInLogFileName, если это необходимо.
client.use_date_in_log_file_name = False
```