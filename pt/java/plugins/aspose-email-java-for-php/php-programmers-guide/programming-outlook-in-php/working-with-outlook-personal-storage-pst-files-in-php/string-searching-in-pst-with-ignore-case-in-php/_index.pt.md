---
title: "Pesquisa de String em PST com Ignorar Caso em PHP"
url: /pt/java/string-searching-in-pst-with-ignore-case-in-php/
weight: 80
type: docs
---

## **Aspose.Email - Pesquisa de String em PST com Ignorar Caso**
Para pesquisar strings em PST com ignorar caso usando **Aspose.Email Java for PHP**, basta invocar o módulo **StringSearchInPST**. Aqui você pode ver um código de exemplo.

**Código PHP**

```php

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

```
## **Baixar Código em Execução**
Baixe **Pesquisa de String em PST com Ignorar Caso (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)