---
title: "Licenciamento"
url: /pt/java/licensing/
weight: 60
type: docs
---

{{% alert color="primary" %}} 

Você pode baixar uma versão de avaliação do **Aspose.Email** para Java a partir de sua página de download. A versão de avaliação fornece absolutamente as mesmas capacidades que a versão licenciada do produto. Além disso, a versão de avaliação simplesmente se torna licenciada quando você compra uma licença e adiciona algumas linhas de código para aplicar a licença.

Assim que você estiver satisfeito com sua avaliação do **Aspose.Email**, você pode adquirir uma licença no site da Aspose. Familiarize-se com os diferentes tipos de assinatura oferecidos. Se você tiver alguma dúvida, não hesite em contatar a equipe de vendas da Aspose.

Toda licença Aspose inclui uma assinatura de um ano para atualizações gratuitas para quaisquer novas versões ou correções que saiam durante esse período. O suporte técnico é gratuito e ilimitado, fornecido tanto para usuários licenciados quanto para usuários de avaliação.

{{% /alert %}} {{% alert color="primary" %}} 

Se você deseja testar o **Aspose.Email** sem limitações da versão de avaliação, solicite uma licença temporária de 30 dias. Consulte [Como obter uma Licença Temporária?](https://purchase.aspose.com/temporary-license) para mais informações.

{{% /alert %}} 
## **Limitações da Versão de Avaliação**
A versão de avaliação do Aspose.Email (sem uma licença especificada) oferece funcionalidade total do produto, exceto por alguns de seus componentes, como Aspose.Email.Mail, Aspose.Email.Pop3 e Aspose.Email.Imap, que contêm algumas limitações de avaliação.

1. O arquivo License.txt é adicionado ao arquivo de mensagem salvo usando Aspose.Email
2. Apenas 50 e-mails podem ser extraídos de uma pasta em um arquivo PST
3. Apenas 3 anexos, assim como imagens incorporadas, podem ser extraídos de um arquivo MSG
4. O número máximo de anexos processados em formato CFB é 1
5. O número máximo de destinatários processados em formato CFB é 1
6. Adiciona "Mensagem de Avaliação" no Assunto durante o salvamento nos formatos CFB, EML ou MSG
7. A Data Final não pode ser posterior a 31-12-2004 no método GenerateOccurrences do padrão de recorrência. Isso permite que você teste o produto de maneira significativa, mas é impossível usá-lo em uma aplicação de produção. Por exemplo, você pode criar um padrão como "começar em 1 de janeiro de 2000 e repetir todo último dia útil do mês" e gerar ocorrências para isso. Ocorrências após 31 de dezembro de 2004 não serão geradas no modo de avaliação
8. Adiciona "Imagem de Marca D'água de Avaliação" durante o salvamento nos formatos XPS ou TIFF.
9. O número máximo de endereços de e-mail ambíguos e nomes de exibição resolvidos pelo MS Exchange Server é 20
10. O tamanho máximo do arquivo de dados permitido para arrastar e soltar com FileDropPanel é 51200 bytes
11. Mostra uma caixa de mensagem com "Mensagem de Avaliação" durante uma operação de arrastar e soltar usada pelo FileDropPanel
12. Apenas 1 arquivo é extraído do fluxo MSO fornecido pelo método InlineAttachmentExtractor.EnumerateMsoPackage
### **Configurando uma Licença**
A licença é um arquivo XML em texto simples que contém detalhes como o nome do produto, número de desenvolvedores para os quais é licenciada, data de expiração da assinatura e assim por diante. O arquivo é assinado digitalmente, então não modifique o arquivo; até mesmo a adição inadvertida de uma quebra de linha extra ao arquivo invalidará sua licença.

Você precisa aplicar uma licença se quiser evitar as limitações da versão de avaliação. Você só precisa definir uma licença uma vez por aplicação ou processo.

A licença pode ser carregada de um fluxo ou arquivo nas seguintes localizações:

1. Caminho explícito.
2. A pasta que contém o Aspose.Email.jar.

Use o método License.setLicense para licenciar o componente. Muitas vezes, a maneira mais fácil de definir uma licença é colocar o arquivo de licença na mesma pasta que o Aspose.Email.jar e especificar apenas o nome do arquivo sem o caminho, conforme mostrado no exemplo a seguir:
#### **Configurando a Licença a partir do Arquivo**
Neste exemplo, **Aspose.Email** tentará encontrar o arquivo de licença na pasta que contém os JARs da sua aplicação.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromFile.java" >}}
#### **Configurando a Licença a partir do Fluxo**
Inicializa uma licença a partir de um fluxo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromStream.java" >}}
### **Aplicar Licença Metered**
Aspose.Email permite que desenvolvedores apliquem chave metered. É um novo mecanismo de licenciamento. O novo mecanismo de licenciamento será usado juntamente com o método de licenciamento existente. Aqueles clientes que desejam ser cobrados com base no uso das funcionalidades da API podem usar o licenciamento metered. Para mais detalhes, consulte a seção [FAQ de Licenciamento Metered](https://purchase.aspose.com/faqs/licensing/metered).

Uma nova classe Metered foi introduzida para aplicar a chave metered. A seguir está o código de exemplo demonstrando como definir chaves públicas e privadas metered.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyMeteredLicense-ApplyMeteredLicense.java" >}}
## **Incluindo o Arquivo de Licença como Embutido**
### **Validar a Licença**
É possível validar se a licença foi configurada corretamente ou não. A classe [License](http://www.aspose.com/api/java/email/com.aspose.email/classes/License) possui o campo isLicensed que retornará verdadeiro se a licença tiver sido configurada corretamente.

**Java**

``` cs

 License license = new License();

license.setLicense("Aspose.Email.Java.lic");

if (License.isLicensed()) {

    System.out.println("Licença está Configurada!");

}

```