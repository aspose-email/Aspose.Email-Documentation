---
title: "Загрузка и сохранение сообщения"
url: /ru/net/loading-and-saving-message/
weight: 40
type: docs
---

# Загрузка и сохранение сообщений

## **Определение форматов файлов**

Aspose.Email API предоставляет возможность определять формат предоставленного файла сообщения. [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) метод [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) класс можно использовать для достижения этой цели. Для определения формата загруженного файла можно использовать следующие классы и методы.

- [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) Class
- [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat) Method
- [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1) Method

В следующем фрагменте кода показано, как определять форматы файлов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}

## **Загрузка сообщения с опциями загрузки**

В следующем фрагменте кода показано, как загрузить сообщение с опциями загрузки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}

### **Сохранение формата встроенного сообщения во время загрузки**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Загрузка сообщения Сохранение или удаление подписи**

Сохранение подписи поддерживается по умолчанию при загрузке файлов EML. Чтобы удалить подпись, вы можете установить [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) недвижимость для *true*.

В приведенном ниже примере кода показано, как удалить подпись при загрузке сообщения:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```
### **Проверка подписи защищенных электронных писем**

The [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) класс позволяет проверять подпись защищенных объектов MailMessage.

The [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) класс хранит результаты проверки.

Следующие методы [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) класс и фрагмент кода позволят вам обработать подпись:

- [Защищенный менеджер электронной почты. Проверьте подпись (сообщение с почтовым сообщением)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) method.
- [Secure Email Manager. Проверьте подпись (сообщение электронной почты, сертификат X509 Certificate 2 для расшифровки)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) method.
- [Secure Email Manager. Проверьте подпись (сообщение электронной почты, сертификат X509 Certificate2 для расшифровки, хранилище X509 Store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2) method.

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


## **Сохранение и преобразование сообщений**

Aspose.Email позволяет легко конвертировать сообщения любого типа в другой формат. Чтобы продемонстрировать эту функцию, приведенный в этой статье код загружает три типа сообщений с диска и сохраняет их в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) может использоваться для сохранения сообщений в других форматах. В статье показано, как использовать эти классы для сохранения образца электронного письма в виде:

- Формат EML.
- MSG для Outlook.
- Формат MHTML.
- Формат HTML.
 
### **Загрузка и сохранение сообщения EML**

В следующем фрагменте кода показано, как загрузить сообщение EML и сохранить его на диск в том же формате.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

### **Загрузите и сохраните сообщение EML с сохранением исходных границ**

В следующем фрагменте кода показано, как загрузить EML и сохранить его как EML с сохранением исходных границ.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

### **Сохранение в формате EML Сохранение вложений TNEF**

В следующем фрагменте кода показано, как сохранить вложения в формате EML с сохранением вложений TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Сохранить EML как MSG**

В следующем фрагменте кода показано, как загрузить сообщение EML и преобразовать его в MSG, используя соответствующую опцию из [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

### **Сохранение в формате MSG с сохраненными датами**

The [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) класс позволяет сохранить исходное сообщение в виде файла сообщений Outlook (MSG) с сохранением дат. В следующем фрагменте кода показано, как сохранить файл в формате MSG с сохраненными датами.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Сохранение почтового сообщения в формате MHTML**

Для получения желаемых результатов можно использовать различные варианты MHTML. В следующем фрагменте кода показано, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и преобразуйте его в MHTML с датой сообщения в системе UTC.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // save a message date as UTC date

// Initialize and load an existing EML file
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Преобразование в MHTML с дополнительными настройками**

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) класс предоставляет дополнительные возможности для сохранения сообщений электронной почты в формате MHTML. Счетчик [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию по электронной почте в выходной файл MHTML. Можно записать следующие дополнительные поля:

- WriteHeader — запишите заголовок письма в выходной файл.
- WriteOutlineAttachments — запись контурных вложений в выходной файл.
- WriteCompleteEmailAddress — запишите полный адрес электронной почты в выходной файл.
- NoEncodeCharacters — не следует использовать передаточную кодировку символов.
- HideExtraPrintHeader — скрыть дополнительный заголовок печати в верхней части выходного файла.
- WriteCompleteToEmailAddress — запишите полный адрес электронной почты получателя в выходной файл.
- WriteCompleteFromEmailAddress — запишите полный адрес электронной почты отправителя в выходной файл.
- WriteCompleteCceMailAddress — запишите в выходной файл полные адреса электронной почты всех получателей, скопированных на бумаге.
- WriteCompleteBCCEmailAddress — запишите в выходной файл полный адрес электронной почты всех получателей, скопированных вслепую.
- renderCalendarEvent — запись текста из календарного события в выходной файл.
- SkipByteOrderMarkInBody — запись байтов метки порядка байтов (BOM) в выходной файл.
- RenderVCardInfo — запись текста из vCard AlternativeView в выходной файл.
- DisplayAsOutlook — отображение заголовка «Из».
- RenderTaskFields — записывает определенные поля Задачи в выходной файл.
- Нет — настройка не указана.

В следующем фрагменте кода показано, как конвертировать файлы EML в MHTML с дополнительными настройками.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Отображение событий календаря при конвертации в MHTML**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) отображает события календаря в выходной файл MTHML. В следующем фрагменте кода показано, как отображать события календаря при преобразовании в формат MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Экспорт электронной почты в MHT без встроенных изображений**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Экспорт электронной почты в MHT с настраиваемым часовым поясом**

[MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс предоставляет [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) свойство для установки настраиваемого часового пояса при экспорте в MHT. В следующем фрагменте кода показано, как экспортировать электронную почту в MHT с помощью настраиваемого TimeZone.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Изменение шрифта при преобразовании в MHT**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

#### **Сохранение тела RTF при преобразовании MSG в EML**

Преобразование файла MSG в тело RTF с сохранением EML может быть выполнено двумя способами:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) собственность [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/) class;

- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) собственность [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/) class;

Оба свойства получают или задают значение, указывающее, следует ли сохранить тело rtf в MailMessage.

Следующие фрагменты кода показывают, как преобразовать файл MSG в EML и сохранить тело RTF:

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

### **Экспорт электронной почты в EML**

В следующем фрагменте кода показано, как экспортировать электронные письма в EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}

### **Сохранение сообщения в формате HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) класс позволяет экспортировать тело сообщения в HTML. В следующем фрагменте кода показано, как сохранить сообщение в формате HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}


#### **Сохранение в формате HTML без встраивания ресурсов**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Сохранение сообщения в виде файла шаблона Outlook (.oft)**

В следующем фрагменте кода показано, как сохранить сообщение в виде файла шаблона Outlook (.oft).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}
