---
title: "Criar Novo PST em PHP"
url: /pt/java/create-new-pst-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Criar Novo PST**
Para criar um novo PST usando **Aspose.Email Java para PHP**, basta invocar o módulo **CreatePST**. Aqui você pode ver um código de exemplo.

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
## **Baixar Código em Execução**
Baixe **Criar Novo PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)