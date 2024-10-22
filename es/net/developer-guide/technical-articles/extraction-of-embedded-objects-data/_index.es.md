---
title: "Extracción de datos de Objetos Incrustados"
url: /es/net/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


A veces, los datos OLE incrustados se representan como un archivo adjunto "oleData.mso" por [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) y necesitan ser extraídos manualmente. Estos archivos oleData.mso son de formato Microsoft Computer Document File (MCDF) y el soporte para tales archivos está más allá de la ocupación de Aspose.Email. Sin embargo, Aspose.Email se puede usar en combinación con otras bibliotecas de código abierto, como OpenMCDF, para leer el contenido de tales archivos para guardarlos en disco. Aspose.Email proporciona la clase [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) para enumerar paquetes MSO desde los datos binarios de oledata.mso, que luego se pueden usar para la extracción de contenidos mediante bibliotecas de lectura de Archivos Compuestos.

Si el tipo de cuerpo del mensaje es HTML (no RTF) y hay objetos OLE en un mensaje, la propiedad MapiPropertyTag.PR_ATTACH_DATA_OBJ está ausente. En este caso, la información sobre los objetos OLE se encuentra en oldedata.mso.
## **Extracción de Objetos Incrustados**
Este artículo muestra cómo extraer el contenido de un archivo así utilizando Aspose.Email y [OpenMCDF](http://sourceforge.net/projects/openmcdf/). Esto se puede hacer de la siguiente manera:

- Enumerar paquetes MSO desde los datos binarios del archivo adjunto oledata.mso
- Para cada dato OLE, leer el CompoundFile
- Leer el flujo con CONTENIDOS
- Guardar el contenido en FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}