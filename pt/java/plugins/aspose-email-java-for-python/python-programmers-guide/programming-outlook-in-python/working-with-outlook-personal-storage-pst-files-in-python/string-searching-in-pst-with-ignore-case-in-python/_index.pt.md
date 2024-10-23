---
title: "Busca de Strings em PST com Ignorar Maiúsculas e Minúsculas em Python"
url: /pt/java/string-searching-in-pst-with-ignore-case-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Busca de Strings em PST com Ignorar Maiúsculas e Minúsculas**
Busca de Strings em PST com Ignorar Maiúsculas e Minúsculas usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

```python



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

```
## **Baixar Código em Execução**
Baixar **Busca de Strings em PST com Ignorar Maiúsculas e Minúsculas (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)