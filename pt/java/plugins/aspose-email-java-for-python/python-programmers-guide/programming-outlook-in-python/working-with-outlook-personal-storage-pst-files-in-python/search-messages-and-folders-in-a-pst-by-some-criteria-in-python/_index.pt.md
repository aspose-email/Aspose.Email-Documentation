---
title: "Pesquisar Mensagens e Pastas em um PST por Alguns Critérios em Python"
url: /pt/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-python/
weight: 60
type: docs
---

## **Aspose.Email - Pesquisar Mensagens e Pastas em um PST por Alguns Critérios**
Para Pesquisar Mensagens e Pastas em um PST por Alguns Critérios usando **Aspose.Email Java para Python**, Use o seguinte código.

**Código Python**

```python



\# Carregar o arquivo PST do Outlook

personalStorage = self.PersonalStorage

pst = personalStorage.fromFile(self.dataDir + "sample1.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = self.PersonalStorageQueryBuilder()

    # Mensagens de alta importância

mapiImportance = self.MapiImportance

builder.getImportance().equals(mapiImportance.High)

messages = folder.getContents(builder.getQuery())

print "Mensagens com alta imp:" 

print messages.size()

#builder = PersonalStorageQueryBuilder()

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

print "Mensagens com IPM.Note:" 

print messages.size()

\# Mensagens com anexos E alta importância

builder.getImportance().equals(mapiImportance.High)

mapiMessageFlags = self.MapiMessageFlags

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Mensagens com anexos: " 

print messages.size()

\# Mensagens com tamanho > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

print "mensagens tamanho > 15Kb:" 

print messages.size()

\# Mensagens não lidas

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

print "Não lidas:" 

print messages.size()

\# Mensagens não lidas com anexos

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Msgs não lidas com anexos: " 

print messages.size()

```
## **Baixar Código em Execução**
Baixe **Pesquisar Mensagens e Pastas em um PST por Alguns Critérios (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)