---
title: String Searching in PST with Ignore Case in PHP
ArticleTitle: String Searching in PST with Ignore Case in PHP
type: docs
weight: 80
url: /java/string-searching-in-pst-with-ignore-case-in-php/
---

## **Aspose.Email - String Searching in PST with Ignore Case**
To string Searching in PST with Ignore Case using **Aspose.Email Java for PHP**, simply invoke **StringSearchInPST** module. Here you can see example code.

**PHP Code**

{{< highlight php >}}

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "search.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$mapiMessage=new MapiMessage();

$mailMessage=new MailMessage();

$fi->addMessage($mapiMessage->fromMailMessage($mailMessage->load($dataDir . "search.pst")));

$builder = new MailQueryBuilder();

$builder->getFrom()->contains("automated", true);

$query = $builder->getQuery();

$coll = $fi->getContents($query);

print "Total Results:" . (string)$coll->size();

{{< /highlight >}}
## **Download Running Code**
Download **String Searching in PST with Ignore Case (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
