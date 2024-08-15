---
title: Public API Changes in Aspose.Email 4.2.0
type: docs
weight: 40
url: /java/public-api-changes-in-aspose-email-4-2-0/
---

{{% alert color="primary" %}} 

The following is a list of any changes made to the public API such as [added](/email/java/public-api-changes-in-aspose-email-4-2-0/), renamed, removed or [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/) members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added Methods**
**`FollowUpOptions.getCategories()` and `FollowUpOptions.setCategories()` Methods**
Gets or sets a string that represents a list of the categories, separated by semicolons.

**`FollowUpOptions.getVotingButtons()` and `FollowUpOptions.setVotingButtons()` Methods**
Gets or sets a string that represents a list of the voting button names, separated by semicolons.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getOptions(MapiMessage message)` Methods**
Gets and sets the additional follow-up options for a message. 

The existing methods `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)` marked as [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/).
Please use the `getOptions(MapiMessage message)` and `setOptions(MapiMessage message, FollowUpOptions options)` methods instead.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Method**
Adds a voting button into a MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Method**
Removes a specified voting button from a MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Method**
Removes voting buttons from a MapiMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Method**
Get the available message voting buttons.
- **`MapiTask.getAttachments` and `MapiTask.setAttachments` Methods**
Get the collection of `MapiAttachments` in a `MapiTask`.
## **Deprecated Methods**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)`**
Please use the getOptions(`MapiMessage` message) and `setOptions(MapiMessage message, FollowUpOptions options)` methods instead, [as mentioned above](/email/java/public-api-changes-in-aspose-email-4-2-0/).

{{% /alert %}}
