---
title: "Buscar Mensagens e Pastas em um PST por Alguns Critérios em PHP"
url: /pt/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Buscar Mensagens e Pastas em um PST**
Para buscar mensagens e pastas em um PST usando **Aspose.Email Java para PHP**, basta invocar o módulo **SearchMessagesAndFoldersInPST**. Aqui você pode ver um exemplo de código.

**Código PHP**

```php

 # Carregar o arquivo PST do Outlook

$personalStorage=new PersonalStorage();

$pst = $personalStorage->fromFile($dataDir . "sample1.pst");

$folder = $pst->getRootFolder()->getSubFolder("myInbox");

$builder = new PersonalStorageQueryBuilder();

\# Mensagens de alta importância

$mapiImportance=new MapiImportance();

$builder->getImportance()->equals($mapiImportance->High);

$messages = $folder->getContents($builder->getQuery());

print "Mensagens com Alta Imp:" . (string)$messages->size();

#builder = new PersonalStorageQueryBuilder();

$builder->getMessageClass()->equals("IPM.Note");

$messages = $folder->getContents($builder->getQuery());

print "Mensagens com IPM.Note:" . (string)$messages->size();

\# Mensagens com anexos E alta importância

$builder->getImportance()->equals($mapiImportance->High);

$mapiMessageFlags=new MapiMessageFlags();

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Mensagens com anexos: " . (string)$messages->size();

\# Mensagens com tamanho > 15 KB

$builder->getMessageSize()->greater(15000);

$messages = $folder->getContents($builder->getQuery());

print "mensagens tamanho > 15Kb:" . (string)$messages->size();

\# Mensagens não lidas

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$messages = $folder->getContents($builder->getQuery());

print "Não lidas:" . (string)$messages->size();//.to_s

\# Mensagens não lidas com anexos

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Mensagens não lidas com anexos: " . (string)$messages->size();

```
## **Baixar Código Funcionando**
Baixe **Buscar Mensagens e Pastas em um PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)