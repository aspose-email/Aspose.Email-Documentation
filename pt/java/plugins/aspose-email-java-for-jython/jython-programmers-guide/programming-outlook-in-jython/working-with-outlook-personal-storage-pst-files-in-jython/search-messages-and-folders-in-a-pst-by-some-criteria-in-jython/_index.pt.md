---
title: "Pesquisar Mensagens e Pastas em um PST por Alguns Critérios em Jython"
url: /pt/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Pesquisar Mensagens e Pastas em um PST**
Para Pesquisar Mensagens e Pastas em um PST usando **Aspose.Email Java para Jython**, basta invocar o módulo **SearchMessagesAndFoldersInPST**. Aqui você pode ver um exemplo de código.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import PersonalStorage

from com.aspose.email import PersonalStorageQueryBuilder

from com.aspose.email import MapiImportance

from com.aspose.email import MapiMessageFlags

class SearchMessagesAndFoldersInPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST/'



        # Carregar o arquivo PST do Outlook

        personalStorage=PersonalStorage()

        pst = personalStorage.fromFile(dataDir + "sample1.pst")

        folder = pst.getRootFolder().getSubFolder("myInbox")

        builder = PersonalStorageQueryBuilder()

            # Mensagens de alta importância

        mapiImportance=MapiImportance

        builder.getImportance().equals(mapiImportance.High)

        messages = folder.getContents(builder.getQuery())

        print "Mensagens com Alta Imp:" 

        print messages.size()

        #builder = PersonalStorageQueryBuilder()

        builder.getMessageClass().equals("IPM.Note")

        messages = folder.getContents(builder.getQuery())

        print "Mensagens com IPM.Note:" 

        print messages.size()

        # Mensagens com anexos E alta importância

        builder.getImportance().equals(mapiImportance.High)

        mapiMessageFlags=MapiMessageFlags

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Mensagens com anexos: " 

        print messages.size()

        # Mensagens com tamanho > 15 KB

        builder.getMessageSize().greater(15000)

        messages = folder.getContents(builder.getQuery())

        print "mensagens tamanho > 15Kb:" 

        print messages.size()

        # Mensagens não lidas

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        messages = folder.getContents(builder.getQuery())

        print "Não lidas:" 

        print messages.size()

        # Mensagens não lidas com anexos

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Mensagens não lidas com anexos: " 

        print messages.size()





if __name__ == '__main__':        

    SearchMessagesAndFoldersInPST()

```
## **Baixar Código em Execução**
Baixe **Pesquisar Mensagens e Pastas em um PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)