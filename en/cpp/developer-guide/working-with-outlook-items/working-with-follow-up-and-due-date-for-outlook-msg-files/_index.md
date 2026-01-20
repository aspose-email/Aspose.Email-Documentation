---
title: Manage Follow-Up Flags and Reminders in Outlook Messages with C++
ArticleTitle: Manage Follow-Up Flags and Reminders in Outlook Messages
linktitle: Manage Follow-Up Flags and Reminders in Outlook Messages
type: docs
weight: 50
url: /cpp/manage-follow-up-flags-and-reminders-in-outlook-messages/
description: Learn how to set, read, complete, and remove Outlook follow-up flags using Aspose.Email for C++.
---


**Follow-up flags** in Outlook help users track important tasks and ensure timely action on specific emails. They can include reminders, due dates, and completion status. 

Automating these features programmatically can help streamline workflows, for example, sending regular reminders to teams or tracking pending responses.

With **Aspose.Email for C++**, developers can create, modify, and manage follow-up flags and reminders in Outlook messages (MapiMessage objects) using the FollowUpManager and FollowUpOptions classes.

## **Set a Follow-Up Flag**

Use the [FollowUpManager::SetOptions()](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_manager#a9bf31a37f1febc46b427ca6ac88b9a6f) method to add a follow-up flag with a start date, due date, and reminder time as shown in the code sample below.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpflag-SetFollowUpflag.cpp" >}}

## **Set a Follow-Up Flag for Recipients**

You can also set a follow-up reminder specifically for recipients of an email message.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cpp" >}}

## **Mark a Follow-Up as Completed**

Mark a follow-up flag as completed when the related task or response is done.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cpp" >}}

## **Remove a Follow-Up Flag**

Clear an existing follow-up flag from an email message as shown in the following code sample.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cpp" >}}

## **Read Follow-Up Options**

Retrieve follow-up information such as flag text, due date, and reminder details.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cpp" >}}
