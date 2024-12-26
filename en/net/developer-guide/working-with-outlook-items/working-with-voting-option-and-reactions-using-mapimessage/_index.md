---
title: Working with Voting Options and Reactions in MSG
ArticleTitle: Working with Voting Options and Reactions in MSG
type: docs
weight: 50
url: /net/working-with-voting-options-and-reactions-msg/
---


## **Create Voting Options with MapiMessage**

Microsoft Outlook provides a feature to create a poll when composing a new email, allowing users to include voting options such as Yes, No, Maybe, etc. Aspose.Email allows similar functionality when creating a new Outlook message programmatically. The [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) class provides the [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) property that can be used to set or get the voting options. [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) refers to a class within the Aspose.Email namespace that represents an email message in the Messaging Application Programming Interface (MAPI) format commonly used by Microsoft Outlook. By using the MapiMessage class, developers can add polling buttons to an email. This article provides a detailed example of how to create a MapiMessage with voting options to create a poll.

### **Create Polls**

The following code snippet demonstrates how to create a poll in an Outlook message using Aspose.Email. The [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) class facilitates setting the voting options.

```csharp
// Create a MapiMessage with the sender, recipient, subject, and body
var msg = new MapiMessage(
    "from@test.com",
    "to@test.com",
    "Flagged message",
    "Make it nice and short, but descriptive. The description may appear in search engines' search results pages..."
);

// Create FollowUpOptions and set the voting buttons
var options = new FollowUpOptions
{
    VotingButtons = "Yes;No;Maybe;Exactly!"
};

// Apply the follow-up options to the message
FollowUpManager.SetOptions(msg, options);
```

- [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/): Provides properties to configure follow-up actions such as voting buttons.
- [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/): A string property where different voting options are separated by semicolons.
- [FollowUpManager.SetOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/setoptions/): Applies the specified follow-up options to the message.

### **Read Voting Options**

To retrieve voting options from a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), you can use the [GetOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getoptions/) method. This method not only retrieves voting buttons but can also provide additional parameters like categories if necessary.

```csharp
// Retrieve follow-up options from the message
var options = FollowUpManager.GetOptions(msg);

// Voting buttons are returned as a string with a semicolon separator
string votingButtons = options.VotingButtons;

// Display the voting buttons
Console.WriteLine($"Voting Options: {votingButtons}");
```

- [GetOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getoptions/): Retrieves the [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) object from the message, which includes the voting buttons and potentially other properties.
- [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/): The options are extracted as a semicolon-separated string, allowing for easy display or manipulation.

### **Read Voting Buttons**

If you need to access only voting buttons as a list of individual strings, you can use the [GetVotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getvotingbuttons/) method, which returns them as a collection.

```csharp
// Read only voting buttons as a collection of string values
var votingButtons = FollowUpManager.GetVotingButtons(msg);

// Display each voting button
foreach (var button in votingButtons)
{
    Console.WriteLine($"Voting Button: {button}");
}
```

- [GetVotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getvotingbuttons/): Returns a collection of voting button strings, making it convenient to iterate over them and perform operations like displaying or modifying.

### **Add Voting Buttons**

You can add additional voting buttons to an existing message using the [AddVotingButton](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addvotingbutton/) method. This can be useful for dynamically updating the voting options.

```csharp
// Add a new voting button to the existing message
FollowUpManager.AddVotingButton(msg, "Indeed!");
```

- [AddVotingButton](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addvotingbutton/): Adds a new voting option to the message's existing voting buttons, allowing for dynamic customization of polls.

### **Delete Voting Buttons**

You may want to remove specific voting buttons or clear all buttons from a message. The following code demonstrates both actions using [RemoveVotingButton](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removevotingbutton/) and [ClearVotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearvotingbuttons/) methods.

```csharp
// Delete a specific voting button
FollowUpManager.RemoveVotingButton(msg, "Exactly!");

// Or delete all voting buttons from the MapiMessage
FollowUpManager.ClearVotingButtons(msg);
```

- [RemoveVotingButton](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removevotingbutton/): Deletes a specific voting button by name.
- [ClearVotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearvotingbuttons/): Removes all voting buttons, effectively resetting the voting options.

### **Read Vote Results**

Aspose.Email also allows reading vote results from a message's recipients. You can access properties like the recipient's response and response time.

```csharp
// Load a MapiMessage from a file
var msg = MapiMessage.Load("sample.msg");

// Iterate through each recipient and display their vote information
foreach (var recipient in msg.Recipients)
{
    Console.WriteLine($"Recipient: {recipient.DisplayName}");

    // Get the recipient's response using the appropriate MapiPropertyTag
    var response = recipient.Properties[MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE].GetString();
    Console.WriteLine($"Response: {response}");

    // Get the response time
    var responseTime = recipient.Properties[MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME].GetDateTime();
    Console.WriteLine($"Response time: {responseTime}\n");
}
```

- [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/#mapirecipient-class): Represents a recipient in the MapiMessage, enabling access to individual response data.
- *[PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/pr_recipient_autoresponse_prop_response/): A property tag that stores the recipient's vote response.
- [PR_RECIPIENT_TRACKSTATUS_TIME](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/pr_recipient_trackstatus_time/): A property tag that records the time when the recipient responded.

## **Retrieve Reaction Information from MSG**

The [GetReactions](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getreactions/) method of the [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) class allows you to retrieve a list of reactions on a MAPI message, making it easy to analyze user engagement. The following code sample demonstrates how to retrieve available reactions for a specified message, providing insight into user interactions:

```cs
// Load the message file
var msg = MapiMessage.Load(fileName);

// Retrieve the list of reactions on the message
var reactions = FollowUpManager.GetReactions(msg);

// Iterate through each reaction and output the details to the console
foreach (var reaction in reactions)
{
    Console.WriteLine($"User: {reaction.Name}, Email: {reaction.Email}, Reaction: {reaction.Type}, Date: {reaction.ReactionDateTime}");
}
```
