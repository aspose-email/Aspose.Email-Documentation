---
title: "Atualizar e Salvar um Email em Jython"
url: /pt/java/update-and-save-an-email-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Atualizar e Salvar um Email**
Para Atualizar e Salvar um Email usando **Aspose.Email Java para Jython**, simplesmente invoque o módulo **UpdateEmail**. Aqui você pode ver um código de exemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddressCollection

from com.aspose.email import MailMessageSaveType

class UpdateEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/UpdateEmail/'



        # Inicializar e Carregar um arquivo MSG existente especificando o MessageFormat

        mailMessage=MailMessage()

        email = mailMessage.load(dataDir + "Message.msg")

        # Inicializar uma variável String para obter o Assunto do Email

        subject = email.getSubject()

        # Adicionar mais informações ao Assunto

        subject = subject + " Este texto é adicionado ao assunto existente"

        # Definir o Assunto do Email

        email.setSubject('Este texto é adicionado ao assunto existente')

        # Inicializar uma variável String para obter o Corpo HTML do Email

        body = email.getHtmlBody()

        # Adicionar mais informações à variável Corpo

        body = body + "<br> Este texto é adicionado ao corpo existente"

        # Definir o Corpo do Email

        email.setHtmlBody(body)

        # Inicializar objeto MailAddressCollection

        contacts = MailAddressCollection()

        # Recuperar lista TO do Email

        contacts = email.getTo()

        # Adicionar outro endereço de email à coleção

        contacts.add("to1@domain.com")

        # Definir a coleção como lista TO do Email

        email.setTo(contacts)

        # Inicializar MailAddressCollection

        contacts = MailAddressCollection()

        # Recuperar lista CC do Email

        contacts = email.getCC()

        # Adicionar outro endereço de email à coleção

        contacts.add("cc2@domain.com")

        # Definir a coleção como lista CC do Email

        email.setCC(contacts)

        # Salvar a mensagem de Email no disco especificando o MessageFormat

        mailMessageSaveType=MailMessageSaveType

        email.save(dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

        # Exibir Status

        print "Mensagem de email atualizada com sucesso."





if __name__ == '__main__':        

    UpdateEmail()

```
## **Baixar Código em Execução**
Baixar **Atualizar e Salvar um Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)