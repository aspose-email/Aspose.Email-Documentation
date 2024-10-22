---
title: "Buscar Mensajes y Carpetas en un PST según Algunos Criterios en PHP"
url: /es/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Buscar Mensajes y Carpetas en un PST**
Para buscar mensajes y carpetas en un PST utilizando **Aspose.Email Java para PHP**, simplemente invoque el módulo **SearchMessagesAndFoldersInPST**. Aquí puede ver un ejemplo de código.

**Código PHP**

```php

 # Cargar el archivo PST de Outlook

$personalStorage=new PersonalStorage();

$pst = $personalStorage->fromFile($dataDir . "sample1.pst");

$folder = $pst->getRootFolder()->getSubFolder("myInbox");

$builder = new PersonalStorageQueryBuilder();

\# Mensajes de alta importancia

$mapiImportance=new MapiImportance();

$builder->getImportance()->equals($mapiImportance->High);

$messages = $folder->getContents($builder->getQuery());

print "Mensajes con alta imp: " . (string)$messages->size();

#builder = new PersonalStorageQueryBuilder();

$builder->getMessageClass()->equals("IPM.Note");

$messages = $folder->getContents($builder->getQuery());

print "Mensajes con IPM.Note: " . (string)$messages->size();

\# Mensajes con archivos adjuntos Y alta importancia

$builder->getImportance()->equals($mapiImportance->High);

$mapiMessageFlags=new MapiMessageFlags();

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Mensajes con adjuntos: " . (string)$messages->size();

\# Mensajes con tamaño > 15 KB

$builder->getMessageSize()->greater(15000);

$messages = $folder->getContents($builder->getQuery());

print "mensajes tamaño > 15Kb: " . (string)$messages->size();

\# Mensajes no leídos

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$messages = $folder->getContents($builder->getQuery());

print "No leídos: " . (string)$messages->size();//.to_s

\# Mensajes no leídos con archivos adjuntos

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Mensajes no leídos con adjuntos: " . (string)$messages->size();

```
## **Descargar Código en Ejecución**
Descargue **Buscar Mensajes y Carpetas en un PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)