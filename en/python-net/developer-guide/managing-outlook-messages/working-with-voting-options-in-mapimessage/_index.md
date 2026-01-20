---
title: Creating and Managing Voting Options
ArticleTitle: Creating and Managing Voting Options
type: docs
weight: 120
url: /python-net/create-manage-voting-options-in-mapimessage/
---


Microsoft Outlook enables users to create a poll while composing a new email, allowing them to include voting options such as Yes, No, Maybe, and more. Similarly, Aspose.Email provides the functionality to create polls when generating a new Outlook message programmatically. The [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) class includes the *voting_buttons* property, which can be used to set or retrieve the desired voting options.

In this article, we’ll explore a detailed example of how to create a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) with voting options to set up a poll effectively.

### **Create a Poll Using MapiMessage**

To create a poll, use the *voting_buttons* property of the [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) class as shown in the code sample below:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Set FollowUpOptions Buttons
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Yes;No;Maybe;Exactly!"

msg.save("voting_btns.msg")
```

### **Read Voting Options from MapiMessages**

The following code snippet shows you how to read voting options from a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/).


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}

### **Read Only Voting Buttons**

To read only voting buttons, consider the following code snippet:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}

### **Add Voting Buttons to Existing Messages**

The following code snippet shows you how to add voting button to an existing message:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}

### **Delete Voting Buttons from Messages**

The following code snippet shows you how to delete a voting button from a message:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}

### **Read Voting Results Information**

The following code snippet shows you how to read voting results information:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}


