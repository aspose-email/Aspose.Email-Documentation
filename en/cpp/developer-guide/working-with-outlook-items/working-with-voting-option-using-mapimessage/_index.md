---
title: Create and Manage Outlook Voting Options in C++
ArticleTitle: Create and Manage Outlook Voting Options
type: docs
weight: 120
url: /cpp/manage-outlook-voting-options-in-mapi-message/
description: Learn how to add, read, and manage Outlook voting buttons in MapiMessage using Aspose.Email for C++.
---



Microsoft Outlook allows users to add voting buttons (such as Yes, No, Maybe) when composing emails to collect quick responses. Aspose.Email for C++ provides full support for creating, modifying, and reading these voting options programmatically through the [FollowUpOptions](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_options/) and [FollowUpManager](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_manager/) classes.

In this article, you will learn to:

- Create a message with voting options
- Read voting options from a MapiMessage
- Add or remove voting buttons
- Retrieve vote results
- Work with existing or new messages


## **Reading Voting Options from a MAPI Message**

Use [FollowUpManager::GetOptions](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_manager#ae3f56d88bee360b60b8ceacab3dc284a) to read all follow-up settings, including voting buttons.

The following code sample demonstrates how to extract follow-up options and voting buttons from an Outlook message file using Aspose.Email for C++. 

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVotingOptions-ReadingVotingOptions.cpp" >}}


## **Reading Only Voting Buttons**

The following code snippet shows you how to read only voting buttons.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cpp" >}}


## **Adding a Voting Button to an Existing Message**

The following code sample demonstrates how to add a custom voting option ("Indeed!") to an existing Outlook message. The modified message is then saved back to a new MSG file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cpp" >}}


## **Deleting Voting Buttons from a Message**

Remove a single option or clear all voting buttons.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cpp" >}}


## **Reading Vote Results Information**

Aspose.Email allows you to extract recipient responses recorded by Outlook.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cpp" >}}
