---
title: "Gerenciar Anexos em Mensagens de Email em Jython"
url: /pt/java/manage-attachments-in-email-message-in-jython/
weight: 50
type: docs
---

## **Aspose.Email - Gerenciar Anexos em Mensagens de Email**
Para adicionar anexos a uma nova mensagem de email usando **Aspose.Email Java para Jython**, chame o método **add_attachments** do módulo **ManageAttachments**. Aqui você pode ver um exemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import Attachment

from com.aspose.email import MessageFormat

class ManageAttachments:

    def __init__(self):



        self.add_attachments()

   

    def add_attachments(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ManageAttachments/'



        # Crie uma instância da classe MailMessage

        message =MailMessage()

        # Defina o assunto da mensagem

        message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

        mail_address = MailAddress

        # Defina o corpo em HTML

        message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

            "<font color=blue>Esta linha está em azul</font>")

        # Defina as informações do remetente

        message.setFrom(MailAddress("from@domain.com", "Nome do Remetente", False))

        # Adicione destinatários TO

        message.getTo().add(MailAddress("to1@domain.com", "Destinatário 1", False))

        # Adicionando anexo

        # Carregue um anexo

        attachment = Attachment(dataDir + "1.txt")

        # Adicione o anexo na instância da classe MailMessage

        message.addAttachment(attachment)

        # Salve a mensagem no disco

        messageFormat=MessageFormat()

        message.save(dataDir + "Add-Attachment.msg", messageFormat.getMsg())

        # Exiba o Status

        print "Anexo adicionado com sucesso."



if __name__ == '__main__':        

    ManageAttachments()

```
## **Baixar Código em Execução**
Baixe **Gerenciar Anexos em Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)