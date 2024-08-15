---
title: "Извлечение данных встроенных объектов"
url: /ru/net/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


Иногда встроенные данные OLE представлены в виде вложения «OleData.mso» следующим образом [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) и его нужно извлекать вручную. Эти файлы OleData.mso представляют собой формат файлов компьютерных документов Microsoft (MCDF), и Aspose.Email не может поддерживать такие файлы. Однако Aspose.Email можно использовать в сочетании с другими библиотеками с открытым исходным кодом, такими как OpenMCDF, для чтения содержимого таких файлов для сохранения на диск. Aspose.Email предоставляет [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) класс для перечисления пакетов MSO из двоичных данных oledata.mso, которые затем можно использовать для извлечения содержимого библиотеками чтения Compound Files.

Если тип тела сообщения — HTML (а не RTF) и в сообщении есть объекты OLE, свойство MapiPropertyTag.pr_attach_data_obj отсутствует. В этом случае информация об объектах OLE содержится в oldedata.mso.
## **Извлечение встроенных объектов**
В этой статье показано, как извлечь содержимое из такого файла с помощью Aspose.Email и [OpenMCDF](http://sourceforge.net/projects/openmcdf/). Это можно сделать следующим образом:

- Перечислите пакеты MSO из двоичных данных вложения oledata.mso
- для всех данных OLE прочтите CompoundFile
- Прочитайте трансляцию с КОНТЕНТОМ
- Сохраните содержимое в FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}
