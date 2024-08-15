---
title: "Agregar archivos a PST en Python"
url: /es/java/adding-files-to-pst-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Agregar archivos a PST**
Para agregar archivos a PST usando **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

```python



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

fi.addFile(self.dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

print "Added file to PST"

```
## **Descargar Running Code**
Download **Agregar archivos a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
