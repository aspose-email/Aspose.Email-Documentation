---
title: "Criar Novo Email em Jython"
url: /pt/java/criando-novo-email-em-jython/
weight: 20
type: docs
---

## **Aspose.Email - Criar Novo Email**
Para criar um novo email usando **Aspose.Email Java para Jython**, basta invocar o módulo **CreateNewEmail**. Aqui você pode ver um exemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MailMessageSaveType

class CreateNewEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/CreateNewEmail/'



        # Cria uma instância da classe MailMessage

        message = MailMessage()

        # Define o assunto da mensagem

        message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

        mail_address = MailAddress

        # Define o corpo Html

        message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

            "<font color=blue>Esta linha está em azul</font>")

        # Define as informações do remetente

        message.setFrom(MailAddress("from@domain.com", "Nome do Remetente", False))

        # Adiciona destinatários TO

        message.getTo().add(MailAddress("to1@domain.com", "Destinatário 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Destinatário 2", False))

        # Adiciona destinatários CC

        message.getCC().add(MailAddress("cc1@domain.com", "Destinatário 3", False))

        message.getCC().add(MailAddress("cc2@domain.com", "Destinatário 4", False))

        # Salva a mensagem nos formatos EML e MSG

        mail_message_save_type = MailMessageSaveType()

        message.save(dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

        message.save(dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

        # Exibe o Status

        print "Mensagens de email criadas com sucesso."



if __name__ == '__main__':        

    CreateNewEmail()

```
## **Baixar Código em Execução**
Baixe **Criar Novo Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)