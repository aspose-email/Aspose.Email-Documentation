---
title: "Создание и сохранение файлов MSG"
url: /ru/net/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email поддерживает создание файлов сообщений Outlook (MSG). В этой статье объясняется, как:

- Создавайте сообщения MSG.
- Создавайте сообщения MSG с вложениями.
- Создайте сообщение MSG с телом RTF.
- Сохраните сообщение как черновик.
- Работа со сжатием тела.
 
## **Создание и сохранение сообщений Outlook**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс имеет [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) метод, позволяющий сохранять файлы Outlook MSG на диск или в потоковом режиме. Приведенные ниже фрагменты кода создают экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс, задайте такие свойства, как from, to, subject и body. [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) метод принимает имя файла в качестве аргумента. Кроме того, сообщения Outlook можно создавать с помощью [сжатый корпус RTF]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) используя [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). Для настройки создайте новое приложение Windows и добавьте ссылку на dll Aspose.Email в проект.

1. Создайте новый экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс и задайте свойства From, To, Subject и Body.
2. Позвоните [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) метод, который принимает объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) тип. The [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) метод преобразует [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Позвоните [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) метод сохранения файла MSG.

Напишите следующий код в событии нажатия кнопки управления приложением Windows.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Создание файлов MSG с вложениями**

[В приведенном выше примере](https://docs.aspose.com/email/ru/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), мы создали простой файл MSG. Aspose.Email также поддерживает сохранение файлов сообщений с вложениями. Все, что вам нужно сделать, это добавить вложения в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр. Добавьте вложения, вызвав *Add()* метод на [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) коллекция. Добавьте список в форму, созданную выше, и добавьте две кнопки, по одной для добавления и удаления вложений. Приложение, добавляющее приложения, работает следующим образом:

1. Когда **Добавить вложение** кнопка нажата, **Диалог «Открыть файл»** отображается, чтобы помочь пользователям найти и выбрать вложение.
2. После выбора файла полный путь добавляется в список.
3. При создании файла MSG пути к вложениям извлекаются из списка и добавляются в [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) collection.

Напишите следующий код в поле **Добавить вложение** событие нажатия кнопки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

Когда **Удалить вложение** кнопка нажата, удалите выбранные элементы из списка. Напишите следующий код в событие нажатия кнопки «Удалить вложение».

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Добавьте код для добавления вложений в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр. Окончательный код функции Write Msg написан следующим образом.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Создание файлов MSG с помощью тела RTF**

С помощью Aspose.Email можно также создавать файлы сообщений Outlook (MSG) с телами RTF. Тело RTF поддерживает форматирование текста. Создайте его, установив [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) имущество. Когда вы конвертируете [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) Например, тело HTML преобразуется в RTF. Таким образом, форматирование тела письма сохраняется.

В следующем примере создается файл MSG с телом RTF. В тексте HTML используется один заголовок, полужирный шрифт и подчеркивание. Это форматирование сохраняется при преобразовании HTML в RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

## **Сохранение сообщения в статусе черновика**

Письма сохраняются как черновики, когда кто-то начал их редактировать, но хочет вернуться к ним, чтобы завершить их позже. Aspose.Email поддерживает сохранение сообщений электронной почты в черновом статусе, установив флаг сообщения. Ниже приведен пример кода для сохранения сообщения электронной почты Outlook (MSG) в виде черновика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}

## **Сжатие RTF при настройке тела сообщения MAPI**

> **_NOTE:_** Процесс сжатия может снизить производительность при создании сообщений. Понимая этот факт и настроив флаг сжатия в соответствии с конкретными требованиями и компромиссом между размером файла и производительностью, разработчики могут эффективно управлять созданием файлов MSG и PST при работе с сообщениями электронной почты.

В этом разделе вы узнаете, как использовать сжатие RTF при настройке тела сообщения MAPI. Сжатие RTF предназначено для уменьшения размера сообщения, а также получаемых файлов PST (Personal Storage Table), которые Microsoft Outlook использует для хранения сообщений электронной почты и других данных. Используя сжатие RTF при настройке тела сообщения, разработчики могут уменьшить объем памяти, необходимый для хранения сообщений электронной почты, или оптимизировать пропускную способность сети при передаче сообщений.

Для этого были разработаны два перегруженных метода:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(строковое содержимое, bodyContentType ContentType, сжатие bool): этот метод позволяет задать содержимое текста сообщения, используя указанное строковое содержимое и указав основной текст ContentType (например, обычный текст, HTML и т. д.). Необязательный параметр сжатия — это значение, указывающее, следует ли сжимать содержимое с помощью сжатия RTF. Если параметр сжатия имеет значение true, содержимое будет сжато, в результате чего размер сообщения уменьшится.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(строковое содержимое, сжатие bool): этот метод специально задает содержимое тела сообщения в формате RTF. Параметр content представляет собой строку, представляющую содержимое RTF, которое будет задано в качестве тела сообщения. Как и в предыдущем методе, параметр сжатия определяет, следует ли применять сжатие RTF к содержимому. Если сжатие верно, содержимое RTF будет сжато для уменьшения размера.

В следующем примере кода показано, как задать html-тело и сохранить его сжатым:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

Существует также [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/) имущество. Если это свойство включено, во время преобразования MailMessage в MapiMessage применяется сжатие текста RTF, что приводит к уменьшению размера файла MSG. Это показано в примере кода ниже:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```
