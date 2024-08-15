---
title: "Работа с опцией голосования с помощью MapiMessage"
url: /ru/cpp/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---

## **Создание опции голосования с помощью MapiMessage**
Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Это позволяет им включать такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Aspose.Email позволяет использовать то же самое при создании нового сообщения Outlook. Класс FollowupOptions предоставляет свойство VotingButtons, которое можно использовать для установки или получения значений параметров голосования. В этой статье приведен подробный пример создания MapiMessage с опциями голосования для создания опроса.
### **Чтение вариантов голосования из MapiMessage**
В следующем фрагменте кода показано, как читать параметры голосования из MapiMessage.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVotingOptions-ReadingVotingOptions.cpp" >}}
### **Кнопки голосования только для чтения**
В следующем фрагменте кода показано, как читать только кнопки голосования.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cpp" >}}
### **Добавление кнопки голосования в существующее сообщение**
В следующем фрагменте кода показано, как добавить кнопку голосования к существующему сообщению.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cpp" >}}
### **Удаление кнопки голосования из сообщения**
В следующем фрагменте кода показано, как удалить кнопку голосования из сообщения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cpp" >}}
### **Ознакомьтесь с информацией о результатах голосования**
В следующем фрагменте кода показано, как читать информацию о результатах голосования.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cpp" >}}
