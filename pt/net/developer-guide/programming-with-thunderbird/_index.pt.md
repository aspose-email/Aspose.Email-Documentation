---
title: "Programação com Thunderbird"
url: /pt/net/programming-with-thunderbird/
weight: 110
type: docs
---

## **Lendo arquivos MBOX**

[Mozilla Thunderbird](https://www.thunderbird.net/pt-BR/) é um cliente de e-mail de código aberto e multiplataforma, desenvolvido pela Mozilla Foundation. Ele armazena e-mails em sua própria estrutura de arquivos, gerenciando índices de mensagens e subpastas através de formatos de arquivo proprietários. Aspose.Email pode trabalhar com estruturas de armazenamento de e-mail do Thunderbird. A classe [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) permite que os desenvolvedores leiam mensagens do arquivo de armazenamento de e-mail do Mozilla Thunderbird. Este artigo mostra como ler as mensagens do armazenamento de e-mail do Thunderbird:

1. Abra o arquivo de armazenamento do Thunderbird no *FileStream*.
1. Crie uma instância da classe [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) e passe o stream acima para o construtor.
1. Chame [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) para obter a primeira mensagem.
1. Use o mesmo [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) em um loop while para ler todas as mensagens.
1. Feche todos os streams.

O seguinte trecho de código mostra como ler todas as mensagens de um armazenamento de e-mail do Thunderbird.

```cs
// O caminho para o diretório de arquivos.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Abra o arquivo de armazenamento com FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Crie uma instância da classe MboxrdStorageReader e passe o stream
var reader = new MboxrdStorageReader(stream, false);
// Comece a ler mensagens
var message = reader.ReadNextMessage();

// Leia todas as mensagens em um loop
while (message != null)
{
    // Manipule a mensagem - mostre o conteúdo
    Console.WriteLine("Assunto: " + message.Subject);
    // Salve esta mensagem no formato EML ou MSG
    message.Save(message.Subject + ".eml", SaveOptions.DefaultEml);
    message.Save(message.Subject + ".msg", SaveOptions.DefaultMsgUnicode);

    // Obtenha a próxima mensagem
    message = reader.ReadNextMessage();
}

// Feche os streams
reader.Dispose();
stream.Close();
```

### **Recuperando propriedades da mensagem**

A classe [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) contém as seguintes propriedades para recuperar informações sobre uma mensagem:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Obtém a data da mensagem
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Obtém o endereço do remetente
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Obtém o assunto da mensagem
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Obtém a coleção de endereços que contém os destinatários da mensagem
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Obtém a coleção de endereços que contém os destinatários em CC
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Obtém a coleção de endereços que contém os destinatários em BCC da mensagem

**Exemplo de código**

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader(fileName, new MboxLoadOptions());

foreach (var mboxMessageInfo in reader.EnumerateMessageInfo())
{
    Console.Writeline($"Assunto: {mboxMessageInfo.Subject}");
    Console.Writeline($"Data: {mboxMessageInfo.Date}");
    Console.Writeline($"De: {mboxMessageInfo.From}");
    Console.Writeline($"Para: {mboxMessageInfo.To}");
    Console.Writeline($"CC: {mboxMessageInfo.CC}");
    Console.Writeline($"Bcc: {mboxMessageInfo.Bcc}");
}
```

### **Extraindo mensagens do MBOX por Identificadores**

A classe [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) inclui o método [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/), que permite iterar através de cada mensagem em um arquivo MBOX. Usando este método, é possível extrair mensagens individuais sem a necessidade de percorrer todo o armazenamento repetidamente. Isso melhora o desempenho e reduz o tempo de processamento.

A classe [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) fornece a propriedade [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/) que fornece acesso a identificadores únicos para cada mensagem no arquivo MBOX. Este identificador pode ser armazenado em um banco de dados ou usado como referência para encontrar e extrair mensagens específicas rapidamente quando necessário.

O método [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) na classe [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) permite que os desenvolvedores extraiam mensagens com base em seu EntryId único. Com o método [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/), você pode aproveitar o EntryId armazenado para recuperar a mensagem correspondente e realizar operações adicionais com ela.

O seguinte exemplo de código demonstra como extrair mensagens de um arquivo MBOX usando identificadores:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

### **Configurando as opções de carregamento ao ler mensagens do MBOX**

Os seguintes recursos permitirão que você especifique várias opções relacionadas ao carregamento e processamento de mensagens:

- Propriedade MailStorageConverter.MboxMessageOptions - Obtém ou define opções de carregamento de e-mail ao analisar um armazenamento Mbox.

- Método MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options) - O parâmetro EmlLoadOptions especifica opções ao ler a mensagem do armazenamento Mbox.

**Exemplo de código**

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Leia mensagens preservando anexos tnef.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Converta mensagens de mbox para pst preservando anexos tnef.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

### **Definindo a Codificação de Texto Preferida ao Carregar Arquivos Mbox para Leitura**

A opção de codificação está disponível para a classe MboxrdStorageReader. Isso fornece opções adicionais para carregar o arquivo mbox e garante que mensagens com conteúdo codificado sejam lidas e processadas corretamente. O seguinte trecho de código mostra como você pode definir a codificação de texto que atende às suas necessidades:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

### **Obtendo o Número Total de Mensagens do Arquivo MBox**

A classe [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) fornece a capacidade de ler o número de itens disponíveis em um arquivo MBox. Isso pode ser usado para desenvolver aplicativos que mostram o progresso da atividade ao processar esse tipo de arquivo.

```cs
// O caminho para o diretório de arquivos.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Número total de mensagens no arquivo Mbox: " + reader.GetTotalItemsCount());
}
```

### **Obter o Tamanho Atual da Mensagem**

```cs
using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    MailMessage msg;
    while ((msg = reader.ReadNextMessage()) != null)
    {
        long currentDataSize = reader.CurrentDataSize;

        msg.Dispose();
    }
}
```

### **Convertendo MBOX para PST Preservando ou Removendo uma Assinatura**

Para remover a assinatura de um arquivo durante o processo de conversão, defina a propriedade [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/) como *true*.

O seguinte exemplo de código mostra como utilizar essa propriedade:

```cs
var pstDataStream = new MemoryStream();
var personalStorage = PersonalStorage.Create(pstDataStream, FileFormatVersion.Unicode);
MailStorageConverter.MboxToPst(new MboxrdStorageReader(new FileStream(fileName, FileMode.Open, FileAccess.Read), new MboxLoadOptions()),
personalStorage,
    "Caixa de Entrada",
new MboxToPstConversionOptions() { RemoveSignature = true });
```

## **Escrevendo arquivos MBOX**

A classe [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) fornece a capacidade de escrever novas mensagens no arquivo de armazenamento de e-mail do Thunderbird. Para escrever mensagens:

1. Abra o arquivo de armazenamento do Thunderbird no *FileStream*.
1. Crie uma instância da classe [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) e passe o stream acima para o construtor.
1. Prepare uma nova mensagem usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Chame o método [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) e passe a instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) acima para adicionar a mensagem ao armazenamento do Thunderbird.
1. Feche todos os streams.

O seguinte trecho de código mostra como escrever mensagens no armazenamento de e-mail do Thunderbird.

```cs
// Abra o arquivo de armazenamento com FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Inicialize MboxStorageWriter e passe o stream acima para ele
var writer = new MboxrdStorageWriter(stream, false);
// Prepare uma nova mensagem usando a classe MailMessage
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "adicionado de Aspose.Email");
message.IsDraft = false;
// Adicione esta mensagem ao armazenamento
writer.WriteMessage(message);
// Feche todos os streams relacionados
writer.Dispose();
stream.Close();
```