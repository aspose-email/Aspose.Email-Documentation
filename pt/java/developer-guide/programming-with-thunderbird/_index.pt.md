---
title: "Programando com Thunderbird"
url: /pt/java/programming-with-thunderbird/
weight: 100
type: docs
---

## **Ler Mensagens do MBOX**
[Mozilla Thunderbird](https://www.thunderbird.net/pt-BR/) é um cliente de email de código aberto e multiplataforma, desenvolvido pela Mozilla Foundation. Ele armazena emails em sua própria estrutura de arquivos, gerenciando índices de mensagens e subpastas por meio de formatos de arquivo proprietários. Aspose.Email pode trabalhar com estruturas de armazenamento de email do Thunderbird. A classe [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) permite que os desenvolvedores leiam mensagens do arquivo de armazenamento de emails do Mozilla Thunderbird. Este artigo mostra como ler as mensagens do armazenamento de email do Thunderbird:

1. Abra o arquivo de armazenamento do Thunderbird em *FileStream*.
1. Crie uma instância da classe [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) e passe o stream acima para o construtor.
1. Chame [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) para obter a primeira mensagem.
1. Use o mesmo [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) em um loop while para ler todas as mensagens.
1. Feche todos os streams.

O seguinte snippet de código mostra como ler todas as mensagens de um armazenamento de email do Thunderbird.
~~~Java
//Obtendo informações de marcador enquanto lê mensagens do arquivo de armazenamento Mbox
try (FileInputStream stream = new FileInputStream(dataDir + "Outlook.pst")) {
    MboxLoadOptions lo = new MboxLoadOptions();
    lo.setLeaveOpen(false);
    try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
        MailMessage msg;
        String[] fromMarker = {null};
        while ((msg = reader.readNextMessage(/* out */fromMarker)) != null) {
            System.out.println(fromMarker[0]);
        }
    }
}
~~~

### **Configurar Opções de Carregamento ao Ler Mensagens do MBOX**

A API Aspose.Email permite as seguintes manipulações com mensagens ao lê-las de um arquivo MBOX:

**Converter Mensagens de MBOX para PST Preservando Anexos TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Converter mensagens de mbox para pst preservando anexos tnef.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
A propriedade [MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) - Obtém ou define opções de carregamento de email ao analisar um armazenamento Mbox.

**Ler Mensagens Preservando Anexos TNEF**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Ler mensagens preservando anexos tnef.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
O método [MboxrdStorageReader.readNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) - O parâmetro EmlLoadOptions especifica opções ao ler uma mensagem do armazenamento Mbox.

**Enumerar Mensagens Preservando Anexos TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Enumerar mensagens preservando anexos tnef.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // fazer algo
}
```
O método [MboxrdStorageReader.enumerateMessages(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) - Especifica EmlLoadOptions ao ler uma mensagem do armazenamento Mbox.

## **Extrair Mensagens do MBOX por Identificadores**

Às vezes, é necessário extrair mensagens selecionadas por identificadores. Por exemplo, seu aplicativo armazena identificadores em um banco de dados e extrai uma mensagem sob demanda. Esta é uma maneira eficiente de evitar percorrer todo o armazenamento a cada vez para encontrar uma mensagem específica para extrair. Para implementar esse recurso para arquivos MBOX, Aspose.Email fornece os seguintes métodos e classes:

- A classe [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) com a propriedade [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) - Obtém o identificador da entrada.
- O método [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) da classe [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Expondo o enumerador, que suporta a iteração de mensagens no armazenamento.
- O método [extractMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) da classe [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Obtém a mensagem do MBOX.

O exemplo de código abaixo demonstra como extrair mensagens do MBOX por identificadores:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Nota:** O ID da mensagem é único dentro do arquivo de armazenamento. Os IDs são criados pela Aspose.Email e não podem ser usados em outras bibliotecas ou aplicativos de processamento MBOX de terceiros.

## **Escrevendo Mensagens**
A classe [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) fornece a capacidade de escrever novas mensagens no arquivo de armazenamento de email do Thunderbird. Para escrever mensagens:

1. Abra o arquivo de armazenamento do Thunderbird em *FileStream*.
1. Crie uma instância da classe [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) e passe o stream acima para o construtor.
1. Prepare uma nova mensagem usando a classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage).
1. Chame o método [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) e passe a instância [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) acima para adicionar a mensagem ao armazenamento do Thunderbird.
1. Feche todos os streams.

O seguinte snippet de código mostra como escrever mensagens no armazenamento de email do Thunderbird.
~~~Java
//Obtendo informações de marcador enquanto escreve mensagens no arquivo de armazenamento Mbox
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
~~~ 

## **Obtendo o Número Total de Mensagens do Arquivo MBox**
A classe [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) fornece a capacidade de ler o número de itens disponíveis em um arquivo MBox. Isso pode ser usado para desenvolver aplicativos que mostram o progresso da atividade enquanto processam tal arquivo.
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Total de mensagens no arquivo Mbox: " + reader.getTotalItemsCount());
}
~~~ 

## **Obter Tamanho da Mensagem Atual**
~~~Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //retorna o número de bytes lidos
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Bytes lidos: " + currentDataSize);
    }
}
~~~ 

## **Definir Codificação de Texto Preferida ao Carregar Arquivos Mbox**

O método [setPreferredTextEncoding(Charset value)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) da classe [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) obtém ou define a codificação preferida para mensagens. Crie um leitor para o arquivo Mbox com as opções de carregamento especificadas e suas mensagens com o conteúdo codificado serão corretamente lidas e processadas. O seguinte exemplo de código mostra como implementar esse recurso em um projeto:

~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~ 

## **Dividir Armazenamento Mbox em Partes Menores**

Aspose.Email fornece os seguintes componentes projetados para ter mais controle sobre o processamento de armazenamento Mbox, permitindo que você divida arquivos grandes em partes gerenciáveis e implemente ações personalizadas durante o processo:

- O método [MboxStorageReader.SplitInto(long chunkSize, String outputPath)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) - Permite que você divida o armazenamento Mbox em partes menores, facilitando o gerenciamento e processamento de grandes arquivos Mbox.

MboxStorageReader.SplitInto(long chunkSize, String outputPath, String partFileNamePrefix) Uma variação do método anterior, este também permite especificar um prefixo personalizado para os nomes de arquivos Mbox divididos.

MboxStorageReader.setEmlCopyingEventHandler Evento Este evento ocorre antes que um email seja copiado para um novo arquivo Mbox. Você pode personalizar ações antes que os emails sejam processados.

MboxStorageReader.setEmlCopiedEventHandler Evento Este evento ocorre após um email ser copiado para um novo arquivo Mbox. Você pode realizar ações de pós-processamento em emails.

MboxStorageReader.setMboxFileCreatedEventHandler Evento Este evento ocorre quando um novo arquivo Mbox é criado. Você pode lidar com esse evento para reagir à criação de arquivo.

MboxStorageReader.setMboxFileFilledEventHandler Evento Este evento ocorre quando um novo arquivo Mbox é preenchido com emails. Você pode responder ao arquivo sendo povoado com emails.

NewStorageEventHandler(Object sender, NewStorageEventArgs e) Representa um delegado para lidar com eventos que ocorrem após um novo arquivo de armazenamento ser criado ou processado.

MimeItemCopyEventHandler(Object sender, MimeItemCopyEventArgs e) Representa um delegado para lidar com eventos relacionados à cópia de itens Mime, geralmente usados em cenários onde um objeto MailMessage é copiado de um armazenamento para outro.

NewStorageEventArgs Representa os argumentos usados em eventos que são gerados após um novo arquivo de armazenamento ser criado ou após ser processado.

MimeItemCopyEventArgs Representa argumentos de evento relacionados à cópia de um objeto MailMessage de um armazenamento para outro, seja antes do início da cópia ou após sua conclusão.

O exemplo de código abaixo demonstra como interagir com arquivos Mbox, lidar com eventos relacionados a esses arquivos e realizar operações como dividir o armazenamento Mbox em partes menores enquanto acompanha a contagem de mensagens e partes:

```java
messageCount = 0;
partCount = 0;

// Crie uma instância de MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Inscreva-se em eventos
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Novo arquivo Mbox criado: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Arquivo Mbox preenchido com mensagens: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Mensagem adicionada ao novo arquivo Mbox. Assunto: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Dividir o armazenamento Mbox em partes menores
mbox.splitInto(10000000, testOutPath, "Prefix");

// Saída do total de messageCount e partCount
System.out.println("Total de mensagens adicionadas: " + messageCount);
System.out.println("Total de partes criadas: " + partCount);
```