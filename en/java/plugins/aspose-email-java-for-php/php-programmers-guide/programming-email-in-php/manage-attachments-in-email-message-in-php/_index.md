---
title: Manage Attachments in Email Message in PHP
ArticleTitle: Manage Attachments in Email Message in PHP
type: docs
weight: 50
url: /java/manage-attachments-in-email-message-in-php/
---

## **Aspose.Email - Manage Attachments in Email Message**
To Add Attachments to a New Email Message using **Aspose.Email Java for PHP**, call **add_attachments** method of **ManageAttachments** module. Here you can see example code.

**PHP Code**

``` php

 public static function add_attachments($dataDir=null){

\# Create a new instance of MailMessage class

$message =new MailMessage();

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

\# Adding attachment

\# Load an attachment

$attachment = new Attachment($dataDir . "1.txt");

\# Add attachment in instance of MailMessage class

$message->addAttachment($attachment);

\# Save message to disc

$messageFormat=new MessageFormat();

$message->save($dataDir . "Add-Attachment.msg", $messageFormat->getMsg());

\# Display Status

print "Added attachment successfully.".PHP_EOL;

}

```
## **Download Running Code**
Download **Manage Attachments in Email Message (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ManageAttachments.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/ManageAttachments.php)
