---
title: "Gerenciar Anexos em Mensagens de Email em Ruby"
url: /pt/java/manage-attachments-in-email-message-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Gerenciar Anexos em Mensagens de Email**
Para adicionar anexos a uma nova mensagem de email usando **Aspose.Email Java for Ruby**, chame o método **add_attachments** do módulo **ManageAttachments**. Aqui você pode ver um código de exemplo.

**Código Ruby**

``` ruby

 def add_attachments()

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Crie uma nova instância da classe MailMessage

    message = Rjb::import('com.aspose.email.MailMessage').new

    # Defina o assunto da mensagem

    message.setSubject("Nova mensagem criada pelo Aspose.Email para Java")

    mail_address = Rjb::import('com.aspose.email.MailAddress')

    # Defina o corpo Html

    message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" +

            "<font color=blue>Esta linha está na cor azul</font>")

    # Defina as informações do remetente

    message.setFrom(mail_address.new("from@domain.com", "Nome do Remetente", false))

    # Adicione os destinatários NO

    message.getTo().add(mail_address.new("to1@domain.com", "Destinatário 1", false))

    # Adicionando anexo

    # Carregue um anexo

    attachment = Rjb::import('com.aspose.email.Attachment').new(data_dir + "attachment.txt")

    # Adicione o anexo à instância da classe MailMessage

    message.addAttachment(attachment)

    # Salve a mensagem no disco

    message.save(data_dir + "Add-Attachment.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

    # Exiba o Status

    puts "Anexo adicionado com sucesso."

end

```
## **Baixar Código em Execução**
Baixe **Gerenciar Anexos em Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/manageattachments.rb)