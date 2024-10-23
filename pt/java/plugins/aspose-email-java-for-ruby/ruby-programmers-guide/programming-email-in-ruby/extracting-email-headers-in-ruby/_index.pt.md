---
title: "Extraindo Cabeçalhos de Email em Ruby"
url: /pt/java/extracting-email-headers-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Extraindo Cabeçalhos de Email**
Para extrair cabeçalhos de email usando **Aspose.Email Java para Ruby**, simplesmente invoque o módulo **ExtractEmailHeaders**. Aqui você pode ver um código de exemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Inicializar e carregar um arquivo EML existente especificando o MessageFormat

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "Imprimindo todos os cabeçalhos:"

\# Imprimir todos os cabeçalhos

i=0

while i < message.getHeaders().getCount()

    puts message.getHeaders().get(i)

    i +=1

end 

```
## **Baixar Código em Execução**
Baixe **Extraindo Cabeçalhos de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)