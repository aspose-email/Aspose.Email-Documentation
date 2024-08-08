---
title: Adding Files to PST in Python
type: docs
weight: 10
url: /java/adding-files-to-pst-in-python/
---

## **Aspose.Email - Adding Files to PST**
To Add Files to PST using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

fi.addFile(self.dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

print "Added file to PST"

{{< /highlight >}}
## **Download Running Code**
Download **Adding Files to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
