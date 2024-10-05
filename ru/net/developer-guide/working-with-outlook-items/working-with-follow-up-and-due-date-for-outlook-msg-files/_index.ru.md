---
title: "Работа с напоминаниями и сроками исполнения для файлов Outlook MSG"
url: /ru/net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 60
type: docs
---


## **Настройка напоминаний и сроков исполнения для файлов Outlook MSG**

Флаг напоминания помечает электронное письмо для выполнения какого-либо действия. Microsoft Outlook позволяет пользователям устанавливать флаги для сообщений и в настройках флага назначать срок исполнения для напоминания. Microsoft Outlook отправляет напоминание получателю, чтобы побудить его ответить на электронное письмо. Программное назначение флагов для электронных писем и установка сроков исполнения позволяет разработчикам программного обеспечения автоматизировать определенные типы электронных писем и помогать получателям помнить о необходимости действий. Например, это может использоваться для отправки ежемесячных сообщений команде продаж, чтобы напомнить им о необходимости завершить свои отчеты; или для отправки сообщения всем сотрудникам, чтобы напомнить им о собрании компании. Aspose.Email для .NET поддерживает установку флага напоминания и срока исполнения для объектов [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с использованием [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) и [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). Существует несколько вариантов, как можно установить флаг напоминания на сообщение. Все они используются в приведенном ниже примере кода:

1. Установить флаг напоминания для сообщения
1. Добавить срок исполнения и дату напоминания к сообщению
1. Добавить флаг к сообщению получателя.
1. Отметить как выполненное.
1. Удалить флаг.
1. Прочитать параметры напоминания.

### **Установка флага FollowUp**

Следующий фрагмент кода показывает, как установить флаг напоминания.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Установка напоминаний для получателей**

Следующий фрагмент кода показывает, как установить напоминания для получателей.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Отметка флага FollowUp как выполненного**

Следующий фрагмент кода показывает, как отметить флаг напоминания как выполненный.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Удаление флага FollowUp**

Следующий фрагмент кода показывает, как удалить флаг напоминания.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Чтение параметров флага напоминания для сообщения**

Следующий фрагмент кода показывает, как прочитать параметры флага напоминания для сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}