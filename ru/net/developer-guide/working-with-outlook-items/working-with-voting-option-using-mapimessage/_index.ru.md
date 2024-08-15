---
title: "Работа с опцией голосования с помощью MapiMessage"
url: /ru/net/working-with-voting-option-using-mapimessage/
weight: 50
type: docs
---


## **Создание опции голосования с помощью MapiMessage**

Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Это позволяет им включать такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Aspose.Email позволяет использовать то же самое при создании нового сообщения Outlook. [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) класс предоставляет [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) свойство, которое можно использовать для установки или получения значения опций голосования. В этой статье представлен подробный пример создания [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с вариантами голосования для создания опроса.

### **Создание опроса с помощью MapiMessage**

В следующем фрагменте кода показано, как создать опрос, [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) класс можно использовать, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Чтение вариантов голосования из MapiMessage**

В следующем фрагменте кода показано, как читать варианты голосования из [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Кнопки голосования только для чтения**

В следующем фрагменте кода показано, как читать только кнопки голосования.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Добавление кнопки голосования к существующему сообщению**

В следующем фрагменте кода показано, как добавить кнопку голосования к существующему сообщению.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Удаление кнопки голосования из сообщения**

В следующем фрагменте кода показано, как удалить кнопку голосования из сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Ознакомьтесь с информацией о результатах голосования**

В следующем фрагменте кода показано, как читать информацию о результатах голосования.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Примерные методы, используемые в примерах**

В следующем фрагменте кода показано, как создать образец сообщения, используемый в примерах.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}
