---
title: "Converter HTML para Outros Formatos"
url: /pt/net/converting-between-formats/convert-html-to-other-formats
weight: 60
type: docs
---

## **Converter HTML para EML**

Aspose.Email para .NET fornece um método para converter arquivos HTML para o formato EML usando os métodos [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) e [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para carregar o arquivo HTML existente e salvá-lo no formato EML, respectivamente:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

No exemplo de código, a classe [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) permite especificar opções adicionais ao carregar um MailMessage do formato HTML. O seguinte exemplo de código demonstra o uso dessa classe. No exemplo, ele especifica uma representação textual do corpo da mensagem:

```cs
// Criar uma instância de HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Definir a propriedade ShouldAddPlainTextView como verdadeira para gerar uma visualização de texto simples juntamente com o HTML
loadOptions.ShouldAddPlainTextView = true;

// Carregar um arquivo HTML
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Acessar a visualização de texto simples da mensagem de email
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Imprimir ou processar a visualização de texto simples
Console.WriteLine("Visualização em Texto Simples:");
Console.WriteLine(plainTextView);
```

## **Converter HTML para EMLX**

Você pode facilmente converter arquivos HTML para EMLX. Todas as propriedades e classes fornecidas pela API para conversão de HTML para EML estão disponíveis para este tipo de conversão também:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
Para configurações adicionais, consulte o parágrafo [Converter HTML para EML](#convert-html-to-eml).

## **Converter HTML para ICS**

Para realizar a tarefa, a biblioteca oferece a classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) para representar e gerenciar eventos de calendário. O seguinte exemplo de código demonstra como criar uma reunião a partir do conteúdo HTML e salvá-la em um arquivo ICS (iCalendar):

```cs
// Conteúdo HTML de exemplo
var htmlContent = File.ReadAllText("content.html");

// Criar e inicializar uma instância da classe Appointment
var appointment = new Appointment(
    "Sala de Reunião 3 na Sede do Escritório", // Localização
    "Reunião Mensal",                          // Resumo
    "Por favor, confirme sua disponibilidade.", // Descrição
    new DateTime(2015, 2, 8, 13, 0, 0),       // Data de início
    new DateTime(2015, 2, 8, 14, 0, 0),       // Data de término
    "from@domain.com",                         // Organizador
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Salvar o evento em um arquivo ICS
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```


## **Gerar MBOX a partir do conteúdo HTML**

Para realizar a conversão de HTML para MBOX, use o método [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class), especificando o caminho do arquivo de conteúdo HTML e uma instância de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analisa o conteúdo HTML e gera um objeto MailMessage correspondente, preservando a estrutura e a formatação do HTML original. Após carregar o conteúdo HTML em um objeto MailMessage, escreva a mensagem em um arquivo MBOX usando a classe [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class):

```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(eml);
    }
}
```

## **Converter HTML para MHTML**

Use o método [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para carregar o arquivo existente, especificando um caminho para ele e uma instância de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analisa o conteúdo HTML e gera um objeto MailMessage correspondente, preservando a estrutura e a formatação do HTML original. Após carregar o conteúdo HTML em um objeto MailMessage, os desenvolvedores podem salvá-lo como um arquivo MHTML usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando o caminho do arquivo de saída desejado e utilizando a opção [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/):

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

A classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) fornece uma variedade de opções para configurar o comportamento e as configurações do arquivo MHTML de saída em vez de SaveOptions.DefaultMhtml. Com suas [propriedades](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#properties), você pode especificar opções adicionais ao salvar o MailMessage no formato MHTML.
As mais populares são:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Permite personalizar como a mensagem de email é salva no formato MHT para melhor atender às suas necessidades.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Obtém ou define um valor indicando se os anexos devem ser salvos.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define se é necessário salvar todos os cabeçalhos no mhtml de saída ou não. O valor padrão é falso.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Define se é necessário manter a data original na mensagem de email ao salvar ou não. O valor padrão é verdadeiro.

O seguinte exemplo de código demonstra como essas propriedades podem ser usadas:

```cs
var mhtSaveOprtions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Converter HTML para MSG**

Após carregar o conteúdo HTML em um objeto MailMessage, salve-o como um arquivo MSG usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando o caminho do arquivo de saída desejado e utilizando a opção [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) neste caso. Esta opção garante que o arquivo de saída seja salvo no formato MSG com codificação Unicode.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Além disso, Aspose.Email para .NET oferece uma gama de recursos e opções avançadas para conversão de HTML para MSG:

## **Converter HTML para OFT**

Após carregar o conteúdo HTML em um objeto MailMessage, salve-o como um arquivo OFT usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando o caminho do arquivo de saída desejado e utilizando a opção [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) nesta situação:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Adicionar mensagem com conteúdo HTML fonte ao PST**

A conversão de HTML para PST envolve a criação de um novo arquivo PST (Tabela de Armazenamento Pessoal) com uma nova pasta, carregando um arquivo HTML e adicionando-o à nova pasta:

1. Crie uma instância de um objeto PersonalStorage que represente um novo arquivo PST usando o método [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
2. Acesse a pasta raiz do arquivo PST e adicione uma subpasta a ela usando o método [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) da classe [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class).
3. Carregue o conteúdo de um arquivo HTML em um objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) usando o método [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) com uma instância de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para especificar que o conteúdo está no formato HTML.
4. Adicione o objeto MapiMessage carregado (representando o conteúdo HTML) à pasta dentro do arquivo PST usando o método [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/).

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{ 
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Adicionar mensagem com conteúdo HTML fonte ao OST**

O seguinte exemplo de código com etapas mostrará como esses componentes funcionam juntos para adicionar conteúdo HTML a um arquivo OST:

1. Carregue um arquivo OST existente com o método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) usado para representar o arquivo de armazenamento que armazenará as mensagens de email. 
2. Carregue o arquivo HTML usando o método [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) que representa uma mensagem de email no formato Microsoft Outlook. 
3. Especifique [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para habilitar opções adicionais ao carregar MailMessage do formato HTML.
4. Recupere a pasta raiz do arquivo OST usando a propriedade [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) do objeto [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
5. Obtenha a pasta Inbox dentro do arquivo OST usando o método [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) na pasta raiz.
6. Adicione o objeto MapiMessage carregado (representando o conteúdo HTML) à pasta Inbox usando o método [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) na pasta.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
``` 

## **Converter HTML para VCF**

O seguinte exemplo de código demonstra como criar um item de contato, populá-lo com conteúdo HTML e salvá-lo em um arquivo VCF:

1. Leia o conteúdo de um arquivo HTML em uma variável string usando o método File.ReadAllText.
2. Crie um novo objeto MapiContact instanciando a classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class).
3. Defina as propriedades do contato: nome de exibição, endereço de email.
4. Defina o conteúdo do corpo do contato como HTML usando [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Salve o contato como um arquivo VCF usando o método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4).

```cs
var content = File.ReadAllText("content.html");
            
// Criar um novo MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "John Doe";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Salvar o contato em um arquivo VCF
contact.Save("contact.vcf", ContactSaveFormat.VCard);
```