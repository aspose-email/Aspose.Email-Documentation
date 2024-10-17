---
title: "Crear nuevo PST en PHP"
url: /es/java/crear-nuevo-pst-en-php/
weight: 60
type: docs
---

## **Aspose.Email - Crear Nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para PHP**, simplemente invoca el módulo **CreatePST**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 # Crear una instancia de PersonalStorage

$personalStorage=new PersonalStorage();

$pst = $personalStorage->create($dataDir . "sample1.pst", 0);

\# Crear una carpeta en la raíz del pst

$pst->getRootFolder()->addSubFolder("myInbox");

\# Agregar mensaje a la carpeta recién creada

$mapi_message = new MapiMessage();

$pst->getRootFolder()->getSubFolder("myInbox")->addMessage($mapi_message->fromFile($dataDir . "Message.msg"));

print "PST creado con éxito.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Crear Nuevo PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)