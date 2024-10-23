---
title: "Analisando Arquivos de Mensagens do Outlook em Jython"
url: /pt/java/analisando-arquivos-de-mensagens-do-outlook-em-jython/
weight: 30
type: docs
---

## **Aspose.Email - Analisando Arquivos de Mensagens do Outlook**
Para analisar um arquivo de mensagem do Outlook usando **Aspose.Email Java para Jython**, basta invocar o módulo **ParseOutlookMessageFile**. Aqui você pode ver um código de exemplo.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Exibir nome do remetente

        print "Nome do Remetente : " 

        print outlook_message_file.getSenderName()

        # Exibir Assunto

        print "Assunto : " 

        print outlook_message_file.getSubject()

        # Exibir Corpo

        print "Corpo : " 

        print outlook_message_file.getBody()





if __name__ == '__main__':        

    ParseOutlookMessageFile()

```
## **Baixar Código em Execução**
Baixe **Analisando Arquivos de Mensagens do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)