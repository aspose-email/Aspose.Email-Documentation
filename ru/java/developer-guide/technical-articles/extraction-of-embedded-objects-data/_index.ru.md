---
title: "Извлечение данных встроенных объектов"
url: /ru/java/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


Иногда данные встроенных OLE представляются в виде вложения "oleData.mso" через [MapiAttachment](https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment) и требуют ручного извлечения. Эти файлы oleData.mso имеют формат Microsoft Computer Document File (MCDF), и поддержка таких файлов выходит за рамки возможностей Aspose.Email. Однако Aspose.Email можно использовать в комбинации с другими библиотеками с открытым исходным кодом, такими как OpenMCDF, для чтения содержимого таких файлов для сохранения на диск. Aspose.Email предоставляет класс [InlineAttachmentExtractor](https://apireference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) для перечисления MSO-пакетов из двоичных данных oledata.mso, которые затем могут быть использованы для извлечения содержимого библиотеками для чтения составных файлов.

Если тип тела сообщения — HTML (не RTF), и в сообщении есть OLE-объекты, свойство MapiPropertyTag.PR_ATTACH_DATA_OBJ отсутствует. В этом случае информация об OLE-объектах содержится в oldedata.mso.
## **Извлечение встроенных объектов**
В этой статье показано, как извлечь содержимое из такого файла, используя Aspose.Email:



~~~Java
// Путь к директории файлов
String dataDir = "/data";

MapiMessage msg = MapiMessage.fromFile(dataDir + "double.msg");
for (MapiAttachment mapiAttachment : msg.getAttachments()) {
    if ("oledata.mso".equals(mapiAttachment.getLongFileName())) {
        IGenericDictionary<String, byte[]> oledata = InlineAttachmentExtractor.enumerateMsoPackage(new ByteArrayInputStream(mapiAttachment.getBinaryData()));

        for (String oleItem : oledata.getKeys()) {
            // Используйте двоичные данные
            processBynaryData(oledata.get_Item(oleItem));
        }
    }
}
~~~