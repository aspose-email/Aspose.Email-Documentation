---
title: "Carregando e Salvando Mensagens"
url: /pt/java/loading-and-saving-message/
weight: 40
type: docs
---

# **Carregando e Salvando Mensagens de Email**

## **Detectar um Formato de Arquivo**

A API Aspose.Email fornece a capacidade de detectar o formato do arquivo da mensagem fornecida. O método [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) da classe [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) pode ser usado para alcançar isso. As seguintes classes e métodos podem ser usados para detectar o formato de arquivo carregado.

- Classe [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/)
- Classe [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/)
- Classe [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/)
- Método [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-)
- Método [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-)

O seguinte trecho de código mostra como detectar formatos de arquivos.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Carregar uma Mensagem de Email**

Para carregar uma mensagem com opções de carregamento específicas, a Aspose.Email fornece a classe [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/) que pode ser usada da seguinte forma:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Preservar o Formato da Mensagem Embutida Durante o Carregamento**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Salvar e Converter Mensagens de Email**

A Aspose.Email facilita a conversão de qualquer tipo de mensagem para outro formato. Para demonstrar esse recurso, o código deste artigo carrega três tipos de mensagens do disco e as salva novamente em outros formatos. A classe base [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) e as classes [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) para configurações adicionais ao salvar [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) podem ser usadas para salvar mensagens em outros formatos. O artigo mostra como usar essas classes para salvar um email de exemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.

### **Carregar e Salvar uma Mensagem de Email**

O seguinte trecho de código mostra como carregar uma mensagem EML e salvá-la no disco no mesmo formato.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Carregar e Salvar uma Mensagem de Email Preservando as Fronteiras Originais**

O seguinte trecho de código mostra como carregar EML e salvar como EML preservando as fronteiras originais.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Salvar como EML Preservando Anexos TNEF**

O seguinte trecho de código mostra como salvar como EML preservando anexos TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Salvar EML como MSG**

O seguinte trecho de código mostra como carregar uma mensagem EML e convertê-la para MSG usando a opção apropriada da [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Salvar EML como MSG com Datas Preservadas**

A classe [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) permite salvar a mensagem fonte como um arquivo de Mensagem do Outlook (MSG) preservando datas. O seguinte trecho de código mostra como salvar como MSG com datas preservadas.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Salvar EML como MHTML**

Diferentes opções de MHTML podem ser usadas para obter os resultados desejados. O seguinte trecho de código mostra como carregar uma mensagem EML em [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e convertê-la para MHTML com uma data da mensagem no sistema UTC.

~~~Java
// Definir opções para saída MHTML
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// salvar a data de uma mensagem como data UTC
saveOptions.setPreserveOriginalDate(false);

// Inicializar e carregar um arquivo EML existente
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~
#### **Formatar Cabeçalhos MHT Globalmente ao Salvar de EML**

Com Aspose.Email, você pode usar as opções de formatação global para o cabeçalho Mht. As opções globais definem a formatação comum de um cabeçalho Mht para todas as instâncias de [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/). Este recurso é projetado para evitar a configuração de formatação para cada instância de [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Use os seguintes métodos da classe [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) e o exemplo de código abaixo para definir a formatação de um cabeçalho Mht:

- [setPageHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - PageHeaderFormat para instâncias de HeadersFormattingOptions se DefaultPageHeaderFormat não for definido.
- [setHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - HeaderFormat para instâncias de HeadersFormattingOptions se DefaultHeaderFormat não for definido.
- [setBeforeHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - BeforeHeadersFormat para instâncias de HeadersFormattingOptions se BeforeHeadersFormat não for definido.
- [setAfterHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - AfterHeadersFormat para instâncias de HeadersFormattingOptions se AfterHeadersFormat não for definido.

```java
// saveOptions1 e saveOptions2 têm a mesma formatação de cabeçalho mht
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Converter EML para MHTML com Configurações Opcionais**

A classe [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) fornece opções adicionais para salvar mensagens de email em formato MHTML. O enumerador [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) possibilita escrever informações adicionais de email no MHTML de saída. Os seguintes campos adicionais podem ser escritos:

- WriteHeader - escreve o cabeçalho do email no arquivo de saída.
- WriteOutlineAttachments - escreve anexos de esboço no arquivo de saída.
- WriteCompleteEmailAddress - escreve o endereço de email completo no arquivo de saída.
- NoEncodeCharacters - nenhuma codificação de transferência de caracteres deve ser usada.
- HideExtraPrintHeader - oculta o cabeçalho de impressão extra do topo do arquivo de saída.
- WriteCompleteToEmailAddress - escreve o endereço de email completo do destinatário no arquivo de saída.
- WriteCompleteFromEmailAddress - escreve o endereço de email completo do remetente no arquivo de saída.
- WriteCompleteCcEmailAddress - escreve os endereços de email completos de qualquer destinatário em cópia no arquivo de saída.
- WriteCompleteBccEmailAddress - escreve o endereço de email completo de qualquer destinatário em cópia oculta no arquivo de saída.
- RenderCalendarEvent - escreve texto do evento de calendário no arquivo de saída.
- SkipByteOrderMarkInBody - escreve os bytes do Byte Order Mark(BOM) no arquivo de saída.
- RenderVCardInfo - escreve texto do VCard AlternativeView no arquivo de saída.
- DisplayAsOutlook - exibe o cabeçalho From.
- RenderTaskFields - escreve campos de Tarefa específicos no arquivo de saída.
- None - Nenhuma configuração especificada.

O seguinte trecho de código mostra como converter arquivos EML para MHTML com configurações opcionais.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Renderizar Eventos de Calendário ao Converter para MHTML**

O [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) renderiza os eventos do Calendário no MTHML de saída. O seguinte trecho de código mostra como renderizar eventos de calendário ao converter para MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Exportar Email para MHT sem Imagens Inline**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Exportar Email para MHT com Fuso Horário Personalizado**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) fornece a propriedade [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) para definir um fuso horário personalizado ao exportar para MHT. O seguinte trecho de código mostra como exportar email para MHT com um fuso horário personalizado.

~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Definir o deslocamento do fuso horário em milissegundos
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~

### **Exportando Email para EML**

O seguinte trecho de código mostra como exportar emails para EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}

### **Salvar Email como HTML**

A classe [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) permite exportar o corpo da mensagem para HTML. O seguinte trecho de código mostra como salvar uma mensagem como HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Salvar Mensagem de Email como HTML com Caminho Relativo para Recursos**

Ao exportar mensagens de email para o formato HTML, é possível escolher salvar recursos de email com caminhos relativos. Este recurso proporciona mais flexibilidade em como os recursos são vinculados no arquivo HTML de saída, tornando mais fácil compartilhar e exibir emails salvos em diferentes sistemas. A propriedade [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) fornece a capacidade de salvar recursos com caminhos relativos. O valor padrão da propriedade é falso (os recursos são salvos com caminhos absolutos). Quando definido como verdadeiro, os recursos são salvos com caminhos relativos. Arquivos HTML com caminhos relativos são mais portáteis e podem ser visualizados corretamente, independentemente da estrutura de arquivos do ambiente de hospedagem. Você pode escolher entre caminhos absolutos e relativos, dependendo dos requisitos. Você pode definir caminhos personalizados para recursos usando o evento [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/).

**Salvar com Caminho Relativo Padrão para Recursos**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
Neste caso, os recursos serão salvos na pasta [nome do arquivo html].files, no mesmo caminho que o arquivo .html e o HTML fará referência aos recursos via caminhos relativos.

**Salvar com Caminho Absoluto para Recursos**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
Como no primeiro caso, os recursos serão salvos na pasta [nome do arquivo html].files por padrão, mas o HTML fará referência aos recursos usando caminhos absolutos.

**Caminho Relativo Personalizado usando o Evento ResourceHtmlRenderingHandler**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

htmlSaveOptions.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {
    @Override
    public void invoke(Object sender, ResourceHtmlRenderingEventArgs args) {
        if (sender instanceof AttachmentBase) {
            AttachmentBase attachment = (AttachmentBase) sender;
            // Como UseRelativePathToResources = true, você deve atribuir um caminho relativo à propriedade PathToResourceFile.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
Ao usar o evento [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) você pode definir caminhos relativos ou absolutos personalizados para recursos. Ao personalizar caminhos com o evento [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) e, uma vez que [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) está definido como verdadeiro, você deve atribuir um caminho relativo à propriedade [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) para garantir a referência correta.

#### **Preservar Ícones Personalizados em uma Mensagem ao Converter para HTML**

Às vezes, a mensagem contém anexos em linha, que são exibidos como imagens de ícones no corpo da mensagem. Esse tipo de mensagem pode criar problemas ao convertê-las para HTML, uma vez que os ícones das imagens são perdidos. Isso ocorre porque os ícones dos anexos não estão mantidos diretamente na mensagem.

O usuário da Aspose.Email pode personalizar os ícones para anexos ao converter a mensagem para HTML. Para isso, o evento [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) é utilizado para personalizar a renderização de arquivos de recurso (como anexos) ao salvar uma mensagem de email como um arquivo HTML. No exemplo de código abaixo, o manipulador de eventos é usado para definir dinamicamente o caminho para os arquivos de recurso (ícones) com base no tipo de conteúdo do anexo. Isso permite a renderização personalizada de recursos na saída HTML com base em seu tipo de arquivo.

```java

 HtmlSaveOptions options = new HtmlSaveOptions();

options.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {

   @Override

   public void invoke(Object sender, ResourceHtmlRenderingEventArgs e) {

        AttachmentBase attachment = (AttachmentBase) sender;

        e.setCaption(attachment.getContentType().getName());

       if (attachment.getContentType().getName().endsWith(".pdf")) {

            e.setPathToResourceFile("pdf_icon.png");

       } else if (attachment.getContentType().getName().endsWith(".docx")) {

            e.setPathToResourceFile("word_icon.jpg");

       } else if (attachment.getContentType().getName().endsWith(".jpg")) {

            e.setPathToResourceFile("jpeg_icon.png");

       } else {

            e.setPathToResourceFile("not_found_icon.png");

       }

   }

});

options.setResourceRenderingMode(ResourceRenderingMode.SubstituteFromFile);

String fileName = "message.msg";

MailMessage mailMessage = MailMessage.load(fileName);

mailMessage.save("fileName.html", options);

```

#### **Definir Hora e Fuso Horário ao Salvar EML como HTML**

Os usuários da Aspose.Email podem definir os formatos de exibição de hora e fuso horário em [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). A classe [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) permite especificar opções de formatação de cabeçalhos ao salvar MailMessage em formato Mhtml ou Html. Os seguintes métodos da classe [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) especificam os campos a serem exibidos no arquivo de saída:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Indica que o texto do evento de calendário deve ser escrito no mhtml de saída.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Indica que o texto do VCard AlternativeView deve ser escrito no html de saída.

O seguinte exemplo de código mostra como definir a hora e o fuso horário ao salvar EML como HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Salvar como HTML sem Embutir Recursos**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Salvar uma Mensagem como um arquivo de Modelo do Outlook (.oft)**

O seguinte trecho de código mostra como salvar uma mensagem como um arquivo de modelo do outlook (.oft).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}