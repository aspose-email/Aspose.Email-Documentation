---
title: "Загрузка и Сохранение Сообщений"
url: /ru/net/loading-and-saving-message/
weight: 40
type: docs
---

# Загрузка и Сохранение Сообщений

## **Определение Форматов Файлов**

API Aspose.Email предоставляет возможность определять формат файла данного сообщения. Метод [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) класса [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) можно использовать для этой цели. Для определения загруженного формата файла можно использовать следующие классы и методы.

- [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/) Класс
- [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/) Класс
- [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) Класс
- [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat) Метод
- [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1) Метод

Следующий фрагмент кода показывает, как определить форматы файлов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}

## **Загрузка Сообщения с Опциями Загрузки**

Следующий фрагмент кода показывает, как загрузить сообщение с опциями загрузки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}

### **Сохранение Встраиваемого Формата Сообщения во Время Загрузки**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Загрузка Сообщения с Сохранением или Удалением Подписи**

Поддерживается сохранение подписи по умолчанию при загрузке файлов EML. Чтобы удалить подпись, вы можете установить свойство [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) в *true*.

Ниже приведен пример кода, который показывает, как удалить подпись при загрузке сообщения:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```
### **Проверка Подписи Безопасных Электронных Писем**

Класс [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) позволяет проверять подпись объектов MailMessage с безопасной электронной почтой.

Класс [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) хранит результаты проверки.

Следующие методы класса [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) и фрагмент кода позволят вам обработать подпись:

- [SecureEmailManager.CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) метод.
- [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) метод.
- [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2) метод.

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


## **Сохранение и Конвертирование Сообщений**

Aspose.Email облегчает конвертацию любого типа сообщения в другой формат. Для демонстрации этой функции код в этой статье загружает три типа сообщений с диска и сохраняет их обратно в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) могут быть использованы для сохранения сообщений в другие форматы. В статье показано, как использовать эти классы для сохранения примера email в:

- Формат EML.
- Outlook MSG.
- Формат MHTML.
- Формат HTML.
  
### **Загрузка и Сохранение сообщения EML**

Следующий фрагмент кода показывает, как загрузить сообщение EML и сохранить его на диск в том же формате.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

### **Загрузка и Сохранение сообщения EML с Сохранением Оригинальных Границ**

Следующий фрагмент кода показывает, как загрузить EML и сохранить как EML, сохраняя оригинальные границы.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

### **Сохранение как EML с Сохранением TNEF Вложений**

Следующий фрагмент кода показывает, как сохранить как EML с сохранением TNEF вложений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Сохранение EML как MSG**

Следующий фрагмент кода показывает, как загрузить сообщение EML и конвертировать его в MSG, используя соответствующую опцию из [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

### **Сохранение как MSG с Сохранением Дат**

Класс [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) позволяет сохранять исходное сообщение как файл Outlook Message (MSG) с сохранением дат. Следующий фрагмент кода показывает, как сохранить как MSG с сохранением дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Сохранение MailMessage как MHTML**

Разные опции MHTML могут быть использованы для получения желаемых результатов. Следующий фрагмент кода показывает, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и конвертировать его в MHTML с датой сообщения в системе UTC.

```csharp
// Для полного примера и файлов данных, пожалуйста, зайдите на https://github.com/aspose-email/Aspose.Email-for-.NET

// Установка опций для вывода MHTML
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // сохранить дату сообщения как дату UTC

// Инициализация и загрузка существующего файла EML
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Конвертация в MHTML с Дополнительными Настройками**

Класс [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) предоставляет дополнительные опции для сохранения электронных сообщений в формате MHTML. Перечислитель [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию об электронной почте в выходной MHTML. Следующие дополнительные поля могут быть записаны:

- WriteHeader – записывать заголовок электронной почты в выходной файл.
- WriteOutlineAttachments – записывать вложения в выходной файл.
- WriteCompleteEmailAddress – записывать полный адрес электронной почты в выходной файл.
- NoEncodeCharacters – никакая кодировка символов не должна использоваться.
- HideExtraPrintHeader – скрыть дополнительный заголовок печати в верхней части выходного файла.
- WriteCompleteToEmailAddress – записывать полный адрес электронной почты получателя в выходной файл.
- WriteCompleteFromEmailAddress – записывать полный адрес электронной почты отправителя в выходной файл.
- WriteCompleteCcEmailAddress – записывать полные адреса электронной почты любых получателей с копией в выходной файл.
- WriteCompleteBccEmailAddress – записывать полный адрес электронной почты любых получателей с сокрытой копией в выходной файл.
- RenderCalendarEvent – записывать текст из события календаря в выходной файл.
- SkipByteOrderMarkInBody – записывать байты отметки порядка байтов (BOM) в выходной файл.
- RenderVCardInfo – записывать текст из альтернативного представления VCard в выходной файл.
- DisplayAsOutlook – отображать заголовок From.
- RenderTaskFields – записывает конкретные поля задачи в выходной файл.
- None – Нет заданных настроек.

Следующий фрагмент кода показывает, как конвертировать файлы EML в MHTML с дополнительными настройками.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Отображение Календарных Событий при Конвертации в MHTML**

Опция [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) отображает события календаря в выходном MTHML. Следующий фрагмент кода показывает, как отобразить календарные события при конвертации в MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Экспорт Электронной Почты в MHT без Встраиваемых Изображений**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Экспорт Электронной Почты в MHT с Настроенной Часовой Зоной**

Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) предоставляет свойство [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) для установки настраиваемого времени при экспорте в MHT. Следующий фрагмент кода показывает, как экспортировать электронное письмо в MHT с настраиваемой часовой зоной.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Изменение Шрифта при Конвертации в MHT**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

#### **Сохранение RTF тела при конвертации MSG в EML** 

Конвертация MSG файла в EML с сохранением RTF тела может быть выполнена двумя способами:

- используя свойство [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) класса [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/);

- используя свойство [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) класса [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/);

Оба свойства получают или устанавливают значение, указывающее, сохранять ли rtf тело в MailMessage.

Следующие фрагменты кода показывают, как конвертировать MSG файл в EML и сохранить RTF тело:

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

### **Экспорт Электронной Почты в EML**

Следующий фрагмент кода показывает, как экспортировать электронные письма в EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}

### **Сохранение Сообщения как HTML**

Класс [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) позволяет экспортировать текст сообщения в HTML. Следующий фрагмент кода показывает, как сохранить сообщение как HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}


#### **Сохранение как HTML без Встраивания Ресурсов**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Сохранение Сообщения как Шаблон Outlook (.oft)**

Следующий фрагмент кода показывает, как сохранить сообщение как шаблон Outlook (.oft).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}