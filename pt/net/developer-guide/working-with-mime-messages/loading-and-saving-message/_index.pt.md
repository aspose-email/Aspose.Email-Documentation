---
title: "Carregando e Salvando Mensagem"
url: /pt/net/loading-and-saving-message/
weight: 40
type: docs
---

# Carregando e Salvando Mensagens

## **Detectando Formatos de Arquivo**

A API Aspose.Email fornece a capacidade de detectar o formato do arquivo da mensagem fornecida. O método [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) da classe [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) pode ser usado para alcançar isso. As seguintes classes e métodos podem ser usados para detectar o formato do arquivo carregado.

- Classe [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/)
- Classe [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/)
- Classe [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/)
- Método [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat)
- Método [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1)

O seguinte trecho de código mostra como detectar formatos de arquivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}

## **Carregando uma Mensagem com Opções de Carregamento**

O seguinte trecho de código mostra como carregar uma mensagem com opções de carregamento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}

### **Preservando o Formato de Mensagem Embutido durante o Carregamento**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Carregando uma Mensagem Preservando ou Removendo uma Assinatura**

A preservação da assinatura é suportada por padrão ao carregar arquivos EML. Para remover a assinatura, você pode definir a propriedade [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) como *true*.

O exemplo de código abaixo mostra como remover uma assinatura ao carregar uma mensagem:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```
### **Verificando a Assinatura de E-mails Seguros**

A classe [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) permite que você verifique a assinatura de objetos MailMessage seguros.

A classe [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) armazena os resultados da verificação.

Os seguintes métodos da classe [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) e um trecho de código permitirão que você processe uma assinatura:

- Método [SecureEmailManager.CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature).
- Método [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1).
- Método [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2).

```cs
var eml = MailMessage.Load(fileName);
var result = new SecureEmailManager().CheckSignature(eml);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MailMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

## **Salvando e Convertendo Mensagens**

Aspose.Email torna fácil converter qualquer tipo de mensagem para outro formato. Para demonstrar esse recurso, o código deste artigo carrega três tipos de mensagens do disco e as salva de volta em outros formatos. A classe base [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) e as classes [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) para configurações adicionais ao salvar [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) podem ser usadas para salvar mensagens em outros formatos. O artigo mostra como usar essas classes para salvar um e-mail de exemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
  
### **Carregar e Salvar uma Mensagem EML**

O seguinte trecho de código mostra como carregar uma mensagem EML e salvá-la no disco no mesmo formato.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

### **Carregar e Salvar uma Mensagem EML Preservando as Fronteiras Originais**

O seguinte trecho de código mostra como carregar EML e salvar como EML preservando as fronteiras originais.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

### **Salvando como EML Preservando Anexos TNEF**

O seguinte trecho de código mostra como salvar como EML preservando anexos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Salvar EML como MSG**

O seguinte trecho de código mostra como carregar uma mensagem EML e convertê-la em MSG usando a opção apropriada da [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

### **Salvando como MSG com Datas Preservadas**

A classe [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) permite que você salve a mensagem original como um arquivo de Mensagem do Outlook (MSG) preservando datas. O seguinte trecho de código mostra como salvar como MSG com Datas Preservadas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Salvando MailMessage como MHTML**

Diferentes opções de MHTML podem ser usadas para obter os resultados desejados. O seguinte trecho de código mostra como carregar uma mensagem EML em [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e convertê-la em MHTML com uma data da mensagem no sistema UTC.

```csharp
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-.NET

// Definir opções para saída MHTML
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // salvar uma data da mensagem como data UTC

// Inicializar e carregar um arquivo EML existente
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Convertendo para MHTML com Configurações Opcionais**

A classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) fornece opções adicionais para salvar mensagens de e-mail no formato MHTML. O enumerador [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) possibilita escrever informações adicionais do e-mail no MHTML de saída. Os seguintes campos adicionais podem ser escritos:

- WriteHeader – escrever o cabeçalho do e-mail no arquivo de saída.
- WriteOutlineAttachments – escrever anexos de contorno no arquivo de saída.
- WriteCompleteEmailAddress – escrever o endereço de e-mail completo no arquivo de saída.
- NoEncodeCharacters – nenhuma codificação de transferência de caracteres deve ser usada.
- HideExtraPrintHeader – ocultar cabeçalho extra de impressão do topo do arquivo de saída.
- WriteCompleteToEmailAddress – escrever o endereço de e-mail completo do destinatário no arquivo de saída.
- WriteCompleteFromEmailAddress – escrever o endereço de e-mail completo do remetente no arquivo de saída.
- WriteCompleteCcEmailAddress – escrever os endereços de e-mail completos de qualquer destinatário com cópia carbono no arquivo de saída.
- WriteCompleteBccEmailAddress – escrever o endereço de e-mail completo de qualquer destinatário com cópia carbono oculta no arquivo de saída.
- RenderCalendarEvent – escrever texto do evento do calendário no arquivo de saída.
- SkipByteOrderMarkInBody – escrever bytes de Byte Order Mark(BOM) no arquivo de saída.
- RenderVCardInfo – escrever texto da VCard AlternativeView no arquivo de saída.
- DisplayAsOutlook – exibir o cabeçalho From.
- RenderTaskFields – escreve campos de Tarefa específicos no arquivo de saída.
- None – Nenhuma configuração especificada.

O seguinte trecho de código mostra como converter arquivos EML para MHTML com configurações opcionais.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Renderizando Eventos de Calendário ao Converter para MHTML**

As [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) renderiza os eventos do Calendário para o MTHML de saída. O seguinte trecho de código mostra como renderizar eventos de calendário ao converter para MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Exportando E-mail para MHT sem Imagens Inline**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Exportando E-mail para MHT com Fuso Horário personalizado**

A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) fornece a propriedade [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) para definir um Fuso Horário personalizado ao exportar para MHT. O seguinte trecho de código mostra como exportar e-mail para MHT com Fuso Horário personalizado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Mudando a Fonte ao Converter para MHT**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

#### **Preservando o corpo RTF ao converter MSG para EML**

A conversão de um arquivo MSG para EML preservando o corpo RTF pode ser feita de duas maneiras:

- usando a propriedade [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) da classe [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/);

- usando a propriedade [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) da classe [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/);

Ambas as propriedades obtêm ou definem um valor indicando se devem manter o corpo rtf em MailMessage.

Os seguintes trechos de código mostram como converter um arquivo MSG para EML e preservar o corpo RTF:

```cs
var loadOptions = new MsgLoadOptions
{
    PreserveRtfContent = true
};

var eml = MailMessage.Load("my.msg", loadOptions);
```

```cs
var conversionOptions = new MailConversionOptions
{
    PreserveRtfContent = true
};

var msg = MapiMessage.Load("my.msg");

var eml = msg.ToMailMessage(conversionOptions);
```

### **Exportando E-mail para EML**

O seguinte trecho de código mostra como exportar e-mails para EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}

### **Salvando Mensagem como arquivo HTML**

A classe [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) permite que você exporte o corpo da mensagem para HTML. O seguinte trecho de código mostra como salvar uma mensagem como HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}

#### **Salvando como HTML sem Embutir Recursos**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Salvando Mensagem como arquivo de Modelo do Outlook (.oft)**

O seguinte trecho de código mostra como salvar uma mensagem como um arquivo de modelo do outlook (.oft).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}