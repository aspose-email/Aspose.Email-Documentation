---
title: "Adicionando Arquivos ao PST em PHP"
url: /pt/java/adicionando-arquivos-ao-pst-em-php/
weight: 10
type: docs
---

## **Aspose.Email - Adicionando Arquivos ao PST**
Para adicionar um arquivo ao PST usando **Aspose.Email Java para PHP**, simplesmente invoque o módulo **AddFileToPST**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "AddFile1.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$fi->addFile($dataDir . "Report.xlsx", "IPM.Document.Excel.Sheet.8");

$pst->dispose();

print "Arquivo adicionado ao PST".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Adicionando Arquivos ao PST (Aspose.Email)** de qualquer um dos sites de codificação social abaixo mencionados:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)