---
title: "Exibindo Informações de Email na Tela em Jython"
url: /pt/java/exibindo-informacoes-de-email-na-tela-em-jython/
weight: 30
type: docs
---

## **Aspose.Email - Exibindo Informações de Email**
Para exibir informações de email usando **Aspose.Email Java para Jython**, basta invocar o módulo **GetEmailInfo**. Aqui você pode ver um código de exemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Crie uma instância de MailMessage carregando um arquivo Eml

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "De: " 

        print message.getFrom()

        print "Para: " 

        print message.getTo()

        print "Assunto: " 

        print message.getSubject()

        print "HtmlBody: " 

        print message.getHtmlBody()

        print "TextBody: " 

        print message.getTextBody()





if __name__ == '__main__':        

    GetEmailInfo()

```
## **Baixar Código em Execução**
Baixe **Exibindo Informações de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)