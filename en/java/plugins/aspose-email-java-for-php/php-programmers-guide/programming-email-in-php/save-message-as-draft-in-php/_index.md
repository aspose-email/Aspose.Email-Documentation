---
title: Save Message as Draft in PHP
type: docs
weight: 60
url: /java/save-message-as-draft-in-php/
---

## **Aspose.Email - Save Message as Draft**
To Save Message as Draft using **Aspose.Email Java for PHP**, simply invoke **SaveMessageAsDraft** module. Here you can see example code.

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

\# Create an instance of MapiMessage and load the MailMessag instance into it

$mapiMessage=new MapiMessage();

$mapi_msg = $mapiMessage->fromMailMessage($message);

\# Set the MapiMessageFlags as UNSENT and FROMME

$mapi_message_flags = new MapiMessageFlags();

\# Save the MapiMessage to disk

$mapi_msg->save($dataDir . "New-Draft.msg");

\# Display Status

print "Draft saved Successfully.".PHP_EOL;

```
## **Download Running Code**
Download **Save Message as Draft (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)
