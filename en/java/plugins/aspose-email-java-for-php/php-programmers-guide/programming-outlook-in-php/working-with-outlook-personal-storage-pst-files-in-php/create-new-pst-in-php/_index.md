---
title: Create New PST in PHP
ArticleTitle: Create New PST in PHP
type: docs
weight: 60
url: /java/create-new-pst-in-php/
---

## **Aspose.Email - Create New PST**
To Create new PST using **Aspose.Email Java for PHP**, simply invoke **CreatePST** module. Here you can see example code.

**PHP Code**

``` php

 # Create an instance of PersonalStorage

$personalStorage=new PersonalStorage();

$pst = $personalStorage->create($dataDir . "sample1.pst", 0);

\# Create a folder at root of pst

$pst->getRootFolder()->addSubFolder("myInbox");

\# Add message to newly created folder

$mapi_message = new MapiMessage();

$pst->getRootFolder()->getSubFolder("myInbox")->addMessage($mapi_message->fromFile($dataDir . "Message.msg"));

print "Created PST successfully.".PHP_EOL;

```
## **Download Running Code**
Download **Create New PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
