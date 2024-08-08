---
title: Parsing Outlook Message Files in PHP
type: docs
weight: 30
url: /java/parsing-outlook-message-files-in-php/
---

## **Aspose.Email - Parsing Outlook Message Files**
To Parse Outlook Message file using **Aspose.Email Java for PHP**, simply invoke **ParseOutlookMessageFile** module. Here you can see example code.

**PHP Code**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Display sender's name

print "Sender Name : " . $outlook_message_file->getSenderName();

#Display Subject

print "Subject : " . $outlook_message_file->getSubject();

\# Display Body

print "Body : " . $outlook_message_file->getBody();

```
## **Download Running Code**
Download **Parsing Outlook Message Files (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
