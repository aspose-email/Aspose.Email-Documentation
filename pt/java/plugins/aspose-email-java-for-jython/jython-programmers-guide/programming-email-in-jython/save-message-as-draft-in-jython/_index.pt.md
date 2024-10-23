---
title: "Salvar Mensagem como Rascunho em Jython"
url: /pt/java/save-message-as-draft-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Salvar Mensagem como Rascunho**
Para salvar mensagem como rascunho usando **Aspose.Email Java para Jython**, basta invocar o módulo **SaveMessageAsDraft**. Aqui você pode ver um exemplo de código.

**Código em Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MapiMessage

from com.aspose.email import MapiMessageFlags

class SaveMessageAsDraft:

    def __init__(self):

        dataDir = Settings.dataDir + 'ProgrammingEmail/SaveMessageAsDraft/'

        # Criar uma instância da classe MailMessage

        message = MailMessage()

            # Definir o assunto da mensagem

        message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

        mail_address = MailAddress

        # Definir corpo HTML

        message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

            "<font color=blue>Esta linha está na cor azul</font>")

        # Definir informações do remetente

        message.setFrom(MailAddress("from@domain.com", "Nome do Remetente", False))

        # Adicionar destinatários TO

        message.getTo().add(MailAddress("to1@domain.com", "Destinatário 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Destinatário 2", False))

        # Criar uma instância de MapiMessage e carregar a instância de MailMessage nela

        mapiMessage=MapiMessage()

        mapi_msg = mapiMessage.fromMailMessage(message)

        # Definir os MapiMessageFlags como UNSENT e FROMME

        mapi_message_flags = MapiMessageFlags()

        # Salvar o MapiMessage no disco

        mapi_msg.save(dataDir + "New-Draft.msg")

        # Exibir Status

        print "Rascunho salvo com sucesso."

if __name__ == '__main__':        

    SaveMessageAsDraft()

```
## **Baixar Código em Execução**
Baixe **Salvar Mensagem como Rascunho (Aspose.Email)** de qualquer um dos sites de codificação social abaixo mencionados:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)