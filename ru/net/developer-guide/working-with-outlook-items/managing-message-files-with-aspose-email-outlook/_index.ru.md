---
title: "Управление файлами сообщений с помощью Aspose.Email.Outlook"
url: /ru/net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Получение типа элемента MAPI**

The [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) enum представляет собой тип элемента MAPI, который можно явно преобразовать в объект соответствующего класса, производный от [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface)интерфейс. Таким образом, пользователи могут избежать проверки [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) значение свойства до преобразования сообщения.

В следующем примере кода показано, как определить тип конвертируемого элемента:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Non-supported type. MapiMessage cannot be converted to an appropriate item type.
        // Just use in MSG format.
        case MapiItemType.None:
            break;
        // An email message. Conversion isn't required.
        case MapiItemType.Message:
            break;
        // A contact item. Can be converted to MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // A calendar item. Can be converted to MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // A distribution list. Can be converted to MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // A Journal entry. Can be converted to MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // A StickyNote. Can be converted to MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // A Task item. Can be converted to MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```
## **Сохранение электронной почты в формате HTML**

Aspose.Email позволяет сохранять ресурсы электронной почты с относительными путями при экспорте сообщений в формат HTML. Эта функция обеспечивает большую гибкость при связывании ресурсов в выходном HTML-файле, упрощая обмен и отображение сохраненных писем в разных системах. Чтобы сохранить ресурсы с относительными путями, используйте [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) имущество. Значение свойства по умолчанию равно false (ресурсы сохраняются с абсолютными путями). Если установлено значение true, ресурсы сохраняются по относительным путям.

HTML-файлы с относительными путями более портативны и могут корректно просматриваться независимо от файловой структуры среды хостинга. В зависимости от требований можно выбирать между абсолютными и относительными путями. Вы можете определить собственные пути к ресурсам, используя [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) event.

В следующем примере кода показано, как **сохранить электронное письмо с относительным путем к ресурсам по умолчанию**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
В этом случае ресурсы будут сохранены в папке [html file name] _files по тому же пути, что и файл HTML, а HTML-код будет ссылаться на ресурсы по относительным путям.

В приведенном ниже примере кода показано, как **сэкономьте с абсолютным путем к ресурсам**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Как и в первом случае, ресурсы по умолчанию сохраняются в папке [html file name] _files, но HTML-код будет ссылаться на ресурсы с использованием абсолютных путей.

Используя [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) событие, вы можете установить собственные относительные или абсолютные пути для ресурсов. При настройке путей с помощью [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) обработчик событий, и так как [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) установлено значение true, вы должны назначить относительный путь к [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/) свойство, обеспечивающее правильную ссылку.

В следующем примере кода показано, как **настраиваемый относительный путь с использованием события ResourceHTMLRendering**

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
	    // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```


## **Преобразование MSG в сообщение MIME**

Aspose.Email API предоставляет возможность преобразования файлов MSG в сообщения MIME с помощью [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage) method.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}


## **Настройка тайм-аута для процесса преобразования и загрузки сообщений**

Следующие функции позволят вам установить тайм-аут в миллисекундах для процесса преобразования и загрузки:

- [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) свойство — ограничивает время преобразования сообщения в миллисекундах.

- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Повышается, если время преобразования в MailMessage истекло.

- [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Ограничивает время преобразования сообщения в миллисекундах.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Повышается, если время преобразования в MailMessage истекло.

В приведенном ниже примере кода показано, как установить тайм-аут при преобразовании сообщения:

```cs
var options = new MailConversionOptions();
// Set the timeout to 5 seconds
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Set a flag indicating the timeout was reached
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

## **Чтение и запись файла шаблона Outlook (.OFT)**

Шаблоны Outlook очень полезны, если вы хотите снова и снова отправлять одно и то же сообщение электронной почты. Вместо того чтобы каждый раз готовить сообщение с нуля, сначала подготовьте сообщение в Outlook и сохраните его как шаблон Outlook (OFT). После этого каждый раз, когда вам нужно отправить сообщение, вы можете создать его на основе шаблона, сэкономив время на написании того же текста в тексте или теме письма, настройке форматирования и т. д. Адрес электронной почты Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс можно использовать для загрузки и чтения файла шаблона Outlook (OFT). Как только шаблон Outlook будет загружен в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс, вы можете обновить отправителя, получателя, текст, тему и другие свойства. После обновления свойств:

- Отправьте электронное письмо, используя [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) класс или
- Сохраните сообщение как MSG и выполните дальнейшие обновления/проверку с помощью Microsoft Outlook.

В приведенных ниже примерах кода мы:

1. Загрузите шаблон, используя [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Обновите некоторые свойства.
1. Сохраните сообщение в формате MSG.

В следующем фрагменте кода показано, как загрузить файл OFT, обновить сообщение и сохранить его в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Сохранение MSG-файла Outlook в качестве шаблона**

В следующем фрагменте кода показано, как сохранить файл Outlook MSG в качестве шаблона.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Определите, является ли сообщение MapiMessage OFT или MSG**

При загрузке объекта MapiMessage из файла вам может потребоваться определить, является ли загруженное сообщение файлом шаблона или обычным файлом электронной почты. Используя [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) собственность [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) класс, вы можете точно определить, является ли электронное письмо шаблоном или нет. Эта функциональность может быть полезна при обработке и обработке различных типов файлов электронной почты в приложениях и системах.

В приведенном ниже примере кода показано, как определить, является ли сообщение MapiMessage OFT или MSG:

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // returns false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // returns true
```

### **Сохранение сообщения MapiMessage или MailMessage в формате OFT**

The [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) класс позволяет указать дополнительные параметры при сохранении MailMessage или MapiMessage в определенном формате.

В следующем примере кода показано, как сохранить сообщение в формате OFT:

```cs
// Save the MailMessage to OFT format
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);

}

// Save the MapiMessage to OFT format
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Управление сообщениями с цифровой подписью**

Aspose.Email реализует полный алгоритм объекта электронной почты S/MIME. Это дает API полную возможность сохранять цифровые подписи при преобразовании сообщений между форматами.

### **Сохранение подписи при преобразовании из EML в MSG**

Aspose.Email сохраняет цифровую подпись при преобразовании из EML в MSG. В следующем фрагменте кода показано, как конвертировать из EML в MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Преобразование сообщений S/MIME из MSG в EML**

Aspose.Email сохраняет цифровую подпись при преобразовании из MSG в EML, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Проверка подписи защищенных электронных писем**

Доступны следующие функции для проверки подписи объектов MapiMessage.

- [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) класс для проверки подписи защищенных писем.
- [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) класс для хранения результатов проверки.
- [Защищенный менеджер электронной почты. Проверьте подпись (сообщение MAPI)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) method.
- [Защищенный менеджер электронной почты. Проверьте подпись (сообщение MAPI, сертификат X509 Certificate 2 для расшифровки)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) method.
- [Secure Email Manager. Проверьте подпись (сообщение MAPI, сертификат X509 Certificate2 для расшифровки, хранилище X509 Store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) method.

В приведенном ниже примере кода показано, как реализовать эти функции в вашем проекте:

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

### **Удаление подписи из сообщения MapiMessage**

Для лучшей совместимости [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) метод и [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) свойство используется для удаления цифровой подписи из сообщения.

В следующем фрагменте кода показано, как реализовать эти функции в своем проекте:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```
## **Расшифруйте сообщение MAPImessage с помощью сертификата**

Если у вас есть зашифрованные сообщения MAPI и вам нужно расшифровать их с помощью закрытого ключа, хранящегося в сертификате, вам могут пригодиться следующие функции Aspose.Email:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Получает значение, указывающее, зашифровано ли сообщение.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Расшифровывает это сообщение (метод ищет у текущего пользователя и компьютера My stores соответствующий сертификат и закрытый ключ).
- [Сообщение MAPI. Расшифровка (сертификат X509 Certificate2)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Расшифровывает это сообщение с помощью сертификата.

В следующем фрагменте кода показано, как работать с зашифрованными сообщениями MAPI:

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Настройка цветовой категории для файлов Outlook MSG**

Цветовая категория обозначает сообщение электронной почты, относящееся к какой-либо важности или категории. Microsoft Outlook позволяет пользователям назначать цветовые категории для различения писем. Для обработки цветовой категории используйте [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). Он содержит такие функции, как [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) and [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) и строку цветовой категории, например «Фиолетовая категория» или «Красная категория» в качестве аргументов.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) и строку цветовой категории, которую нужно удалить из сообщения.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) используется для удаления всех цветовых категорий из сообщения.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) используется для извлечения всех цветовых категорий из определенного сообщения.

В следующем примере выполняются задачи, указанные ниже:

1. Добавьте цветовую категорию.
1. Добавьте еще одну цветовую категорию.
1. Получите список всех категорий.
1. Удалить все категории.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Доступ к последующей информации из файла MSG**

Aspose.Email API предоставляет возможность доступа к последующей информации из отправленного или полученного сообщения. Он может извлекать информацию о прочтении, доставке, прочтении и результатах голосования из файла сообщения.

### **Получение информации о прочтении и получении**

В следующем фрагменте кода показано, как получить информацию о прочтении и получении.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Создание сообщений для пересылки и ответа**

Aspose.Email API предоставляет возможность создавать и форматировать сообщения для пересылки и ответа. [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) классы API используются для создания сообщений Reply и Forward соответственно. Можно указать, что сообщение «Ответить» или «Переслать» можно создать с помощью любого из режимов [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/) перечисление. Это перечисление имеет следующие значения:

- **OriginalMessageAdditionMode.None** - Исходное сообщение не включено в ответное сообщение.
- **OriginalMessageAdditionMode.Attachment** - Исходное сообщение включено в ответное сообщение в виде вложения
- **OriginalMessageAdditionMode.Textpart** - Исходное сообщение включено в виде текста в текст ответного сообщения

### **Создание ответного сообщения**

В следующем фрагменте кода показано, как создать ответное сообщение.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Создание пересылающего сообщения**

В следующем фрагменте кода показано, как создать сообщение для пересылки.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}
