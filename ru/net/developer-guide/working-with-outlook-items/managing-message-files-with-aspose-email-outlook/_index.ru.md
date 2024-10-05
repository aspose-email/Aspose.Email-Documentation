---
title: "Управление файлами сообщений с Aspose.Email.Outlook"
url: /ru/net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Получение типа элемента MAPI**

Перечисление [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) представляет тип элемента MAPI, который может быть явно преобразован в объект соответствующего класса, производного от интерфейса [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface). Таким образом, пользователи могут избежать проверки значения свойства [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) перед преобразованием сообщения.

В следующем примере кода показано, как определить тип элемента для преобразования:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Несоответствующий тип. MapiMessage не может быть преобразован в соответствующий тип элемента.
        // Просто используйте в формате MSG.
        case MapiItemType.None:
            break;
        // Электронное сообщение. Преобразование не требуется.
        case MapiItemType.Message:
            break;
        // Элемент контакта. Может быть преобразован в MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // Элемент календаря. Может быть преобразован в MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // Распределительный список. Может быть преобразован в MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // Запись журнала. Может быть преобразована в MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // Заметка. Может быть преобразована в MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // Элемент задачи. Может быть преобразован в MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```
## **Сохранение электронной почты в формате HTML**

Aspose.Email позволяет сохранять ресурсы электронной почты с относительными путями при экспорте сообщений в формат HTML. Эта функция предоставляет большую гибкость в том, как ресурсы связаны в выходном HTML-файле, что упрощает обмен и отображение сохраненных электронных писем на различных системах. Чтобы сохранить ресурсы с относительными путями, используйте свойство [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/). Значение свойства по умолчанию - false (ресурсы сохраняются с абсолютными путями). При установке в true ресурсы сохраняются с относительными путями.

HTML-файлы с относительными путями более портативны и могут отображаться правильно независимо от структуры файловой системы хостинг-среды. Вы можете выбирать между абсолютными и относительными путями в зависимости от требований. Вы можете определить пользовательские пути для ресурсов, используя событие [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/).

Следующий пример кода демонстрирует, как **сохранить электронную почту с использованием относительного пути к ресурсам**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
В этом случае ресурсы будут сохранены в папке [html file name]_files, по тому же пути, что и .html файл, а HTML будет ссылаться на ресурсы через относительные пути.

Пример кода ниже демонстрирует, как **сохранить с абсолютным путем к ресурсам**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Как и в первом случае, ресурсы будут сохранены в папке [html file name]_files по умолчанию, но HTML будет ссылаться на ресурсы, используя абсолютные пути.

Используя событие [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), вы можете устанавливать пользовательские относительные или абсолютные пути для ресурсов. При настройке путей с помощью обработчика события [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), и поскольку [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) установлено в true, вы должны назначить относительный путь свойству [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/), чтобы обеспечить правильную ссылку.

Следующий пример кода демонстрирует, как **настроить относительный путь с использованием события ResourceHtmlRendering**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

htmlSaveOptions.ResourceHtmlRendering += (o, args) =>
{
    if (o is AttachmentBase attachment)
    {
	    // Поскольку UseRelativePathToResources = true, вы должны назначить относительный путь свойству PathToResourceFile.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```

## **Преобразование MSG в MIME сообщение**

API Aspose.Email предоставляет возможность преобразования файлов MSG в MIME сообщения с помощью метода [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}

## **Установка времени ожидания для процесса преобразования и загрузки сообщений**

Следующие функции позволят вам установить таймаут в миллисекундах для процесса преобразования и загрузки:

- свойство [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) - ограничивает время в миллисекундах во время преобразования сообщения.

- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - возникает, если время вышло во время преобразования в MailMessage.

- [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - ограничивает время в миллисекундах во время преобразования сообщения.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - возникает, если время вышло во время преобразования в MailMessage.

Ниже приведен пример кода, который показывает, как установить таймаут во время преобразования сообщения:

```cs
var options = new MailConversionOptions();
// Установите таймаут на 5 секунд
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Установите флаг, указывающий, что таймаут был достигнут
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

## **Чтение и запись файла шаблона Outlook (.OFT)**

Шаблоны Outlook очень полезны, когда вы хотите отправлять аналогичное электронное сообщение снова и снова. Вместо того чтобы готовить сообщение с нуля каждый раз, сначала подготовьте сообщение в Outlook и сохраните его как шаблон Outlook (OFT). После этого, когда вам нужно будет отправить сообщение, вы можете создать его из шаблона, экономя время на написание одного и того же текста в теле или заголовке, настройке форматирования и т.д. Класс Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) можно использовать для загрузки и чтения файла шаблона Outlook (OFT). После того как шаблон Outlook загружен в экземпляре класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), вы можете обновить отправителя, получателя, тело, тему и другие свойства. После обновления свойств:

- Отправьте электронное сообщение с помощью класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) или
- Сохраните сообщение в формате MSG и выполните дальнейшие обновления/проверки с помощью Microsoft Outlook.

В приведенных ниже примерах кода мы:

1. Загружаем шаблон с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Обновляем некоторые свойства.
1. Сохраняем сообщение в формате MSG.

Следующий фрагмент кода показывает, как загрузить файл OFT, обновить сообщение и сохранить его в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Сохранение файла MSG Outlook как шаблона**

Следующий фрагмент кода показывает, как сохранить файл MSG Outlook как шаблон.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Определение, является ли MapiMessage OFT или MSG**

При загрузке объекта MapiMessage из файла вам может понадобиться определить, является ли загруженное сообщение файлом шаблона или файлом обычной электронной почты. Используя свойство [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class), вы можете точно определить, является ли электронное сообщение шаблоном или нет. Эта функция может быть полезной при работе и обработке различных типов файлов электронной почты в приложениях и системах.

Пример кода ниже демонстрирует, как определить, является ли MapiMessage OFT или MSG:

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // возвращает false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // возвращает true
```

### **Сохранение MapiMessage или MailMessage в формате OFT**

Класс [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) позволяет задавать дополнительные параметры при сохранении MailMessage или MapiMessage в определенном формате.

Следующий пример кода демонстрирует, как сохранить сообщение в формате OFT:

```cs
// Сохраните MailMessage в формате OFT
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// или альтернативный способ #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// или альтернативный способ #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
}

// Сохраните MapiMessage в формате OFT
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// или альтернативный способ #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// или альтернативный способ #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Управление цифровыми подписями сообщений**

Aspose.Email реализует полный алгоритм объекта электронной почты S/MIME. Это дает API полную мощность для сохранения цифровых подписей при преобразовании сообщений между форматами.

### **Сохранение подписи при преобразовании из EML в MSG**

Aspose.Email сохраняет цифровую подпись при преобразовании из EML в MSG. Следующий фрагмент кода показывает, как преобразовать из EML в MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Преобразование S/MIME сообщений из MSG в EML**

Aspose.Email сохраняет цифровую подпись при преобразовании из MSG в EML, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Проверка подписи защищенных электронных писем**

Для проверки подписи объектов MapiMessage доступны следующие функции:

- класс [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) для проверки подписи защищенных электронных писем.
- класс [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) для хранения результатов проверки.
- метод [SecureEmailManager.CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3).
- метод [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4).
- метод [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5).

Ниже приведен пример кода, показывающий, как реализовать функции в вашем проекте:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions());
var result = new SecureEmailManager().CheckSignature(msg);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MapiMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

### **Удаление подписи из MapiMessage**

Для лучшей совместимости используется метод [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) и свойство [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) для удаления цифровой подписи из сообщения.

Следующий фрагмент кода показывает, как реализовать эти функции в вашем проекте:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```
## **Расшифровка MapiMessage с помощью сертификата**

Если у вас есть зашифрованные сообщения MAPI и вам необходимо расшифровать их с помощью закрытого ключа, хранящегося в сертификате, следующие функции Aspose.Email могут быть полезными:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Получает значение, указывающее, зашифровано ли сообщение.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Расшифровывает это сообщение (метод ищет текущего пользователя и сертификаты на компьютере для соответствующего сертификата и закрытого ключа).
- [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Расшифровывает это сообщение с сертификатом.

Следующий фрагмент кода показывает, как работать с зашифрованными сообщениями MAPI:

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Установка цветовой категории для файлов MSG Outlook**

Цветовая категория помечает электронное сообщение как важное или относящееся к какой-либо категории. Microsoft Outlook позволяет пользователям назначать цветовые категории для различения электронных писем. Для работы с цветовой категорией используйте [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). Он содержит функции, такие как [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) и [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) принимает [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) и строку цветовой категории, например, "Фиолетовая категория" или "Красная категория" в качестве аргументов.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) принимает [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) и строку цветовой категории, которую необходимо удалить из сообщения.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) используется для удаления всех цветовых категорий из сообщения.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) используется для извлечения всех цветовых категорий из конкретного сообщения.

Следующий пример выполняет следующие задачи:

1. Добавляет цветовую категорию.
2. Добавляет ещё одну цветовую категорию.
3. Извлекает список всех категорий.
4. Удаляет все категории.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Доступ к информации о последующем обслуживании из файла MSG**

API Aspose.Email предоставляет возможность доступа к информации о последующем обслуживании из отправленного или полученного сообщения. Он может извлекать информацию о прочтении, удостоверении доставки и результатах голосования из файла сообщения.

### **Извлечение информации о прочтении и удостоверении доставки**

Следующий фрагмент кода показывает, как извлекать информацию о прочтении и удостоверении доставки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Создание сообщений пересылки и ответа**

API Aspose.Email предоставляет возможность создания и форматирования сообщений пересылки и ответа. Классы [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) и [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) API используются для создания сообщений Ответа и Пересылки соответственно. Сообщение Ответа или Пересылки может быть задано для создания с использованием любого из режимов перечисления [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/). Это перечисление имеет следующие значения:

- **OriginalMessageAdditionMode.None** - Исходное сообщение не включается в ответное сообщение.
- **OriginalMessageAdditionMode.Attachment** - Исходное сообщение включается как вложение в ответное сообщение
- **OriginalMessageAdditionMode.Textpart** - Исходное сообщение включается как текст в теле ответного сообщения

### **Создание сообщения ответа**

Следующий фрагмент кода демонстрирует, как создать сообщение ответа.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Создание сообщения пересылки**

Следующий фрагмент кода демонстрирует, как создать сообщение пересылки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}