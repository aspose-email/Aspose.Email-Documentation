---
title: "Extracción de datos de objetos incrustados"
url: /es/java/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


A veces, los datos OLE incrustados se representan como un archivo adjunto «OLEData.mso» mediante [MapiAttachment](https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment) y debe extraerse manualmente. Estos archivos.mso de OleData están en formato Microsoft Computer Document File (MCDF) y Aspose.Email no admite dichos archivos. Sin embargo, Aspose.Email se puede usar en combinación con otras bibliotecas de código abierto, como OpenMCDF, para leer el contenido de dichos archivos y guardarlos en el disco. Aspose.Email proporciona [InlineAttachmentExtractor](https://apireference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) clase para enumerar los paquetes MSO a partir de los datos binarios de oledata.mso, que luego pueden usarse para la extracción de contenido mediante bibliotecas de lectura de Compound Files.

Si el tipo de cuerpo de un mensaje es HTML (no RTF) y hay objetos OLE en un mensaje, la propiedad MAPIPropertyTag.PR_ATTACH_DATA_OBJ está ausente. En este caso, la información sobre los objetos OLE se encuentra en oldedata.mso.
## **Extracción de objetos incrustados**
Este artículo muestra cómo extraer el contenido de un archivo de este tipo usando Aspose.Email:



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