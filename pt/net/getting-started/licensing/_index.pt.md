---
title: "Licenciamento"
url: /pt/net/licensing/
weight: 80
type: docs
---


## **Avaliar Aspose.Email**
Você pode baixar o Aspose.Email para .NET gratuitamente para avaliação. A versão de avaliação fornece quase todas as funcionalidades do produto com algumas limitações. A mesma versão de avaliação se torna licenciada quando você compra uma licença e adiciona algumas linhas de código para aplicar a licença.

Se você quiser testar o Aspose.Email sem as limitações da versão de avaliação, também pode solicitar uma Licença Temporária de 30 dias. Consulte [Como obter uma Licença Temporária?](https://purchase.aspose.com/temporary-license)
### **Limitações da Versão de Avaliação**
A versão de avaliação do Aspose.Email (sem uma licença especificada) oferece funcionalidade total do produto, exceto por algumas limitações de avaliação.

1. O arquivo License.txt é adicionado ao arquivo de mensagem salvo usando o Aspose.Email
1. Apenas 50 emails podem ser extraídos de uma pasta em um arquivo PST
1. Apenas 3 anexos, assim como imagens inline, podem ser extraídos de um arquivo MSG
1. O número máximo de anexos processados no formato CFB é 1
1. O número máximo de destinatários processados no formato CFB é 1
1. Adiciona "Mensagem de Avaliação" no Assunto durante o salvamento nos formatos CFB, EML ou MSG
1. A Data de Término não pode ser posterior a 31-12-2004 no método GenerateOccurrences do padrão de recorrência. Isso permite que você teste o produto de forma significativa, mas torna impossível utilizá-lo em uma aplicação de produção. Por exemplo, você pode criar um padrão como "iniciar em 1 de janeiro de 2000 e repetir a cada último dia útil do mês" e gerar ocorrências para ele. Ocorrências após 31 de dezembro de 2004 não serão geradas no modo de avaliação
1. Adiciona "Imagem de Marca D'água de Avaliação" durante o salvamento nos formatos XPS ou TIFF.
1. O número máximo de endereços de e-mail e nomes exibidos ambíguos resolvidos pelo MS Exchange Server é 20
1. O comprimento máximo do arquivo de dados permitido para ser arrastado e solto com FileDropPanel é de 51200 bytes
1. Exibe uma caixa de mensagem com "Mensagem de Avaliação" durante uma operação de arrastar e soltar usada pelo FileDropPanel
1. Apenas 1 arquivo é extraído do dado de stream MSO dado pelo método InlineAttachmentExtractor.EnumerateMsoPackage
## **Aplicando uma Licença**
Você pode facilmente baixar uma versão de avaliação do Aspose.Email a partir de sua [página de download](https://www.nuget.org/packages/Aspose.Email/). A versão de avaliação fornece exatamente as mesmas capacidades que a versão licenciada do Aspose.Email. Além disso, a versão de avaliação simplesmente se torna licenciada quando você compra uma licença e adiciona algumas linhas de código para aplicar a licença.
### **Sobre a Licença**
A licença é um arquivo XML de texto simples que contém detalhes como o nome do produto, número de desenvolvedores a quem está licenciada, data de expiração da assinatura, etc. O arquivo é digitalmente assinado, então não modifique o arquivo. Mesmo a adição inadvertida de uma quebra de linha extra no arquivo invalidará a licença.

Você precisa definir uma licença antes de utilizar o Aspose.Email se quiser evitar suas limitações de avaliação. É necessário definir uma licença apenas uma vez por aplicação (ou processo).
### **Aplicar Licença Usando Arquivo ou Objeto Stream**
#### **Definindo uma Licença no Aspose.Email para .NET**
No Aspose.Email, a licença pode ser carregada a partir de um arquivo, stream ou um recurso incorporado. Aspose.Email tenta encontrar a licença nos seguintes locais:

- Caminho explícito
- A pasta que contém a dll do componente (incluída no Aspose.Email)
- A pasta que contém a montagem que chamou a dll do componente (incluída no Aspose.Email)
- A pasta que contém a montagem de entrada (seu .exe)
- Um recurso incorporado na montagem que chamou a dll do componente (incluída no Aspose.Email) Existem dois métodos comuns para definir a licença, que são discutidos abaixo:
#### **Aplicar Licença usando Arquivo ou Objeto Stream**
A maneira mais fácil de definir uma licença é colocar o arquivo da licença na mesma pasta que a dll do componente (incluída no Aspose.Email) e especificar apenas o nome do arquivo sem o caminho.

``` java

 // Instanciar uma instância da licença e definir o arquivo da licença através de seu caminho

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense("Aspose.Email.lic");

```

``` java

 // Instanciar uma instância da licença e definir a licença através de um stream

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense(myStream);

```

Quando você chama o método SetLicense, o nome da licença deve ser o mesmo que o nome do seu arquivo de licença. Por exemplo, você pode alterar o nome do arquivo da licença para "Aspose.Email.lic.xml". Então, em seu código, você deve usar o nome de licença modificado (ou seja, Aspose.Email.lic.xml) para o método SetLicense.
### **Aplicar Licença Metered**
Aspose.Email permite que os desenvolvedores apliquem uma chave metered. É um novo mecanismo de licenciamento. O novo mecanismo de licenciamento será utilizado juntamente com o método de licenciamento existente. Aqueles clientes que desejam ser cobrados com base no uso dos recursos da API podem usar o licenciamento metered. Para mais detalhes, consulte a seção [FAQ de Licenciamento Metered](https://purchase.aspose.com/faqs/licensing/metered).

Uma nova classe Metered foi introduzida para aplicar a chave metered. A seguir está o código de exemplo demonstrando como definir as chaves públicas e privadas metered.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Licensing-ApplyMeteredLicense-ApplyMeteredLicense.cs" >}}
## **Incluindo o Arquivo de Licença como um Recurso Incorporado**
Outra maneira interessante de embalar a licença com sua aplicação e garantir que ela não será perdida é incluí-la como um recurso incorporado em uma das montagens que chama a dll do componente (incluída no Aspose.Email). Para incluir o arquivo de licença como um recurso incorporado, execute as seguintes etapas:

- No Visual Studio .NET, inclua o arquivo de licença (.lic) no projeto usando o menu Arquivo | Adicionar Item Existente...
- Selecione o arquivo no Gerenciador de Soluções e defina a Ação de Compilação como Recurso Incorporado na janela Propriedades
- Para acessar a licença incorporada na montagem (como recurso incorporado), não é necessário chamar os métodos GetExecutingAssembly e GetManifestResourceStream da classe System.Reflection.Assembly do Microsoft .NET Framework. Tudo o que precisa ser feito é adicionar o arquivo da licença como um recurso incorporado ao seu projeto e passar o nome do arquivo da licença no método SetLicense. A classe License irá automaticamente encontrar o arquivo de licença nos recursos incorporados.

Por favor, revise o exemplo dado abaixo para entender este método de configuração de licença (incorporada) em suas aplicações.

``` java

 // Instanciar a classe License

Aspose.Email.License license = new Aspose.Email.License();

// Passar apenas o nome do arquivo da licença incorporado na montagem

license.SetLicense("Aspose.Email.lic");

```