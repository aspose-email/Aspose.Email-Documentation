---
title: "Criando e Salvando Notas do Outlook em PHP"
url: /pt/java/creating-and-saving-outlook-notes-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Criando e Salvando Notas do Outlook**
Para criar notas do Outlook usando **Aspose.Email Java para PHP**, basta invocar o módulo **CreateOutlookNote**. Aqui você pode ver um código de exemplo.

**Código PHP**

``` php

 $note = new MapiNote();

$note->setSubject("Nota de cor azul");

$note->setBody("Esta é uma nota de cor azul");

$noteColor=new NoteColor();

$note->setColor($noteColor->Blue);

$note->setHeight(500);

$note->setWidth(500);

$noteSaveFormat=new NoteSaveFormat();

$note->save($dataDir . "MapiNote.msg", $noteSaveFormat->Msg);

print "Nota do Outlook criada com sucesso.".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Criando e Salvando Notas do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookNote.php)