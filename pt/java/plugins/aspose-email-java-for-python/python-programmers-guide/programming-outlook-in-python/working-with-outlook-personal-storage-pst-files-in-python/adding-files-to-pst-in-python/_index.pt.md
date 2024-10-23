---
title: "Adicionando Arquivos ao PST em Python"
url: /pt/java/adding-files-to-pst-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Adicionando Arquivos ao PST**
Para adicionar arquivos ao PST usando **Aspose.Email Java para Python**, utilize o seguinte código.

**Código em Python**

```python



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

fi.addFile(self.dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

print "Arquivo adicionado ao PST"

```
## **Baixar Código em Execução**
Baixe **Adicionando Arquivos ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)