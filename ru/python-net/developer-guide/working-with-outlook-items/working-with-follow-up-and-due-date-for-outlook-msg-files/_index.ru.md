---
title: "Работа с отслеживанием и сроками выполнения файлов Outlook MSG"
url: /ru/python-net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


Флаг отслеживания означает, что в сообщении электронной почты содержится какое-либо действие. Microsoft Outlook позволяет пользователям отмечать сообщения и при настройке флага назначать срок отправки последующих сообщений. Microsoft Outlook отправляет получателю напоминание с просьбой ответить на сообщение электронной почты. Пометка писем и программная настройка сроков выполнения позволяют разработчикам программного обеспечения автоматизировать определенные типы электронных писем и помогать получателям не забывать принимать меры. Например, его можно использовать для отправки ежемесячных сообщений отделу продаж с напоминанием о необходимости заполнения отчетов или для отправки всем сотрудникам сообщений с напоминанием о собрании компании. Aspose.Email для .NET поддерживает настройку флага отслеживания и срока выполнения для объектов MapiMessage с помощью FollowupManager и FollowupOptions. Существует несколько вариантов, в которых флаг отслеживания может быть установлен на сообщении. Все они используются в приведенном ниже примере кода:

1. Установите флаг отслеживания для сообщения
1. Добавьте к сообщению срок и дату напоминания
1. Добавьте флаг к сообщению получателя.
1. Отметить как завершенное.
1. Удалить флаг.
1. Ознакомьтесь с вариантами последующих действий.

## **Настройка флага FollowUp**

В следующем фрагменте кода показано, как установить флаг FollowUp.

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Define follow-up options
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Follow Up", dt_start_date, dt_due_date, dt_reminder_date)

# Set follow-up options for the MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Save the MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Настройка отслеживания получателей**
В следующем фрагменте кода показано, как настроить отслеживание получателей.

```py
import aspose.email as ae
from datetime import datetime

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Mark the message as draft
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Add the follow-up flag for recipients
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Follow up", dt_reminder_date)

# Save the MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Пометка флага FollowUp как завершенного**

В следующем фрагменте кода показано, как пометить флаг FollowUp как завершенный.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Mark the message as completed
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Save the updated MapiMessage
mapi_message.save("MarkedCompleted_out.msg")
```
## **Удаление флага FollowUp**
В следующем фрагменте кода показано, как удалить флаг FollowUp.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Clear the follow-up flag
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Save the updated MapiMessage
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Прочитайте варианты флагов отслеживания сообщения**

В следующем фрагменте кода показано, как прочитать опции флага отслеживания для сообщения.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Get the follow-up options
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```
