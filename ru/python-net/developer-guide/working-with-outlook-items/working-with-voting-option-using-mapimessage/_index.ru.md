---
title: "Работа с опцией голосования с помощью MapiMessage"
url: /ru/python-net/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---


## **Создание опции голосования с помощью MapiMessage**
Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Это позволяет им включать такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Aspose.Email позволяет использовать то же самое при создании нового сообщения Outlook. [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) класс предоставляет свойство VotingButtons, которое можно использовать для установки или получения значений параметров голосования. В этой статье приведен подробный пример создания MapiMesasge с опциями голосования для создания опроса.

### **Создание опроса с помощью MapiMessage**

В следующем примере кода показано, как использовать *voting_buttons* собственность [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) класс для создания опроса:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Set FollowUpOptions Buttons
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Yes;No;Maybe;Exactly!"

msg.save("voting_btns.msg")
```

### **Чтение вариантов голосования из MapiMessage**
В следующем фрагменте кода показано, как читать параметры голосования из MapiMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}


### **Кнопки голосования только для чтения**
В следующем фрагменте кода показано, как читать только кнопки голосования.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Добавление кнопки голосования в существующее сообщение**
В следующем фрагменте кода показано, как добавить кнопку голосования к существующему сообщению.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Удаление кнопки голосования из сообщения**
В следующем фрагменте кода показано, как удалить кнопку голосования из сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Ознакомьтесь с информацией о результатах голосования**
В следующем фрагменте кода показано, как читать информацию о результатах голосования.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Установить флаг неотправленных сообщений**
В следующем фрагменте кода показано, как использовать примеры методов, используемых в примерах.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Flagged message", "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```
