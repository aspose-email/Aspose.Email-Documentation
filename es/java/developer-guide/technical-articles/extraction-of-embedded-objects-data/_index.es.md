---
title: "Extracción de datos de objetos embebidos"
url: /es/java/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


A veces, los datos OLE embebidos se representan como un archivo adjunto "oleData.mso" mediante [MapiAttachment](https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment) y deben ser extraídos manualmente. Estos archivos oleData.mso están en formato Microsoft Computer Document File (MCDF) y el soporte para tales archivos está más allá de la ocupación de Aspose.Email. Sin embargo, Aspose.Email se puede usar en combinación con otras bibliotecas de código abierto, como OpenMCDF, para leer el contenido de tales archivos para guardarlos en disco. Aspose.Email proporciona la clase [InlineAttachmentExtractor](https://apireference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) para enumerar paquetes MSO a partir de los datos binarios de oledata.mso, que luego se pueden usar para la extracción de contenidos mediante bibliotecas de lectura de Archivos Compuestos.

Si el tipo de cuerpo de un mensaje es HTML (no RTF), y hay objetos OLE en un mensaje, la propiedad MapiPropertyTag.PR_ATTACH_DATA_OBJ está ausente. En este caso, la información sobre objetos OLE se encuentra en oledata.mso.
## **Extracción de Objetos Embebidos**
Este artículo muestra cómo extraer el contenido de un archivo así utilizando Aspose.Email:



~~~Java
// La ruta al directorio de archivos
String dataDir = "/data";

MapiMessage msg = MapiMessage.fromFile(dataDir + "double.msg");
for (MapiAttachment mapiAttachment : msg.getAttachments()) {
    if ("oledata.mso".equals(mapiAttachment.getLongFileName())) {
        IGenericDictionary<String, byte[]> oledata = InlineAttachmentExtractor.enumerateMsoPackage(new ByteArrayInputStream(mapiAttachment.getBinaryData()));

        for (String oleItem : oledata.getKeys()) {
            // Usar datos binarios
            processBynaryData(oledata.get_Item(oleItem));
        }
    }
}
~~~