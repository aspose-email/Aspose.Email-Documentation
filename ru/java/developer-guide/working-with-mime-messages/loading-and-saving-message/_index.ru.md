---
title: "Загрузка и сохранение сообщений"
url: /ru/java/loading-and-saving-message/
weight: 40
type: docs
---

# **Загрузка и сохранение email сообщений**

## **Определение формата файла**

Aspose.Email API предоставляет возможность определить формат файла предоставленного сообщения. Метод [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) класса [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) можно использовать для достижения этой цели. Следующие классы и методы могут быть использованы для определения загруженного формата файла.

- [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/) Класс
- [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/) Класс
- [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/) Класс
- [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) Метод
- [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-) Метод

Следующий фрагмент кода показывает, как определить форматы файлов.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Загрузка email сообщения**

Для загрузки сообщения с определенными параметрами загрузки Aspose.Email предоставляет класс [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/), который можно использовать следующим образом:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Сохранение встроенного формата сообщения при загрузке**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Сохранение и конвертация email сообщений**

Aspose.Email упрощает конвертацию любого типа сообщения в другой формат. Чтобы продемонстрировать эту функцию, код в этой статье загружает три типа сообщений с диска и сохраняет их снова в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) могут быть использованы для сохранения сообщений в другие форматы. В статье показано, как использовать эти классы для сохранения примера email в:

- EML формат.
- Outlook MSG.
- MHTML формат.
- HTML формат.

### **Загрузка и сохранение email сообщения**

Следующий фрагмент кода показывает, как загрузить EML сообщение и сохранить его на диск в том же формате.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Загрузка и сохранение email сообщения с сохранением оригинальных границ**

Следующий фрагмент кода показывает, как загрузить EML и сохранить как EML, сохраняя оригинальные границы.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Сохранение как EML с сохранением вложений TNEF**

Следующий фрагмент кода показывает, как сохранить как EML с сохранением вложений TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Сохранение EML в MSG**

Следующий фрагмент кода показывает, как загрузить EML сообщение и конвертировать его в MSG, используя соответствующий параметр из [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Сохранение EML в MSG с сохранением дат**

Класс [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) позволяет сохранять исходное сообщение как файл Outlook Message (MSG), сохраняя даты. Следующий фрагмент кода показывает, как сохранить как MSG с сохранением дат.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Сохранение EML как MHTML**

Различные параметры MHTML могут быть использованы для достижения желаемых результатов. Следующий фрагмент кода показывает, как загрузить EML сообщение в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и конвертировать его в MHTML с датой сообщения в системе UTC.

~~~Java
// Установить параметры для вывода MHTML
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// сохранить дату сообщения как дату UTC
saveOptions.setPreserveOriginalDate(false);

// Инициализировать и загрузить существующий EML файл
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~

#### **Глобальное форматирование заголовков MHT при сохранении из EML**

С помощью Aspose.Email вы можете использовать глобальные параметры форматирования для заголовка Mht. Глобальные параметры устанавливают общее форматирование заголовка Mht для всех экземпляров [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/). Эта функция предназначена для избежания установки форматирования для каждого экземпляра [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Используйте следующие методы класса [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) и приведенный ниже пример кода, чтобы установить форматирование заголовка Mht:

- [setPageHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - PageHeaderFormat для экземпляров HeadersFormattingOptions, если DefaultPageHeaderFormat не установлен.
- [setHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - HeaderFormat для экземпляров HeadersFormattingOptions, если DefaultHeaderFormat не установлен.
- [setBeforeHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - BeforeHeadersFormat для экземпляров HeadersFormattingOptions, если BeforeHeadersFormat не установлен.
- [setAfterHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - AfterHeadersFormat для экземпляров HeadersFormattingOptions, если AfterHeadersFormat не установлен.

```java
// saveOptions1 и saveOptions2 имеют одинаковое форматирование заголовка mht
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Конвертация EML в MHTML с дополнительными настройками**

Класс [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) предоставляет дополнительные параметры для сохранения email сообщений в формат MHTML. Перечисление [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию о email в выходной MHTML. Следующие дополнительные поля могут быть записаны:

- WriteHeader - записать заголовок email в выходной файл.
- WriteOutlineAttachments - записать вложения в виде схемы в выходной файл.
- WriteCompleteEmailAddress - записать полный адрес email в выходной файл.
- NoEncodeCharacters - не использовать кодирование символов при передаче.
- HideExtraPrintHeader - скрыть дополнительный печатный заголовок в верхней части выходного файла.
- WriteCompleteToEmailAddress - записать полный адрес электронной почты получателя в выходной файл.
- WriteCompleteFromEmailAddress - записать полный адрес электронной почты отправителя в выходной файл.
- WriteCompleteCcEmailAddress - записать полные адреса электронной почты любых получателей с копией в выходной файл.
- WriteCompleteBccEmailAddress - записать полный адрес электронной почты любых получателей с скрытой копией в выходной файл.
- RenderCalendarEvent - записать текст из события календаря в выходной файл.
- SkipByteOrderMarkInBody - записать байты Byte Order Mark(BOM) в выходной файл.
- RenderVCardInfo - записать текст из VCard AlternativeView в выходной файл.
- DisplayAsOutlook - отображать заголовок From.
- RenderTaskFields - записать конкретные поля задач в выходной файл.
- None - Настройка не указана.

Следующий фрагмент кода показывает, как конвертировать EML файлы в MHTML с дополнительными настройками.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Отображение событий календаря при конвертации в MHTML**

[RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) рендерит события календаря в выходной MTHML. Следующий фрагмент кода показывает, как отображать события календаря при конвертации в MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Экспорт email в MHT без встроенных изображений**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Экспорт email в MHT с пользовательским часовым поясом**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) предоставляет свойство [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) для установки пользовательского часового пояса при экспорте в MHT. Следующий фрагмент кода показывает, как экспортировать email в MHT с пользовательским часовым поясом.

~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Установите смещение часового пояса в миллисекундах
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~ 

### **Экспорт email в EML**

Следующий фрагмент кода показывает, как экспортировать email в EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}

### **Сохранение email как HTML**

Класс [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) позволяет экспортировать текст сообщения в HTML. Следующий фрагмент кода показывает, как сохранить сообщение в формате HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Сохранение email сообщения как HTML с относительным путем к ресурсам**

При экспорте email сообщений в формат HTML возможно выбрать сохранение ресурсов email с относительными путями. Эта функция предоставляет большую гибкость в том, как ресурсы связаны в выходном HTML файле, что упрощает обмен и отображение сохраненных email на разных системах. Свойство [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) предоставляет возможность сохранять ресурсы с относительными путями. Значение по умолчанию - false (ресурсы сохраняются с абсолютными путями). Когда установлено в true, ресурсы сохраняются с относительными путями. HTML файлы с относительными путями более универсальны и могут отображаться корректно независимо от структуры файловой системы хостинга. Вы можете выбрать между абсолютными и относительными путями в зависимости от требований. Вы можете определить пользовательские пути для ресурсов, используя событие [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/).

**Сохранение с относительным путем к ресурсам по умолчанию**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
В этом случае ресурсы будут сохранены в папке [имя html файла].files, в том же пути, что и .html файл, и HTML будет ссылаться на ресурсы через относительные пути.

**Сохранение с абсолютным путем к ресурсам**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
Как и в первом случае, ресурсы будут сохранены в папке [имя html файла].files по умолчанию, но HTML будет ссылаться на ресурсы, используя абсолютные пути.

**Пользовательский относительный путь с использованием события ResourceHtmlRenderingHandler**

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
            // Поскольку UseRelativePathToResources = true, вы должны присвоить относительный путь свойству PathToResourceFile.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
Используя событие [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/), вы можете задать пользовательские относительные или абсолютные пути для ресурсов. При настройке путей с помощью обработчика события [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) и поскольку [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) установлен в true, вы должны присвоить относительный путь свойству [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) для корректного обращения.

#### **Сохранение пользовательских значков в сообщении при конвертации в HTML**

Иногда сообщение содержит встроенные вложения, которые отображаются как иконки в теле сообщения. Такие сообщения могут создавать проблемы при конвертации их в HTML, так как иконки теряются. Это происходит потому, что иконки вложений не хранятся непосредственно в сообщении.

Пользователь Aspose.Email может настроить иконки для вложений при конвертации сообщения в HTML. Для этого используется событие [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) для настройки рендеринга файлов ресурсов (таких как вложения) при сохранении email сообщения в виде HTML файла. В приведенном ниже примере кода обработчик события используется для динамической установки пути к файлам ресурсов (иконкам) на основе типа содержимого вложения. Это позволяет настраивать рендеринг ресурсов в HTML-выходе на основе их типа файла.

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

#### **Установите время и часовой пояс при сохранении EML как HTML**

Пользователи Aspose.Email могут задавать форматы отображения времени и часового пояса в [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). Класс [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) позволяет указывать параметры форматирования заголовков при сохранении MailMessage в формат Mhtml или Html. Следующие методы класса [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) указывают поля, которые должны отображаться в выходном файле:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Указывает, что текст из события календаря должен быть записан в выходном mhtml.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Указывает, что текст из VCard AlternativeView должен быть записан в выходном html.

Следующий пример кода показывает, как установить время и часовой пояс при сохранении EML в HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Сохранение как HTML без встраивания ресурсов**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Сохранение сообщения как шаблона Outlook (.oft)**

Следующий фрагмент кода показывает, как сохранить сообщение как шаблон Outlook (.oft) файл.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}