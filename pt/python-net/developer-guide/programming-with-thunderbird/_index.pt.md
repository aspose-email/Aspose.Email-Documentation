---
title: "Programação com Thunderbird"
url: /pt/python-net/programming-with-thunderbird/
weight: 80
type: docs
---


## **Lendo Mensagens**
Mozilla Thunderbird é um cliente de email open source e multiplataforma, desenvolvido pela Mozilla Foundation. Ele armazena emails em sua própria estrutura de arquivos, gerenciando índices de mensagens e subpastas através de formatos de arquivo proprietários. Aspose.Email pode trabalhar com estruturas de armazenamento de email do Thunderbird. A classe MboxrdStorageReader permite que os desenvolvedores leiam mensagens do arquivo de armazenamento de email do Mozilla Thunderbird. Este artigo mostra como ler as mensagens do armazenamento de email do Thunderbird:

1. Abra o arquivo de armazenamento do Thunderbird
1. Crie uma instância da classe MboxrdStorageReader e passe o stream acima para o construtor.
1. Chame read_next_message() para obter a primeira mensagem.
1. Use o mesmo read_next_message() em um loop while para ler todas as mensagens.
1. Feche todos os streams.

O seguinte trecho de código mostra como ler todas as mensagens de um armazenamento de email do Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Recuperando propriedades da mensagem**

Para ler e recuperar informações de um arquivo Mbox, Aspose.Email fornece a classe [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) para criar um objeto leitor para o arquivo Mbox e a classe [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) para carregar o arquivo. As seguintes propriedades da classe [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) podem ser usadas para acessar e exibir detalhes específicos da mensagem:

- 'date' - Obtém a data da mensagem.
- 'from_address' - Obtém o endereço de quem enviou.
- 'subject' - Obtém o assunto da mensagem.
- 'to' - Obtém a coleção de endereços que contém os destinatários da mensagem.
- 'cc' - Obtém a coleção de endereços que contém os destinatários em cópia.
- 'bcc' - Obtém a coleção de endereços que contém os destinatários em cópia oculta da mensagem.

O seguinte exemplo de código demonstra o uso dessas propriedades para ler e extrair informações da mensagem de um arquivo Mbox: 

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader(file_name, ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    print(f"Assunto: {mbox_message_info.subject}")
    print(f"Data: {mbox_message_info.date}")
    print(f"De: {mbox_message_info.from_address}")
    print(f"Para: {mbox_message_info.to}")
    print(f"CC: {mbox_message_info.cc}")
    print(f"Bcc: {mbox_message_info.bcc}")
```
### **Extrair Mensagens do MBOX por Identificadores**

Para ler mensagens de um arquivo MBOX, Aspose.Email fornece o método 'create_reader()' da classe [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) para criar um objeto leitor para o arquivo. Ele aceita o nome do arquivo e [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) como argumentos, permitindo ao usuário carregar o arquivo MBOX com opções específicas, se necessário.

Para extrair mensagens, os seguintes métodos e propriedades são usados:

- 'enumerate_message_info()' método da classe [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Itera através de cada mensagem no arquivo MBOX.
- 'extract_message()' método da classe [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Extrai cada mensagem pelo seu ID de Entrada.
- 'entry_id' propriedade da classe [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) - Obtém o identificador da entrada.

Finalmente, a mensagem é convertida em formato EML usando [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

O exemplo de código abaixo demonstra o uso desses recursos para ler e extrair mensagens de um arquivo MBOX:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())

```
### **Configurando as opções de carregamento ao ler mensagens de MBOX**

Com a classe Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class), você pode especificar opções adicionais ao carregar MailMessage do formato Eml. Como exemplo, você pode definir uma opção para preservar anexos TNEF ao carregar um arquivo EML com a propriedade 'preserve_tnef_attachments' da classe [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

Você pode ler a próxima mensagem de email do arquivo mbox usando as opções de carregamento especificadas com o método 'read_next_message' da classe [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) e converter o arquivo para o formato PST com o método 'mbox_to_pst' da classe [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class).

O exemplo de código abaixo demonstra o uso desses métodos e propriedades para trabalhar com arquivos de armazenamento de email, incluindo leitura de mensagens do formato mbox, preservação de anexos TNEF e conversão de mensagens do mbox para formato pst:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Ler mensagens preservando anexos tnef.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Converter mensagens de mbox para pst preservando anexos tnef.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Definindo a Codificação de Texto Preferida ao Carregar Arquivos Mbox para Leitura**

Você pode especificar a codificação de texto a ser usada ao carregar um arquivo MBOX. A propriedade 'preferred_text_encoding' disponível para a classe [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) define uma opção adicional e garante que uma mensagem com o conteúdo codificado será lida e processada corretamente.

O seguinte trecho de código mostra como usar esse recurso em um projeto:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Convertendo MBOX para PST Preservando ou Removendo uma Assinatura**

Para remover a assinatura de um arquivo durante o processo de conversão, defina a propriedade MboxToPstConversionOptions.remove_signature como true.

O seguinte exemplo de código mostra como utilizar essa propriedade:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Escrevendo Mensagens**
A classe MboxrdStorageWriter fornece a capacidade de escrever novas mensagens no arquivo de armazenamento de email do Thunderbird. Para escrever mensagens:

1. Abra o arquivo de armazenamento do Thunderbird em FileStream.
1. Crie uma instância da classe MboxrdStorageWriter e passe o stream acima para o construtor.
1. Prepare uma nova mensagem usando a classe MailMessage.
1. Chame o método write_message() e passe a instância MailMessage acima para adicionar a mensagem ao armazenamento do Thunderbird.
1. Feche todos os streams.

O seguinte trecho de código mostra como escrever mensagens no armazenamento de email do Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Obtendo o Número Total de Mensagens do Arquivo MBox**
A classe MboxrdStorageReader fornece a capacidade de ler o número de itens disponíveis em um arquivo MBox. Isso pode ser utilizado para desenvolver aplicações que mostram o progresso da atividade enquanto processam tal arquivo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Obter o Tamanho da Mensagem Atual**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}