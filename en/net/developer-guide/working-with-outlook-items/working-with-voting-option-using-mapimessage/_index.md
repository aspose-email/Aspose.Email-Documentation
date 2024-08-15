---
title: Working with Voting Option Using MapiMessage
type: docs
weight: 50
url: /net/working-with-voting-option-using-mapimessage/
---


## **Creating Voting Option Using MapiMessage**

Microsoft Outlook allows users to create a poll when composing a new message. It allows them to include voting options such as Yes, No, Maybe, etc. Aspose.Email allows the same while creating a new Outlook message. The [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) class provides the [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) property that can be used to set or get the value of voting options. This article provides a detailed example of creating a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) with voting options for creating a poll.

### **Creating a Poll using MapiMessage**

The following code snippet shows you how to create a poll, the [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) class can be used as shown in the following code snippet.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Reading Voting Options from a MapiMessage**

The following code snippet shows you how to read voting options from a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Reading Only Voting Buttons**

The following code snippet shows you how to read only voting buttons.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Adding a voting button to an Existing Message**

The following code snippet shows you how to add a voting button to an existing message.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Deleting a Voting button from a Message**

The following code snippet shows you how to delete the vote button from a Message.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Read the Vote Results Information**

The following code snippet shows you how to read the vote results information.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Sample Methods Used In Examples**

The following code snippet shows you how to create the sample message used in examples.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}
