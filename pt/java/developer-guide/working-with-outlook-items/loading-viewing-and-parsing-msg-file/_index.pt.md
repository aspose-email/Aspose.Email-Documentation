---
title: "Carregando, Visualizando e Analisando arquivo MSG"
url: /pt/java/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


Este tópico explica como carregar um arquivo de Mensagem do Microsoft Outlook (*.msg). A classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) é usada para carregar arquivos MSG e fornece várias funções de carregamento estáticas para diferentes cenários. O seguinte trecho de código mostra como carregar arquivos MSG a partir de um arquivo ou de um fluxo.

## **Carregando Arquivos MSG**

O seguinte trecho de código mostra como carregar arquivos MSG.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

// Criar uma instância de MapiMessage a partir de um arquivo
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Obter assunto
System.out.println("Assunto:" + msg.getSubject());

// Obter endereço do remetente
System.out.println("De:" + msg.getSenderEmailAddress());

// Obter corpo
System.out.println("Corpo" + msg.getBody());

// Obter informações dos destinatários
System.out.println("Destinatário: " + msg.getRecipients());

// Obter anexos
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Nome do Anexo: " + att.getFileName());
    System.out.println("Nome de Exibição do Anexo: " + att.getDisplayName());
}
~~~

O seguinte exemplo de código mostra como usar **MailMessage** para carregar uma mensagem no formato MSG.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

Deve-se observar que a mensagem resultante é convertida para o formato EML, incluindo anexos de mensagens embutidas. Não utilize este método de carregamento se você deseja preservar algumas propriedades específicas do formato msg da mensagem original.

Para preservar o formato original dos anexos de mensagens embutidas, use a propriedade [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--) .

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Carregando a Partir de um Fluxo**

O seguinte trecho de código mostra como carregar um arquivo a partir de um fluxo.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// Criar uma instância de MapiMessage a partir de um arquivo
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Criar uma instância de MapiMessage a partir de um fluxo
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Obter assunto
    System.out.println("Assunto:" + msg.getSubject());

    // Obter endereço do remetente
    System.out.println("De:" + msg.getSenderEmailAddress());

    // Obter corpo
    System.out.println("Corpo" + msg.getBody());

}
~~~

## **Convertendo EML para MSG Preservando o Formato EML Embutido**

Arquivos EML podem ser carregados na classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) instanciando um objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) e passando-o para o método [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-). Se o arquivo EML contiver arquivos EML embutidos, use [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-) para reter o formato dos arquivos EML embutidos. O trecho de código abaixo mostra como carregar arquivos EML na [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) enquanto preserva o formato dos arquivos EML embutidos.

{{% alert %}}
**Experimente!**

Converta e-mails e arquivos de mensagens online com o gratuito [**Aplicativo de Conversão Aspose.Email**](https://products.aspose.app/email/pt/Conversion).
{{% /alert %}}

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Preservar o Formato da Mensagem Embutida
options.setPreserveEmbeddedMessageFormat(true);

//Converter EML para MSG com Opções
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~