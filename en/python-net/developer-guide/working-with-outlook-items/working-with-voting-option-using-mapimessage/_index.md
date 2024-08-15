---
title: Working with Voting Option Using MapiMessage
type: docs
weight: 120
url: /python-net/working-with-voting-option-using-mapimessage/
---


## **Creating Voting Option Using MapiMessage**
Microsoft Outlook lets users create a poll when composing a new message. It lets them include voting options such as Yes, No, Maybe, etc. Aspose.Email allows the same while creating a new Outlook message. The [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) class provides the VotingButtons property that can be used to set or get the value of voting options. This article provides a detailed example of creating a MapiMesasge with voting options for creating a poll.

### **Creating a Poll using MapiMessage**

The following code sample shows how to use the *voting_buttons* property of the [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) class to create a poll:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Set FollowUpOptions Buttons
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Yes;No;Maybe;Exactly!"

msg.save("voting_btns.msg")
```

### **Reading Voting Options from a MapiMessage**
The following code snippet shows you how to Read Voting Options from a MapiMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}


### **Reading Only Voting Buttons**
The following code snippet shows you how to read only voting buttons.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Adding voting button to an Existing Message**
The following code snippet shows you how to add voting button to an existing message.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Deleting Voting button from a Message**
The following code snippet shows you how to delete vote button from a Message.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Read the Vote Results Information**
The following code snippet shows you how to read the vote results information.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Set unsent message flag**
The following code snippet shows you how to how to sample methods used in examples.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Flagged message", "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```
