---
title: Create New Email in PHP
type: docs
weight: 20
url: /java/create-new-email-in-php/
---

## **Aspose.Email - Create New Email**
To Create new Email using **Aspose.Email Java for PHP**, simply invoke **CreateNewEmail** module. Here you can see example code.

**PHP Code**

``` php

 # Create a new instance of MailMessage class

$message = new MailMessage();

\# Set subject of the message

$message->setSubject("New message created by Aspose.Email for Java");

$mail_address = new MailAddress();

\# Set Html body

$message->setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" .

"<font color=blue>This line is in blue color</font>");

\# Set sender information

$message->setFrom(new MailAddress("from@domain.com", "Sender Name", false));

\# Add TO recipients

$message->getTo()->add(new MailAddress("to1@domain.com", "Recipient 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Recipient 2", false));

\# Add CC recipients

$message->getCC()->add(new MailAddress("cc1@domain.com", "Recipient 3", false));

$message->getCC()->add(new MailAddress("cc2@domain.com", "Recipient 4", false));

\# Save message in EML and MSG formats

$mail_message_save_type = new MailMessageSaveType();

$message->save($dataDir . "Message.eml", $mail_message_save_type->getEmlFormat());

$message->save($dataDir . "Message.msg", $mail_message_save_type->getOutlookMessageFormat());

\# Display Status

print "Created email messages Successfully.".PHP_EOL;


```
## **Download Running Code**
Download **Create New Email (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/CreateNewEmail.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/CreateNewEmail.php)
