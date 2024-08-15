---
title: "Работа с отслеживанием и сроками выполнения файлов Outlook MSG"
url: /ru/net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 60
type: docs
---


## **Настройка сроков и сроков выполнения файлов Outlook MSG**

Флаг «Повторное действие» отмечает сообщение электронной почты, требующее какого-либо действия. Microsoft Outlook позволяет пользователям отмечать сообщения и при настройке флага назначать срок выполнения последующих действий. Microsoft Outlook отправляет получателю напоминание с просьбой ответить на сообщение электронной почты. Пометка писем и программная настройка сроков выполнения позволяют разработчикам программного обеспечения автоматизировать определенные типы электронных писем и помогать получателям не забывать принимать меры. Например, его можно использовать для отправки ежемесячных сообщений отделу продаж с напоминанием о необходимости заполнения отчетов или для отправки всем сотрудникам сообщений с напоминанием о собрании компании. Aspose.Email для .NET поддерживает настройку флажка и срока выполнения [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) объекты, использующие [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). Существует несколько вариантов, в которых на сообщении можно установить следующий флаг. Все они используются в приведенном ниже примере кода:

1. Установите флажок отслеживания для сообщения
1. Добавьте к сообщению срок и дату напоминания
1. Добавьте флаг к сообщению получателя.
1. Отметить как завершенное.
1. Удалить флаг.
1. Ознакомьтесь с вариантами последующих действий.

### **Настройка флага FollowUp**

В следующем фрагменте кода показано, как установить дополнительный флаг.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Настройка отслеживания получателей**

В следующем фрагменте кода показано, как настроить отслеживание для получателей.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Пометка флага FollowUp как завершенного**

В следующем фрагменте кода показано, как пометить следующий флаг как завершенный.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Удаление флага FollowUp**

В следующем фрагменте кода показано, как удалить последующий флаг.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Прочитайте варианты флагов отслеживания сообщения**

В следующем фрагменте кода показано, как прочитать варианты последующих флагов для сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}
