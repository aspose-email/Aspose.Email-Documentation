---
title: "Convertendo Mensagens de Email em Ruby"
url: /pt/java/converting-email-messages-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Convertendo Mensagens de Email**
Para converter mensagens de email usando **Aspose.Email Java for Ruby**, chame o método **convert_eml_to_msg** do módulo **Converter**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 def convert_eml_to_msg()    

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Inicializar e carregar um arquivo EML existente especificando o MessageFormat

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Salvar a mensagem de email no disco em formato Unicode

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Exibir Status

    puts "Convertido eml para msg com sucesso."

end

```
## **Baixar Código em Execução**
Baixe **Convertendo Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)