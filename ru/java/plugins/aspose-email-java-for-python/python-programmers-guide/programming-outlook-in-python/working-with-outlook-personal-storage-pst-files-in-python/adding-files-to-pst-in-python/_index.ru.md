---
title: "Добавление файлов в PST на Python"
url: /ru/java/adding-files-to-pst-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Добавление файлов в PST**
Чтобы добавить файлы в PST с использованием **Aspose.Email Java for Python**, используйте следующий код.

**Код на Python**

```python



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

fi.addFile(self.dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

print "Добавлен файл в PST"

```
## **Скачать рабочий код**
Скачайте **Добавление файлов в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)