---
title: "Извлечение данных встроенных объектов"
url: /ru/net/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


Иногда встроенные данные OLE представляются как вложение "oleData.mso" с помощью [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) и должны быть извлечены вручную. Эти файлы oleData.mso имеют формат Microsoft Computer Document File (MCDF), и поддержка таких файлов выходит за рамки возможностей Aspose.Email. Однако Aspose.Email может использоваться в комбинации с другими библиотеками с открытым исходным кодом, такими как OpenMCDF, для чтения содержимого таких файлов для сохранения на диск. Aspose.Email предоставляет класс [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) для перечисления пакетов MSO из двоичных данных oledata.mso, которые затем могут быть использованы для извлечения содержимого библиотеками чтения Compound Files.

Если тип тела сообщения - HTML (не RTF), и в сообщении есть объекты OLE, свойство MapiPropertyTag.PR_ATTACH_DATA_OBJ отсутствует. В этом случае информация об объектах OLE содержится в oldedata.mso.
## **Извлечение встроенных объектов**
Эта статья показывает, как извлечь содержимое из такого файла с помощью Aspose.Email и [OpenMCDF](http://sourceforge.net/projects/openmcdf/). Это можно сделать следующим образом:

- Перечислить пакеты MSO из двоичных данных вложения oledata.mso
- для каждого OLE-данных прочитать CompoundFile
- Прочитать поток с СОДЕРЖИМЫМ
- Сохранить содержимое в FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}