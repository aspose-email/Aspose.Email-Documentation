---
title: "Работа с параметром голосования с использованием MapiMessage"
url: /ru/cpp/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---

## **Создание параметра голосования с использованием MapiMessage**
Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Это позволяет им включать варианты голосования, такие как Да, Нет, Может быть и т.д. Aspose.Email предоставляет такую же возможность при создании нового сообщения Outlook. Класс FollowUpOptions предоставляет свойство VotingButtons, которое можно использовать для задания или получения значения вариантов голосования. Эта статья предоставляет подробный пример создания MapiMessage с вариантами голосования для создания опроса.
### **Чтение вариантов голосования из MapiMessage**
Следующий фрагмент кода показывает, как прочитать варианты голосования из MapiMessage.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVotingOptions-ReadingVotingOptions.cpp" >}}
### **Чтение только кнопок голосования**
Следующий фрагмент кода показывает, как читать только кнопки голосования.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cpp" >}}
### **Добавление кнопки голосования в существующее сообщение**
Следующий фрагмент кода показывает, как добавить кнопку голосования в существующее сообщение.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cpp" >}}
### **Удаление кнопки голосования из сообщения**
Следующий фрагмент кода показывает, как удалить кнопку голосования из сообщения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cpp" >}}
### **Чтение информации о результатах голосования**
Следующий фрагмент кода показывает, как прочитать информацию о результатах голосования.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cpp" >}}