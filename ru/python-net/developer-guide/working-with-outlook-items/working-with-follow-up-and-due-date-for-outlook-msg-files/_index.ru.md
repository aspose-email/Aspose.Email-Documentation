---
title: "Работа с флагом "Напомнить" и сроком исполнения для файлов MSG Outlook"
url: /ru/python-net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


Флаг "Напомнить" помечает электронное сообщение для выполнения каких-либо действий. Microsoft Outlook позволяет пользователям помечать сообщения, а в настройках флага назначать срок исполнения для напоминания. Microsoft Outlook отправляет напоминание получателю, чтобы побудить его ответить на электронное сообщение. Программное управление пометкой электронных писем и установкой сроков исполнения позволяет разработчикам программного обеспечения автоматизировать определенные типы электронных писем и помогать получателям помнить о необходимости предпринять действия. Например, это может использоваться для отправки ежемесячных сообщений команде продаж, чтобы напомнить им о необходимости завершить свои отчеты; или для отправки сообщения всем сотрудникам, чтобы напомнить им о корпоративной встрече. Aspose.Email для .NET поддерживает установку флага "Напомнить" и срока исполнения для объектов MapiMessage с использованием FollowUpManager и FollowUpOptions. Существует несколько вариантов, как можно установить флаг "Напомнить" на сообщение. Все они используются в приведенном ниже примере кода:

1. Установить флаг "Напомнить" для сообщения
1. Добавить срок исполнения и дату напоминания к сообщению
1. Добавить флаг к сообщению получателя.
1. Отметить как завершенное.
1. Удалить флаг.
1. Прочитать параметры напоминания.

## **Установка флага "Напомнить"**

Следующий фрагмент кода показывает, как установить флаг "Напомнить".

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Создать новое MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Это сообщение протестирует возможность добавления опций напоминания к новому сообщению MAPI."

# Преобразовать MailMessage в MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Определить параметры напоминания
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Follow Up", dt_start_date, dt_due_date, dt_reminder_date)

# Установить параметры напоминания для MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Сохранить MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Установка напоминания для получателей**

Следующий фрагмент кода показывает, как установить напоминание для получателей.

```py
import aspose.email as ae
from datetime import datetime

# Создать новое MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Это сообщение протестирует возможность добавления опций напоминания к новому сообщению MAPI."

# Преобразовать MailMessage в MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Отметить сообщение как черновик
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Добавить флаг напоминания для получателей
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Follow up", dt_reminder_date)

# Сохранить MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Отметка флага "Напомнить" как завершенного**

Следующий фрагмент кода показывает, как отметить флаг "Напомнить" как завершенный.

```py
import aspose.email as ae

# Загрузить MapiMessage из файла
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Отметить сообщение как завершенное
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Сохранить обновленный MapiMessage
mapi_message.save("MarkedCompleted_out.msg")
```

## **Удаление флага "Напомнить"**

Следующий фрагмент кода показывает, как удалить флаг "Напомнить".

```py
import aspose.email as ae

# Загрузить MapiMessage из файла
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Очистить флаг напоминания
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Сохранить обновленный MapiMessage
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Чтение опций флага напоминания для сообщения**

Следующий фрагмент кода показывает, как прочитать опции флага напоминания для сообщения.

```py
import aspose.email as ae

# Загрузить MapiMessage из файла
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Получить параметры напоминания
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```