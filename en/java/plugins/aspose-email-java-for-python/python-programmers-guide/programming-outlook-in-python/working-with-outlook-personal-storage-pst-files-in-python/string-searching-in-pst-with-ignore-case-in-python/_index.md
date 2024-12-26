---
title: String Searching in PST with Ignore Case in Python
ArticleTitle: String Searching in PST with Ignore Case in Python
type: docs
weight: 70
url: /java/string-searching-in-pst-with-ignore-case-in-python/
---

## **Aspose.Email - String Searching in PST with Ignore Case**
String Searching in PST with Ignore Case using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "search.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

mapiMessage = self.MapiMessage

mailMessage = self.MailMessage

fi.addMessage(mapiMessage.fromMailMessage(mailMessage.load(self.dataDir + "search.pst")))

builder = self.MailQueryBuilder()

builder.getFrom().contains("automated", True)

query = builder.getQuery()

coll = fi.getContents(query)

print "Total Results:"

print coll.size()

{{< /highlight >}}
## **Download Running Code**
Download **String Searching in PST with Ignore Case (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
