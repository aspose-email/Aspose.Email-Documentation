---
title: "Создание и Сохранение MSG Файлов"
url: /ru/net/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email поддерживает создание файлов сообщений Outlook (MSG). Эта статья объясняет, как:

- Создать сообщения MSG.
- Создать сообщения MSG с вложениями.
- Создать сообщение MSG с телом в формате RTF.
- Сохранить сообщение как черновик.
- Работать с сжатием тела.
  
## **Создание и Сохранение Сообщений Outlook**

Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) имеет метод [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/), который может сохранять файлы Outlook MSG на диск или в поток. Приведенные ниже фрагменты кода создают экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), устанавливают такие свойства, как от кого, кому, тема и текст. Метод [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) принимает имя файла в качестве аргумента. Кроме того, сообщения Outlook могут быть созданы с [сжатыми RTF телами]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) с использованием [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). Чтобы настроить, создайте новое Windows-приложение и добавьте ссылку на библиотеку Aspose.Email в проект.

1. Создайте новый экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и установите свойства From, To, Subject и Body.
2. Вызовите метод [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), который принимает объект типа [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Метод [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) преобразует [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Вызовите метод [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) для сохранения файла MSG.

Напишите следующий код в событии нажатия кнопки управления Windows-приложения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Создание MSG Файлов С Вложениями**

[В примере выше](https://docs.aspose.com/email/ru/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages) мы создали простой MSG файл. Aspose.Email также поддерживает сохранение файлов сообщений с вложениями. Все, что вам нужно сделать, это добавить вложения в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Добавьте вложения, вызвав метод *Add()* на коллекции [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/). Добавьте список на форму, созданную выше, и добавьте две кнопки, по одной для добавления и удаления вложений. Приложение, которое добавляет вложения, работает так:

1. Когда кнопка **Добавить вложение** нажата, отображается **Диалог открытия файла**, чтобы помочь пользователям просмотреть и выбрать вложение.
2. Когда файл выбран, полный путь добавляется в список.
3. Когда файл MSG создан, пути вложений берутся из списка и добавляются в коллекцию [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/).

Напишите следующий код в событии нажатия кнопки **Добавить вложение**.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

Когда кнопка **Удалить вложение** нажата, удалите выбранные элементы из списка. Напишите следующий код в событии нажатия кнопки Удалить вложение.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Добавьте код для добавления вложений в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Окончательный код для функции Write Msg записан ниже.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Создание MSG Файлов С Телом В Формате RTF**

Вы также можете создавать файлы сообщений Outlook (MSG) с телами в формате Rich Text (RTF) с Aspose.Email. Тело в формате RTF поддерживает форматирование текста. Создайте его, установив свойство [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/). Когда вы преобразуете экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) в экземпляр [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), HTML-тело преобразуется в RTF. Таким образом, форматирование тела электронного письма сохраняется.

Следующий пример создает файл MSG с телом в формате RTF. В нем есть один заголовок, а также жирный и подчеркнутый текст, примененные в HTML-теле. Это форматирование сохраняется при преобразовании HTML в RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

## **Сохранение Сообщения в Статусе Черновика**

Электронные письма сохраняются как черновики, когда кто-то начинает их редактировать, но хочет вернуться к ним, чтобы закончить позже. Aspose.Email поддерживает сохранение электронных сообщений в статусе черновика путем установки флага сообщения. Ниже приведен пример кода для сохранения электронного сообщения Outlook (MSG) как черновика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}

## **Сжатие RTF при установке тела MAPI сообщения**

> **_ПРИМЕЧАНИЕ:_** Процесс сжатия может замедлить производительность при создании сообщений. Поняв этот факт и настроив флаг сжатия в зависимости от конкретных требований и компромисса между размером файла и производительностью, разработчики могут эффективно управлять созданием файлов MSG и PST при работе с электронными сообщениями.

В этом разделе вы узнаете, как использовать сжатие RTF при установке тела сообщения MAPI. Сжатие RTF предназначено для уменьшения размера сообщения, а также полученных файлов PST (Personal Storage Table), которые Microsoft Outlook использует для хранения электронных писем и других данных. Используя сжатие RTF при настройке тела сообщения, разработчики могут уменьшить количество памяти, необходимой для хранения электронных сообщений, или оптимизировать пропускную способность сети при передаче сообщений.

Для этой цели были разработаны два перегруженных метода:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(string content, BodyContentType contentType, bool compression): Этот метод позволяет установить содержимое тела сообщения, используя указанное строковое содержимое и указав тип содержимого тела (например, обычный текст, HTML и т.д.). Необязательный параметр сжатия — это значение, которое указывает, должно ли содержимое быть сжато с помощью сжатия RTF. Если параметр сжатия равен true, содержимое будет сжато, что приведет к уменьшению размера сообщения.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(string content, bool compression): Этот метод специально устанавливает содержимое тела сообщения в формате RTF. Параметр content — это строка, представляющая RTF-содержимое, которое будет установлено в качестве тела сообщения. Как и в предыдущем методе, параметр сжатия определяет, должно ли применяться сжатие RTF к содержимому. Если сжатие равно true, RTF-содержимое будет сжато, чтобы уменьшить размер.

Следующий пример кода показывает, как установить HTML-тело и сохранить его в сжатом виде:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// установить HTML-тело и сохранить его в сжатом виде
// это уменьшит размер сообщения
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

Также есть свойство [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/). Когда это свойство включено, сжатие тела RTF применяется при преобразовании MailMessage в MapiMessage, в результате чего размер файла MSG становится меньше. Это показано в следующем примере кода:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```