---
title: "Загрузка и сохранение сообщений"
url: /ru/java/loading-and-saving-message/
weight: 40
type: docs
---

# **Загрузка и сохранение сообщений электронной почты**

## **Определите формат файла**

Aspose.Email API предоставляет возможность определять формат предоставленного файла сообщения. [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) метод [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) класс можно использовать для достижения этой цели. Для определения формата загруженного файла можно использовать следующие классы и методы.

- [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/) Class
- [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) Method
- [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-) Method

В следующем фрагменте кода показано, как определять форматы файлов.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Загрузить сообщение электронной почты**

Чтобы загрузить сообщение с определенными параметрами загрузки, Aspose.Email предоставляет [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/) класс, который можно использовать следующим образом:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Сохраняйте формат встроенного сообщения во время загрузки**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Сохраняйте и конвертируйте сообщения электронной почты**

Aspose.Email позволяет легко конвертировать сообщения любого типа в другой формат. Чтобы продемонстрировать эту функцию, приведенный в этой статье код загружает три типа сообщений с диска и сохраняет их в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) может использоваться для сохранения сообщений в других форматах. В статье показано, как использовать эти классы для сохранения образца электронного письма в виде:

- Формат EML.
- MSG для Outlook.
- Формат MHTML.
- Формат HTML.
 
### **Загрузка и сохранение сообщения электронной почты**

В следующем фрагменте кода показано, как загрузить сообщение EML и сохранить его на диск в том же формате.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Загрузите и сохраните сообщение электронной почты с сохранением исходных границ**

В следующем фрагменте кода показано, как загрузить EML и сохранить его как EML с сохранением исходных границ.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Сохранение в формате EML Сохранение вложений TNEF**

В следующем фрагменте кода показано, как сохранить вложения в формате EML с сохранением вложений TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Сохранить EML в MSG**

В следующем фрагменте кода показано, как загрузить сообщение EML и преобразовать его в MSG, используя соответствующую опцию из [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Сохраните EML в MSG с сохраненными датами**

The [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) класс позволяет сохранить исходное сообщение в виде файла сообщений Outlook (MSG) с сохранением дат. В следующем фрагменте кода показано, как сохранить файл в формате MSG с сохраненными датами.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Сохранить EML как MHTML**

Для получения желаемых результатов можно использовать различные варианты MHTML. В следующем фрагменте кода показано, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и преобразуйте его в MHTML с датой сообщения в системе UTC.

~~~Java
// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// save a message date as UTC date
saveOptions.setPreserveOriginalDate(false);

// Initialize and load an existing EML file
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~
#### **Глобальное форматирование заголовков MHT при сохранении из EML**

С помощью Aspose.Email вы можете использовать глобальные параметры форматирования заголовка Mht. Глобальные параметры задают общее форматирование заголовка Mht для всех [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) экземпляры. Эта функция разработана таким образом, чтобы не задавать форматирование для каждого экземпляра [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Используйте следующие методы [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) класс и пример кода ниже для настройки форматирования заголовка Mht:

- [Задать формат заголовка страницы (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - Формат заголовка страницы для экземпляров HeadersFormattingOptions, если формат заголовка страницы по умолчанию не установлен.
- [SetHeaderFormat (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - Формат заголовка для экземпляров HeadersFormattingOptions, если формат заголовка по умолчанию не установлен.
- [Задать перед форматом заголовков (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - Формат BeforeHeaders для экземпляров параметров форматирования заголовков, если параметр BeforeHeadersFormat не установлен.
- [Задать после формата заголовков (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - Формат AfterHeaders для экземпляров параметров форматирования заголовков, если параметр AfterHeadersFormat не установлен.

```java
// saveOptions1 and saveOptions2 have the same mht header formatting
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Конвертируйте EML в MHTML с дополнительными настройками**

The [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) класс предоставляет дополнительные возможности для сохранения сообщений электронной почты в формате MHTML. Счетчик [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию по электронной почте в выходной файл MHTML. Можно записать следующие дополнительные поля:

- WriteHeader — запишите заголовок письма в выходной файл.
- WriteOutlineAttachments — запись контурных вложений в выходной файл.
- WriteCompleteEmailAddress — запишите полный адрес электронной почты в выходной файл.
- NoEncodeCharacters — не следует использовать передаточную кодировку символов.
- HideExtraPrintHeader — скрыть дополнительный заголовок печати в верхней части выходного файла.
- WriteCompleteToEmailAddress — запишите полный адрес электронной почты получателя в выходной файл.
- WriteCompleteFromEmailAddress — запишите полный адрес электронной почты отправителя в выходной файл.
- WriteCompleteCceMailAddress — запишите полные адреса электронной почты всех получателей, скопированных с помощью углеродной копии, в выходной файл.
- WriteCompleteBCCEmailAddress — запишите в выходной файл полный адрес электронной почты всех получателей, скопированных вслепую.
- renderCalendarEvent — запись текста из календарного события в выходной файл.
- SkipByteOrderMarkInBody — запись байтов метки порядка байтов (BOM) в выходной файл.
- RenderVCardInfo — запись текста из vCard AlternativeView в выходной файл.
- DisplayAsOutlook — отображение заголовка From.
- RenderTaskFields — записывает определенные поля Задачи в выходной файл.
- Нет — настройка не указана.

В следующем фрагменте кода показано, как конвертировать файлы EML в MHTML с дополнительными настройками.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Рендеринг событий календаря при конвертации в MHTML**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) отображает события календаря в выходной файл mthml.В следующем фрагменте кода показано, как отображать события календаря при преобразовании в MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Экспорт электронной почты в MHT без встроенных изображений**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Экспорт электронной почты в MHT с настраиваемым часовым поясом**

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс предоставляет [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) свойство для установки настраиваемого часового пояса при экспорте в MHT. В следующем фрагменте кода показано, как экспортировать электронную почту в MHT с помощью настраиваемого TimeZone.

~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Set the timezone offset in milliseconds
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~

### **Экспорт электронной почты в EML**

В следующем фрагменте кода показано, как экспортировать электронные письма в EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}

### **Сохранить электронную почту в формате HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) класс позволяет экспортировать тело сообщения в HTML. В следующем фрагменте кода показано, как сохранить сообщение в формате HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Сохранить сообщение электронной почты в формате HTML с относительным путем к ресурсам**

При экспорте сообщений электронной почты в формат HTML можно сохранить ресурсы электронной почты с относительными путями. Эта функция обеспечивает большую гибкость при связывании ресурсов в выходном HTML-файле, что упрощает обмен сохраненными письмами и их отображение в разных системах. [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) свойство предоставляет возможность экономить ресурсы с помощью относительных путей. Значение свойства по умолчанию равно false (ресурсы сохраняются с абсолютными путями). Если установлено значение true, ресурсы сохраняются по относительным путям. HTML-файлы с относительными путями более портативны, и их можно правильно просматривать независимо от файловой структуры среды хостинга. В зависимости от требований можно выбирать между абсолютными и относительными путями. Вы можете определить собственные пути к ресурсам, используя [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) event.

**Сохранить с относительным путем к ресурсам по умолчанию**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
В этом случае ресурсы будут сохранены в папке [html-имя файла] .files по тому же пути, что и файл HTML, а HTML-код будет ссылаться на ресурсы по относительным путям.

**Экономьте, используя абсолютный путь к ресурсам**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
Как и в первом случае, ресурсы по умолчанию сохраняются в папке [html file name] .files, но HTML-код будет ссылаться на ресурсы с использованием абсолютных путей.

**Настраиваемый относительный путь с использованием события ResourceHTMLRenderingHandler**

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
            // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
Используя [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) событие, вы можете установить собственные относительные или абсолютные пути для ресурсов. При настройке путей с помощью [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) обработчик событий, и так как [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) установлено значение true, вы должны назначить относительный путь к [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) свойство, обеспечивающее правильную ссылку.

#### **Сохранение пользовательских значков в сообщении при преобразовании в HTML**

Иногда сообщение содержит встроенные вложения, которые отображаются в виде значков в теле сообщения. Такие сообщения могут создавать проблемы при преобразовании их в формат HTML, поскольку изображения значков теряются. Это связано с тем, что значки вложения не хранятся непосредственно в сообщении.

Пользователь Aspose.Email может настроить значки для вложений при преобразовании сообщения в HTML. Для этого [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) событие используется для настройки отображения файлов ресурсов (например, вложений) при сохранении сообщения электронной почты в виде HTML-файла. В приведенном ниже примере кода обработчик событий используется для динамической установки пути к файлам ресурсов (значкам) в зависимости от типа содержимого вложения. Это позволяет настраивать отображение ресурсов в выходных данных HTML в зависимости от типа файла.

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

#### **Установите время и часовой пояс при сохранении EML в формате HTML**

Пользователи Aspose.Email могут устанавливать форматы отображения времени и часового пояса в [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) класс позволяет указать параметры форматирования заголовков при сохранении MailMessage в формате Mhtml или Html. Следующие методы [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) класс укажите поля, которые будут отображаться в выходном файле:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Указывает, что текст календарного события должен быть записан в выходной файл mhtml.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Указывает, что текст из vCard AlternativeView должен быть записан в выходной html-файл.

В следующем примере кода показано, как установить время и часовой пояс при сохранении EML в HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Сохранение в формате HTML без встраивания ресурсов**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Сохранение сообщения в виде файла шаблона Outlook (.oft)**

В следующем фрагменте кода показано, как сохранить сообщение в виде файла шаблона Outlook (.oft).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}
