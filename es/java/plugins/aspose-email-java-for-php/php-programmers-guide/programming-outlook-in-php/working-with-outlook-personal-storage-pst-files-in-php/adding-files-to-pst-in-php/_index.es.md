---
title: "Agregar Archivos a PST en PHP"
url: /es/java/adding-files-to-pst-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Agregar Archivos a PST**
Para agregar un archivo a PST utilizando **Aspose.Email Java para PHP**, simplemente invoca el módulo **AddFileToPST**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "AddFile1.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$fi->addFile($dataDir . "Report.xlsx", "IPM.Document.Excel.Sheet.8");

$pst->dispose();

print "Archivo agregado a PST".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Agregar Archivos a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)