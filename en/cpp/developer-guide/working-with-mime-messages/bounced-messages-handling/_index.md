---
title: Detect and Process Bounced Emails Using Aspose.Email for C++
ArticleTitle: Detect and Process Bounced Emails
type: docs
weight: 60
url: /cpp/detect-process-bounced-emails/
description: Learn how to identify and process bounced emails with Aspose.Email for C++.
---


When sending emails, some messages may fail to reach their recipients, for example, due to an invalid recipient address or a full mailbox. These undelivered messages are known as **bounced emails**.

Aspose.Email for C++ provides a convenient way to detect and analyze bounced messages using the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) and [BounceResult](https://reference.aspose.com/email/cpp/class/aspose.email.bounce.bounce_result/) classes.
The [MailMessage::CheckBounced()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a7a17dbb21820034194ebb374160c58d8) method determines whether a message is a bounce and returns a [BounceResult](https://reference.aspose.com/email/cpp/class/aspose.email.bounce.bounce_result/) object that contains detailed information such as:

* Whether the message is bounced
* The recipient address
* The type of bounce action
* The reason and status code of the bounce

This allows developers to automatically identify delivery failures and take appropriate action like cleaning invalid addresses from mailing lists.


The following code example demonstrates how to **check if an email message has bounced and retrieve detailed information about it**:

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}




