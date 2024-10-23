---
title: "Trabalhando com Listas de Distribuição em Ruby"
url: /pt/java/trabalhando-com-listas-de-distribuicao-em-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Trabalhando com Listas de Distribuição**
Para criar uma lista de distribuição usando **Aspose.Email Java para Ruby**, simplesmente invoque o módulo **DistributionList**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

oneOffmembers = Rjb::import('com.aspose.email.MapiDistributionListMemberCollection').new

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("John R. Patrick", "JohnRPatrick@armyspy.com"))

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("Tilly Bates", "TillyBates@armyspy.com"))

dlist = Rjb::import('com.aspose.email.MapiDistributionList').new("Lista simples", oneOffmembers)

dlist.setBody("Corpo de teste")

dlist.setSubject("Assunto de teste")

dlist.setMileage("Quilometragem de teste")

dlist.setBilling("Cobrança de teste")

dlist.save(data_dir + "distlist.msg")

puts "Lista de distribuição salva com sucesso."

```
## **Baixar Código em Execução**
Baixe **Trabalhando com Listas de Distribuição (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)