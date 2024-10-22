---
title: "Criar Novo PST em Jython"
url: /pt/java/create-new-pst-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Criar Novo PST**
Para criar um novo PST usando **Aspose.Email Java para Jython**, basta invocar o módulo **CreatePST**. Aqui você pode ver um exemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

from com.aspose.email import NoteColor

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class CreatePST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST/'



        # Criar uma instância de PersonalStorage

        personalStorage=PersonalStorage()

        pst = personalStorage.create(dataDir + "sample1.pst", 0)

        # Criar uma pasta na raiz do pst

        pst.getRootFolder().addSubFolder("myInbox")

        # Adicionar mensagem à pasta recém-criada

        mapi_message = MapiMessage()

        pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(dataDir + "Message.msg"))

        print "PST criado com sucesso."





if __name__ == '__main__':        

    CreatePST()

```
## **Baixar Código em Execução**
Baixe **Criar Novo PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)