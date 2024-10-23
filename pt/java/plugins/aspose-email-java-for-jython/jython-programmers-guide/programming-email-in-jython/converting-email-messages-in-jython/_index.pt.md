---
title: "Convertendo Mensagens de Email em Jython"
url: /pt/java/converting-email-messages-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Convertendo Mensagens de Email**
Para converter mensagens de email usando **Aspose.Email Java para Jython**, chame o método **convert_eml_to_msg** do módulo **Converter**. Aqui você pode ver um exemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):



        # Carregando EML, Salvando como MSG

        self.convert_eml_to_msg()



    def convert_eml_to_msg(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'



        # Inicializa e carrega um arquivo EML existente especificando o MessageFormat

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Salva a mensagem de email no disco em formato Unicode

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Exibir Status

        print "Email convertido para msg com sucesso."



if __name__ == '__main__':        

    Converter()

```
## **Baixar Código em Execução**
Baixe **Convertendo Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)