---
title: "Licenciamento"
url: /pt/python-net/licensing/
weight: 60
type: docs
---


## **Avalie o Aspose.Email**
Você pode baixar o Aspose.Email para Python via .NET gratuitamente para avaliação. A versão de avaliação oferece quase toda a funcionalidade do produto, com certas limitações. A mesma versão de avaliação se torna licenciada quando você adquire uma licença e adiciona algumas linhas de código para aplicar a licença.

Se você deseja testar o Aspose.Email sem limitações da versão de avaliação, também pode solicitar uma Licença Temporária de 30 Dias. Consulte [Como obter uma Licença Temporária?](https://purchase.aspose.com/temporary-license)
### **Limitações da Versão de Avaliação**
A versão de avaliação do Aspose.Email (sem uma licença especificada) fornece toda a funcionalidade do produto, exceto algumas limitações de avaliação.

1. O arquivo License.txt é adicionado à mensagem salva usando o Aspose.Email
1. Apenas 50 e-mails podem ser extraídos de uma pasta em um arquivo PST
1. Apenas 3 anexos, bem como imagens incorporadas, podem ser extraídos de um arquivo MSG
1. O número máximo de anexos processados no formato CFB é 1
1. O número máximo de destinatários processados no formato CFB é 1
1. Adiciona "Mensagem de Avaliação" no Assunto durante o salvamento nos formatos CFB, EML ou MSG
1. A Data Final não pode ser posterior a 31-12-2004 no método GenerateOccurrences do padrão de recorrência. Isso permite que você teste o produto de forma significativa, mas impossível de usar em uma aplicação de produção. Por exemplo, você pode criar um padrão como "começar em 1 de janeiro de 2000 e repetir todos os últimos dias úteis do mês" e gerar ocorrências para ele. Ocorrências após 31 de dezembro de 2004 não serão geradas no modo de avaliação
1. Adiciona "Imagem de Marca d'Água de Avaliação" durante o salvamento nos formatos XPS ou TIFF.
1. O número máximo de endereços de e-mail ambíguos e nomes de exibição resolvidos pelo MS Exchange Server é 20
1. O comprimento máximo do arquivo de dados permitido para ser arrastado e solto com FileDropPanel é 51200 bytes
1. Exibe uma caixa de mensagem com "Mensagem de Avaliação" durante uma operação de arrastar e soltar usada pelo FileDropPanel
1. Apenas 1 arquivo é extraído do fluxo MSO dado pelo método InlineAttachmentExtractor.EnumerateMsoPackage
## **Aplicando uma Licença**
Você pode baixar facilmente uma versão de avaliação do Aspose.Email em sua página de download. A versão de avaliação oferece absolutamente as mesmas capacidades que a versão licenciada do Aspose.Email. Além disso, a versão de avaliação simplesmente se torna licenciada quando você adquire uma licença e adiciona algumas linhas de código para aplicar a licença.
### **Sobre a Licença**
A licença é um arquivo XML de texto simples que contém detalhes como o nome do produto, o número de desenvolvedores para os quais está licenciada, a data de expiração da assinatura e assim por diante. O arquivo é digitalmente assinado, portanto, não modifique o arquivo. Até a adição inadvertida de uma quebra de linha extra no arquivo o invalidará.

Você precisa definir uma licença antes de utilizar o Aspose.Email se quiser evitar suas limitações de avaliação. É necessário definir uma licença apenas uma vez por aplicativo (ou processo).
### **Aplicar Licença Usando Objeto de Arquivo**
#### **Aplicar Licença usando Objeto de Arquivo**
A maneira mais fácil de definir uma licença é colocar o arquivo de licença na mesma pasta que a dll do componente (incluída no Aspose.Email) e especificar apenas o nome do arquivo sem seu caminho.

``` java

 // Instanciar uma instância da licença e definir o arquivo de licença através de seu caminho

license lic = new license();

license.set_license("Aspose.Email.Python.lic");

```

Quando você chama o método SetLicense, o nome da licença deve ser o mesmo que o nome do seu arquivo de licença. Por exemplo, você pode alterar o nome do arquivo de licença para "Aspose.Email.Python.lic.xml". Então, em seu código, você deve usar o nome da licença modificado (ou seja, Aspose.Email.Python.lic.xml) para o método set_license.