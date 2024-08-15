---
title: "Crear un nuevo PST en PHP"
url: /es/java/create-new-pst-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Crear un nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para PHP**, simplemente invoca **CreatePST** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

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
## **Descargar Running Code**
Download **Crear un nuevo PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
