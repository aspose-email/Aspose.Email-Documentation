---
title: "Agregar Archivos a PST en Python"
url: /es/java/adding-files-to-pst-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Agregar Archivos a PST**
Para agregar archivos a PST usando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código en Python**

```python



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

fi.addFile(self.dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

print "Archivo agregado a PST"

```
## **Descargar Código en Ejecución**
Descarga **Agregar Archivos a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)