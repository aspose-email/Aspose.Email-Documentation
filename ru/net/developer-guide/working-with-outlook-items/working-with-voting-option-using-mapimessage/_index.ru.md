---
title: "Работа с вариантами голосования с помощью MapiMessage"
url: /ru/net/working-with-voting-option-using-mapimessage/
weight: 50
type: docs
---


## **Создание варианта голосования с помощью MapiMessage**

Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Он позволяет им включать варианты голосования, такие как Да, Нет, Может быть и т.д. Aspose.Email предлагает аналогичные возможности при создании нового сообщения Outlook. Класс [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) предоставляет свойство [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/), которое можно использовать для установки или получения значения вариантов голосования. Эта статья представляет собой подробный пример создания [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с вариантами голосования для создания опроса.

### **Создание опроса с помощью MapiMessage**

Следующий код показывает, как создать опрос, класс [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) можно использовать, как показано в следующем коде.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Чтение вариантов голосования из MapiMessage**

Следующий код показывает, как читать варианты голосования из [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Чтение только кнопок голосования**

Следующий код показывает, как читать только кнопки голосования.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Добавление кнопки голосования в существующее сообщение**

Следующий код показывает, как добавить кнопку голосования к существующему сообщению.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Удаление кнопки голосования из сообщения**

Следующий код показывает, как удалить кнопку голосования из сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Чтение информации о результатах голосования**

Следующий код показывает, как читать информацию о результатах голосования.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Методы примерa, используемые в примерах**

Следующий код показывает, как создать тестовое сообщение, использованное в примерах.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}