---
title: Parsing Outlook Message Files
type: docs
weight: 40
url: /java/parsing-outlook-message-files/
---

{{% alert color="primary" %}} 

Using Aspose.Email for Java, developers can not only load but also parse contents from Outlook message files.

- To load MSG files from disk, use the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) class' static [fromFile](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#fromFile\(java.lang.String\)) method.
- To parse MSG file contents, use the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) exposes a number of methods.

This topic shows how to loaded and then parsed and MSG file to display its contents.

{{% /alert %}} 

Aspose.Email for Java provides the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) class that is used to open and parse an MSG file. As there may be many recipients in an MSG file, the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) class exposes the [getRecipients()](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessageItemBase#getRecipients\(\)) method that returns a [MapiRecipientCollection](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipientCollection) which represents a collection of [MapiRecipient](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipient) objects. The [MapiRecipient](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipient) object further exposes methods for working with recipient attributes.

The following sequence of steps serves this purpose:

1. Create an instance of the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) class to load an MSG file from the [fromFile](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#fromFile\(java.lang.String\)) static method.
1. Display the sender name, subject, and body from the MSG file using [getSenderName()](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#getSenderName\(\)), [getSubject()](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessageItemBase#getSubject\(\)) and [getBody()](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#getBody\(\)) methods.
1. Call the [getRecipients()](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessageItemBase#getRecipients\(\)) method exposed by the [MapiRecipient](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipient) class to get a reference to the collection of [MapiRecipient](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipient) objects associated with the MSG file.
1. Loop through the [MapiRecipientCollection](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipientCollection) collection to display contents for each [MapiRecipient](https://apireference.aspose.com/java/email/com.aspose.email/MapiRecipient) object through its public methods.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParsingOutlookMessageFiles-.java" >}}

{{% alert %}}
**Try it out!**

Parse email files online with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}
