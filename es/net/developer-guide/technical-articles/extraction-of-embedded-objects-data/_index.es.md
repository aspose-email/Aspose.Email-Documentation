---
title: "Extracción de datos de objetos incrustados"
url: /es/net/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


A veces, los datos OLE incrustados se representan como un archivo adjunto «OLEData.mso» mediante [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) y debe extraerse manualmente. Estos archivos.mso de OleData están en formato Microsoft Computer Document File (MCDF) y Aspose.Email no admite dichos archivos. Sin embargo, Aspose.Email se puede usar en combinación con otras bibliotecas de código abierto, como OpenMCDF, para leer el contenido de dichos archivos y guardarlos en el disco. Aspose.Email proporciona [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) clase para enumerar los paquetes MSO a partir de los datos binarios de oledata.mso, que luego pueden usarse para la extracción de contenido mediante bibliotecas de lectura de Compound Files.

Si el tipo de cuerpo de un mensaje es HTML (no RTF) y hay objetos OLE en un mensaje, la propiedad MAPIPropertyTag.PR_ATTACH_DATA_OBJ está ausente. En este caso, la información sobre los objetos OLE se encuentra en oldedata.mso.
## **Extracción de objetos incrustados**
Este artículo muestra cómo extraer el contenido de un archivo de este tipo usando Aspose.Email y [OpenMCDF](http://sourceforge.net/projects/openmcdf/). Esto se puede hacer de la siguiente manera:

- Enumere los paquetes MSO a partir de los datos binarios del archivo adjunto oledata.mso
- para cada dato OLE, lea el CompoundFile
- Lea la transmisión con CONTENIDO
- Guarda el contenido en FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}
