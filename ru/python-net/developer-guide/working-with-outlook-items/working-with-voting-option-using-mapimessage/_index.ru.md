---
title: "Работа с вариантами голосования с использованием MapiMessage"
url: /ru/python-net/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---


## **Создание варианта голосования с использованием MapiMessage**
Microsoft Outlook позволяет пользователям создавать опрос при написании нового сообщения. Он позволяет им включать варианты голосования, такие как Да, Нет, Может быть и т.д. Aspose.Email позволяет сделать то же самое при создании нового сообщения Outlook. Класс [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) предоставляет свойство VotingButtons, которое можно использовать для установки или получения значения вариантов голосования. В этой статье приводится подробный пример создания MapiMessage с вариантами голосования для создания опроса.

### **Создание опроса с использованием MapiMessage**

Следующий пример кода показывает, как использовать свойство *voting_buttons* класса [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) для создания опроса:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Установка кнопок FollowUpOptions
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Yes;No;Maybe;Exactly!"

msg.save("voting_btns.msg")
```

### **Чтение вариантов голосования из MapiMessage**
Следующий фрагмент кода показывает, как читать варианты голосования из MapiMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}


### **Чтение только кнопок голосования**
Следующий фрагмент кода показывает, как читать только кнопки голосования.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Добавление кнопки голосования к существующему сообщению**
Следующий фрагмент кода показывает, как добавить кнопку голосования к существующему сообщению.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Удаление кнопки голосования из сообщения**
Следующий фрагмент кода показывает, как удалить кнопку голосования из сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Чтение информации о результатах голосования**
Следующий фрагмент кода показывает, как читать информацию о результатах голосования.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Установка флага несообщенного сообщения**
Следующий фрагмент кода показывает, как использовать методы, используемые в примерах.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Помеченное сообщение", "Сделайте его приятным и коротким, но описательным. Описание может появляться на страницах результатов поиска поисковых систем...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```