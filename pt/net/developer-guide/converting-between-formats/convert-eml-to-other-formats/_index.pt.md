---
title: "Converter EML para HTML"
url: /pt/net/converting-between-formats/
weight: 60
type: docs
---

## **Converter EML para HTML**

Para integrar o conteúdo de e-mail em aplicações web, a conversão de EML para HTML é a escolha certa, facilitando uma apresentação de e-mail visualmente atraente.

Para converter EML para HTML, você precisará das seguintes classes:

- A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) é usada para criar um objeto representando uma mensagem de e-mail. Ela permite acessar propriedades da mensagem, como assunto, corpo, remetente e endereços dos destinatários, etc. Com seus métodos, você pode criar, carregar e analisar, modificar, salvar e-mails ou realizar outras manipulações com eles.
- A classe [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) fornece opções para salvar mensagens de e-mail em vários formatos. Ela permite que os usuários personalizem a forma como as mensagens de e-mail são salvas em diferentes formatos. Com esta classe, os usuários podem especificar opções para salvar anexos, cabeçalhos, metadados e propriedades de mensagens de e-mail, definir opções de codificação ou escolher se devem salvar mensagens com criptografia ou não.

No exemplo de código abaixo, essas classes trabalham juntas para carregar um arquivo EML existente e especificar o formato da mensagem como EML. Subsequentemente, elas salvam a mensagem de e-mail carregada como um arquivo HTML usando as opções de salvamento HTML padrão especificadas:

1. Use o método [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) para carregar o arquivo existente em um objeto MailMessage especificando o formato da mensagem.
2. Salve o objeto MailMessage carregado como um arquivo HTML usando o método [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3). Use [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) para especificar as opções de salvamento para o formato HTML.

```cs
// Inicializar e carregar um arquivo EML existente especificando o MessageFormat
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Salvar Recursos EML em um Arquivo Separado**

Aspose.Email fornece a enumeração [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) permitindo que os desenvolvedores manipulem recursos em um arquivo HTML. No exemplo de código abaixo, essa enumeração é usada para salvar recursos em um arquivo e inserir na HTML a tag 'src' com o caminho para este arquivo:

1. Carregue a mensagem de e-mail do arquivo de origem usando o método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Crie uma instância de [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) com opções de renderização e recursos especificados.
3. Salve a mensagem de e-mail carregada como um arquivo HTML no local de destino usando o método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) com o parâmetro HtmlSaveOptions.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Incorporar Recursos em um Arquivo HTML**

Em alguns casos, é necessário incorporar recursos, como imagens, diretamente no arquivo HTML para distribuição e apresentação sem problemas. Com Aspose.Email para .NET, você pode facilmente realizar isso usando a enumeração [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration):

1. Carregue a mensagem de e-mail do arquivo de origem usando o método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Crie um novo objeto [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) e defina a propriedade ResourceRenderingMode para EmbedIntoHtml.
3. Salve a mensagem de e-mail carregada como um arquivo HTML usando o método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3), especificando o caminho do arquivo de destino e passando o objeto HtmlSaveOptions como parâmetro para incorporar recursos no arquivo HTML.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Converter EML para ICS**

O seguinte exemplo de código demonstra como extrair dados de eventos de calendário de um arquivo EML e salvá-los em um arquivo ICS separado para uso ou manipulação posterior.

```cs
// Carregar o arquivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar a visualização alternativa com MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Se uma visualização ICS for encontrada, salve-a em um arquivo
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```
### **Personalização**

Aspose.Email para .NET fornece ferramentas para personalizar o conteúdo ICS (iCalendar) extraído de arquivos EML (Email Eletrônico).

**Personalizar os detalhes do evento**

O seguinte exemplo de código demonstra como definir vários detalhes da nomeação, como o resumo, localização e descrição. O código utiliza a classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) que representa compromissos ou eventos de calendário em formato ICS (iCalendar). A classe fornece propriedades e métodos para criar, modificar e gerenciar eventos de calendário programaticamente.

```cs
// Carregar o arquivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar a visualização alternativa com MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Se uma visualização ICS for encontrada, carregue-a para um objeto da classe Appointment
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Personalize os detalhes do evento
appointment.Summary = "Resumo Personalizado do Evento";
appointment.Location = "Localização Personalizada";
appointment.Description = "Descrição Personalizada do Evento";

// Adicione ou modifique os participantes conforme necessário
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Salve o conteúdo ICS personalizado em um arquivo
appointment.Save("customized_appointment.ics");
```
**Criar um padrão de recorrência**

O seguinte exemplo de código demonstra como criar um padrão de recorrência semanal para um compromisso, onde o compromisso ocorre a cada 5 semanas aos sábados. O código utiliza a propriedade [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) da classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) que obtém ou define o padrão de recorrência.

```cs
var pattern = new WeeklyRecurrencePattern(5, 7);
pattern.EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Adicionar EML ao MBOX**

MBOX é um formato comumente usado para armazenar várias mensagens de e-mail em um único arquivo, tornando-o adequado para arquivamento e migração de e-mails. Use a classe [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) para escrever mensagens de e-mail em um arquivo MBOX. O seguinte exemplo de código demonstra como realizar essa tarefa:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
} 
```

## **Converter EML para MHTML**

Com o Aspose.Email para .NET, você pode facilmente converter arquivos EML para o formato MHTML para vários propósitos, como arquivamento, compatibilidade, visualização offline, etc. Carregue a mensagem de e-mail usando o [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), então use a classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) como um parâmetro para o método [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para especificar o formato do arquivo de saída ao salvar a mensagem como um arquivo separado:

```cs
// Inicializar e carregar um arquivo EML existente especificando o MessageFormat
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions();
message.Save("output.mhtml", mhtSaveOptions);
```

A classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) fornece várias opções para personalizar os arquivos MHTML de saída para atender às suas necessidades específicas:

- Preservar o formato de data original. Você pode optar por preservar a formatação original das mensagens de e-mail durante o processo de conversão:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Definir a codificação de saída. Você pode especificar a codificação a ser usada ao escrever os arquivos MHTML de saída:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8; 
  ```

- Incluir anexos. Isso pode ser útil se você deseja preservar anexos ao converter e-mails para o formato MHTML:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Converter EML para MSG**

Seja para migrar dados de e-mail, arquivar mensagens ou integrar-se ao Microsoft Outlook, o Aspose.Email fornece soluções para atingir suas metas. Os arquivos MSG são amplamente utilizados pelo Microsoft Outlook. Para conversão de EML para MSG, use o método [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) para carregar o arquivo EML existente especificando como ele será carregado com [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

O seguinte exemplo de código demonstra como converter arquivos EML para formato MSG:

```cs
// Carregar mensagem de e-mail
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Salvar como MSG
var msgSaveOptions = new MsgSaveOptions();
message.Save("output.msg", msgSaveOptions);
} 
```

## **Converter EML para OFT**

Para converter arquivos EML para o formato de Modelo do Outlook (OFT), carregue a mensagem de e-mail existente usando o método [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) e salve-a com [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) especificando as opções padrão para salvar uma mensagem no formato OFT:

```cs
// Carregar o arquivo EML a ser convertido
var message = MailMessage.Load("My File.eml"); 
// salvar EML como um OFT 
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Adicionar EML ao PST**

Para converter arquivos EML para o formato de Tabela de Armazenamento Pessoal (PST), carregue a mensagem usando o método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3), crie o arquivo de saída com [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) e adicione o e-mail à pasta de Caixa de Entrada criada no arquivo de armazenamento usando o método [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/): 

```cs
using (var msg = MapiMessage.Load("sourceFile.eml", new EmlLoadOptions()))
{
    using (var personalStorage = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
    {
        var inbox = personalStorage.RootFolder.AddSubFolder("Inbox");
        inbox.AddMessage(msg);
    }
}
```

## **Adicionar EML ao OST**

Os desenvolvedores podem facilmente converter arquivos EML para o formato de Tabela de Armazenamento Offline do Outlook (OST), permitindo integração com o Microsoft Outlook. O seguinte exemplo de código demonstra como adicionar uma mensagem EML a um arquivo OST:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Carregar o arquivo EML
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Adicionar a mensagem EML ao arquivo OST
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```
O parâmetro [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) especifica opções adicionais para carregar arquivos EML, como preservar formatos de mensagens incorporadas, remover assinaturas e muito mais. 

## **Converter EML para VCF**

Aspose.Email para .NET oferece funcionalidade para converter arquivos EML para o formato vCard (VCF), permitindo que os desenvolvedores extraiam informações de contato de mensagens de e-mail. Para esse propósito, a biblioteca oferece o método [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) permitindo que os desenvolvedores acessem visualizações alternadas dentro das mensagens de e-mail e extraiam o conteúdo VCF incorporado dentro dos arquivos EML para uso posterior:

```cs
// Carregar o arquivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar a visualização alternativa com MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// Se uma visualização VCF for encontrada, salve-a em um arquivo
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```