---
title: "Extraindo Cabeçalhos de E-mail em Jython"
url: /pt/java/extracting-email-headers-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Extraindo Cabeçalhos de E-mail**
Para Extrair Cabeçalhos de E-mail usando **Aspose.Email Java para Jython**, basta invocar o módulo **ExtractEmailHeaders**. Aqui você pode ver um código de exemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Inicialize e carregue um arquivo EML existente especificando o MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Imprimindo todos os Cabeçalhos:"

        # Imprima todos os cabeçalhos

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':        

    ExtractEmailHeaders()

```
## **Baixar Código em Execução**
Baixe **Extraindo Cabeçalhos de E-mail (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)