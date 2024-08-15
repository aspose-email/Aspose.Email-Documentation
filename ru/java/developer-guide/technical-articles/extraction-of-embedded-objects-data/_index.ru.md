---
title: "Извлечение данных встроенных объектов"
url: /ru/java/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


Иногда встроенные данные OLE представлены в виде вложения «OleData.mso» следующим образом [MapiAttachment](https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment) и его нужно извлекать вручную. Эти файлы OleData.mso представляют собой формат файлов компьютерных документов Microsoft (MCDF), и Aspose.Email не может поддерживать такие файлы. Однако Aspose.Email можно использовать в сочетании с другими библиотеками с открытым исходным кодом, такими как OpenMCDF, для чтения содержимого таких файлов для сохранения на диск. Aspose.Email предоставляет [InlineAttachmentExtractor](https://apireference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) класс для перечисления пакетов MSO из двоичных данных oledata.mso, которые затем можно использовать для извлечения содержимого библиотеками чтения Compound Files.

Если тип тела сообщения — HTML (а не RTF) и в сообщении есть объекты OLE, свойство MapiPropertyTag.pr_attach_data_obj отсутствует. В этом случае информация об объектах OLE содержится в oldedata.mso.
## **Извлечение встроенных объектов**
В этой статье показано, как извлечь содержимое из такого файла с помощью Aspose.Email:



~~~Java
// The path to the File directory
String dataDir = "/data";

MapiMessage msg = MapiMessage.fromFile(dataDir + "double.msg");
for (MapiAttachment mapiAttachment : msg.getAttachments()) {
    if ("oledata.mso".equals(mapiAttachment.getLongFileName())) {
        IGenericDictionary<String, byte[]> oledata = InlineAttachmentExtractor.enumerateMsoPackage(new ByteArrayInputStream(mapiAttachment.getBinaryData()));

        for (String oleItem : oledata.getKeys()) {
            // Use binary data
            processBynaryData(oledata.get_Item(oleItem));
        }
    }
}
~~~