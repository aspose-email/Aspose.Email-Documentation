---
title: "Criar Novo PST em Ruby"
url: /pt/java/create-new-pst-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Criar Novo PST**
Para criar um novo PST usando **Aspose.Email Java para Ruby**, basta invocar o módulo **CreatePST**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Criar uma instância de PersonalStorage

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "sample1.pst", 0)

\# Criar uma pasta na raiz do pst

pst.getRootFolder().addSubFolder("myInbox")

\# Adicionar mensagem à pasta recém-criada

mapi_message = Rjb::import('com.aspose.email.MapiMessage')

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(data_dir + "Message.msg"))

puts "PST criado com sucesso."

```
## **Código em Execução para Download**
Baixe **Criar Novo PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)